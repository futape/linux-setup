# X.Org X-Server Treiber

+   <https://wiki.ubuntuusers.de/grafikkarten/intel>



## Deinstallation

Bei der Verwendung von neueren Intel GPUs (ab 2007), sollte der Intel X-Treiber entfernt werden und stattdessen der eingebauten `modesetting` Treiber verwendet werden. Vgl.

>	If your Intel GPU is recent enough (2007 or newer) it is recommended to remove the legacy Intel driver "xserver-xorg-video-intel" and to use the built-in modesetting driver instead [...]
>	The legacy driver is no longer maintained and only useful for the old i800x and i900x family of chipsets.
>
>	*([Cinnamon freezes when changing resolution (Intel GPU)](https://www.linuxmint.com/rel_sonya_cinnamon.php))*

und

>	Von der Nutzung dieses Treibers wird abgeraten, wenn Ihre Hardware hinreichend aktuell ist (ca. 2007 und neuer). Sie können versuchsweise diesen Treiber deinstallieren und stattdessen den Server seinen eingebauten »modesetting«-Treiber nutzen lassen.
>
>	*(<https://packages.debian.org/stretch/xserver-xorg-video-intel>)*

```sh
sudo apt-get remove xserver-xorg-video-intel
```