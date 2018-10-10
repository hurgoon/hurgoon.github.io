---
layout: post
title: Collection Array
date: 2018-10-10 14:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Collection, Array, Dictionary, Set]
---

## Collection

### Array
```swift
    // 설정
    var meetingRooms: Array<String> = ["Bansky", "Rivera", "Picasso"]
    var groups: [Int] = []

    // 추가 및 제거
    meetingRooms += ["Renoir"]
    meetingRooms.append("Lee Jung-Seoup")
    meetingRooms.remove(at: 2)

    // 값 추출
    meetingRooms.first
    meetingRooms.last
```

### Dictionary
```swift
    // 설정
    var roomCapacity: [String:Int] = [:]
    var roomCapacity: [String:Int] = ["Bansky":4, "Rivera":3]


    // 추가 및 제거 (+= 못씀...)
    roomCapacity["Picasso"] = 8
    roomCapacity.removeValue(forKey: "Bansky")

    // 값 추출
    roomCapacity["Picasso"]  // 추가나 추출이나...


    // Dictionary Key값 or Value값만 따오기(Array로 보이나 LazyMapCollection이라고 함)
    let roomNames = roomCapacity.keys
    let roomCapacities = roomCapacity.value
```

### Set(순서를 가지고 있지 않은 Collection. 집합연산하기 좋다. 반드시 "Set"명기필요!)
```swift
    // 설정
    let submultipleOf30: Set = [1, 2, 3, 5, 6, 10, 15, 30]
    let submultipleOf8: Set = [1, 2, 4, 8]

    // 집합연산
    let intersect(교집합) = submultipleOf30.intersection(submultipleOf8)
    let union(합집합) = submultipleOf30.union(submultipleOf8)
    let subtract(차집합) = submultipleOf30.subtracting(submultipleOf8)
    let symmetricDifference(차집합의 여집합) = submultipleOf30.symmetricDifference(submultipleOf8)
```
