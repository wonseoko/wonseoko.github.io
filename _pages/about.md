---
permalink: /about/
title: "About"
header:
  overlay_image: https://source.unsplash.com/random
  #overlay_image: https://source.unsplash.com/1600x900/?christmas
  overlay_filter: 0.4
  caption: "Photo credit: [**Unsplash Source Random**](https://source.unsplash.com)"
excerpt: 이 사이트는 소프트웨어 개발 기술과 서버 운영에 관한 경험담을 주로 다루고 있습니다.
layouts_gallery:
  - url: /assets/images/mm-layout-splash.png
    image_path: /assets/images/mm-layout-splash.png
    alt: "splash layout example"
  - url: /assets/images/mm-layout-single-meta.png
    image_path: /assets/images/mm-layout-single-meta.png
    alt: "single layout with comments and related posts"
  - url: /assets/images/mm-layout-archive.png
    image_path: /assets/images/mm-layout-archive.png
    alt: "archive layout example"
last_modified_at: 2021-11-15 12:23:42 +0900
toc: true
toc_sticky: true
tags:
  - MFC
  - XTP
  - Qt
  - OpenGL
  - Ogre3D
  - VTK
  - Raspberry Pi
  - Kubernetes
  - Docker Swarm
  - MAUI
  - UNO
  - Go
  - Consulting
  - DevOps
  - CI/CD
  - Faas
---

이 사이트는 소프트웨어 개발 기술과 서버 운영에 관한 경험담을 주로 다루고 있습니다.

이 사이트에서 사용하는 대부분의 이미지는 <a href="https://unsplash.com">Unsplash</a>에서 
제공하는 이미지를 사용하고 있으며, 일부는 <a href="https://source.unsplash.com/">Unsplash Source</a>의 랜덤 및 검색 서비스를 통해 제공하고 있습니다.
{: .notice--info}

## 저는 누구?

오랜시간 C++를 주 언어로 사용하며 멀티 플랫폼을 지원하는 데스크탑 3D 응용프로그램을 주로 개발해왔습니다. GUI 프로그램 개발시 C++ 개발 편의성의 한계로 인해 종종 .NET으로 외도를 자주합니다. 

> 개발언어 자체적으로 바인딩이 있고 없고의 차이는 GUI 프로그램을 개발하는 사람에게는 아주 큰 차이가 있다고 생각합니다. 
>> 물론 C++용 바인딩 라이브러리가 있는것은 알고 있지만, 개인적으로 무겁고 범용적이지 않다 생각하여 사용하지 않습니다.
>
> 대신 대체할 만한 코드를 직접 만들어서 꽤 만족스럽게 사용하고 있습니다. 조만간 이 곳을 통해 공유하고자 합니다.

최근 멀티 플랫폼 응용프로그램 제작을 위해 .NET 6 에서 제공하는 Maui를 관심있게 지켜보고 있으나, Linux에 대한 지원이 없어 아마도 Uno를 주력으로 사용할 것 같습니다.

최소한 제가 함께 일했던 CAE 분야의 결정권을 가지신 분들은 예전부터 가지고 있던 코드들이 C/C++로 된 경우가 많다 보니 C++ 기반의 개발을 선호합니다. 그리고 아직도 .NET의 실행 속도를 믿지 못하는 경우가 많습니다.
{: .notice--warning}

최근에는 C++를 적극 활용할 수 있는 WebAssembly에 많은 관심을 가지고 있습니다. 물론 WebAssembly는 여러 언어로 제작이 가능합니다.

서버 프로그래밍은 현재 .NET 6 Core를 기반으로 하는 C#과 구글의 Go 언어에 많은 관심을 가지고 있습니다.

## 주요 사용 기술
과거에 주로 [MFC](https://docs.microsoft.com/cpp/mfc)를 기반으로 하는 윈도우용 [CAE](https://en.wikipedia.org/wiki/Computer-aided_engineering) 프로그램을 개발해 오다가, 트렌드에 어울리는 [GUI](https://ko.wikipedia.org/wiki/%EA%B7%B8%EB%9E%98%ED%94%BD_%EC%82%AC%EC%9A%A9%EC%9E%90_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4)를 위해 Codejock사의 [XTP](https://codejock.com/products/toolkitpro/)를 오랜기간 사용해 왔으며, 이 후 맥과 리눅스 지원을 위해 [Qt](https://www.qt.io/)를 도입하여 멀티 플랫폼을 지원하는 프로그램을 주로 개발해 왔습니다.

그래픽 엔진은 상황에 따라 간단한 그래픽 처리는 [OpenGL](https://www.opengl.org/)을 기반으로 직접 라이브러리를 구성하여 사용 하고, 좀 더 전문적이고 다양한 플랫폼 지원과 안정적인 운영을 위해서는 [Ogre3D](https://www.ogre3d.org/)를 사용 하고, 수치해석 또는 시뮬레이션을 위한 CAE 분야에서는 [VTK](https://vtk.org/)를 활용하여 다양한 결과물을 생성하도록 하였습니다.

관련하여 비슷한 분야에서 제품 개발을 위한 전반적인 컨설팅이 필요하신 분들께 여러 부분에서 많은 도움을 드리고 있습니다.

## 서버 구성 및 운영
개인 홈 서버 운영을 위해 직접, 웹호스팅, VPS등 여러가지 시험을 해보다 맘에 드는 솔루션을 찾지못해 방황하다가.. 최근 라즈베리파이4를 클러스터로 운영하는 것을 보고 따라서 구축을 한 후 너무 맘에 들어서 행복해 하고 있습니다.

그래서 이 사이트를 통해 라즈베리파이4 클러스터 및 쿠버네티스, 도커 스웜에 관한 이야기도 함께 다루고자 합니다. 아마도 CI/CD, DevOps, Faas, Minecraft등등 다룰 이야기가 많을 것 같습니다. ^^

## 취미 생활
초등학생 때 부터 오락실에서 살 정도로 게임을 좋아했습니다. 덕분에 컴퓨터를 좋아하게 되고 고등학교때 C언어 전문학원을 다니고 지금껏 개발자로 살고 있나 봅니다. 그 때는 DOS에서 실행하는 프로그램 만들던 시절이였습니다. 안철수 아저씨가 영웅같이 보이던 시절이었네요;;

성인이 되어서는 World of Warcraft가 출시되어 10년 이상 함께 했던 듯 싶습니다. 와우 특성상 시간 소비가 크고 레이드 준비로 스트레스가 적지 않다보니 지금도 생각은 나지만 놓아준지가 꽤 되었습니다.

PC게임을 버리고 뒤 늦게 콘솔 게임에 입문을 했습니다. 결혼을 하고 아이들이 태어나자 함께 하고 싶은 마음에 XBox에 키넥트 연결해서 저스트댄스도 흔들어 주고 하다가 이제는 초등학생이 된 아이들과 함께 마인크래프트도 하고 던전스도 하고 포르자 호라이즌도 함께 즐기고 있습니다.

조금만 더 크면 함께 좀비도 잡고 피 튀기는 게임들을 즐겨보고 싶습니다. 사실 광고처럼 아이들과 함께 와우가 해보고 싶긴한데 그럴 기회가 올까 궁금하네요 ^^

## 이 사이트는
Github Pages를 통해 제공되며, Jekyll + minimal-mistakes theme를 사용하여 만들어졌습니다.