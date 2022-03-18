---
layout: post
title: pageControl
date: 2018-10-17 17:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, pageControl]
---

## pageControl

### 1. pageControl 생성
  scrollView의 하위로 생성되지 않도록 해야함.
```swift
// ViewController class안에 생성
@IBOutlet weak var pageControl: UIPageControl!
```

### 2. pageControl 조건 설정   
```swift
// viewDidLoad 안에서 페이지 갯수 설정
pageControl.numberOfPages = 4

// ViewController에 func 작성
func scrollViewDidEndDecelerating(_ scrollView: UIScrollView) {
        pageControl.currentPage = Int(scrollView.contentOffset.x / scrollView.frame.width)
    }
```
scrollView의 contentOffset x 좌표를 스크롤 프레임의 가로 길이로 나눈다.
contentOffset x 좌표가 한페이지가 넘어가면 스크롤 프레임과 동일하게 되고,
페이지를 넘길수록 배수가 된다.
Int로 나눈 값을 변환하고 scrollViewDidEndDecelerating 메소드(스크롤 감속 완료?)로
currentPage를 설정한다
