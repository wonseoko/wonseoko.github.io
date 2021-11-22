---
title: "Jekyll Theme: minimal-mistakes"
date: 2021-11-12 12:03:47 +0900
last_modified_at: 2021-11-22 19:42:36 +0900
header:
  teaser: /assets/images/unsplash/mistake-52jRtc2S_VE.jpg
  overlay_image: /assets/images/unsplash/mistake-52jRtc2S_VE.jpg
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/52jRtc2S_VE)"
categories:
  - Blog
tags:
  - jekyll
  - Jekyll Theme
  - Liquid
  - Minimal Mistakes
  - YAML Front Matter
gallery_home:
  - url: /assets/images/owonseok/capture-home-2021-11-22.jpg
    image_path:  /assets/images/owonseok/capture-home-2021-11-22.jpg
    alt: "2021년 11월 22일 현재 홈페이지 화면"
    title: "2021년 11월 22일 현재 홈페이지 화면"
---

이 포스트는 현재 이 웹사이트에 적용되어 있는 [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes){: target=_blank} 테마를 어떻게 커스터마이징을 했는지에 대해 이야기 합니다.


## Minimal Mistakes란?
Minimal Mistakes는 웹사이트를 멋있게 만들어주는 Jekyll 테마의 한 종류가 되겠습니다. 왜 이 테마를 선택했는지 물어보신다면 무료 오픈 테마중에서 가장 잘 만들어지고 활용성이 높은 여러 Layout을 제공하고 있으니깐요.

물론 완벽하다고 생각되지는 않습니다만, 네 무료인것을 고려하면 아주 훌륭한 테마입니다. 저 보고 직접 HTML + CSS를 이용해서 이런 웹사이트를 만들라고 하면 전 쉽게 만들지 못할 것 같습니다.

하지만 위에서 언급했듯이 Minimal Mistakes는 여러 Layout을 제공해 주는 덕에 자신의 입맛에 맞는 여러 페이지 또는 포스트를 꾸밀수 있습니다. 이를 위해서는 YAML Front Matter라는 것에 대한 이해가 필요합니다.


## YAML Front Matter란?

