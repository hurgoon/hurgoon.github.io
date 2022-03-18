---
layout: post
title: Function Type
date: 2018-10-25 18:20:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Function, func]
---

## Function Type 예제
>하기 내용은 글그리님의 [블로그](https://eastroot1590.tistory.com/entry/Swift-%ED%95%A8%EC%88%98-%EC%8B%AC%ED%99%94-Function-Type?category=793494)를 참조했음을 밝힙니다

### 1. 함수를 파라미터로 갖는 예제
```swift
// func 설정
func plus(a: Int, b:Int) -> Int {
	return a + b
}
func minus(a: Int, b: Int) -> Int {
	return a - b
}
func multiply(a: Int, b: Int) -> Int {
	return a * b
}

// func를 파라미터로 받는 func 설정
func printMath(f: (Int, Int)->Int, a: Int, b: Int) {
	print("result = \(f(a,b))")
}

// 실행문
printMath(f: plus, a: 5, b: 3)		// 8
printMath(f: minus, a: 5, b: 3)		// 2
printMath(f: multiply, a: 5, b: 3)	// 15
```

### 2. 함수를 반환 값으로 하는 예제
```swift
func plusplus(_ input: Int) -> Int {
	return input + 1
}
func minusminus(_ input: Int) -> Int {
	return input - 1
}

func factory(index: Bool) -> (Int)->Int {
	return index ? plusplus : minumminus   // 조건에 따라 리턴에 func를 넣어 돌린다... 하아...
}

var gage1 = 5
var gage2 = -7

let goToZero1 = factory(index: gage1 < 0)	// 인덱스가 false라서 func마이너스 가동
let goToZero2 = factory(index: gage2 < 0)	// 인덱스가 true라서 func플러스 가동
```
