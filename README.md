# Configuration for the local development environment

## Install Python packages with pip
```
pip install awscli --upgrade --user
python -m pip install --user boto3
python -m pip install --user flask
python -m pip install --user flask-restful

```

## VIM configuration setup
* Create a .vimrc file in the home directory
* Add the below snippets to enable *formatting*, *line number*, *file type indent* and *custom file type indent*
```
  filetype plugin indent on
  syntax on
  set number
  autocmd BufEnter *.tf :setlocal filetype=yaml
  
```

## Settings for the .bash_profile
```
alias python=python3
alias pip=pip3
export JAVA_HOME=/Library/Java/JavaVirtualMachines/OpenJDK-8/Contents/Home
export M2_HOME=/opt/apache-maven
export PYTHON_HOME=/Users/smuralee/Library/Python/3.7
export TERRAFORM_HOME=/opt/terraform-install
export PATH=$PATH:$PYTHON_HOME/bin:$JAVA_HOME/bin:$M2_HOME/bin:$TERRAFORM_HOME

```

## Settings for the Visual Studio Code - settings.json
```
{
    "editor.fontSize": 20,
    "terminal.integrated.fontSize": 20,
    "debug.console.fontSize": 20,
    "markdown.preview.fontSize": 20,
    "workbench.colorTheme": "Dracula",
    "editor.minimap.enabled": false,
    "workbench.iconTheme": "vscode-icons"
}

```

## Setting up OpenJDK (with source) in Ubuntu 18.04 LTS
```
sudo apt-get install openjdk-11-jdk
sudo apt-get install openjdk-11-source
```
## Delete the docker images and containers
```
docker system prune --volumes -f
docker rmi $(docker images -q)
docker system prune -a

```
