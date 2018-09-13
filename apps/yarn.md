# Yarn

+	<https://yarnpkg.com/en/>
+	<https://yarnpkg.com/en/docs/install#debian-stable>



## Installation

+	`yarn`

```sh
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update
sudo apt-get install yarn
```