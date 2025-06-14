
![[Beaconchain Dashboard](https://beaconcha.in/mobile)](.github/banner.png)  
[![Build](https://github.com/gobitfly/eth2-beaconchain-explorer-app/actions/workflows/build.yaml/badge.svg)](https://github.com/gobitfly/eth2-beaconchain-explorer-app/actions/workflows/build.yaml)  

# Beaconchain Dashboard App

Beaconchain Dashboard is an open source ethereum 2.0 validator performance tracker app for Android and iOS. It utilizes the beaconcha.in API. 


[![Get it on Google Play](https://beaconcha.in/img/android.png)](https://play.google.com/store/apps/details?id=in.beaconcha.mobile)
[![Get it App Store](https://beaconcha.in/img/ios.png)](https://apps.apple.com/at/app/beaconchain-dashboard/id1541822121)

## About

Beaconchain Dashboard is an Angular app written in Typescript, HTML & CSS. It utilizes the Ionic framework for mobile components and Ionic Capacitor as bridge for native code.

## Features

- Keep track on your validators online status, balances, returns and more  
- Various notification alerts for your validators  
- Combined dashboard view  
- Support for up to 100 validators  
- Ethereum client update notifications  
- Network warnings  
- Support for multiple currencies  
- Mainnet & Testnet support  
- Add validators with public key, index or eth 1.0 deposit addresses  
- Light Theme & Dark Theme  

## Device support

- Android 5.0 or newer
- iOS 11 or newer

## Development
### Getting started

1. Clone repo
2. Install dependencies
```
npm install -g @ionic/cli native-run cordova-res
npm i
```
  
NOTE: You need to provide your own google-services.json for Android and GoogleService-Info.plist for iOS.  

### Browser
To run the app in your browser, simply use

`ionic serve`

to start a local webserver with livereload enabled.

### Android

**Prerequisites**
* Install [Android Studio](https://developer.android.com/studio#downloads]) (recommended 4.1.1 or newer)
* Use Android Studio to install the Android SDK: https://capacitorjs.com/docs/android

For Linux Users: Open capacitor.config.json (in the root of the project) and adapt the paths for the _linuxAndroidStudioPath_ variable to reflect your local setup.

Build the the app at least once before proceeding:

`ionic build`

#### Livereload

Make sure port 8100 is accessable on your computer and use the following command to run a livereload server

`ionic capacitor run android --livereload --external --host=192.168.0.124 --disableHostCheck`

Adapt the --host param to match your computers IP. 

#### Build for production

`ionic capacitor run android --prod --release`

#### Install via Android Studio
To install the app on a real device, follow this guide: https://developer.android.com/studio/run/device

Or to run it in an emulator, follow up here: https://developer.android.com/studio/run/emulator


### iOS
**Prerequisites**
* macOS with Catalina or newer
* Xcode 12.2 or newer

Build the the app at least once before proceeding:

`ionic build`

#### Livereload

Make sure port 8100 is accessable on your mac and use the following command to run a livereload server

`ionic capacitor run ios --livereload --external --host=192.168.0.124 --disableHostCheck`

Adapt the --host param to match your macs IP. 

#### Build for production

`ionic capacitor run ios --prod --release`

### Best Practices

* Use components when we need it for multiple pages.
* Use pipes for currency conversion or interpreting a value
* Keep in mind that the app can be used in light and dark theme, use css vars when styling. Global theme attributes can be found in src/app/theme/variables.scss and src/app/global.scss.

## License

This project is licensed under GPLv3. [LICENSE](LICENSE)
<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/gobitfly/eth2-beaconchain-explorer-app">Beaconchain</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://beaconscan.com//dashboard/LuxTFPXcHjULov8sPCJsNAdLPQkEvkf3Z1l0EwLFx7">Mahdi amolimoghaddam</a> is licensed under <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"></a></p>
