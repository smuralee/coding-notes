# Unix Terminal Commands

## UNIX commands
* Find directory or files recursively
```
find . -type d -name ".idea" -print
find . -type f -name "*.iml" -print
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
