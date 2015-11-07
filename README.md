FlurryPlugin
============

## Attention

This is a fork of https://github.com/jfpsf/flurry-phonegap-plugin that fixes some current (2015-11-07) problems.

## Installation

    cordova plugin add https://github.com/piotrowski/flurry-phonegap-plugin.git

### Integration

1. Call the startSession() method, with your app key, after the device is ready
2. Call the other Flurry plugin methods as appropriate
3. In Android, call flurry.endSession when the app is paused and again call flurry.startSession when the app resumes, or it won't log the session.
4. In iOS, setSessionReportsOnCloseEnabled and setSessionReportsOnPauseEnabled to log the session.

## Example 

	self.log('Flurry Analytics Init');
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

## Contributors

- [jfpsf](https://github.com/jfpsf)
- [Koray Balcı](https://github.com/koraybalci)
- [Patrick heneise (The Mobile Firm)](https://github.com/PatrickHeneise)
- [Ivan Karpan](https://github.com/IvanKarpan)
- [LilDevine89](https://github.com/LilDevine89)

## License
Apache 2.0
