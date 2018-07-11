# Docker CE

+	<https://www.docker.com>
+	<https://docs.docker.com/install/linux/docker-ce/ubuntu/>
+	<https://docs.docker.com/install/linux/linux-postinstall/>



## Installation

+   `docker-ce`

<!---->

1.	Notwendige Pakete installieren:

		sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
2.	GPG Key des Repositorys hinzufügen:

		curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
3.	Repository hinzufügen:

		sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu xenial stable"
4.	Neue Pakte einlesen:

		sudo apt-get update
5.	Docker installieren:

		sudo apt-get install docker-ce



## Einrichtung

Docker für nicht-root User nutzbar machen indem der Nutzer zur `docker`  Gruppe hinzugefügt wird:

	sudo groupadd docker
	sudo usermod -aG docker $USER

Anschließend ab- und wieder anmelden damit die Zuordnung wirksam wird.
