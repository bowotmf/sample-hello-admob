\*\*\*No Longer Supported\*\*\*
===============================

>   This sample is no longer supported by the Intel XDK team and is
>   not guaranteed to work with the current release (v3491 or later) of the
>   [Intel® XDK](http://xdk.intel.com).

Hello AdMob
===========

See [LICENSE.md](<LICENSE.md>) for license terms and conditions.

Project Details
---------------

The Hello AdMob sample presents banner and full screen AdMob ads
within a simple mobile application. The app shows how to use the
following API methods that are part of the
[Admob Floatinghotspot Plugin](https://github.com/floatinghotpot/cordova-plugin-admob):

- AdMob.createBannerView() : Create Banner View
- AdMob.showAd : Show Banner Ad
- AdMob.destroyBannerView() : Remove Banner Ad
- AdMob.createInterstitialView() : Create Interstitial View
- AdMob.showInterstitialAd() : Show Interstitial View

Each button click is bound with methods that encapsulate the functionality of the
plugin API. These methods are defined in `js\app.js`.

The initialization code for Admob:

```javascript
function initAdMob() {
    "use strict";
    var fName = "initAdmob():";
    console.log(fName, "entry");

    try {
        if( window.plugins && window.plugins.AdMob ) {
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
            if( /(android)/i.test(navigator.userAgent) ) {
                admobid = ad_units.android;
            }
            else if( /(iphone|ipad)/i.test(navigator.userAgent) ) {
                admobid = ad_units.ios;
            }
            else {
                admobid = ad_units.wp8;
            }

            window.plugins.AdMob.setOptions({
                publisherId: admobid.banner,
                interstitialAdId: admobid.interstitial,
                bannerAtTop: false,   // set to true, to put banner at top
                overlap: false,       // set to true, to allow banner overlap webview
                offsetTopBar: false,  // set to true to avoid ios7 status bar overlap
                isTesting: false,     // receiving test ad
                autoShow: true        // auto show interstitial ad when loaded
            });
            registerAdEvents();
        }
    }
    catch (e) {
        console.log(fName, "catch, failure");
    }

    console.log(fName, "exit");
}
```

Testing
-------

**Simulator:** Does not support third party plugins.
When testing third party plugins, the app must be built and tested on device.

**Emulator:** Does not support third party plugins.
When testing third party plugins, the app must be built and tested on device.

**App Preview:** Does not support third party plugins.
When testing third party plugins, the app must be built and tested on device.

**Built App:** This sample app only works as a built app, because it uses third-party plugins.

Learn how to [import third party plugins into Intel XDK](https://software.intel.com/en-us/xdk/docs/adding-third-party-plugins-to-your-xdk-cordova-app).

This sample application was tested on iOS and Android devices.
