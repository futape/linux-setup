# Brennen & Rippen (cdrtools)

+   <https://wiki.ubuntuusers.de/cdrecord>
+   <https://wiki.ubuntuusers.de/mkisofs>
+   <https://launchpad.net/~brandonsnider/+archive/ubuntu/cdrtools>
+   <https://de.wikipedia.org/wiki/Cdrtools>
+   <http://cdrecord.org/>



## Installation

+   `cdrecord`
+   `mkisofs`
+   `cdda2wav`

```sh
sudo add-apt-repository ppa:brandonsnider/cdrtools
sudo apt-get update
sudo apt-get install cdrecord mkisofs cdda2wav
```



### Hinweise

+   Die cdrtools Version aus dem oben stehenden PPA enthält seit Version 3.01a21 eine Emulation der crdkit Komponenten *genisoimage* und *wodim*, sowie eine Emulation von *readom* und erlaubt somit die problemlose Nutzung von Applikationen, die für deren Verwendung programmiert wurden.
+   Bei der Installation werden die cdrkit Komponenten automatisch entfernt, sodass deren Emulation durch cdrtools nicht mit dem echten cdrkit kollidiert. Auch *icedax* wird entfernt, obwohl dessen cdrtools Pendant *cdda2wav* dieses nicht ersetzt (*Replace*), sondern lediglich mit ihm kollidiert (*Conflict*), entsprechend erfolgt auch keine Emulation von *icedax*. Die anderen Komponenten *cdrecord* und *mkisofs* kollidieren (*Conflict*) **und** ersetzen ihre cdrkit Pendants *wodim* und *genisoimage*. Das ebenfalls von cdrtools emulierte *readom* wird hingegen durch kein anderes Paket entfernt.



## Alternative (cdrkit)

+   `wodim`
+   `genisoimage`
+   `icedax`

<!---->

    sudo apt-get install wodim genisoimage icedax
