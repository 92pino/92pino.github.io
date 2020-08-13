---
layout: post
title: Git이란 무엇일까?
author: Jinbae
image: "assets/images/github/images.jpg"
categories: [Git]
tags: [Git]
sitemap:
  changefreq: daily
  priority: 1.0
---

오늘은 패스트캠퍼스 IOS스쿨에서 배운 Git을 정리하면서  Git이란 무엇인지? 그리고 Git 사용의 이점이 무엇인지? 사용법은 어떻게 되는지에 대해서 포스팅해보려고 합니다.

먼저,

## Git이란 무엇일까?
(참고 : [https://git-scm.com/book/ko/v2](https://git-scm.com/book/ko/v2) 공식 사이트 한글 번역)

![Git Logo](../../images/git/git_logo.png)

```
프로그램 등의 소스 코드 관리를 위해 2005년에 개발된 분산 버전 관리 시스템(DVCS)
리누스 토르발스가 BitKeeper 유료화에 자극받아 리눅스 커널 프로젝트에 사용하기 위해 개발 네트워크에 접근하거나 중앙 서버에 의존하지 않고도 사용 가능
```
<br>
이러한 Git은 <br>
1. 빠른 속도
2. 단순한 구조
3. 비선형적인 개발(수천 개의 동시 다발적인 브랜치)
4. 완벽한 분산
5. 리눅스 커널 같은 대형 프로젝트에도 유용할 것(속도나 데이터 크기 면에서)

위와 같은 초기 목표를 탄생 이후 아직까지 유지가 되어가고있다.

## 이런 Git을 왜 사용하는것일까?

공식홈페이지에는 다음과 같은 장점들을 가지고 있다.

- Branching and Merging
- Small and fast
- Distributed
- Data assurance
- Staging area
- Free and open source

### ✔︎ Branching and Merging
---

- Git가 다른 버전관리 프로그램들보다 가지는 가장 큰 장점은 branching 모델이다
- Git은 로컬에 다수의 branch를 허용해주며, 각각에 대한 완벽한 독립성을 제공해주며 각 branch는 쉽게 생성/merge/삭제를 할 수 있다.

이러한 기능들로 인해 실험적인 코딩으로 인해 발생하는 오류들을 최소화하고 다시 원점으로 복귀하는 시간을 절약할 수 있다.

### ✔︎ Small and fast
---

Git은 거의 모든 동작들을 로컬에서 우선적으로 실시하기 때문에 서버와 연동하기 위해 네트워크를 타지 않아도 되어서 속도면에서 엄청난 장점이 있다.<br>
그리고 속도와 성능은 git의 초기 목표이기도 하다.

### ✔︎ Distributed
---

모든 버전관리 프로그램들이 제공하는 또 다른 유용한 기능이 바로 어디서든지 checkout, git에서는 clone을 하면 바로 작업이 가능하다는 점이다. 이것은 메인 서버에 소스를 두고 여러 작업 환경에서 동시에 작업을 할 수도 있고, 각각의 작업환경에 따라서 다른 branch도 관리를 할 수 있게 되는 것이다. 각각의 작업환경에서 별도로 작업한 소스들은 언제든지 메인서버로 업로드하고 merge가 가능하며 git 특유의 로컬에서 많은 동작들을 수행하는 특징 때문에 이 분산 환경에서 제공하는 코딩은 더욱더 빛을 발하게 된다.

### ✔︎ Data assurance
---

Git에서 사용하고 있는 데이터 모델은 모든 파일을 확실하게 암호화시켜주고 단 하나의 bit까지도 틀리지 않게 보관해준다. 모든 파일은 체크썸 검사를 하고, 다운을 받을 때에도 다시 실시를 하여 Git에서 모든 bit까지 보장을 해주게 된다. 또한 Git 저장소에 있는 파일이나 commit 메세지를 무단으로 수정하려면 commit할 때 부여하는 commit id가 바뀌기 때문에 내가 commit한 것인지 확실하게 보장할 수 있고, 히스토리 관리에도 유용하다.

### ✔︎ Free and open source
---

Git는 GPLv2 오픈소스 라이센스를 사용해서 무료로 사용할 수 있다.
