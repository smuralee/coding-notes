# Environment Setup

## VIM configuration setup
* Create a .vimrc file in the home directory
* Add the below snippets to enable *formatting*, *line number*, *file type indent* and *custom file type indent*
* Supporting .tf file as YAML

```shell
filetype plugin indent on
syntax on
set number
autocmd BufEnter *.tf :setlocal filetype=yaml
  
```

## Settings for the .bash_profile
```shell
alias python=python3
alias pip=pip3
export JAVA_HOME=/Library/Java/JavaVirtualMachines/OpenJDK-8/Contents/Home
export M2_HOME=/opt/apache-maven
export TERRAFORM_HOME=/opt/terraform-install
export PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin:$TERRAFORM_HOME

```

## Setup a Python Virtual Environment
```shell
pip install virtualenv
cd python-scripts
virtualenv venv
source venv/bin/activate
pip install <package>
deactivate
```
