# DevOps with Docker
Mooc.fi course for Docker

## Docker commands cheatsheet

### 1. Listing images and containers

List images you have currently downloaded
```
docker images
```

List containers that are running
```
docker container ls
```

### 2. Running images

Run docker image; run detached
```
> docker run <image>
> docker run -d <image>
```

Stop image that is being run
```
docker stop <container name or ID>
```

### 3. Removing containers and images

Remove container
```
docker rm <container ID or name>
```
> Example: Delete two images by selecting with IDs
```
docker rm 48 f7
```

Prune container (removes all stopped containers)
```
docker container prune
```

Prune all dangling containers; prune images as well
```
docker system prune
docker system prune -a
```

Remove image
```
docker rmi <image>
```

### 4. Building, pushing and pulling

Build a new image
```
docker build .
```

Pull image without running it
```
docker pull <image name>
```

### 5. Enter running containers

Enter a container and use its command line
```
docker exec -it <container name or ID> <command>
```

> Example:
```
docker exec -it looper bash
```

### 6. Managing running containers

View logs; stream logs
```
docker logs <container name or ID>
docker logs -f <container name or ID>
```

Pause and unpause containers
```
docker pause <container name or ID>
docker unpause <container name or ID>
```