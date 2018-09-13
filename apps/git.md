# Git

+   <http://wiki.ubuntuusers.de/Git>



## Installation

+   `git`
+   `git-gui`

<!---->

    sudo add-apt-repository ppa:git-core/ppa
    sudo apt-get update
    sudo apt-get install git git-gui



## Einrichtung

1.	Nutzerinformationen festlegen:
	
	```sh
	git config --global user.name "<name>"
	git config --global user.email "<email>"
	```
2.	Editor wählen:
	
	```sh
	git config --global core.editor "subl -n -w"
	```