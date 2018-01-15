# git-flow

+   <https://github.com/nvie/gitflow>
+   <https://github.com/nvie/gitflow/wiki/Linux>



## Installation

+   `git-flow`

<!---->

    sudo apt-get install git-flow



## Einrichtung

1.	Falls beim Erstellen eines neuen Feature Branches vorher immer der aktuelle Stand gepulled werden soll kann folgende Konfiguration vorgenommen werden:

		git config --global gitflow.feature.start.fetch true

	Dasselbe kann auch für `release`, `hotfix` und `support` Branches konfiguriert werden.
