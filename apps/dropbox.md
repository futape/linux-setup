# Dropbox

+   <http://wiki.ubuntuusers.de/Dropbox>
+   <https://www.dropbox.com>



## Installation

+   `nemo-dropbox`
+   `dropbox`
+	Dropbox Daemon

<!---->

    sudo apt-get install nemo-dropbox



### Alternative

+   `dropbox`
+	Dropbox Daemon

<!---->

1.  Neueste `.deb` Datei von <https://www.dropbox.com/install-linux> herunterladen.
2.  Installieren.



### Alternative 2

+   `nautilus-dropbox`
+   `dropbox`
+	Dropbox Daemon

<!---->

    sudo apt-get install nautilus-dropbox



### Alternative 3

+   `dropbox`
+	Dropbox Daemon

<!---->

    sudo add-apt-repository 'deb http://linux.dropbox.com/ubuntu xenial main'
    sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 5044912E
    sudo apt-get update
    sudo apt-get install dropbox



## Einrichtung & Dienst-Installation

1.  Dropbox starten.
2.  Dropbox-Verzeichnis auf `~` (`$HOME`) setzen, sodass das Synchronisierte Verzeichnis `~/Dropbox` ist. Dropbox hängt automatisch `Dropbox` an den Pfad an.
    `~/Dropbox` ist ein Symlink auf `/media/daten/Dropbox`, also hätte man theoretisch auch `/media/daten` auswählen können.
3.  Bei Problemen beim Installieren des Dropbox-Dienstes (Daemon), zuerst versuchen Dropbox mittels `dropbox start -i` zu starten.
    Falls das auch nicht klappt, den Dienst mittels `cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -` für 64-bit Systeme bzw. `cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -` für 32-bit Systeme installieren. Der Dienst (`dropboxd` Binary) wird automatisch nach `~/.dropbox-dist` entpackt.
