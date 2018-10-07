---
layout: post
title: UserDefaults
date: 2018-10-07 22:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img: save.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, UserDefaults]
---

## UserDefaults로 데이터 저장하기
1. UserDefaults 구축
```swift
let userDefaultsEmail = UserDefaults.standard
userDefaultsEmail.set(userEmail, forKey: "userEmail")

let userDefaultsPassword = UserDefaults.standard
userDefaultsPassword.set(userPassword, forKey: "userPassword")

// 싱크로나이즈드 스위밍...
userDefaultsEmail.synchronize()
userDefaultsPassword.synchronize()
```

2. UserDefaults 호출
```swift
// 상수로 빼내어 사용토록 하자
let storedEmail = UserDefaults.standard.string(forKey: "userEmail")
let storedPassword = UserDefaults.standard.string(forKey: "userPassword")
```

UserDefaults 관련, 정리가 잘 되어있는 일본 블로그
[https://i-app-tec.com/ios/nsuserdefaults.html](https://i-app-tec.com/ios/nsuserdefaults.html)
