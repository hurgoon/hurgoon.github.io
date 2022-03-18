---
layout: post
title: AppDelegate
date: 2018-10-15 16:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, AppDelegate]
---

## AppDelegate 기본 코드

### 코드로 작성시
```swift
  func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

        window = UIWindow(frame: UIScreen.main.bounds)
        window?.backgroundColor = .white
        window?.rootViewController = ViewController()
        window?.makeKeyAndVisible()

        return true
    }
```
