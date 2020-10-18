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

<h1><a href="#SWIFT">SWIFT</a></h1>

- [옵셔널이란?](#WhatIsOptional)
- [값타입과 참조타입의 차이는?](#Struct_Class)

<h1><a href="#ARC">ARC</a></h1>

- [ARC란 무엇인가?](#WhatIsARC)
- [Strong, Weak, Unowned 차이](#Strong_Weak_Unowned)
- [](#weakSelf)

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

<h2 id="SWIFT">SWIFT</h2>
---

<h1 id="WhatIsOptional">옵셔널이란?</h1>

> 옵셔널이란 값이 존재할수도 있고, 존재하지 않을수도 있는 값을 뜯한다.  
> ## 옵셔널이 필요한 이유 ##
> - Swift의 안정성을 보장하기 위해
> - 메모리 참조 관리에 효과적이기 때문 (ex: Optional Chaining)

<h1 id="OptionalChaining">옵셔널 체이닝이란?</h1>

> 옵셔널 체이닝이란 프로퍼티, 메서드, 서브스크립트를 nil이 될 수 있는 옵셔널로 호출하고 질의하는 것으로 만약 옵셔널이 값을 포함하고 있다면 성공적으로 호출되고 nil이라면 nil을 반환하게 된다.  
> 연결에서 어느 하나라도 nil일 경우 전체 연결을 실패

<h1 id="Struct_Class">값타입과 참조타입의 차이는?</h1>

- 값타입  
  > 간단하게 문서를 복사한 것이라고 이해를 하면 된다.  
  원본을 파쇄하더라고 복사본은 남아있고, 복사본을 수정한다고해서 원본이 수정되거나 그 반대가 되거나 하진 않는다.

  ---

- 참조타입  
  > 간단하게 바로가기라고 이해하면 된다.  
  원본이 사라지게되면 주소값이 사라지기 때문에 바로라기도 찾을수 없음으로 보인다.  
  바로가기를 수정하게되면 원본도 수정되고, 원본을 수정하게되면 바로가기도 같이 수정된다.  
  값을 복사하는 것이 아닌 레퍼런스/주소값을 참조하고 있는 형태이다.

만약 인스턴스가 변하지 않는 값이라면 값타입과 참조타입의 차이가 없다고 생각한다.  
하지만 고유한 값이 있어야 할 경우 각각의 개체가 각각의 값을 가져야 한다면 값타입이 더 안전하고 적절하다

메모리 영역도 다르다.  
값타입은 Stack에 참조타입은 Heap에

<h2 id="ARC">ARC</h2>
---

<h1 id="WhatIsARC">ARC란 무엇인가?</h1>

> Swift에서 자동으로 앱의 메모리 사용량을 추적하고 관리하기 위해 사용되는 방식  
> 참조 카운팅이 0이 될 경우에만 메모리에서 해제한다.  
> 만약 서로 다른 객체가 서로를 강하게 참조한다면 순환참조가 발생해 메모리 누수가 발생하게된다.  
> ==> 순환 참조를 방지하기 위해 weak 또는 unowned 키워드를 사용하면 reference count를 증가시키지 않아 순환 참조를 방지할 수 있다.

<h1 id="Strong_Weak_Unowned">Strong, Weak, Unowned 차이</h1>

- Strong  
  > 객체를 소유하여 레퍼런스 카운트를 증가하는 프로퍼티  
  > 값을 지정하는 시점에 retain, 값을 해제하는 시점에 release된다.
  > 카운트를 증가시켜 ARC로 인한 메모리 해제를 피하고 객체를 안전하게 사용하고자 할 때 사용된다.(별도 키워드를 적지 않는다면 strong이 default값)

- Weak
  > 객체를 소유하지 않고 주소값만을 가지고 있다.  
  > 자신이 참조는 하지만 weak 메모리를 해제시킬 수 있는 권한은 다른 클래스에 있다.  
  > 값 지정시 Retain이 발생하지 않는다. 또한 해제하는 시점에도 releasee되지 않는다. 이로 인해 언제 어떻게 메모리가 해제되는지 알 수 없다.  
  > 하지만 메모리가 해제될 경우 자동으로 레퍼런스를 nil로 초기화해준다. (weak가 옵셔널타입이어야 하는 이유)

<h1 id="weakSelf">[weak self] in</h1>

클로저 블럭 내에서 ```[weak self] in```  코드를 넣는 방법으로 클로저의 순환 참조를 해결하는데 ```[weak self] in```코드가 하는 역할과 그 이유는?

클로저에서 값 캡쳐 시점은 클로저가 호출될 때이다.

```[weak self] in```의 역할은 ARC가 프로퍼티의 갯수를 카운팅 하지 않도록 만들며 카운팅이 되지 않기에 순환참조가 일어나지 않도록 만드는 역할을 한다.  
> weak 참조는 ARC에 의해 참조되는 인스턴스가 메모리에서 해제 될 때 프로퍼티의 값을 nil로 만들기 때문에 순환 참조가 발생하지 않는다.

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