자세한 내용은 [YAML Front Matter](https://jekyllrb.com/docs/front-matter/) 내용과 검색을 통해 충분히 이해하실 수 있으실 겁니다.

Jekyll에서는 변환 될 웹사이트에 대한 모든 설정을 루트에 있는 _config.yml을 통해 설정하도록 되어 있습니다. 파일 확장자에서 눈치채셨겠지만, 그 설정 파일의 내용은 YAML 형식을 취하고 있습니다. 자세한 내용은 [Jekyll Docs](https://jekyllrb.com/docs/)를 통해 이해하실 수 있습니다.

YAML Front Matter는 사용자가 생성하는 HTML, 마크다운 형식의 페이지 또는 포스트 문서내에서 `---` 으로 시작하고, 끝나는 블럭 사이에 사용하는 YAML 형식을 의미합니다. 

사용자가 각 페이지에서 필요로 하는 값을 선언하면, 이는 Layout의 설정값 보다 우선하게 되며, Layout의 설정값은 _config.yml의 설정값 보다 우선하는 형태를 취하는 것이며 이를 통해 사용자가 원하는 각 페이지의 특성을 정의할 수 있게 되는 것입니다.

YAML Front Matter는 각 페이지, 포스트, Layout등에서 해당 파일의 변수 조건을 선언하는 설정 영역이라 이해하시면 되겠습니다.


## Jekyll의 Layout, Include 소개

Jekyll에서 사용되는 형식중에 루트에 위치한 _layout, _include 폴더는 서로 상반되는 개념의 확장 페이지 모음에 해당합니다.  

Layout은 내가 만드는 페이지에서 단 하나만 선언이 가능하며, 내가 만드는 페이지의 모든 내용을 선언 한 Layout의 '\{\{ content \}\}' 영역에 출력하는 형태로 미리 만들어 놓은 여러 형태에 맞춰 컨텐츠를 출력하는 방식입니다. 현재의 Layout은 상위 Layout을 지정할 수 있고, 그 상위 Layout은 또 자신의 상위 Layout을 지정하는 형태로 확장이 가능합니다.

반면 include는 현재 만드는 페이지의 컨텐츠 중 일부 내용을 원하는 형태로 출력하기 위한 페이지 조각의 개념으로 사용하고 있습니다. 때문에 일반적으로 include해서 사용하는 페이지는 파라미터를 통해 데이터를 전달하고 출력을 하도록 합니다.


## Minimal Mistakes 테마 사용 방법

Minimal Mistakes는 3가지 방식으로 사용을 할 수 있습니다. 
* 젬 기반 설치
* 원격 테마
* 소스에 직접 복사

이중에서 저는 원격 테마 방식을 선택했습니다. 가장 간단하고, 버전업이 되었을때 그 변화에 대응하기가 가장 수월하다 생각되었기 때문입니다. 단, 단점도 존재하는데요 원본을 직접 수정하지 못하기 때문에 발생하는 한계도 있을 것입니다.

다음에서는 어떻게 이를 극복했는지에 대해 소개하고자 합니다.


## 시작하기전에

이 글을 읽고 계신 분들은 이미 owonseok.com에 접속하셨음을 의미합니다. 아직 초반이라 페이지 수가 많지 않지만, 다음과 같은 홈페이지 화면과 몇 개의 포스트 목록을 보고 계실 것입니다. 

{% include gallery id="gallery_home" caption="2021년 11월 22일 현재 홈페이지 화면" %}

참고로 위 화면은 minimal mistakes에서 제공하는 예제 포스트가 포함 된 화면입니다. 예시를 위해 포함되었습니다.

이 화면에서 보여드리는 목록은 현재 minimal mistakes에서 제공하는 layout이 아닙니다. 때문에 사용자가 직접 구성을 해야 만 합니다.


## 시작해봅시다

먼저 Jekyll에서 사용자 정의가 가능한 부분과 관련 된 폴더에 대해서 이해를 하셔야 합니다. 

이 웹사이트를 기준으로 설명드리면, 우선 테마 자체는 리모트 테마를 사용하고 있고 기반 코드는 [minimal-mistakes/docs](https://github.com/mmistakes/minimal-mistakes/tree/master/docs)를 루트로 하고 있습니다.

절대 [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)가 루트가 아닙니다. 그 아래 docs를 루트로 사용하고 있습니다. 이는 리모트 테마로 설정을 했기 때문입니다.

여러 분들이 저를 따라 만들고자 하신다면 저 처럼 docs 이하 부분을 여러분의 저장소 루트에 복사하시면 됩니다.

참고로 현재 이 웹사이트의 코드는 당연하게도 [제 Github 저장소](https://github.com/owonseok/owonseok.github.io)를 통해 확인 가능합니다.
{: .notice--info}

초기 상태에는 _include 폴더나 assets/css 폴더가 존재하지 않습니다. 네.. 눈치채셨나요? 우리는 _include, _layout, /assets/css 폴더에 별도의 파일을 추가하여 기존 Layout이나 CSS 스타일 값을 재정의 해서 사용 할 것입니다. Jekyll에서는 이 사용자 정의 폴더의 내용을 빌드시 참조하여 원 소스의 내용과 통합 시켜줍니다.

이 중에서 우리가 손을 대야 하는 부분은 [/assets/css/main.scss](https://github.com/owonseok/owonseok.github.io/blob/main/assets/css/main.scss) 파일입니다. 파일 내용을 보시면 아시겠지만 기존 소스에서 정의 된 부분 중 수정을 필요로 하는 부분을 다시 재 정의 한 것입니다.

설명은 파일내의 주석으로 확인하시기 바랍니다.


## Header Overlay Image 활용하기

minimal mistakes에서 가장 매력이 있는 부분은 아마도 [Header Overlay Image](https://mmistakes.github.io/minimal-mistakes/layout/uncategorized/layout-header-overlay-image/) 라는 기능일 것입니다.

이 기능은 포스트의 요약을 위한 이미지와 요약문, 읽기시간, 작성일 등을 표시해 주는 기능을 합니다. 내가 작성해서 올리는 페이지 또는 포스트에 YAML Front Matter를 잘 정의해 주기만 하면 아주 멋진 페이지를 만들어 주는 기능입니다.

저는 제가 작성하는 대부분의 포스트에 이 기능을 활용해서 멋지게 표시가 되도록 노력을 합니다. 매번 적절한 이미지를 구하는 것이 쉽지 않았지만, minimal mistakes 예제에서 사용되었던 Unsplash를 알고 이를 통해 많은 어려움을 해결했습니다.

아무튼 이 Header Overlay Image의 조각을 찾아 들어가보면 원본 소스에서 [_includes/page_hero.html](https://github.com/mmistakes/minimal-mistakes/blob/master/_includes/page__hero.html) 파일을 확인하실 수 있습니다. 파일 내용을 살펴보면 기본적으로 page.header의 정보를 이용해서 멋진 화면을 만들어 주는 것을 확인 하실 수 있습니다.

저는 이 기능을 별도의 [_includes/excerpt_hero.html](https://github.com/owonseok/owonseok.github.io/blob/main/_includes/excerpt_hero.html) 파일로 복사하고 page.header를 참조하는 대신 include.var 변수를 참조하도록 수정하였습니다. 그리고 목록으로 사용할 것이기 때문에 div corner를 둥글게 만들어 줬습니다. 그리고 [_layouts/home_hero.html](https://github.com/owonseok/owonseok.github.io/blob/main/_layouts/home_hero.html)을 추가하였습니다.

home_hero layout은 기본적으로 paginator.posts를 읽어들여 페이지당 개수에 맞춰 포스트 내용을 excerpt_hero.html를 이용해서 출력하도록 해줍니다.

이 때 해당 포스트 post.header.overlay_image, post.header.image 있을 경우에는 그대로 사용을 하고 없을 경우에는 적절한 랜덤 컬러를 생성시켜 overlay_color를 부여해서 이미지 대신 사용하도록 하였습니다. 위의 갤러리 이미지의 목록 제일 마지막 항목이 그에 해당하는 항목입니다.

그리고 원래 이미지의 Caption으로 활용하던 부분을 카테고리 링크로 사용하도록 하였습니다. 또한 해당 카테고리가 만일 별도의 페이지를 가지고 있는 경우에는 '/categories/#category' 로 이동하던 부분을 '/category' 페이지로 이동하도록 하여 각 카테고리를 위해 만들어진 별도의 멋진 페이지로 이동하도록 하였습니다.

_include, _layout 내의 html 파일을 조작하기 위해서는 [Liquid Template Language](https://shopify.github.io/liquid/)에 대한 이해를 필요로 합니다. 물론 제공 변수는 Jekyll 에서 제공하는 변수를 사용합니다.
{: .notice--info}


## Collection, Posts 이해하기

jekyll에서는 collection, pages, posts 등의 컨텐츠 형태가 있습니다. 이 중에서 collection은 가장 상위의 개념으로 pages, posts를 모두 포함하고 있습니다. 즉, pages, posts 구분없이 전체 데이터를 활용해야 하는경우 site.collections를 활용합니다. site.posts는 site.collections의 일부이지만 jekyll에 의해 post가 하나도 없어도 만들어지는 post를 위한 특수 컬렉션입니다.

주의! site.collections에는 사용자가 정의한 데이터 컬렉션도 포함되기 때문에 label을 잘 활용해서 데이터를 구분해야 합니다.
{: .notice--danger}

일반적으로 포스트에 접근하는 경우에는 site.posts, site.paginator.posts를 사용하며, site.pages를 통해 페이지에 접근합니다. site.data는 _data 폴더 아래 정의한 모든 데이터를 포함하고 있습니다. 우리가 쓰는 웹사이트 네비게이션 데이터와 웹사이트 언어 표시를 위한 데이터등이 이 곳에 정의 되어 있습니다.
{: .notice--info}

다음은 일반적으로 하나의 컬렉션을 등록하는 순서입니다.
* 루트 폴더에 원하는 이름의 컬렉션명을 '_' 으로 시작하도록 작명합니다. minimal mistakes 예제를 기반으로 하셨다면 아마도 `_docs`가 docs 컬렉션이 됨을 이해 하실 수 있습니다.
* 컬렉션에 해당하는 여러 페이지를 해당 폴더에 작성합니다. 그리고 컬렉션의 네비게이션 데이터를 [_data/navigation.yml](https://github.com/owonseok/owonseok.github.io/blob/main/_data/navigation.yml) 파일에 수동으로 작성해 줘야 합니다.
* _config.yml 에서 해당 폴더가 컬렉션임을 등록해 줘야 합니다. 그리고 `output: true`가 선언되어야만 그 안의 페이지가 출력을 할 수 있습니다.
* 네비게이션 데이터가 구성이 되었으면, _config.yml의 `defaults:` 선언 부분에서 해당 컬렉션에 대한 네비를 기본으로 등록하여 해당 컬렉션의 페이지를 볼 때 자동으로 네비가 표시되어 연재를 순회하도록 해줍니다.

아래는 _config.yml 에서 컬렉션을 등록하는 부분입니다.
```yaml
# Collections
collections:
  docs:
    output: true
    permalink: /:collection/:path/
```

다음은 _config.yml 에서 docs 컬렉션에 대한 기본값 지정을 통해 네비가 표시되도록 하고 있습니다.
```yaml
# Defaults
defaults:
  # _docs
  - scope:
      path: ""
      type: docs
    values:
      layout: single
      read_time: false
      author_profile: false
      share: false
      comments: false
      sidebar:
        nav: "docs"
```

주의! 컬렉션은 포스트가 아니기 때문에 포스트 처럼 사용자가 글을 올릴때 마다 자동으로 표시가 되지 않습니다. 이를 위해서는 별도의 출력 페이지를 작성해 줘야만 할텐데 저는 게으르고 재활용이 가능한 방법을 선호하기에 컬렉션을 활용한  방법은 적합하지 않다고 판단했습니다. 추후에 포스트를 정리해서 책 처럼 꾸미게 된다면 그 때는 컬렉션을 활용할 듯 싶습니다.
{: .notice--danger}

이전에 경험했던 내용들을 모두 정리해서 컬렉션으로 한 번에 글을 올리려 하다보니 생각보다 많은 시간이 걸린다는 것을 뒤늦게 깨달았습니다. 헌데 모든 글을 꼭 페이지로 작성해서 한 번에 올릴 필요가 없다고 생각을 한 후로는 어떻게 포스트를 통해서 이 글들을 묶을 것인지에 대한 고민하다 포스트의 카테고리와 defaults를 이용해서 컬렉션처럼 관리가 가능함을 알게되었습니다.


## Post Category 활용법

Jekyll에서 포스트는 기본적으로 _posts 아래 작성을 해야 합니다. 사용자가 각 포스트 파일에서 Front Matter를 통해 포스트 마다 여러개의 카테고리를 지정할 수도 있습니다. 하지만 모든 파일내에 카테고리를 지정하는 것은 별로 능률적으로 보이지 않습니다. 파일이 많아지면 관리에 어려움이 있을 수도 있습니다.

그래서 Jekyll은 폴더로 카테고리를 자동화 해주는 기능이 있습니다. 
* `/cars/_posts/mustang.md` 라고 작성을 하면 mustang.md는 기본적으로 cars라는 카테고리에 포함되는 포스트로 인식됩니다. 
* `/cars/ford/_posts/mustang.md` 라고 작성을 하면 mustang.md는 cars, ford 두 개의 카테고리에 포함되는 포스트로 인식됩니다. 일반적으로 mustang.md의 url은 `/cars/ford/mustang/` 형태를 취하게 됩니다. 물론 mustang.md내에서 Front Matter로 추가 카테고리를 부여하면 그 카테고리까지 포함이 됩니다.
* `/cars/index.md` 라고 작성을 하면 `/cars/`를 나타내는 페이지로 작동을 하게 됩니다.
* `/cars/ford/index.md` 라고 작성을 하면 `/cars/ford/`를 나타내는 페이지로 작동을 하게 됩니다.

`/_posts/cars/ford/mustang.md` 의 경우 별도의 카테고리가 할당되지 않으며, 단지 관리상 편이점만 있을 뿐입니다.
{: .notice--danger}

일반적으로 루트 아래 카테고리 폴더를 만들고 포스트는 그 하위 _posts 안에 위치시키고, index.md or index.html은 해당 경로를 대표하는 페이지로 인식하고, name.md는 하위 페이지로 인식하게 됩니다.

주의! `_`로 시작하는 폴더는 자동으로 컬렉션으로 인식이 됩니다. 물론 설정에서 `_cars`라는 컬렉션에 대한 노출이 지정되기 전까지는 아무런 동작을 하지 않습니다. 때문에 카테코리는 절대 `_`로 시작을 하면 안됩니다. 카테고리가 아닌 컬렉션으로 인식되기 때문입니다.
{: .notice--danger}


## defaults 선언이 중요한 이유

defaults는 정말 많은 부분을 단순화 시켜줄 수 있는 기능입니다. 개인적으로 아쉽게도 [Front Matter Defaults](http://jekyllrb.com/docs/configuration/front-matter-defaults/)에서는 가장 중요한 scope에 대한 설명이 부족하지 않았나 생각되어 집니다.

위에서 제가 컬렉션을 카테고리로 대체할 수 있다고 했던 이유는 이 defaults를 이용해서 특정 카테고리에 대한 네비게이션을 기본으로 지정할 수 있었기 때문입니다.

헌데 Jekyll 문서에서는 이에 대한 설명이 없었고, 저는 똑똑하지 않았기 때문에 이 defaults의 scope를 조작할 수 있음을 이해하는데 오랜시간이 걸렸었습니다.

다시 defaults 부분을 살펴봅시다.
```yaml
# Defaults
defaults:
  # _docs
  - scope:
      path: ""
      type: docs
```
path를 지정하지 않았기 때문에 docs 컬렉션에 해당하는 모든 페이지를 대상으로 합니다.

그렇다면 특정 category post를 지정하려면 어떻게 해야 할까요?
```yaml
# Defaults
defaults:
  # _posts
  - scope:
      path: "category"
      type: posts
```
네.. 그렇습니다. `"category"` 부분에 여러분이 원하는 카테고리를 지정하시면 됩니다.

그럼 다음과 같이 하면 어떻게 될까요?
```yaml
# Defaults
defaults:
  # _posts
  - scope:
      path: "rpi4cluster"
```

rpi4cluster 폴대내의 모든 페이지를 인식하고, 만일 하위에 _posts가 있을 경우 그 안에 있는 포스트들을 rpi4cluster 카테고리 포스트로 분류합니다.

이 웹사이트의 경우 현재 `/rpi4cluster/index.md`, `/rpi4cluster/_posts/*.md` 형태로 구성을 시켜 rpi4cluster  카테고리가 생성 되었고, 그에 대한 네비게이션 데이터를 작성하고, defaults를 통해 모든 rpi4cluster 카테고리에 있는 포스트는 자동으로 네비게이션이 표시되도록 구성되어 있습니다. 그리고 `/rpi4cluster/`에 접속하면 `/rpi4cluster/index.md`를 통해 rpi4cluster를 소개하는 인트로 페이지가 표시되도록 하였습니다.


## 마치며
쉽고 편하게 쓰려고 Jekyll 이라는 것을 통해 웹사이트를 구축하는데 내 입맛에 맞추려면 3가지 언어를 알아야 하다니 참 어렵습니다. 네.. 뭐든지 남과 다르게 만들고 싶다는 생각이 들 때 부터 많은 것을 알아야 하는 것은 변하지 않는것 같습니다.
