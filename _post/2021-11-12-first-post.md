---
title: "Github Pages 개설"
date: 2021-11-12T12:03:47+09:00
last_modified_at: 2021-11-12T12:03:47+09:00
header:
  overlay_image: "/assets/images/unsplash/github-yancy-min.jpg"
  overlay_filter: 0.5
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/842ofHC6MaI)"
categories:
  - Github Pages
tags:
  - Github Pages
  - Jekyll
  - Markdown
excerpt: "Github Pages를 선택한 이유와 Git, Markdown을 이용한 응용법에 대한 생각을 정리하였습니다."
---

새롭게 블로그 운영을 위해 Github Pages를 기반으로 하는 정적 사이트를 만들었습니다.

이 포스트는 왜 Github Pages를 선택하게 되었는지에 대한 생각입니다.

## 어떻게 데이터를 유지할 수 있을까?

개인적으로 블로그 데이터에 대한 유지 문제로 인해 항상 많은 고민이 있었습니다.

* 만약 블로그 서비스 업체가 없어지거나 내가 서비스 업체가 맘에 들지 않아 옮겨야 하는 경우
* VPS 또는 자체 서버에 워드프레스등으로 직접 호스팅을 하다 데이터를 이전해야 하는 경우

## Git 그리고 Markdown

기존에 개발 할 때와 동일하게 git 저장소에 마크다운 파일을 추가하고 Github Pages에서 이를 Jekyll을 통해 정적사이트로 변환해서 사이트를 구축해 주는 것을 알게되었고, 필요하면 외부에서 해당 Markdown 파일을 불러들여 운영할수도 있다는 것을 알게되었습니다.

예를들어 WordPress에서는 Plugin을 통해 Import 하거나, `Asp.net Core` 에서도 비슷한 지원 모듈을 통해 사이트를 구축할 수 있음을 확인하게 되었습니다.

즉, 블로그 페이지나 포스팅 원문을 git 저장소에 그대도 유지한채 Github Pages를 통해 기본 사이트를 운영하고, 필요하면 별도의 동적사이트와 연동시켜서 혼용을 할 수도 있고, 무엇보다 원본을 그대로 유지한채 사용하기 때문에 추후에 다른 형태의 사이트로 변환을 하는데 있어서도 아무런 문제가 없는 버전관리가 가능한 파일 구조를 취하기에 데이터베이스에 있는 데이터를 관리하는 것보다는 훨씬 매력적이게 다가왔습니다.

## 다짐

앞으로 이 사이트를 통해 저의 여러가지 지식과 경험을 정리할 예정입니다.
누군가에게 가치가 있는 사이트가 될 수 있도록 노력하겠습니다.