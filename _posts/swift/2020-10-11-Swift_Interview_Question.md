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
- [Scene Delegate에 대해 설명하시오](#SceneDelegate)

<h1><a href="#FP">Functional Programming</a></h1>

- [함수형 프로그래밍이 무엇인지 설명하시오.](#FunctionalProgramming)
- [고차 함수가 무엇인지 설명하시오.](#HighOrderFunction)

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

<h1 id="AppLifeCycle">ㅁ 앱이 foreground에 있을 때와 background에 있을 때 어떤 제약사항이 있나요?</h1>
```swift
application(_:didFinishLaunching:) - 앱이 처음 시작될 때 실행
applicationWillResignActive:       - 앱이 active 에서 inactive로 이동될 때 실행 
applicationDidEnterBackground:     - 앱이 background 상태일 때 실행 
applicationWillEnterForeground:    - 앱이 background에서 foreground로 이동 될때 실행 (아직 foreground에서 실행중이진 않음)
applicationDidBecomeActive:        - 앱이 active상태가 되어 실행 중일 때
applicationWillTerminate:          - 앱이 종료될 때 실행
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

<h1 id="SceneDelegate">ㅁ Scene Delegate에 대해 설명하시오</h1>

<h2 id="FP">Functional Programming</h2>
---

<h1 id="FunctionalProgramming">ㅁ 함수형 프로그래밍이 무엇인지 설명하세요.</h1>

-  함수형 프로그래밍이란 값으로 저장될 수 있고, 인자, return값으로 돌려받을 수 있는것  
- 함수가 1급 시민인 언어
  > 1급 시민(1급 객체)이란 다음 조건을 만족하는 객체를 의미  
  > - 변수나 상수에 저장 및 할당 할 수 있어야한다.
  > - 파라미터로 전달 할 수 있어야한다.
  > - 함수(객체)에서 return 할 수 있어야한다.

<h1 id="HighOrderFunction">ㅁ 고차 함수가 무엇인지 설명하시오.</h1>

> 고차함수란?  
  함수의 인자로 함수를 취하거나 결과를 함수로 반환하는 함수  
  대표적으로 map, filter, reduce가 있다.

## map
기존 데이터를 변형하여 새로운 컬렉션을 생성하는 함수

```swift
let names = ["Chirs", "Pino", "Alex"]
let nameArr = names.map { $0 + "'s name" }
print(nameArr)
```

## filter
기존 데이터 값을 필터링하여 추출하는 함수

```swift
let num = [1, 2, 3, 4, 5, 6]
let oddNum = num.filter { $0 % 2 != 0 }
print(odd)  // [1, 3, 5]
```

## reduce
컨테이너 내부 컨텐츠를 하나로 통합하는 함수

```swift
let someNum: [Int] = [2, 8, 15]

let sum: Int = someNUm.reduce(0, {
  (first: Int, second: Int) -> Int in
  return first + second
})
```

## compactMap
1차원 배열에서 nil을 제거하고 옵셔널 바인딩을 하고싶을 때 사용하는 함수

```swift
let num: [Int] = [1, nil, 2, nil, 3]
let result: [Int] = num.compactMap { $0 }
```

## flatMap
2차원 배열을 1차원 배열로 flat하게 만들어주는 함수

```swift
let num: [[Int?]] = [[1, 2, 3], [4, 5, 6], [nil, 7, 8]]
let result = num.flatMap { $0 }.compactMap { $0 }
print(result) // [1, 2, 3, 4, 5, 6, 7, 8]
```