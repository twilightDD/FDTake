# FDTake

[![CI Status](http://img.shields.io/travis/fulldecent/FDTake.svg?style=flat)](https://travis-ci.org/William Entriken/FDTake)
[![Version](https://img.shields.io/cocoapods/v/FDTake.svg?style=flat)](http://cocoapods.org/pods/FDTake)
[![License](https://img.shields.io/cocoapods/l/FDTake.svg?style=flat)](http://cocoapods.org/pods/FDTake)
[![Platform](https://img.shields.io/cocoapods/p/FDTake.svg?style=flat)](http://cocoapods.org/pods/FDTake)
[![Readme Score](http://readme-score-api.herokuapp.com/score.svg?url=fulldecent/FDTake)](http://clayallsopp.github.io/readme-score?url=fulldecent/FDTake)


## Usage

To run the example project, clone the repo, and run `pod install` from the Example directory first.

To use it in your project, add an `FDTakeController` to your view controller and implement:

    fdTakeController.gotPhoto = {
        ...
    }

then call:

    fdTakeController.present()

The full API is:

```swift
/// Public initializer
public override init()

/// Convenience method for getting a photo
public class func getPhotoWithCallback(getPhotoWithCallback callback: (photo: UIImage, info: [NSObject : AnyObject]) -> Void)

/// Convenience method for getting a video
public class func getVideoWithCallback(getVideoWithCallback callback: (video: NSURL, info: [NSObject : AnyObject]) -> Void)

/// Whether to allow selecting a photo
public var allowsPhoto: Bool

/// Whether to allow selecting a video
public var allowsVideo: Bool

/// Whether to allow capturing a photo/video with the camera
public var allowsTake: Bool

/// Whether to allow selecting existing media
public var allowsSelectFromLibrary: Bool

/// Whether to allow editing the media after capturing/selection
public var allowsEditing: Bool

/// Whether to use full screen camera preview on the iPad
public var iPadUsesFullScreenCamera: Bool

/// Enable selfie mode by default
public var defaultsToFrontCamera: Bool

/// The UIBarButtonItem to present from (may be replaced by a overloaded methods)
public var presentingBarButtonItem: UIBarButtonItem?

/// The UIView to present from (may be replaced by a overloaded methods)
public var presentingView: UIView?

/// The UIRect to present from (may be replaced by a overloaded methods)
public var presentingRect: CGRect?

/// The UITabBar to present from (may be replaced by a overloaded methods)
public var presentingTabBar: UITabBar?

/// The UIViewController to present from (may be replaced by a overloaded methods)
public lazy var presentingViewController: UIViewController { get set }

/// A photo was selected
public var didGetPhoto: ((photo: UIImage, info: [NSObject : AnyObject]) -> Void)?

/// A video was selected
public var didGetVideo: ((video: NSURL, info: [NSObject : AnyObject]) -> Void)?

/// The user selected did not attempt to select a photo
public var didDeny: (() -> Void)?

/// The user started selecting a photo or took a photo and then hit cancel
public var didCancel: (() -> Void)?

/// A photo or video was selected but the ImagePicker had NIL for EditedImage and OriginalImage
public var didFail: (() -> Void)?

/// Custom UI text (skips localization)
public var takePhotoText: String?

/// Custom UI text (skips localization)
public var takeVideoText: String?

/// Custom UI text (skips localization)
public var chooseFromLibraryText: String?

/// Custom UI text (skips localization)
public var chooseFromPhotoRollText: String?

/// Custom UI text (skips localization)
public var cancelText: String?

/// Custom UI text (skips localization)
public var noSourcesText: String?

/// Presents the user with an option to take a photo or choose a photo from the library
public func present()

/// Dismisses the displayed view. Especially handy if the sheet is displayed while suspending the app,
public func dismiss()
```

Other available options are documented at <a href="http://cocoadocs.org/docsets/FDTake/">CocoaDocs for FDTake</a>.


## How it works

 1. See if device has camera
 2. Create action sheet with appropriate options ("Take Photo" or "Choose from Library"), as available
 3. Localize "Take Photo" and "Choose from Library" into user's language
 4. Wait for response
 5. Bring up image picker with selected image picking method
 6. Default to selfie mode if so configured
 7. Get response, extract image from a dictionary
 8. Dismiss picker, send image to delegate


## Support

 * Supports iPhones, iPods, iPads and tvOS (but not tested)
 * Supported languages:
   - English
   - Chinese Simplified
   - Turkish (thanks Suleyman Melikoglu)
   - French (thanks Guillaume Algis)
   - Dutch (thanks Mathijs Kadijk)
   - Chinese Traditional (thanks Qing Ao)
   - German (thanks Lars Häuser)
   - Russian (thanks Alexander Zubkov)
   - Norwegian (thanks Sindre Sorhus)
   - Arabic (thanks HadiIOS)
   - Polish (thanks Jacek Kwiecień)
   - Spanish (thanks David Jorge)
   - Hebrew (thanks Asaf Siman-Tov)
   - Danish (thanks kaspernissen)
   - Sweedish (thanks Paul Peelen)
   - Portugese (thanks Natan Rolnik)
   - Greek (thanks Konstantinos)
   - Italian (thanks Giuseppe Filograno)
   - Hungarian (thanks Andras Kadar)
   - Please help translate <a href="https://github.com/fulldecent/FDTake/blob/master/FDTakeExample/en.lproj/FDTake.strings">`FDTake.strings`</a> to more languages
 * Pure Swift support and iOS 8+ required
 * Compile testing running on Travis CI
 * In progress: functional test cases ([please help](https://github.com/fulldecent/FDTake/issues/72))
 * In progress: UI test cases ([please help](https://github.com/fulldecent/FDTake/issues/72))
 * In progress: select last photo used ([please help](https://github.com/fulldecent/FDTake/issues/22))


## Installation

FDTake is available through [CocoaPods](http://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'FDTake'
```


## Author

William Entriken, github.com@phor.net


## License

FDTake is available under the MIT license. See the LICENSE file for more info.
