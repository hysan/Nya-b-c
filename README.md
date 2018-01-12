# README

This is a clone of the game [Meow Letters](https://github.com/ana-balica/meow_letters_py) but written in JavaScript using HTML5 features. It works offline and you can add it to your mobile or tablet device as a web app too! I've also made an Android APK using PhoneGap. It's optimized to run smoothly even on devices as old as iPhone 4 and an HP Touchpad running Android.

Here's a link to a working [demo](http://nyabc.lovescomputers.com) of the game.

## Gameplay

After cloning it, I changed parts of the gameplay to include chaining, combos, better randomization, speedups, and other features making it more interesting to play. The central mechanic remains the same though: select the letters in the correct alphabetical order to clear them from the screen and gain points.

## Screenshots

![Menu Screen](/screenshots/menu.png?raw=true "Menu Screen")

![Settings](/screenshots/settings.png?raw=true "Settings")

![Scoreboard](/screenshots/scoreboard.png?raw=true "Scoreboard")

![Gameplay 1](/screenshots/gameplay-1.png?raw=true "Gameplay 1")

![Gameplay 2](/screenshots/gameplay-2.png?raw=true "Gameplay 2")

![Game Over](/screenshots/gameover.png?raw=true "Game Over")

## Requirements

- HTML5
- CSS3
- PhoneGap / Cordova

## Setup

### Android

To deploy to Android, you need to create an APK using PhoneGap. Do this like so:

```sh
hg clone https://username@repos.purposelyutteringnonsense.com/hg/Workshop/Nyan-Letters-HTML5 --insecure
cd Nyan-Letters-HTML5

## First some prerequisites:
# I assume Java is already installed as is the Android SDK.
# My JAVA_HOME=/usr/lib/jvm/java-7-openjdk
export PATH=$PATH:/path/to/android-sdk-linux:/path/to/android-sdk-linux/tools
# Apache Ant: http://ant.apache.org/bindownload.cgi
wget http://ftp.riken.jp/net/apache//ant/binaries/apache-ant-1.9.4-bin.tar.gz
tar zxf apache-ant-1.9.4-bin.tar.gz
export ANT_HOME=/path/to/your/workspace/apache-ant-1.9.4:/path/to/your/workspace/apache-ant-1.9.4/bin
export PATH=$PATH:$ANT_HOME
# Node.js: http://nodejs.org/download/
wget http://nodejs.org/dist/v0.10.30/node-v0.10.30-linux-x64.tar.gz
tar zxf node-v0.10.30-linux-x64.tar.gz
# PhoneGap: http://phonegap.com/install/
./node-v0.10.30-linux-x64/bin/npm install -g phonegap

## Now you can create the Android APK:
./node-v0.10.30-linux-x64/bin/phonegap create Nyan-Letters
cp -R src/* Nyan-Letters/www
cd Nyan-Letters
# This helps determine the settings for Android in: platforms/android/build.xml
vim www/config.xml
../node-v0.10.30-linux-x64/bin/phonegap build android
# This should build the APK in debug mode and place it here:
# platforms/android/ant-build/NyanLetters-debug.apk
# If you want a release build, use:
# ./platforms/android/cordova/build --release
# This will place the release APK here:
# platforms/android/ant-build/NyanLetters-release-unsigned.apk
# Note: You need to manually sign the release APK or else it can't be installed.
```
