---
layout: post
title: Swift InterView Question 정리
author: Jinbae
image: "assets/images/swift/Interview.jpeg"
categories: [Swift]
tags: [Swift]
sitemap:
  changefreq: daily
  priority: 1.0
---

iOS 인터뷰를 대비한 정리글 입니다.  
[출처 : JeaSungLEE/iOSInterviewquestions](https://github.com/JeaSungLEE/iOSInterviewquestions)

# 목차
<h1><a href="#iOS">iOS</a></h1>
- [Bounds와 Frame의 차이점](#BoundsFrame)
- [실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.](#realDevice)
- [앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?](#AppLifeCycle)

<h2 id="iOS">iOS</h2>
---
<h1 id="BoundsFrame">ㅁ Bounds와 Frame의 차이점을 설명하시오</h1>
> Bounds와 Frame의 차이는 ***어떠한 좌표계를 기준***으로 하는가에 따라 표현이 달라진다.

### Frame
superView의 좌표계를 기준으로 하여 현재 view의 원점을 나타낸다.

### Bounds
현재 view(자기자신)의 좌표계를 기준으로 원점을 나타낸다.


<h1 id="realDevice">ㅁ 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오.</h1>
simulator에서 할수 있는 것
- iOS 앱의 기본 기능 테스트
- UI 레이아웃 테스트

그 외에는 실제 디바이스에서밖에 동작하지 않는다.
[참고](https://browserstack.com/test-on-ios-simulator)

<h1 id="AppLifeCycle">앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?</h1>
```swift
test
```
- Not Running  
  앱이 실행되지 않은 상태
- Foreground상태
  - Inactive  
    앱이 실행중이지만 아직 아무런 이벤트를 받지 않은 상태
  - Active  
    앱이 실행중이며 현재 이벤트를 받고 있고 발생한 상태
- Background  
  앱이 백그라운드에 있는 상태이지만 여전히 실행되고있는 코드가 있는 상태
- Suspened  
  앱이 백그라운드에 있고 실행되는 코드가 없는 상태