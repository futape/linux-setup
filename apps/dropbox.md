# Dropbox

+   <http://wiki.ubuntuusers.de/Dropbox>
+   <https://www.dropbox.com>



## Installation

+   `nemo-dropbox`
+   `dropbox` (Als Abhängigkeit von `nemo-dropbox` installiert)
+	Dropbox Daemon

```sh
sudo apt-get install nemo-dropbox
```



## Einrichtung & Dienst-Installation

1.  Dropbox starten.
2.  Dropbox-Verzeichnis auf `~` (`$HOME`) setzen, sodass das Synchronisierte Verzeichnis `~/Dropbox` ist. Dropbox hängt automatisch `Dropbox` an den Pfad an.
3.  Bei Problemen beim Installieren des Dropbox-Dienstes (Daemon), zuerst versuchen Dropbox mittels `dropbox start -i` zu starten.
    Falls das auch nicht klappt, den Dienst mittels `cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -` für 64-bit Systeme bzw. `cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -` für 32-bit Systeme installieren. Der Dienst (`dropboxd` Binary) wird automatisch nach `~/.dropbox-dist` entpackt.
