# Remove Images

Remove all Docker images

```
docker rmi -f $(docker images -qa)
```

Options:
* f - Force removal of the image
* q - Only show numeric IDs
* a - Show all images (default hides intermediate images)

# Run Python simplehttpserver container

```
docker run -it -p 8080:8000 python python3 -m http.server
```

# Cleanup

```
docker rm $(docker ps -aq)
docker rmi $(docker images -aq) -f
docker volume prune -f
```
