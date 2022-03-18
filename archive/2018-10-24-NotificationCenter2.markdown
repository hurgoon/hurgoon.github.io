---
layout: post
title: NotificationCenter2
date: 2018-10-24 11:30:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, NotificationCenter, Notification]
---

## NotificationCenter2 (업그레이드 버젼)

### 1. 방송할 컨텐츠 준비
```swift
// ViewController class안에 생성
var someValue: Float = 0
var someValue2: Float = 0
```

### 2. NotificationCenter Post   
```swift
// func 안에서 생성
let data: [String: Float] = [
            "someValue": someValue,
            "someValue2": someValue2,
        ]
NotificationCenter.default.post(name: .notiName, object: self, userInfo: data)
```
### 3. Extension 파일 생성
```swift
// 파일명 : NotificationNameExtension.swift
extension Notification.Name {
    static let notiName = Notification.Name(rawValue: "notiNameValue")
}
```

### 4. NotificationCenter Observer
```swift
// View func안에 생성
NotificationCenter.default.addObserver(forName: NSNotification.Name.NotiName, object: nil, queue: OperationQueue.main) { (notification) in

    let userInfo = notification.userInfo as! [String: Float]  // userInfo 타이 캐스팅이 필요함

    self.label.backgroundColor = UIColor(
        red: CGFloat(userInfo["someValue"]!),
        green: CGFloat(userInfo["someValue2"]!)
    )
}
```
필요한 데이터만 넘기는 깔끔한(?) 노티 사용법
