<h1 align="center">Onesignal ReactNative Expo</h1>
<p>
  <a href="https://github.com/OneSignal/onesignal-expo-plugin/graphs/commit-activity" target="_blank">
    <img alt="Maintenance" src="https://img.shields.io/badge/Maintained%3F-yes-green.svg" />
  </a>
  <a href="https://twitter.com/onesignaldevs" target="_blank">
    <img alt="Twitter: onesignaldevelopers" src="https://img.shields.io/twitter/follow/onesignaldevs?style=social" />
  </a>
</p>

> The OneSignal Expo plugin allows you to use OneSignal without leaving the managed workflow. Developed in collaboration with SweetGreen.

* 📄 [Docs](https://documentation.onesignal.com/docs/react-native-sdk-setup)
* 🖤 [npm](https://www.npmjs.com/package/onesignal-expo-plugin)

## Overview
This plugin is an [Expo Config Plugin](https://docs.expo.dev/guides/config-plugins/). It extends the Expo config to allow customizing the prebuild phase of managed workflow builds (no need to eject to a bare workflow). For the purposes of OneSignal integration, the plugin facilitates automatically generating/configuring the necessary native code files needed to get the [OneSignal React-Native SDK](https://github.com/OneSignal/react-native-onesignal) to work. You can think of adding a plugin as adding custom native code.

## More information:
* The official OneSignal Expo Plugin [repo](https://github.com/OneSignal/onesignal-expo-plugin)
---

## Install

```sh
expo install onesignal-expo-plugin
```

**Note:**
Even though onesignal-expo-plugin defines `react-native-onesignal` as a dependency and it gets put into the `node_modules` it seems the native parts don't get built into the app for some reason.

After installing the onseignal-expo-plugin, install now the react-native-onesignal plugin by running the following command.

```sh
yarn add react-native-onesignal
```

If you frogot to run the following command after you have built your project, you can fix this by running `expo prebuild --clean`. This should delete android and ios and do a clean native build, then run the `yarn add react-native-onesignal`.

## Configuration in app.json / app.config.js
### Plugin
Add the plugin to the [plugin array](https://docs.expo.dev/versions/latest/config/app/):

**app.json**
```json
{
  "plugins": [
    [
      "onesignal-expo-plugin",
      {
        "mode": "development",
        "devTeam": "91SW8A37CR"
      }
    ]
  ]
}
```

or

**app.config.js**
```js
export default {
  ...
  plugins: [
    [
      "onesignal-expo-plugin",
      {
        mode: process.env.NODE_ENV || "development",
        devTeam: "91SW8A37CR"
      }
    ]
  ]
};
```

#### Plugin Options
* `mode`: used to configure [APNs environment](https://developer.apple.com/documentation/bundleresources/entitlements/aps-environment) entitlement.
   - `"development"`
   - `"production"`
* `devTeam`: *optional* - used to configure Apple Team ID. You can find your Apple Team ID by running `expo credentials:manager`.

### OneSignal App ID
Add your OneSignal App ID to your [Expo constants via the `extra` param](https://docs.expo.dev/versions/latest/config/app/):

**Example:**
```json
{
  "extra": {
    "oneSignalAppId": "<YOUR APP ID HERE>"
  }
}
```

You can then access the value to pass to the `setAppId` function:

```js
import OneSignal from 'react-native-onesignal';
import Constants from "expo-constants";
OneSignal.setAppId(Constants.manifest.extra.oneSignalAppId);
```

Alternatively, pass the OneSignal app ID directly to the function:

```js
OneSignal.setAppId("YOUR-ONESIGNAL-APP-ID");
```

## Run
```sh
$ expo prebuild

# Build your native iOS project
$ expo run:ios

# Build your native Android project
$ expo run:android
```
---

## Show your support

Give a ⭐️ if this project helped you!

## OneSignal Developers

* Website: https://onesignal.com/onesignal-developers
* Twitter: [@OneSignalDevs](https://twitter.com/onesignal)
* Github: [@OneSignalDevelopers](https://github.com/OneSignal)
* Discord: [@onesignal](https://linkedin.com/company/onesignal)
