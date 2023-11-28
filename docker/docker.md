# docker

## to delete all containers (cmd == prune)

```bash
docker system prune
```

## retrieving logs (cmd == logs)

```bash
docker create busybox echo hi there
docker start dfjk9euerkfjekrj
docker logs dfjk9euerkfjekrj
```

## stopping container (cmd == stop/kill)

`stop` -> SIGTERM (signal to terminate)
`kill` -> SIGKILL (signal to kill) -> shut down right now

```bash
docker stop <container id> # 10 seconds
docker kill <container id>
```

## executing commands in running containers (cmd == exec -it)

```bash
docker exec -it <container id> <command>
docker exec -it 8fjdfjdfu9e redis-cli
docker exec -it euy7wehwhwy sh
```

