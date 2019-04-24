# Environment Setup Notes

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
