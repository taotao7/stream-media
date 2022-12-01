# electron-quick-start

This Electron application is based on the [Electron Quick Start Guide](https://electronjs.org/docs/tutorial/quick-start) and demonstrates how to use [Radiant Media Player](https://www.radiantmediaplayer.com) with DASH and Widevine DRM. 
This demo app can be used as a basis to build video oriented Electron app where DRM content is required. 

It uses [Electron for Content Security](https://github.com/castlabs/electron-releases). Electron for Content Security (ECS) is a fork of Electron created by castLabs to facilitate the use of Google's Widevine Content Decryption Module (CDM) for DRM-enabled playback within Electron, including support for Verified Media Path (VMP) and persistent license storage. It is intended to be used as a drop-in replacement for stock Electron and currently has full support for Windows and macOS platforms, with partial support for Linux (which lacks support for persistent licenses due to VMP limitations on the platform).

## To Use
From your command line:

```bash
# Clone this repository
git clone https://github.com/radiantmediaplayer/electron-quick-start.git
# Go into the repository
cd electron-quick-start
# Install dependencies
npm install
# Important: Configure index.html with your Radiant Media Player license key
# Run the app
npm start
```

## Documentation for using Radiant Media Player with DASH and Widevine DRM in an Electron app

In `package.json` you can see that devDependencies for Electron points to `github:castlabs/electron-releases#v18.0.1+wvcus`. This set up has been tested with version 18.0.1 of castLabs Electron for Content Security and Radiant Media Player version 7.6.1. Other versions of ECS (Electron 15+) and Radiant Media Player 7+ should work as well. 

In `index.html` we have our Radiant Media Player configured to use DASH with Widevine DRM with a demo live stream. Make sure to add your [PLATFORM Edition license key](https://www.radiantmediaplayer.com/pricing.html) before testing.

In `main.js` we have made changes to automatically prepare our application for Widevine DRM support. 

## Supported Widevine DRM features

The following features are supported:
- Playback of Widevine DRM encrypted content with DASH
- Support for Widevine Verified Media Path
- Persistent license storage

#### NOTE: All Electron for Content Security releases are pre-signed for development, i.e. for use with Widevine UAT or servers accepting development clients. If your license requests are failing when testing your streams then it could be that you need to use [EVS](https://github.com/castlabs/electron-releases/wiki/EVS) to VMP-sign your application for production for it to work against a production DRM service.

More information on how to use Radiant Media Player with [DASH and Widevine DRM can be found here](https://www.radiantmediaplayer.com/docs/latest/dash-drm-documentation.html).

To achieve Widevine support the Widevine CDM will be installed on first launch and enabled as an option for playback of DRM protected content using common EME APIs. Subsequent launces will trigger a backround update check. If an update is available it will be downloaded and applied on next launch.

For more advanced use-cases see [castLabs Electron for Content Security documentation](https://github.com/castlabs/electron-releases).

## Supported environments
- Windows 7+
- macOS 10.11+
- Linux Ubuntu 14.14+, Fedora 24+ and Debian 8+ (lacking support for persistent licenses due to VMP limitations)

## License for electron-quick-start
[CC0 1.0 (Public Domain)](LICENSE.md)

## License for Radiant Media Player
Radiant Media Player is a commercial HTML5 media player, not covered by the above CC0 1.0 license. 

Radiant Media Player license can be found here: [https://www.radiantmediaplayer.com/terms-of-service.html](https://www.radiantmediaplayer.com/terms-of-service.html). 

You may request a free trial for Radiant Media Player at: [https://www.radiantmediaplayer.com/free-trial.html](https://www.radiantmediaplayer.com/free-trial.html).
