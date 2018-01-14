# Video Decoding/Encoding Treiber (VA-API & VDPAU Emulation)

+   <https://wiki.ubuntuusers.de/Video-Dekodierung_beschleunigen>
+   <https://en.wikipedia.org/wiki/Video_Acceleration_API>
+   <https://01.org/linuxgraphics/community/vaapi>
+   <http://freedesktop.org/wiki/Software/vaapi/>
+   <https://en.wikipedia.org/wiki/VDPAU#Generic_VDPAU_driver>



## Installation

+   `libva1`
+   `i965-va-driver`
+   `libvdpau-va-gl1`

<!---->

    sudo apt-get install libva1 i965-va-driver libvdpau-va-gl1



## Einrichtung

Um VDPAU mittels libvdpau-va-gl zu emulieren, muss diese Library als VDPAU Driver eingerichtet werden. Dies geschieht über die Umgebungsvariable `VDPAU_DRIVER`.

    echo "export VDPAU_DRIVER=va_gl" | sudo tee /etc/profile
