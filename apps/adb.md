# ADB

+   <http://bernaerts.dyndns.org/android/339-android-oneplustwo-oneplusx-enable-adb-mtp-detection-ubuntu-trusty#h2-declare-vendor-id-for-adb>
+   <https://github.com/NicolasBernaerts/ubuntu-scripts/blob/master/android/adb_usb.ini>



## Installation

+   `adb`

<!---->

    sudo apt-get install adb



## Einrichtung

    mkdir ~/.android
    wget --header='Accept-Encoding:none' -q -O - https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/adb_usb.ini >> ~/.android/adb_usb.ini
    chmod a+r ~/.android/adb_usb.ini
    adb kill-server
    adb start-server
