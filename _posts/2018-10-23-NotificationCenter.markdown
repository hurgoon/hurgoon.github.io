---
layout: post
title: NotificationCenter
date: 2018-10-23 20:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, NotificationCenter, Notification]
---

## NotificationCenter

### 1. 방송할 컨텐츠 준비
```swift
// ViewController class안에 생성
var someValue: Float = 0
```

### 2. NotificationCenter Post   
```swift
// func 안에서 생성
NotificationCenter.default.post(name: NSNotification.Name.notiName, object: self)
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
NotificationCenter.default.addObserver(forName: NSNotification.Name.notiName, object: nil, queue: OperationQueue.main) { (Notification) in
    let dataVC = Notification.object as! ViewController
    self.label.backgroundColor = UIColor(
        red: CGFloat(dataVC.redValue ),
        green: CGFloat(dataVC.greenValue),
        blue: CGFloat(dataVC.blueValue),
        alpha: CGFloat(dataVC.alphaValue))
}
```
뷰콘트롤러 안에있는 내용 몽땅 넘기는 무식한(?) 방법... 
