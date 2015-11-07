cordova-plugin-flurry
============

This plugin exposes the Flurry SDK for iOS and Android

Includes:
- Flurry iOS SDK 7.2.0
- Flurry Android SDK 6.1.0


## Installation

    cordova plugin add https://github.com/piotrowski/cordova-plugin-flurry.git

### Usage

1. After the device is ready call `startSession()` with your app key as a parameter
2. In your application code call the other Flurry plugin methods as appropriate

#### Preparation
- Android: Call flurry.endSession when the app is paused and flurry.startSession when the app resumes
- iOS: Call setSessionReportsOnCloseEnabled and setSessionReportsOnPauseEnabled

## Example 

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

## License
Apache 2.0
