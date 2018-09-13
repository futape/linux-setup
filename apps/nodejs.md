# Node.js

+   <https://nodejs.org>
+   <https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions>
+   <https://github.com/nodesource/distributions#deb>
+   <https://github.com/nodejs/node>
+   <https://wiki.ubuntuusers.de/Node.js/>



## Installation

+   `nodejs`
+	npm
+   `build-essential`

<!---->

    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    sudo apt-get install nodejs build-essential



## Einrichtung

Bei der globalen Installation von Node.js Packages (via npm) kann es aufgrund von mangelnden Berchtigungen auf die Verzeichnisse in die npm die Dateien der global installierten Packages schreiben will, zu `EACCES` Fehlern kommen. Diese sollten nicht mithilfe von `sudo` umgangen werden, sondern es sollte folgendes ausgeführt werden:

1.  Zuerst führt man `npm config get prefix` aus, dies gibt das Verzeichnis zurück in dem npm die Dateien global installierter Packages verteilt. Ist dies nicht gerade ein zu genereller Pfad wie `/usr` sondern bspw. `/usr/local`, könnte man theoretisch einfach den Owner der relevanten Verzeichnisse zum aktuellen Nutzer ändern:

         sudo chown -R $USER:$(id -g) $(npm config get prefix)/{lib/node_modules,bin,share}

    (Vgl. <https://docs.npmjs.com/getting-started/fixing-npm-permissions#option-1-change-the-permission-to-npms-default-directory>)

    Allerdings ist dies keine schöne Lösung, z.B. dann nicht wenn es sich um ein System mit mehreren Nutzern handelt. Deshalb geht man besser wie folgt vor (vgl. <https://docs.npmjs.com/getting-started/fixing-npm-permissions#option-2-change-npms-default-directory-to-another-directory> und <https://wiki.archlinux.org/index.php/Node.js_#Installing_packages>).
2.  Man ändert das Verzeichnis in das npm die Dateien installiert zu einem, auf das man selber (und damit auch npm) Schreibzugriff hat.

        mkdir ~/.npm-packages
        npm config set prefix '~/.npm-packages'

    Alternativ hätte man dies auch mittels der `NPM_CONFIG_PREFIX` Umgebungsvariable definieren können (s. auch <https://github.com/npm/npm/issues/13548>).
3.  Anschließend fügt man das Verzeichnis in das via npm global installierte Binaries geschrieben werden, dem `$PATH` zu:

        echo 'PATH="$HOME/.npm-packages/bin:$PATH"' >> ~/.profile
        source ~/.profile
