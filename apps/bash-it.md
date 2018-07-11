# Bash-it

+   <https://github.com/Bash-it/bash-it>



## Installation

+	Bast-it

<!---->

1.	`git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it`
2.	`~/.bash_it/install.sh` und erstelle ein Backup des ` .bashrc` Datei (anstatt die Bas-it Konfiguration enzuhängen)
3.	Lade das `.bashrc` Backup in am Anfang der neuen `.bashrc`:
	
		if [ -f ~/.bashrc.bak ]; then
			. ~/.bashrc.bak
		fi
4.	Lade `.bashrc` Datei im `.profile` bzw. `.bash_profile` (falls nicht bereits vorhanden):

		if [ -f ~/.bashrc ]; then
			. ~/.bashrc
		fi
