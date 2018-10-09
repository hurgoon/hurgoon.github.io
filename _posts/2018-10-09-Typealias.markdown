---
layout: post
title: Typealias
date: 2018-10-09 23:45:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img: flight.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Typealias]
---

## Typealias

```swift
    // 설정
    typealias Time = (h: Int, m: Int, s: Int)
    typealias Duration = (start: Time, end: Time)

    // 상수에 시작시간과 종료시간을 인풋
    let todayStudyTime: Duration = ((13, 10, 20), (15, 20, 23))

    // 추출
    print("나는 오늘 \(todayStudyTime.end.h)시까지 공부했다)")
```
