# My Demo Ionic App
This is a Demo application based on the Ionic Conference Application. I made this up as a way to track everything I had to do to get my other Ionic application running with Electron builds in addition to Android.

## WARNING
This is what I had to do, please do not take this as an authoritative source. I wrote this after I worked everything out so I may have missed a step. This is presented as is with no warranty. That said, if something below helps you, by all means use it.

## Resources
1. https://medium.com/@LohaniDamodar/lets-make-desktop-application-with-ionic-3-and-electron-44316f82901d
1. https://competenepal.com/ionic2-electron-part-2/
1. https://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html#requirements-and-support
1. https://ionicframework.com/getting-started/

## Steps [resource in brackets]
- Install Node.js [4]
- Install Ionic & Cordova globally [4]
- Install Java JDK 1.8 (on my UbuntuMATE 17.10 machine, JDK 1.9 didn't work with Cordova)
- Install Android Studio
- Configure the SDK based on Cordova version [3]
- Install Gradle
- Create new Ionic Project [4]
- Add ANDROID_HOME and JAVA_HOME environment variables [3]
- Add ANDROID_HOME/tools and ANDROID_HOME/tools/bin to PATH [3]
- `ionic cordova platforms remove android` (this and the next 3 steps handled an issue I had with config.xml not existing for android)
- Delete platforms, www and plugins directory
- `npm install`
- `ionic cordova platforms add android`
- `ionic cordova requirements` to ensure everything is there
- `ionic cordova build android` to build a debug apk, my release apks are showing up as corrupt when I try to install them. I will update this once I figure out why.
- Install electron, electron-builder and foreman [1]
- Edit package.json to add content needed for electron and electron-builder [1]
- `mkdir config` and `cp node_modules/@ionic/app-scripts/config/webpack.config.js config` [1]
- Add externals array to devConfig and prodConfig after plugins array [1]
- `mkdir electron` and create electron/electron.js (remember to comment out 'win.webContents.openDevTools();' when building releases) [1]
- Add additional scripts to package.json. I left out the start because I wanted to use `ionic lab` with foreman [1]
- Create Procfile for foreman. For the ionic: line, I replaced `npm start` with `ionic lab`. [1]
- `npm run dev` to bring up Electron and Ionic Lab. You will need to Ctrl+R the Electron window after `ionic lab` starts [1]
- `npm run ebuild` to build an executable, I am on linux and so it makes and AppImage by default. [2]

That's it, you will see additional info in [2] about accessing electron functions but I haven't done that yet. I will update this if I end up doing so. I will also update this as time goes on and I learn more about Ionic, Cordova and Electron.

