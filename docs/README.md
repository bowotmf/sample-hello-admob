## Hello Admob App

_The source code for this sample can be found here: [https://github.com/gomobile/sample-hello-admob](https://github.com/gomobile/sample-hello-admob "https://github.com/gomobile/sample-hello-admob") or download the_ [Intel® XDK](https://software.intel.com/en-us/html5/tools) to check out all of the HTML5 samples and templates.


## Introduction

Intel XDK® is a HTML5 hybrid application development environment that allow users to develop, debug, test on-device and build projects for various mobile platforms. Along with development features, this development environment provides various HTML5 templates and samples intended for running on various mobile devices and platforms. For more information on getting started, go to the [Intel XDK Overview](/en-us/xdk/docs/intel-xdk-overview).

## Purpose

By leveraging the [Apache Cordova* plug-ins](http://plugins.cordova.io/#/), you can develop compelling HTML5 hybrid apps for any platform and use case. [Apache Cordova](http://cordova.apache.org/) is a set of device APIs that allow a mobile app developer to access native device function such as the camera or accelerometer from JavaScript. Besides the standard APIs, various plug-ins are available in the [Apache Cordova Plug-ins Registry](http://plugins.cordova.io/#/) and located across the web on github. .

With this sample app, you can show banner and full screen Admob ads within your mobile application. 

The app shows how to use the following API methods:


[Admob floatinghotspot Plugin](https://github.com/floatinghotpot/cordova-plugin-admob "Plugin Documentation")

- AdMob.createBannerView() : Create Banner View
- AdMob.showAd : Show Banner Ad
- AdMob.destroyBannerView() : Remove Banner Ad
- AdMob.createInterstitialView() : Create Interstitial View
- AdMob.showInterstitialAd() : Show Interstitial View

Each button click is bound with methods that encapsulate the functionality of the plugin or API. These methods are defined in `js\app.js`.
Initialization code for Admob:

    function initAdMob() {
    "use strict";
    var fName = "initAdmob():";
    console.log(fName, "entry");
    try {
    	if (window.plugins && window.plugins.AdMob) {
		    //Login to https://apps.admob.com to get AD-UNIT-ID
		    var ad_units = {
			    ios: {
			    banner: 'ADD_YOUR_AD-UNIT-ID_HERE',
			    interstitial: 'ADD_YOUR_AD-UNIT-ID_HERE'
			    },
			    android: {
			    banner: 'ADD_YOUR_AD-UNIT-ID_HERE',
			    interstitial: 'ADD_YOUR_AD-UNIT-ID_HERE'
			    },
			    wp8: {
			    banner: 'ADD_YOUR_AD-UNIT-ID_HERE',
			    interstitial: 'ADD_YOUR_AD-UNIT-ID_HERE'
			    }
			 };
		    var admobid = "";
		    if (/(android)/i.test(navigator.userAgent)) {
		    	admobid = ad_units.android;
		    } else if (/(iphone|ipad)/i.test(navigator.userAgent)) {
		    	admobid = ad_units.ios;
		    } else {
		    	admobid = ad_units.wp8;
		    }

		    window.plugins.AdMob.setOptions({
			    publisherId: admobid.banner,
			    interstitialAdId: admobid.interstitial,
			    bannerAtTop: false, // set to true, to put banner at top
			    overlap: false, // set to true, to allow banner overlap webview
			    offsetTopBar: false, // set to true to avoid ios7 status bar overlap
			    isTesting: false, // receiving test ad
			    autoShow: true // auto show interstitial ad when loaded
		    });
	    registerAdEvents();
	    } 
    } catch (e) {
    console.log(fName, "catch, failure");
    }
    console.log(fName, "exit");
    }

## Testing

**Emulator:** Does not support third party plugins. When testing third party plugins, the app must be built and tested on device.

**App Preview:** Does not support third party plugins. When testing third party plugins, the app must be built and tested on device.

**Built app:** This sample app only works on a built app as it uses third party plugins. 

Learn how to import third party plugins into Intel XDK **[here](https://software.intel.com/en-us/xdk/docs/adding-third-party-plugins-to-your-xdk-cordova-app)**.


This sample application has been tested on iOS and Android devices.

