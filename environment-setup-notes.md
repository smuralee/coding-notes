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

## Settings for the .bash_profile on Mac
```shell
alias python=python3
alias pip=pip3
export JAVA_HOME=/Library/Java/JavaVirtualMachines/OpenJDK-8/Contents/Home
export M2_HOME=/opt/apache-maven
export TERRAFORM_HOME=/opt/terraform-install
export PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin:$TERRAFORM_HOME

```

## Settings for the .bashrc or .profile on Linux
```shell
# Java Classpath
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH="$PATH:$HOME/bin:$JAVA_HOME/bin:$HOME/.local/bin"

# GO Classpath
export PATH="$HOME/.cargo/bin:$PATH"

# RUST Classpath
export PATH="$PATH:/usr/local/go/bin"

# Install Ruby Gems to ~/gems
export GEM_HOME="$HOME/gems"
export PATH="$HOME/gems/bin:$PATH"

# Alias for the python installations
alias python=python3
alias pip=pip3

# Colour scheme for terminal
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;31m\]\w\[\033[00m\]\$ '

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
