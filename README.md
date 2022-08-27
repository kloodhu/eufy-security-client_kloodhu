# eufy-security-client

![Logo](docs/_media/eufy-security-client.png)

[![node](https://img.shields.io/node/v/eufy-security-client.svg)](https://www.npmjs.com/package/eufy-security-client)
[![NPM version](http://img.shields.io/npm/v/eufy-security-client.svg)](https://www.npmjs.com/package/eufy-security-client)
[![Downloads](https://img.shields.io/npm/dm/eufy-security-client.svg)](https://www.npmjs.com/package/eufy-security-client)
[![Total Downloads](https://img.shields.io/npm/dt/eufy-security-client.svg)](https://www.npmjs.com/package/eufy-security-client)
[![Dependency Status](https://img.shields.io/librariesio/release/npm/eufy-security-client)](https://libraries.io/npm/eufy-security-client)
[![Known Vulnerabilities](https://snyk.io/test/github/bropat/eufy-security-client/badge.svg)](https://snyk.io/test/github/bropat/eufy-security-client)

[![NPM](https://nodei.co/npm/eufy-security-client.png?downloads=true)](https://nodei.co/npm/eufy-security-client/)

The development of this shared library was inspired by the work of the following people:

* FuzzyMistborn (<https://github.com/FuzzyMistborn/python-eufy-security>)
* keshavdv (<https://github.com/keshavdv/python-eufy-security>)
* JanLoebel (<https://github.com/JanLoebel/eufy-node-client>)

Credits go to them as well.

If you appreciate my work and progress and want to support me, you can do it here:

[![ko-fi](https://www.ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/E1E332Q6Z)
[![Donate](https://img.shields.io/badge/Donate-PayPal-blue.svg)](https://www.paypal.me/pbroetto)

**This project is not affiliated with Anker and Eufy (Eufy Security). It is a personal project that is maintained in spare time.**

## Description

This shared library allows to control [Eufy security devices](https://us.eufylife.com/collections/security) by connecting to the Eufy cloud servers and local/remote stations over p2p.

You need to provide your Cloud login credentials.

One client instance will show all devices from one Eufy Cloud account and allows to control them.

## Features

* Connects to Eufy cloud (supports 2fa)
* Connects to station/devices using p2p communication (supported: local and remote connectivity)
* Supports receiving push notification (unified push messages interface)
* Basic P2P implementation that supports also commands not already implemented
* Get info and parameters from stations/devices over https and/or p2p
* P2P functionality already implemented:
  * Station:
    * Change guard mode
    * Reboot station
  * Devices:
    * Start livestream (local/remote p2p or rtmp over cloud)
    * Stop livestream (local/remote p2p or rtmp over cloud)
    * Enable/disable device
    * Enable/disable auto night vision (only camera products)
    * Enable/disable led (only camera 2 products, indoor cameras, floodlight camera, solo cameras and doorbells)
    * Enable/disable anti-theft detection (only camera 2 products)
    * Enable/disable motion detection
    * Enable/disable pet detection (only indoor cameras)
    * Enable/disable sound detection (only indoor cameras)
    * Enable/disable RTSP stream (only camera2 products, indoor cameras and solo cameras)
    * Change video watermark setting (only camera products)
    * Start/cancel download video
    * Quick response (only doorbells)
    * Lock/unlock (only smart lock products)
    * And many more, check it out...

## Documentation

Look [here](https://bropat.github.io/eufy-security-client/).

*As an example, you can look at the following projects: [ioBroker.eufy-security](https://github.com/bropat/ioBroker.eufy-security), [eufy-security-ws](https://github.com/bropat/eufy-security-ws), [eufy_security](https://github.com/fuatakgun/eufy_security)*

## Known working devices

For a list of supported devices, please see [here](https://bropat.github.io/eufy-security-client/#/supported_devices).

If more devices work (or also not) please report them by opening a GitHub issue.

## How to report issues and feature requests

Please use GitHub issues for this.

## Changelog

### 2.2.0-rc.2 (2022-08-27)

* (bropat) Added snooze command for supported devices (#173, #176)
* (bropat) Added support for video type store to NAS for indoor cameras (#147)
* (bropat) Fixed issue with energy saving measures interrupting running streams
* (bropat) Better error handling for not supported p2p commands
* (bropat) Fixed signalling of event `station command result`
* (bropat) Updated docs - Added supported devices SoloCam L20 (T8122), SoloCam L40 (T8123), SoloCam S40 (T8124), SoloCam E20 (T8130)
* (bropat) Changed default persistent directory path for saving persistent data

### 2.2.0-rc.1 (2022-08-19)

* (bropat) **Breaking Change** Renamed all lock settings parameters according to standard
* (bropat) Renewed p2p device address discovery (now also includes local discovery via broadcast; cloud discovery optimised)
* (bropat) Added support for Doorbell Dual notification types (package delivered, package taken, package stranded, someone loitering, radar motion detected)
* (bropat) Added Smart Safe support (tested only T7401; #182 **WIP**)
* (thieren) Added station event for connection timeout (#202)
* (bropat) Fixed issue #196
* (bropat) Fixed issue #201
* (bropat) Fixed emitting of event "locked" for lock devices
* (bropat) Small bugfixes and optimizations

### 2.1.2 (2022-07-30)

* (Palmke) Dual Doorbell family detection (#177)
* (Palmke) Fixed issue #187
* (bropat) Fixed issue #186

### 2.1.1 (2022-07-16)

* (Palmke) Add alarm arm delay event (#180)
* (thieren) Fix: stream command for T8420 (#171)
* (Palmke) Don't send the alarm armed p2p events as alarm events (#169)
* (bropat) Fixed issue #167
* (bropat) Fixed issue #161
* (bropat) Updated versions of the package dependencies

### 2.1.0 (2022-06-12)

* (bropat) Added toggle for Spotlight for Outdoor Cam Pro (T8441; #123)
* (bropat & thieren) Added talkback commands for supported devices (#38, #153; thanks @thieren)
* (fabianluque) Added missing RTSP properties for Floodlight T8423 (#146)
* (Palmke) Add alarm delay event (#88, #155)
* (Palmke) P&T T8410: Set motion zone and image mirror (#156)
* (Palmke) Send an event when the alarm is armed and alarm events from p2p (#105, #157)
* (bropat) Implemented simple request throttling for Eufy Cloud
* (bropat) Fixed push notification token renewal
* (bropat) Fixed issue #161

### 2.0.1 (2022-05-03)

* (bropat) **Breaking Change** Fixed regression in device data loading
* (bropat) Target set back to ES2019

### 2.0.0 (2022-04-30)

* (bropat) **Breaking Change** Requires node version >= 14.17
* (bropat) **Breaking Change** HTTPApi class, EufySecurity class and Device classes instantiation changed
* (bropat) **Breaking Change** Timestamp for device and station properties has been removed
* (bropat) Added support for Battery Doorbell Dual (T8213; #126)
* (bropat) Added support for Video Doorbell Dual (T8203; #141)
* (bropat) Added support for IndoorCam Mini (T8414; #143)
* (bropat) Added continuos recording setting for some supported cameras
* (bropat) Added continuos recording type setting for some supported cameras
* (bropat) Added default angle setting for IndoorCam Mini (T8414)
* (bropat) Added default angle idle time setting for IndoorCam Mini (T8414)
* (bropat) Added notification interval time setting for some supported cameras
* (bropat) Added calibrate command for some supported cameras
* (bropat) Added set default angle command for IndoorCam Mini (T8414
* (bropat) Added set privacy angle command for IndoorCam Mini (T8414)
* (bropat) Removed PREFER_LOCAL P2P connectivity mode. Default mode is now QUICKEST.
* (bropat) Added new charging status "solar charging" (value: 4; issue #127)
* (bropat) Fixed Eufy cloud authentication token renewal
* (bropat) Fixed some Eufy cloud authentication issues
* (bropat) Fixed authentication issues when changing country setting
* (bropat) Fixed possible wrong battery values on some devices
* (bropat) Fixed issue if device doesn't support P2P communication
* (bropat) Fixed issue #136
* (bropat) Fixed issue #122
* (bropat) Updated versions of the package dependencies

### 1.6.6 (2022-02-12)

* (bropat) Fixed issue where no devices/stations are found (#116)

### 1.6.5 (2022-02-08)

* (bropat) Fixed regression in authentication flow introduced when fixing issue #116
* (bropat) Updated versions of the package dependencies

### 1.6.4 (2022-02-07)

* (bropat) Fixed issue #116 (choosing the correct country as in the Eufy App is esentially)

**Note:** Selecting the correct country is essential for the devices to be found (should match the setting in the Eufy app).

### 1.6.3 (2022-02-06)

* (bropat) Initialize MQTT connection only if supported devices are found

### 1.6.2 (2022-02-05)

* (bropat) Fixed MQTT connection issue (error: 5)

### 1.6.1 (2022-02-05)

* (bropat) Fixed small issue on driver upgrade of persistence data (has no impact; error entry in log on first startup)

### 1.6.0 (2022-02-05)

* (bropat) Supports new [Home Management](https://communitysecurity.eufylife.com/t/tips-for-eufy-security-app-v4-0/2420747) feature of Eufy Security 4.0
* (bropat) Added support for Smart Lock Touch & Wifi (T8520; #89)
* (bropat) Implemented Eufy MQTT notification subscription for Smart Lock Touch & Wifi (T8520)
* (bropat) Added auto lock setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added auto lock schedule setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added auto lock schedule start time setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added auto lock schedule end time setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added auto lock timer setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added notification setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added notification locked setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added notification unlocked setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added one touch locking setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added scramble passcode setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added sound setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added wrong try protection setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added wrong try attempts setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added wrong try lockdown time setting for Smart Lock Touch & Wifi (T8520)
* (bropat) Added lock/unlock command for Smart Lock Touch & Wifi (T8520)
* (bropat) Added lock calibration command for Smart Lock Touch & Wifi (T8520)
* (bropat) Improved p2p communication with energy saving devices
* (bropat) Added new HTTPApi methods supporting Eufy Security 4.0
* (bropat) Some small improvements were made to the HTTPApi
* (bropat) Fixed issue #97
* (bropat) Fixed issue #102
* (bropat) Fixed issue #109
* (bropat) Updated versions of the package dependencies

### 1.5.0 (2021-12-19)

* (bropat) Added support for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range standard sensitivity setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range advanced left sensitivity setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range advanced middle sensitivity setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range advanced right sensitivity setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion detection range test mode setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion tracking sensitivity setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion auto-cruise setting for floodlight cam 2 pro (T8423)
* (bropat) Added motion out-of-view detection setting for floodlight cam 2 pro (T8423)
* (bropat) Added light setting color temperature manual setting for floodlight cam 2 pro (T8423)
* (bropat) Added light setting color temperature mamotion setting for floodlight cam 2 pro (T8423)
* (bropat) Added light setting color temperature schedule setting for floodlight cam 2 pro (T8423)
* (bropat) Added light setting motion activation mode setting for floodlight cam 2 pro (T8423)
* (bropat) Added video nightvision image adjustment setting for floodlight cam 2 pro (T8423)
* (bropat) Added video color nightvision setting for floodlight cam 2 pro (T8423)
* (bropat) Added auto calibration setting for floodlight cam 2 pro (T8423)
* (bropat) Added start/stop rtsp livestream command for floodlight cam 2 pro (T8423)
* (bropat) Added battery and wifi rssi properties to eufycam 1/E
* (bropat) Implemented another p2p-keepalive mechanism found in some floodlights (e.g. T8420)
* (bropat) Fixed support for floodlight (T8420) - tested with FW: 1.0.0.35 HW: 2.2
* (bropat) Fixed status led setting for floodlight (T8420)
* (bropat) Fixed motion detected setting for floodlight (T8420)
* (bropat) Fixed motion detected sensitivity setting for floodlight (T8420)
* (bropat) Fixed audio recording setting for floodlight (T8420)
* (bropat) Fixed enable/disable device for floodlight (T8420)
* (bropat) Fixed start livestream command for floodlight (T8420)
* (bropat) Fixed issue #79
* (bropat) Fixed issue #66
* (bropat) Fixed some other minor issues
* (bropat) Added docs (:construction:)
* (bropat) Updated versions of the package dependencies

### 1.4.0 (2021-11-22)

* (bropat) Implemented captcha authentication mechanism (API v2)
* (bropat) Fixed issue #69

### 1.3.0 (2021-11-20)

* (bropat) Implemented new encrypted authentication mechanism (API v2)
* (bropat) Dropped old plaintext authentication mechanism (API v1)
* (bropat) Fixed issue #67
* (bropat) Exchanged axios with got for HTTP/2 support

**Note:** If you have 2FA enabled, you will need to authenticate again after this update.

### 1.2.4 (2021-11-17)

* (bropat) Fixed issue #63

### 1.2.3 (2021-11-16)

* (bropat) Fixed issue #64
* (bropat) Fixed issue #65
* (bropat) Updated versions of the package dependencies

### 1.2.2 (2021-11-06)

* (bropat) Fixed issue of wrong channel value on event rtsp livestream stopped
* (bropat) Updated versions of the package dependencies

### 1.2.1 (2021-10-23)

* (bropat) Changed event detection for start/stop local RTSP streaming
* (bropat) Fixed regression introduced by fixing issue #51
* (bropat) Fixed new implementation that detects interrupted p2p streams
* (bropat) Fixed missing start/stop local RTSP streaming commands to hasCommand and getCommands

### 1.2.0 (2021-10-17)

* (bropat) Extended p2p implementation to better support solo cameras and other battery powered devices
* (bropat) Revised p2p implementation to send commands sequentially
* (bropat) Added support for Floodlight T8422
* (bropat) Added support for SoloCam E40 (T8131)
* (bropat) Added experimental feature for supported devices: start/stop local RTSP streaming
* (bropat) Added new properties for solo cameras: battery, batteryTemperature, wifiSignalLevel, state, chargingStatus, lastChargingDays, lastChargingRecordedEvents, lastChargingTotalEvents, batteryUsageLastWeek
* (bropat) Implemented interrupted p2p stream detection
* (bropat) Fixed issue #51
* (bropat) Fixed push notifications for solo cameras (motion and person detection)
* (bropat) Fixed "livestream stopped" if live stream is started for multiple devices of the same station (1 p2p session could start only 1 live stream at a time)
* (bropat) Fixed "download finished" if download is started for multiple devices of the same station (1 p2p session could start only 1 download at a time)
* (bropat) Fixed an issue where the P2P connection type PREFER_LOCAL did not attempt to connect if no local IP address was found
* (bropat) Updated versions of the package dependencies

### 1.1.2 (2021-08-19)

* (bropat) Fixed push notification issue on new indoor outdoor camera device (thx to @lenoxys)
* (bropat) Fixed issue where device doesn't support p2p connection

### 1.1.1 (2021-08-13)

* (bropat) Fixed p2p video streaming for some devices (fallback mechanism implemented)
* (bropat) Fixed p2p audio codec detection

### 1.1.0 (2021-08-11)

* (bropat) Added brightness light setting for 2c/2c pro cameras, new solo cameras and new outdoor cameras
* (bropat) Added enable/disable light setting for 2c/2c pro cameras, new solo cameras and new outdoor cameras
* (bropat) Added trigger/reset alarm sound for indoor cameras, solo cameras and floodlight cameras
* (bropat) Added video streaming quality setting for 2c pro cameras
* (bropat) Added video recording quality setting for 2c pro cameras
* (bropat) Added trigger alarm sound for indoor cameras, solo cameras (incl. new) and floodlight cameras
* (bropat) Added reset alarm sound for indoor cameras, solo cameras (incl. new) and floodlight cameras
* (bropat) Added battery charging state for keypad devices
* (bropat) Added new property "batteryIsCharging" for keypad devices
* (bropat) Added property "wifiRssi" for keypad devices
* (bropat) Added new property "nightvision" for devices supporting the "light" nightvision mode
* (bropat) Added new properties "switchModeWithAccessCode", "autoEndAlarm" and "turnOffAlarmWithButton" for station with registered keypad
* (bropat) Added default values for some properties that, if not set first, were not listed in the cloud response
* (bropat) Fixed issue with guard mode setting where the "Off" state was not handled correctly (only supported with keypad) (#27)
* (bropat) Fixed issue in class EufySecurity if start cloud stream command fails
* (bropat) Fixed issue with "locked" event for locks
* (bropat) Fixed issue with nightvision setting for devices with light (b&w, light, off)
* (bropat) Fixed issue in station property value conversion for number or boolean types
* (bropat) Fixed issue where "motionDetection" property was incorrectly updated instead of "motionDetected" when a push notification arrived
* (lenoxys) Handle Lock Push Event for Lock / Unlock #36

### 1.0.0 (2021-08-07)

* (bropat) Added new method "getSensorHistory" to HTTPApi class for getting entry sensor history data
* (bropat) Added new events "station connect" and "station close" to EufySecurity class
* (bropat) Added new "chargingStatus", "wifiSignalLevel", "rtspStreamUrl", "chirpVolume", "chirpTone", "videoHdr", "videoDistortionCorrection" and "videoRingRecord" properties for supported devices
* (bropat) Added enable/disable led setting for camera 1 products
* (bropat) Added motion detection sensitivity setting for camera 1 products and wired doorbell
* (bropat) Added motion detection type setting for camera 1 products
* (bropat) Added motion audio recording setting for camera 1 products and wired doorbell
* (bropat) Added ringtone volume setting for wired doorbell
* (bropat) Added enable/disable indoor chime setting for wired doorbell
* (bropat) Added notification ring setting for wired doorbell
* (bropat) Added notification motion setting for wired doorbell
* (bropat) Added video streaming quality setting for wired doorbell
* (bropat) Added video recording quality setting for wired doorbell
* (bropat) Added video HDR setting for wired doorbell
* (bropat) Added video distortion correction setting for wired doorbell
* (bropat) Added video ring recording setting for wired doorbell
* (bropat) Added notification type setting for camera 1 products, solo cameras and wired doorbell
* (bropat) Added chirp volume setting for entry sensor
* (bropat) Added chirp tone setting for entry sensor
* (bropat) Implemented queuing of p2p commands in class P2PClientProtocol if connection to station isn't already present
* (bropat) Renamed some properties for typo issues
* (bropat) Renamed some properties to correct the use of camelcase
* (bropat) Fixed issue where data was not updated (cloud and p2p polling)
* (bropat) Fixed issue with resetting api_base when changing credentials
* (bropat) Fixed some issues with clearing timeouts in class P2PClientProtocol
* (bropat) Fixed issue in class P2PClientProtocol not detecting video codec for some devices (#)
* (bropat) Fixed event "rtsp url" returning the url value containing nulls "\0"
* (bropat) Updated versions of the package dependencies

### 0.9.4 (2021-07-23)

* (bropat) Fixed regression on p2p connection timeout and reconnect tentatives
* (bropat) Updated versions of the package dependencies

### 0.9.3 (2021-07-20)

* (bropat) Fixed p2p livestream video regression
* (bropat) Merged #22 - Add custom modes in alarm mode (thx to @piitaya)

### 0.9.1 (2021-07-17)

* (bropat) Exported some missing error classes and types
* (bropat) Checking valid direction values for panAndTilt command

### 0.9.0 (2021-07-16)

* (bropat) **Breaking Change** Station/EufySecurity "guard mode" event changed to emit only the guard mode
* (bropat) Added Station/EufySecurity "current mode" event that emits only the current mode change
* (bropat) Added more Eufy Cloud error codes to "ResponseErrorCode"
* (bropat) Added more server push notification types to "ServerPushEvent"
* (bropat) Added pan an tilt functionality to supported indoor cameras
* (bropat) Added functionality to handle invitations on "HTTPApi"
* (bropat) Added error detection if stopping or starting stream that isn't running or already running
* (bropat) Added new setting "acceptInvitations" to "EufySecurity" to accept invitations automatically
* (bropat) Added floodlight camera light switch
* (bropat) Added motion detection sensitivity for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added motion detection type for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added motion tracking for indoor camera pan & tilt cameras
* (bropat) Added video stream quality setting for indoor cameras, solo cameras, floodlight cameras and battery doorbell
* (bropat) Added video recording quality setting for indoor cameras
* (bropat) Added WDR setting for battery doorbells
* (bropat) Added microphone mute setting for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added audio recording setting for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added enable/disable speaker setting for indoor cameras, solo cameras, floodlight cameras, camera 2 products
* (bropat) Added speaker volume setting for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added power source setting for camera 2 products cameras, eufy cameras and eufy E cameras
* (bropat) Added power working mode setting for solo cameras, camera 2 products, battery doorbells, eufy cameras and eufy E cameras
* (bropat) Added power custom working mode recording clip length setting for solo cameras, floodlight cameras, camera 2 products, battery doorbells, eufy cameras and eufy E cameras
* (bropat) Added power custom working mode recording retrigger interval setting for solo cameras, floodlight cameras, camera 2 products, battery doorbells, eufy cameras and eufy E cameras
* (bropat) Added power custom working mode recording ends if motion stops setting for solo cameras, floodlight cameras, camera 2 products, battery doorbells, eufy cameras and eufy E cameras
* (bropat) Added video streaming quality setting for indoor cameras, solo cameras, floodlight cameras and battery doorbells
* (bropat) Added video recording quality setting for indoor 2k cameras
* (bropat) Added motion detection sensitivity setting for indoor cameras, floodlight cameras and camera 2 products
* (bropat) Added enable/disable motion tracking setting for indoor pan & tilt cameras
* (bropat) Added motion detection type setting for indoor cameras, solo cameras, floodlight cameras, camera 2 products and battery doorbells
* (bropat) Added enable/disable WDR setting for battery doorbells
* (bropat) Added ringtone volume setting for battery doorbells
* (bropat) Added enable/disable chime indoor setting for battery doorbells
* (bropat) Added enable/disable chime homebase setting for battery doorbells
* (bropat) Added chime homebase ringtone volume setting for battery doorbells
* (bropat) Added chime homebase ringtone type setting for battery doorbells
* (bropat) Added notification type setting for solo cameras, floodlight cameras, camera 2 products, battery doorbells, eufy cameras and eufy E cameras
* (bropat) Added enable/disable person notification setting for indoor cameras
* (bropat) Added enable/disable pet notification setting for indoor cameras
* (bropat) Added enable/disable all other motion notification setting for indoor cameras
* (bropat) Added enable/disable all sound notification setting for indoor cameras
* (bropat) Added enable/disable crying notification setting for indoor cameras
* (bropat) Added enable/disable motion notification setting for battery doorbells
* (bropat) Added enable/disable ring notification setting for battery doorbells
* (bropat) Added trigger alarm sound for camera 2 products
* (bropat) Added reset alarm sound for camera 2 products
* (bropat) Added trigger alarm sound for homebase 1+2
* (bropat) Added reset alarm sound for homebase 1+2
* (bropat) Added alarm tone setting for homebase 1+2
* (bropat) Added alarm volume setting for homebase 1+2
* (bropat) Added prompt volume setting for homebase 1+2
* (bropat) Added time format setting for homebase 1+2
* (bropat) Added enable/disable switch mode app notification setting for homebase 1+2
* (bropat) Added enable/disable switch mode geofence notification setting for homebase 1+2
* (bropat) Added enable/disable switch mode schedule notification setting for homebase 1+2
* (bropat) Added enable/disable switch mode keypad notification setting for homebase 1+2
* (bropat) Added enable/disable start alarm delay notification setting for homebase 1+2
* (bropat) Added new floodlight, solo and outdoor cameras (untested!)
* (bropat) Added alarm event for Station
* (bropat) Picture url attribute is now also updated via push notifications
* (bropat) Fixed issue where the "pollingIntervalMinutes" setting of "EufySecurity" was not respected
* (bropat) Fixed p2p livestream for floodlight camera
* (bropat) Fixed p2p enable/disable device for floodlight camera
* (bropat) Fixed p2p enable/disable autonightvision for floodlight camera
* (bropat) Fixed p2p download video
* (bropat) Fixed P2PClientProtocol "close" event that was emitted even if there was no connection and a reconnection was attempted
* (bropat) Fixed "guard mode" and "current mode" event not emittet in some conditions
* (bropat) Fixed possible race conditions processing unordered p2p packets
* (bropat) Optimized p2p lookup functionality
* (bropat) Other small bugfixes and code cleanup
* (bropat) Updated versions of the package dependencies

### 0.8.3 (2021-06-01)

* (bropat) Fixed regression in p2p protocol

### 0.8.2 (2021-05-26)

* (bropat) Fixed issue [#2](https://github.com/bropat/eufy-security-client/issues/2)
* (bropat) Added new high level property "type" for devices/stations
* (bropat) Updated versions of the package dependencies

### 0.8.1 (2021-05-14)

* (bropat) Fixed (raw) property value refresh for devices and stations
* (bropat) Fixed "enabled" property for standalone devices
* (bropat) Fixed "lanIpAddress" property for standalone devices
* (bropat) Fixed "macAddress" property for standalone devices
* (bropat) Added "station raw property changed" and "device raw property changed" event for high level class EufySecurity

### 0.8.0 (2021-05-12)

* (bropat) **Breaking Changes** (renamed emitter, renamed some functions etc.)
* (bropat) Added high level class EufySecurity
* (bropat) Added high level properties with metadata information
* (bropat) Better error handling
* (bropat) Fixed Guard Mode Emitter
* (bropat) Fixed push notification for indoor and floodlight cams
* (bropat) Cleanup code
* (bropat) Updated versions of the package dependencies

### 0.7.2 (2021-04-10)

* (bropat) Added new HTTP API methods: getVideoEvents, getAlarmEvents, getHistoryEvents, getAllVideoEvents, getAllAlarmEvents, getAllHistoryEvents
* (bropat) P2P session: Added station serial number to logging entries for debugging purposes
* (bropat) Updated versions of the package dependencies

### 0.7.1 (2021-04-02)

* (bropat) Lowered UDP receive buffer size for FreeBSD
* (bropat) Fixed lookup timeout issue on "local prefered" connection establishment

### 0.7.0 (2021-03-30)

* (bropat) Added support for smart locks
* (bropat) Added new P2P feature: lock/unlock smart lock products
* (bropat) Optimized speed of P2P connection establishment
* (bropat) Implemented P2P connection setup preference: local prefered, local only or quickest connection
* (bropat) Trying to solve issue [#2](https://github.com/bropat/eufy-security-client/issues/2)
* (bropat) Dropped support for NodeJS 10.x (min. requirement 12)
* (bropat) Updated versions of the package dependencies

### 0.6.0 (2021-03-11)

* (bropat) Added new command types to enum CommandType
* (bropat) Added new P2P feature: enable/disable pet detection for indoor cameras
* (bropat) Added new P2P feature: enable/disable sound detection for indoor cameras
* (bropat) Added new P2P feature: enable/disable led for wired doorbells
* (bropat) Added some functions to p2p station class: getLANIPAddress, getGuardMode, getCurrentMode
* (bropat) Added new device class: BatteryDoorbellCamera, IndoorCamera, SoloCamera
* (bropat) Added new functions to some device classes returning specific parameter values
* (bropat) Renamed interface ParameterValue to StringValue and added new: BooleanValue, NumberValue
* (bropat) All functions of the Device base class that return parameter values, return now the value and timestamp of the last modification
* (bropat) Fixed enable/disable led (for battery doorbells, indoor cameras, floodlight camera and solo cameras)
* (bropat) Fixed enable/disable motion detection (for wired doorbells, indoor cameras, floodlight camera and solo cameras)
* (bropat) Fixed change video watermark setting (for wired doorbells, battery doorbells, indoor cameras and floodlight camera)
* (bropat) Fixed issue with multibyte string with function buildCommandWithStringTypePayload
* (bropat) Fixed issue on PushMessage interface (fixed parsing of file_path)

### 0.5.1 (2021-03-05)

* (bropat) Fixed download of videos via p2p (wrong channel value in callback)
* (bropat) Updated versions of the dev package dependencies

### 0.5.0 (2021-03-03)

* (bropat) Added new P2P feature: enable/disable motion detection for camera products
* (bropat) Added new P2P feature: enable/disable rtsp stream for camera2 products, indoor and solo cameras
* (bropat) Added option to P2P session to enable quick start livestream (after receiving first video frame)
* (bropat) Added new methods to HTTPApi for setting custom HTTP session headers: PhoneModel, Country, Language
* (bropat) Changed return type of HTTPApi authenticate function
* (bropat) Fixed issue during livestreaming if p2p connection is lost

### 0.4.4 (2021-02-20)

* (bropat) Fixed possible race condition that sometimes interrupts the livestream

### 0.4.3 (2021-02-18)

* (bropat) Added new P2P feature: quick response for doorbell products
* (bropat) Fixed wired doorbell p2p livestream (should fix also indoor, floodlight and solo cameras)
* (bropat) Fixed issue on new PushMessage interface
* (bropat) Updated versions of the package dependencies

### 0.4.2 (2021-02-15)

* (bropat) Fixed battery doorbell start livestream P2P command
* (bropat) Added CMD_DOORBELL_SET_PAYLOAD as nested command type

### 0.4.1 (2021-02-14)

* (bropat) Fixed small typo
* (bropat) Uniform debug messages

### 0.4.0 (2021-02-13)

* (bropat) Added new P2P feature: Enable/disable device (for camera products)
* (bropat) Added new P2P feature: Enable/disable auto night vision (for camera products)
* (bropat) Added new P2P feature: Enable/disable led (for camera 2 products, indoor cameras, floodlight camera and solo cameras)
* (bropat) Added new P2P feature: Enable/disable anti-theft detection (for camera 2 products)
* (bropat) Added new P2P feature: Change video watermark setting (for camera products)
* (bropat) Fixed P2P command retry on error 503
* (bropat) Fixed issue on new PushMessage interface
* (bropat) Fixed issue with handling unencrypted video data

### 0.3.0 (2021-02-11)

* (bropat) Added new P2P feature: Download video
* (bropat) Implemented refreshing of device and station parameters via P2P
* (bropat) Migrated to TypedEmitter (tiny-typed-emitter)
* (bropat) Implemented new managed push notification class: PushNotificationService
* (bropat) Removed old push notification class: PushRegisterService
* (bropat) Renamed previous PushMessage interface to RawPushMessage
* (bropat) Introduced new PushMessage interface that normalizes all push notification types into one
* (bropat) Fixed issue where readable streams were not correctly destroyed when terminating p2p video streams
* (bropat) Fixed P2P start livestream command for Floodlight / Indoor / Solo cameras
* (bropat) Implemented refresh of GUARD_MODE on change of SCHEDULE_MODE over p2p (instantly)

### 0.2.2 (2021-02-06)

* (bropat) Exported missing P2P interface: StreamMetadata

### 0.2.1 (2021-02-06)

* (bropat) Added typescript declaration files

### 0.2.0 (2021-02-06)

* (bropat) initial release

## License

MIT License

Copyright (c) 2021 bropat <patrick.broetto@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
