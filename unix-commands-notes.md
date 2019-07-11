# Unix Terminal Commands

## UNIX commands
* Find directory or files recursively
```
find . -type d -name ".idea" -print
find . -type f -name "*.iml" -print
```

* List all global packages of npm, pip and brew
```
npm list -g --depth 0
pip list
brew list
```

* Update packages
```
npm i -g <package-name>
pip install <package-name>
brew install <package-name>
```

## Docker Commands

### Delete the docker images and containers
```
docker system prune --volumes -f
docker rmi $(docker images -q)
docker system prune -a

```

## AWS Commands

* *Login into ECR* - `$(aws ecr get-login --no-include-email)`
