---
layout: post
title: Property Observers
date: 2018-11-01 20:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Property, Observers, willSet, didSet]
---

## Property Observers

### willSet & didSet
```swift
class StepCounter {
    var totalSteps: Int = 0 {
        willSet(newSteps) { // (newSteps) 삭제하고 newValue로 사용가능
            print("About to set totalSteps to \(newSteps)")
        }
        didSet {  // oldValue 대신에 원하는 것으로 ()안에 대체 가능
            if totalSteps > oldValue {
                print("Added \(totalSteps - oldValue) Steps")
            }
        }
    }
}

var steps = StepCounter()
steps.totalSteps = 3
steps.totalSteps = 400
```

willSet은 새로운 값이 들어오면 캐치해서 명령을 실행한다.
didSet은 바로 이전 값을 남겨서 사용한다...  이제야 알다니.... ;ㅁ;
