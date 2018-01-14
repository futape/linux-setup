# MTP

+   <http://bernaerts.dyndns.org/android/339-android-oneplustwo-oneplusx-enable-adb-mtp-detection-ubuntu-trusty>
+   <https://github.com/NicolasBernaerts/ubuntu-scripts/blob/master/android/51-android.rules>
+   <https://github.com/NicolasBernaerts/ubuntu-scripts/blob/master/android/69-mtp.rules>

<!---->

1.  Lese- und Schreibrecht auf Android-Geräte Nutzer in der Grupper `plugdev` gewähren:

        wget --header='Accept-Encoding:none' -q -O - https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/51-android.rules | sudo tee /etc/udev/rules.d/51-android.rules
        sudo chmod a+r /etc/udev/rules.d/51-android.rules
2.  Zugriff auf Android-Geräte über MTP (via `libmtp`) einrichten:

        wget --header='Accept-Encoding:none' -q -O - https://raw.githubusercontent.com/NicolasBernaerts/ubuntu-scripts/master/android/69-mtp.rules | sudo tee /etc/udev/rules.d/69-mtp.rules
        sudo chmod a+r /etc/udev/rules.d/69-mtp.rules
3.  Den `udev` Daemon neustarten:

        sudo service udev restart
