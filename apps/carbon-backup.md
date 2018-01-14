# Helium/Carbon Backup

+   <https://www.clockworkmod.com/carbon>



## Installation

1.  *Helium Desktop* für Linux von <https://www.clockworkmod.com/carbon> herunterladen.
2.  Verzeichnis entpacken und `carbon/linux` Verzeichnis nach `/opt/carbon-backup` kopieren.

        sudo cp -r carbon/linux /opt/carbon-backup
3.  `carbon-backup`-Befehl unter `/usr/bin` einrichten. Datei mit folgendem Inhalt füllen.

        #!/bin/bash

        /opt/carbon-backup/run.sh
4.  Datei ausführbar machen.

        sudo chmod +x /usr/bin/carbon-backup
