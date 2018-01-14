# Sublime Text 3

+   <http://www.sublimetext.com/3>
+   <http://www.sublimetext.com/docs/3/linux_repositories.html#apt>
+   <http://docs.sublimetext.info/en/sublime-text-3/getting_started/install.html#id3>
+   <https://wiki.ubuntuusers.de/Sublime_Text/>



## Installation

+   `sublime-text`

<!---->

    wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
    echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
    sudo apt-get update
    sudo apt-get install sublime-text



### Alternative

+   Sublime Text 3

<!---->

1.  Die neueste `.deb` Datei von <http://docs.sublimetext.info/en/sublime-text-3/getting_started/install.html#id3> oder `https://download.sublimetext.com/apt/files/sublime-text_build-<build>_<amd64|i386>.deb` herunterladen.
2.  Installieren.



### Alternative 2

+   Sublime Text 3

<!---->

1.  Neuesten Tarball von <http://www.sublimetext.com/3> herunterladen.
2.  Entpacken.
3.  Entpacktes Verzeichnis nach `/opt` kopieren.
4.  Für die Binary `/opt/sublime_text_3/sublime_text` einen Symlink in `/usr/bin` erstellen.

        sudo ln -s /opt/sublime_text_3/sublime_text /usr/bin/subl
5.  Eine `.desktop` Datei erstellen (Die Leerzeile am Ende nicht vergessen). Ein geeignetes Icon befindet sich unter `/opt/sublime_text_3/Icon/128x128/sublime-text.png`.

        [Desktop Entry]
        Name=Sublime Text 3
        Comment=Sublime Text is a sophisticated text editor for code, markup and prose.
        Categories=TextEditor;IDE;Development
        GenericName=Text Editor
        Icon=/opt/sublime_text_3/Icon/128x128/sublime-text.png

        Exec=subl
        Terminal=false
        Type=Application



## Einrichtung

1.  Sublime Text öffnen und unter ***Help* &gt; *Enter License*** den Lizensschlüssel eingeben.
