---
permalink: /about/
title: "About"
header:
  overlay_image: /assets/images/unsplash/hello-WHUDOzd5IYU.jpg
  overlay_color: "#333"
  caption: "Photo credit: [**Unsplash**](https://unsplash.com/photos/WHUDOzd5IYU)"
excerpt: "C++를 주 언어로 사용하는 멀티 플랫폼을 지원하는 데스크탑 3D 응용프로그램 개발자입니다. GUI 프로그램 개발시 C++ 개발 편의성의 한계로 인해 종종 .NET으로 외도를 자주합니다. "
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

C++를 주 언어로 사용하는 멀티 플랫폼을 지원하는 데스크탑 3D 응용프로그램 개발자입니다. GUI 프로그램 개발시 C++ 개발 편의성의 한계로 인해 종종 .NET으로 외도를 자주합니다. 

> 언어적으로 바인딩이 있고 없고의 차이는 GUI 프로그램을 개발하는 사람에게는 아주 큰 차이가 있다고 생각합니다. 
>> 물론 C++용 바인딩 라이브러리가 있는것은 알고 있지만, 개인적으로 무겁고 범용적이지 않다 생각하여 사용하지 않습니다.
>
> 대신 대체할 만한 코드를 직접 만들어서 꽤 만족스럽게 사용하고 있습니다. 조만간 이 곳을 통해 공유하고자 합니다.

최근 멀티 플랫폼 응용프로그램 제작을 위해 .NET 6 에서 제공하는 Maui를 관심있게 지켜보고 있으나, Linux에 대한 지원이 없어 아마도 Uno를 주력으로 사용할 것 같습니다.

> 하지만 CAE 분야에서 적어도 내가 함께 일했던 분들은 아직도 .NET의 실행 속도를 믿지 못하고, 예전부터 가지고 있던 코드들이 C++로 된 경우가 많다 보니 C++ 기반의 개발을 선호합니다.

서버 프로그래밍은 현재 .NET 6 Core를 기반으로 하는 C#과 구글의 Go 언어에 많은 관심을 가지고 있습니다.

최근에는 C++를 적극 활용할 수 있는 WebAssembly에 많은 관심을 가지고 있습니다.

## 주요 사용 기술
과거에 주로 [MFC](https://docs.microsoft.com/cpp/mfc)를 기반으로 하는 윈도우용 [CAE](https://en.wikipedia.org/wiki/Computer-aided_engineering) 프로그램을 개발해 오다가, 트렌드에 어울리는 [GUI](https://ko.wikipedia.org/wiki/%EA%B7%B8%EB%9E%98%ED%94%BD_%EC%82%AC%EC%9A%A9%EC%9E%90_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4)를 위해 Codejock사의 [XTP](https://codejock.com/products/toolkitpro/)를 오랜기간 사용해 왔으며, 이 후 맥과 리눅스 지원을 위해 [Qt](https://www.qt.io/)를 도입하여 멀티 플랫폼을 지원하는 프로그램을 주로 개발해 왔습니다.

그래픽 엔진은 상황에 따라 간단한 그래픽 처리는 [OpenGL](https://www.opengl.org/)을 기반으로 직접 라이브러리를 구성하여 사용 하고, 좀 더 전문적이고 다양한 플랫폼 지원과 안정적인 운영을 위해서는 [Ogre3D](https://www.ogre3d.org/)를 사용 하고, 수치해석 또는 시뮬레이션을 위한 CAE 분야에서는 [VTK](https://vtk.org/)를 활용하여 다양한 결과물을 생성하도록 하였습니다.

관련하여 비슷한 분야에서 제품 개발을 위한 전반적인 컨설팅이 필요하신 분들께 여러 부분에서 많은 도움을 드리고 있습니다.

## 서버 구성 및 운영
개인 홈 서버 운영을 위해 직접, 웹호스팅, VPS등 여러가지 시험을 해보다 맘에 드는 솔루션을 찾지못해 방황하다가.. 최근 라즈베리파이4를 클러스터로 운영하는 것을 보고 따라서 구축을 한 후 너무 맘에 들어서 행복해 하고 있습니다.

그래서 이 사이트를 통해 라즈베리파이4 클러스터 및 쿠버네티스, 도커 스웜에 관한 이야기도 함께 다루고자 합니다. 아마도 CI/CD, DevOps, Faas, Minecraft등등 다룰 이야기가 많을 것 같습니다. ^^

## 이 사이트는
Github Pages를 통해 제공되며, Jekyll + minimal-mistakes theme를 사용하여 만들어졌습니다.