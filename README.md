![VisionDetect](https://preview.ibb.co/insD1k/Vision_Detector_Logo.png)
> VisionDetect let you track user face gestures like blink, smile etc.

[![Swift Version][swift-image]][swift-url]
[![Build Status][travis-image]][travis-url]
[![License][license-image]][license-url]
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![CocoaPods Compatible](https://img.shields.io/cocoapods/v/EZSwiftExtensions.svg)](https://img.shields.io/cocoapods/v/LFAlertController.svg)  
[![Platform](https://img.shields.io/cocoapods/p/LFAlertController.svg?style=flat)](http://cocoapods.org/pods/LFAlertController)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

Inspired from https://github.com/aaronabentheuer/AAFaceDetection , added some new features(like take a photo) and will add in near future. Moved from KVO to Delegation structure to easy use :)

## Delegate Methods

``` swift
    func didNoFaceDetected()
    func didFaceDetected()
    func didSmile()
    func didNotSmile()
    func didBlinked()
    func didNotBlinked()
    func didWinked()
    func didNotWinked()
    func didLeftEyeClosed()
    func didLeftEyeOpened()
    func didRightEyeClosed()
    func didRightEyeOpened()
```

## Features
> You can easily take a picture or save it to photo album.

``` swift
    self.vDetect.takeAPicture(completionHandler: { (image) in

    })
```
``` swift
    self.vDetect.saveToCamera()
```

## Requirements

- iOS 8.0+
- Xcode 7.3

## Installation

#### CocoaPods
You can use [CocoaPods](http://cocoapods.org/) to install `VisionDetect` by adding it to your `Podfile`:

```ruby
platform :ios, '8.0'
use_frameworks!
pod 'VisionDetect', :git=>'https://github.com/miletliyusuf/VisionDetect.git'
```

To get the full benefits import `VisionDetect` wherever you import UIKit

``` swift
import VisionDetect
```
#### Carthage
Create a `Cartfile` that lists the framework and run `carthage update`. Follow the [instructions](https://github.com/Carthage/Carthage#if-youre-building-for-ios) to add `$(SRCROOT)/Carthage/Build/iOS/VisionDetect.framework` to an iOS project.

```
github "miletliyusuf/VisionDetect"
```
#### Manually
1. Download and drop ```VisionDetect.swift``` in your project.  
2. Congratulations!  

## Usage example

```swift
import VisionDetect

class YourViewController: UIViewController {

    @IBOutlet weak var imageView:UIImageView!

    var vDetect:VisionDetect!

    override func viewDidLoad() {
        super.viewDidLoad()

        vDetect = VisionDetect(cameraPosition: VisionDetect.CameraDevice.FaceTimeCamera, optimizeFor: VisionDetect.DetectorAccuracy.HigherPerformance)
        vDetect.delegate = self
        vDetect.onlyFireNotificatonOnStatusChange = false
        vDetect.beginFaceDetection()

        self.view.addSubview(vDetect.visageCameraView)
    }
}

extension YourViewController: VisionDetectDelegate {
    func didLeftEyeClosed() {
        self.vDetect.takeAPicture(completionHandler: { (image) in
            self.imageView.image = image
            self.vDetect.endFaceDetection()
            self.vDetect.visageCameraView.removeFromSuperview()
        })
    }
}

```

## Contribute

We would love you for the contribution to **VisionDetect**, check the ``LICENSE`` file for more info.

## Meta

Yusuf Miletli – [@ysfmltli](https://twitter.com/ysfmltli) – miletliyusuf@gmail.com

Distributed under the MIT license. See ``LICENSE`` for more information.

[https://github.com/miletliyusuf/VisionDetect](https://github.com/miletliyusuf/)

[swift-image]:https://img.shields.io/badge/swift-3.0-orange.svg
[swift-url]: https://swift.org/
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-url]: LICENSE
[travis-image]: https://img.shields.io/travis/dbader/node-datadog-metrics/master.svg?style=flat-square
[travis-url]: https://travis-ci.org/dbader/node-datadog-metrics
[codebeat-image]: https://codebeat.co/badges/c19b47ea-2f9d-45df-8458-b2d952fe9dad
[codebeat-url]: https://codebeat.co/projects/github-com-vsouza-awesomeios-com
[logo.png]: https://ibb.co/h5jCsQ
