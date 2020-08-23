# Local Development Settings

## VIM configuration
* Create a .vimrc file in the home directory
* Add the below snippets to enable *formatting*, *line number*, *file type indent* and *custom file type indent*
* Supporting .tf file as YAML

```shell
filetype plugin indent on
syntax on
set number
autocmd BufEnter *.tf :setlocal filetype=yaml
```

## .bash_profile for MacOS

```shell
alias python=python3
alias pip=pip3
export JAVA_HOME=/Library/Java/JavaVirtualMachines/OpenJDK-8/Contents/Home
export M2_HOME=/opt/apache-maven
export TERRAFORM_HOME=/opt/terraform-install
export PATH=$PATH:$JAVA_HOME/bin:$M2_HOME/bin:$TERRAFORM_HOME
```

## .profile on Linux

```shell
# Java Classpath
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH="$JAVA_HOME/bin:$PATH"

# RUST Classpath
export PATH="$HOME/.cargo/bin:$PATH"

# GO Classpath
export PATH="$PATH:/usr/local/go/bin"

# Install Ruby Gems to ~/gems
export GEM_HOME="$HOME/gems"
export PATH="$HOME/gems/bin:$PATH"
```

## .bashrc on Linux

```shell
# Alias for the python installations
alias python=python3
alias pip=pip3

# Colour scheme for terminal
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;31m\]\w\[\033[00m\]\$ '

export PATH="$PATH:$HOME/bin:$HOME/.local/bin"
```

## Python Virtual Environment

```shell
pip install virtualenv
cd python-scripts
virtualenv venv
source venv/bin/activate
pip install <package>
deactivate
```

## Visual Studio Code - settings.json

```json
{
    "editor.fontSize": 20,
    "terminal.integrated.fontSize": 20,
    "debug.console.fontSize": 20,
    "markdown.preview.fontSize": 20,
    "workbench.colorTheme": "Dracula",
    "editor.minimap.enabled": false,
    "workbench.iconTheme": "vscode-icons",
    "[typescript]": {
        "editor.defaultFormatter": "vscode.typescript-language-features"
    },
    "vsicons.projectDetection.autoReload": true,
    "editor.formatOnSave": true
}
```
