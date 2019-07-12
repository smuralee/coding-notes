# Unix Terminal Commands

## UNIX commands
* Find directory or files recursively
```shell
find . -type d -name ".idea" -print
find . -type f -name "*.iml" -print
```

* List all global packages of npm, pip and brew
```shell
npm list -g --depth 0
pip list
brew list
```

* Update packages
```shell
npm i -g <package-name>
pip install <package-name>
brew install <package-name>
```

## Docker Commands

* Delete the docker images and containers
```shell
docker system prune --volumes -f
docker rmi $(docker images -q)
docker system prune -a

```

## AWS Commands

* Login into ECR
```shell
$(aws ecr get-login --no-include-email)
```
