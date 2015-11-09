cordova-plugin-flurry
============

This plugin exposes the Flurry SDK for iOS and Android

Includes:
- Flurry iOS SDK 7.2.0
- Flurry Android SDK 6.1.0

It is a drop in replacement for https://github.com/jfpsf/flurry-phonegap-plugin and heavily based on it.

## Installation

    cordova plugin add https://github.com/piotrowski/cordova-plugin-flurry.git

## Usage

1. After the device is ready call `startSession()` with your app key as a parameter
2. In your application code call the other Flurry plugin methods as appropriate

### Preparation
- Android: Call flurry.endSession when the app is paused and flurry.startSession when the app resumes
- iOS: Call setSessionReportsOnCloseEnabled and setSessionReportsOnPauseEnabled

### Example 

	if (window.plugins && window.plugins.flurry) {
		var ua = navigator.userAgent.toLowerCase();
		var isAndroid = ua.indexOf("android") > -1; //&& ua.indexOf("mobile");
		if (isAndroid) {
			window.plugins.flurry.startSession('Your API Key', function () {
				console.log('Flurry Success!');
			}, function () {
				alert('Flurry Error!');
			});
		} else {
			window.plugins.flurry.startSession('Your API Key', function () {
				console.log('Flurry Success!');
				window.plugins.flurry.setSessionReportsOnCloseEnabled(true); // iOS only
				window.plugins.flurry.setSessionReportsOnPauseEnabled(true); // iOS only
			}, function () {
				alert('Flurry Error!');
			});
		}
	}

### Methods

TODO

### TODO

- Update to current Flurry SDK versions
- clean up "preparation" docs (Android part is not reflected in example)
- clean up flurryplugin.js (endSession + startSession shouldn't be necessary any more)
- clean up usage example
- rid of package name com.phonegap.plugins.flurry
- flurryPlugin => flurry
- add remark on Google Play Services and Google Repository that have to be installed locally to be able to build

## License
Apache 2.0
