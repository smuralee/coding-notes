# Container Commands

## Docker Commands

### Delete the docker images and containers
```
docker system prune --volumes -f
docker rmi $(docker images -q)
docker system prune -a

```

## AWS Commands

* *Login into ECR* - `$(aws ecr get-login --no-include-email)`
