---
layout: post
title: AutoLayout by code
date: 2018-10-15 19:00:00 +0900
description: 디스크립션 입력란  # Add post description (optional)
img:  # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Swift, AutoLayout]
---

## AutoLayout by code

### Basic Setup
```swift
    let firstView = UIView()
    let secondView = UIView()

    override func viewDidLoad() {
        super.viewDidLoad()

        firstView.backgroundColor = .darkGray
        secondView.backgroundColor = .blue

        view.addSubview(firstView)
        firstView.addSubview(secondView)

        setupAutoresizingMask()
        activeNSLayoutConstraintConstaints()
    }
```

### Using setupAutoresizingMask
```swift
private func setupAutoresizingMask() {
        firstView.frame = CGRect(x: 50, y: 50, width: view.bounds.width - 100, height: view.bounds.height - 100)
        secondView.frame = CGRect(x: 25, y: 25, width: firstView.bounds.width - 50, height: firstView.bounds.height - 50)

        firstView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
        secondView.autoresizingMask = [.flexibleWidth, .flexibleHeight]
    }
```

### Using NSLayoutConstraint (iOS 6.0 부터 사용됨)
```swift
private func activeNSLayoutConstraintConstaints() {
       firstView.translatesAutoresizingMaskIntoConstraints = false  // 반드시 false로 시작
       secondView.translatesAutoresizingMaskIntoConstraints = false

       // firstView <-> View
       NSLayoutConstraint(item: firstView, attribute: .top, relatedBy: .equal, toItem: view, attribute: .top, multiplier: 1, constant: 50).isActive = true
       NSLayoutConstraint(item: firstView, attribute: .leading, relatedBy: .equal, toItem: view, attribute: .leading, multiplier: 1, constant: 50).isActive = true
       NSLayoutConstraint(item: firstView, attribute: .trailing, relatedBy: .equal, toItem: view, attribute: .trailing, multiplier: 1, constant: -50).isActive = true
       NSLayoutConstraint(item: firstView, attribute: .bottom, relatedBy: .equal, toItem: view, attribute: .bottom, multiplier: 1, constant: -50).isActive = true

       // secondView <-> firstView
       NSLayoutConstraint(item: secondView, attribute: .top, relatedBy: .equal, toItem: firstView, attribute: .top, multiplier: 1, constant: 50).isActive = true
       NSLayoutConstraint(item: secondView, attribute: .leading, relatedBy: .equal, toItem: firstView, attribute: .leading, multiplier: 1, constant: 50).isActive = true
       NSLayoutConstraint(item: secondView, attribute: .trailing, relatedBy: .equal, toItem: firstView, attribute: .trailing, multiplier: 1, constant: -50).isActive = true
       NSLayoutConstraint(item: secondView, attribute: .bottom, relatedBy: .equal, toItem: firstView, attribute: .bottom, multiplier: 1, constant: -50).isActive = true
   }
```

### Using activateVisualFormat (iOS 6.0 부터 사용됨)
```swift
private func activateVisualFormat() {
        firstView.translatesAutoresizingMaskIntoConstraints = false
        secondView.translatesAutoresizingMaskIntoConstraints = false

        let views: [String: Any] = ["firstView": firstView, "secondView":secondView]
        let metrics: [String: Any] = ["margin": 50]

        var allConstraints: [NSLayoutConstraint] = []
        allConstraints += NSLayoutConstraint.constraints(withVisualFormat: "H:|-margin-[firstView]-margin-|", metrics: metrics, views: views)
        allConstraints += NSLayoutConstraint.constraints(withVisualFormat: "V:|-margin-[firstView]-margin-|", metrics: metrics, views: views)
        allConstraints += NSLayoutConstraint.constraints(withVisualFormat: "H:|-30-[secondView]-30-|", metrics: nil, views: views)
        allConstraints += NSLayoutConstraint.constraints(withVisualFormat: "V:|-30-[secondView]-30-|", metrics: nil, views: views)

        NSLayoutConstraint.activate(allConstraints)
    }
```

>Visual Format Syntax
[https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/VisualFormatLanguage.html](https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/AutolayoutPG/VisualFormatLanguage.html)
