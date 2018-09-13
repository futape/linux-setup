# VirtualBox

+   <http://wiki.ubuntuusers.de/VirtualBox/Installation>
+   <https://www.virtualbox.org/wiki/Linux_Downloads>



## Installation

+   `virtualbox-5.2`
+   `dkms`

<!---->

    sudo add-apt-repository 'deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib'

Falls vorhanden, `deb-src` Zeile für das VirtualBox Repository in `/etc/apt/sources.list` (oder in entsprechender Datei unter `sources.list.d`) entfernen.

    wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
    sudo apt-get update
    sudo apt-get install virtualbox-5.2 dkms



## Einrichtung & *Oracle VM VirtualBox Extension Pack*-Installation

1.  Das, der installierten VirtualBox Version entsprechende, Oracle VM VirtualBox Extension Pack von <https://www.virtualbox.org/wiki/Downloads> herunterladen. Falls der entsprechnde Download dort nicht angeboten wird, die gewünschte Version unter <http://download.virtualbox.org/virtualbox> auswählen und die `.vbox-extpack` Datei (`Oracle_VM_VirtualBox_Extension_Pack-<version>-*.vbox-extpack`) manuell herunterladen.
2.  Die `.vbox-extpack` Datei mit einem Doppelklick in VirtualBox öffnen.
3.  Den Installationsprozess abschließen.
4.  VirtualBox beenden.
5.  Nutzer, welche VirtualBox nutzen dürfen, der Gruppe `vboxusers` hinzufügen.
    Für den aktuellen Nutzer bspw. mittels `sudo adduser $USER vboxusers`.
6.  Umgebung neu laden damit die neue Gruppe und die Änderungen an den Nutzern wirksam werden.

        newgrp - vboxusers



## Gast-Erweiterungen

Gast-Erweiterungen für installierte Gast-Betriebssysteme wie unter <http://wiki.ubuntuusers.de/VirtualBox/Installation#Gast-Erweiterungen> beschrieben installieren.
