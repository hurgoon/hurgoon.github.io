---
layout: post
title: Prepare and CallBack
date: 2018-10-24 11:30:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Prepare, CallBack]
---

## Prepare and CallBack

### 1. Prepare 셋팅
```swift
// Navigation Controller 구축, Bar Button 아이템으로 Storyboard Segue 설정(Show)
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {

    let nextViewController = segue.destination as! SlideViewController

    nextViewController.callBack = { [weak self](color: UIColor) -> Void in
        self?.mainView.backgroundColor = color
    }
}
```

### 2. CallBack 셋팅
```swift
var callBack: ((UIColor) -> Void)?

// 버튼을 누르면 컬러정보가 저장됨
@IBAction func tap(_ sender: UIButton) {
    let color = UIColor(
        red: CGFloat(redSlider.value),
        green: CGFloat(greenSlider.value),
        blue: CGFloat(blueSlider.value),
        alpha: 1)

    callBack?(color)
}
```
