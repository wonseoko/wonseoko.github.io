---
title: "Jekyll build시 발생되는 Liquid Template 버그"
header:
  overlay_image: /assets/images/owonseok/unknown-build-failure-of-github-pages.png
  overlay_filter: 0.5
  caption: "Photo credit: O Wonseok"
categories:
  - Blog
tags:
  - Jekyll
  - Liquid
  - Minimal Mistakes
date: 2021-11-13 14:14:18 +0900
last_modified_at: 2021-11-13 14:14:18 +0900
---

Jekyll 사이트 빌드시 특정 문서내에서 일반 문장이나, 주석으로 처리가 되어 있어도 Liquid 명령어가 포함된 경우 빌드시 참조 에러가 발생.

### 증상

Github Pages 자체에서 제공하는 Jekyll 빌드시 오류가 발생되었으나, 아무런 메시지가 나타나지 않음.

### 상황
minimal-mistakes 에서 제공하는 예제 사이트를 기반으로 사이트 구조를 구성한 뒤 예제로 있던 포스트를 제거하고 내가 작성한 포스트를 올리는 과정에서 발생함.

기존 예제 포스트와 내가 추가한 포스트가 함께 있으면 빌드 오류가 발생하지 않으나, 예제 포스트를 제거하면 에러가 발생함.

원인을 찾아보려 하지만 Github Pages 빌드로그에는 아무것도 표시되지 않고 메뉴얼만 참고하라고 나옴. ㅠㅠ

### 로컬에 Jekyll 설치
Ruby 설치, Jekyll 및 관련 Gem 설치후 i18n 에러 발생
직접 Jekyll Build가 불가능 해서 bundle exec jekyll build로 수행.

### 로컬에서 빌드 후 에러확인
다음과 같은 에러 메시지 획득!!
```sh
  Liquid Exception: Could not find post "2010-09-09-post-gallery" in tag 'post_url'. Make sure the post exists and the name is correct. in D:/_git_/owonseok.github.io/_docs/14-helpers.md
             ERROR: YOUR SITE COULD NOT BE BUILT:
                    ------------------------------------
                    Could not find post "2010-09-09-post-gallery" in tag 'post_url'. Make sure the post exists and the name is correct.
```

### 결론
결국 문서내에서 사용하는 Liquid Template의 참조 링크가 빌드시 에러로 출력되었으나, Github Pages 내에서 보고되지 않아 로컬 빌드에서 에러 메시지를 참고하여 해결함.

> 단, 다음 구문을 주석처리 하여도 빌드시 참조하는 버그가 있음을 확인.
```
{% raw %}{% post_url 2010-09-09-post-gallery %}{% endraw %}
```

> 이를 임시적으로 인식하지 못하도록 하기 다음과 같은 식으로 교체함.
```
<% post_url 2010-09-09-post-gallery %>
```