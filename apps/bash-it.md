# Bash-it

+   <https://github.com/Bash-it/bash-it>



## Installation

+	Bash-it

<!---->

1.	Git installieren
2.	`git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it`
3.	`~/.bash_it/install.sh` und erstellt ein Backup des ` .bashrc` Datei (anstatt die Bash-it Konfiguration enzuhängen)
4.	Lade das `.bashrc` Backup in am Anfang der neuen `.bashrc`:
	
		if [ -f ~/.bashrc.bak ]; then
			. ~/.bashrc.bak
		fi
5.	Lade `.bashrc` Datei im `.profile` bzw. `.bash_profile` (falls nicht bereits vorhanden):

		if [ -f ~/.bashrc ]; then
			. ~/.bashrc
		fi
6.	Bash-it über die `.bashrc` Datei konfigurieren:

	+	`BASH_IT_THEME` auf `pure` setzen
	+	`export SCM_GIT_SHOW_MINIMAL_INFO=true` hinzufügen