---
title: "CMake에서 find_package(VTK)를 두 번 이상 호출하면 발생하는 오류 대응법"
date: 2022-01-03 18:03:21 +0900
last_modified_at: 2022-01-03 18:03:21 +0900
header:
  teaser: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_image: /assets/images/unsplash/github-842ofHC6MaI.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"
tags:
  - CMake
  - VTK
  - vcpkg
---

vcpkg와 CMake를 사용하여 프로젝트를 구성할 때 find_package로 VTK를 중복 호출할 때 발생하는 에러에 대응하는 방법을 설명합니다.

## 발단

최근 기존에 개발해오던 프로젝트를 vcpkg를 활용하도록 변경 작업을 진행하다보니, 아직은 완전하지 않은 vcpkg의 한계로 인해 Visual Studio 솔루션 만으로는 여러 프로젝트를 vcpkg와 연동해서 작업을 하는 것에는 한계가 발생하더군요.

때문에 CMake로 프로젝트를 구성할 수 밖에 없었고, 그 에 따른 CMake 프로젝트 설정을 하다가 각 프로젝트에서 각각 VTK를 참조하는 상황이 발생되었는데, 이를 루트 CMakeLists.txt에서 add_subdirectory로 각각 불러오는 경우 find_package(VTK)가 중복 호출되면서 에러가 발생함을 확인하게 되었습니다.

해결을 위해 검색을 하다보니 이 문제는 이미 ITK와 VTK가 중복 참조 될 때도 발생이 되는 문제 였으며, 이미 vcpkg 저장소에도 이슈로 등록이 되었던 것이 확인이 되었으나, 1년이 넘은 지금 까지도 패치가 적용되지 않았음이 의아하게 생각되어 집니다.

우선 관련 이슈 내용은 다음을 참조하시기 바랍니다.
> [https://github.com/microsoft/vcpkg/issues/14978#issuecomment-740077047](https://github.com/microsoft/vcpkg/issues/14978#issuecomment-740077047)


## 단순 로컬 패치

사용자 로컬PC의 파일을 패치 할 경우 경로는 다음과 같습니다.
> vcpkg\installed\x64-windows\share\vtk\FindLZ4.cmake

변경 내용
```cmake
# ===== original =====
#
#find_package(LZ4 CONFIG REQUIRED)
#set_target_properties(lz4::lz4 PROPERTIES IMPORTED_GLOBAL TRUE)
#if(NOT TARGET LZ4::LZ4)
#  add_library(LZ4::LZ4 ALIAS lz4::lz4)
#endif()
#
# ===== patched =====
#
find_package(LZ4 CONFIG REQUIRED)
if(NOT TARGET LZ4::LZ4)
  add_library(LZ4::LZ4 INTERFACE IMPORTED)
  target_link_libraries(LZ4::LZ4 INTERFACE lz4::lz4)
endif()
```

사용자 로컬PC의 파일 패치는 단독 사용의 경우에만 임시적으로 사용이 가능하며, 팀원과 공유하거나 영구적 패치를 위해서는 vcpkg 저장소의 내용을 변경해야 합니다.

단, vcpkg에서는 일반적으로 vcpkg 저장소를 포크해서 private한 라이브러리를 추가하거나, 포트 변경 사항을 적용하여 사용하도록 권장하고 있습니다.
{: .notice--warning}


## 저장소 Port 파일 패치

제대로 수정을 적용하기 위해서는 vcpkg를 포크한 후 port 파일을 수정하여 패치를 진행해야 프로젝트를 사용하는 모든 사람이 변경 내용을 반영 받을 수 있게 됩니다.

port 파일 수정은 다음 경로의 패치 파일을 수정해야 합니다.
> vcpkg\ports\vtk\FindLZ4.patch

```patch
diff --git a/CMake/FindLZ4.cmake b/CMake/FindLZ4.cmake
index 8c94e3bcd..ade3f9451 100644
--- a/CMake/FindLZ4.cmake
+++ b/CMake/FindLZ4.cmake
@@ -1,38 +1,5 @@
-find_path(LZ4_INCLUDE_DIR
-  NAMES lz4.h
-  DOC "lz4 include directory")
-mark_as_advanced(LZ4_INCLUDE_DIR)
-find_library(LZ4_LIBRARY
-  NAMES lz4 liblz4
-  DOC "lz4 library")
-mark_as_advanced(LZ4_LIBRARY)
-
-if (LZ4_INCLUDE_DIR)
-  file(STRINGS "${LZ4_INCLUDE_DIR}/lz4.h" _lz4_version_lines
-    REGEX "#define[ \t]+LZ4_VERSION_(MAJOR|MINOR|RELEASE)")
-  string(REGEX REPLACE ".*LZ4_VERSION_MAJOR *\([0-9]*\).*" "\\1" _lz4_version_major "${_lz4_version_lines}")
-  string(REGEX REPLACE ".*LZ4_VERSION_MINOR *\([0-9]*\).*" "\\1" _lz4_version_minor "${_lz4_version_lines}")
-  string(REGEX REPLACE ".*LZ4_VERSION_RELEASE *\([0-9]*\).*" "\\1" _lz4_version_release "${_lz4_version_lines}")
-  set(LZ4_VERSION "${_lz4_version_major}.${_lz4_version_minor}.${_lz4_version_release}")
-  unset(_lz4_version_major)
-  unset(_lz4_version_minor)
-  unset(_lz4_version_release)
-  unset(_lz4_version_lines)
-endif ()
-
-include(FindPackageHandleStandardArgs)
-find_package_handle_standard_args(LZ4
-  REQUIRED_VARS LZ4_LIBRARY LZ4_INCLUDE_DIR
-  VERSION_VAR LZ4_VERSION)
-
-if (LZ4_FOUND)
-  set(LZ4_INCLUDE_DIRS "${LZ4_INCLUDE_DIR}")
-  set(LZ4_LIBRARIES "${LZ4_LIBRARY}")
-
-  if (NOT TARGET LZ4::LZ4)
-    add_library(LZ4::LZ4 UNKNOWN IMPORTED)
-    set_target_properties(LZ4::LZ4 PROPERTIES
-      IMPORTED_LOCATION "${LZ4_LIBRARY}"
-      INTERFACE_INCLUDE_DIRECTORIES "${LZ4_INCLUDE_DIR}")
-  endif ()
-endif ()
+find_package(LZ4 CONFIG REQUIRED)
+if(NOT TARGET LZ4::LZ4)
+  add_library(LZ4::LZ4 INTERFACE IMPORTED)
+  target_link_libraries(LZ4::LZ4 INTERFACE lz4::lz4)
+endif()
\ No newline at end of file
```

수정 할 부분은 맨 아래 부분의 내용이며, 위에 표시해둔 변경 내용을 반영하시면 됩니다.
