---
layout: post
title: Layout by code
date: 2018-10-15 18:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, Layout]
---

## AppDelegate 기본 코드

### 코드로 작성시
```swift
class ViewController: UIViewController {

    let redView = UIView()
    let blueView = UIView()

    override func viewDidLoad() {
        super.viewDidLoad()

        redView.backgroundColor = .red
        blueView.backgroundColor = .blue

        view.addSubview(redView)
        view.addSubview(blueView)
    }

    override func viewWillLayoutSubviews() {
        super.viewWillLayoutSubviews()

        let margin: CGFloat = 20
        let safeLayoutInsets = view.safeAreaInsets
        let horizontalInset = safeLayoutInsets.left + safeLayoutInsets.right

        let yOffset = safeLayoutInsets.top + margin
        let viewWidth = (view.bounds.midX - margin - 5 - (horizontalInset / 2 ))
        let viewHieght = view.bounds.height - yOffset - (safeLayoutInsets.bottom + margin)

        redView.frame = CGRect(
            x: safeLayoutInsets.left + margin,
            y: yOffset,
            width: viewWidth,
            height: viewHieght
        )

        blueView.frame = CGRect(
            origin: CGPoint(
                x: redView.frame.maxX + 10, 
                y: yOffset),
            size: redView.bounds.size
        )

    }
}
```
