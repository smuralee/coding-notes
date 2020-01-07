# CLI Commands

## Linux commands

```shell
# Find directory or files recursively
find . -type d -name ".idea" -print
find . -type f -name "*.iml" -print

# List the directories starting with "."
ls -ld .*?
```

## Docker commands

```shell
# Delete the docker images and containers
docker system prune --volumes -f
docker rmi $(docker images -q)
docker system prune -a
```

## Install packages

```shell
pip install <package-name>
npm i -g <package-name>
brew install <package-name>

# Setting up OpenJDK (with source)
sudo apt-get install openjdk-11-jdk
sudo apt-get install openjdk-11-source
```

## Upgrade packages

```shell
# --user : Installs to the user directory
# --upgrade : Upgrades to the newest available version
pip install <package-name> --upgrade --user

# Installs the latest npm package
npm i -g <package-name>

# Updates and upgrades all the packages installed via Homebrew
brew update
brew upgrade
# Verifies if sym links and installs are proper
brew doctor
```

## List all global packages of pip, npm and brew

```shell
npm list -g --depth 0
pip list
brew list
```

## Delete packages

```shell
# Deleting the packages installed from pip
pip freeze > requirements.txt
pip uninstall -r requirements.txt -y
```

