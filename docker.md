# Docker Cheatsheet

## Images

```bash
docker images                              # List local images
docker pull <image>:<tag>                  # Pull an image from registry
docker pull nginx:latest                   # Pull latest nginx
docker build -t <name>:<tag> .             # Build image from Dockerfile
docker build -t myapp:1.0 -f Dockerfile . # Build with specific Dockerfile
docker push <image>:<tag>                  # Push image to registry
docker rmi <image>                         # Remove an image
docker rmi $(docker images -q)             # Remove all images
docker tag <image> <newname>:<tag>         # Tag an image
docker image prune                         # Remove dangling images
docker image prune -a                      # Remove all unused images
docker save -o image.tar <image>           # Export image to tar
docker load -i image.tar                   # Import image from tar
docker history <image>                     # Show image layer history
docker inspect <image>                     # Inspect image details
```

## Containers

```bash
docker run <image>                         # Run a container
docker run -it <image> bash                # Run interactively with bash
docker run -d <image>                      # Run in detached mode
docker run --name mycontainer <image>      # Run with a name
docker run -p 8080:80 <image>             # Map host:container port
docker run -v /host/path:/container/path <image>  # Mount a volume
docker run -e ENV_VAR=value <image>        # Set environment variable
docker run --rm <image>                    # Remove container on exit
docker run --network <network> <image>     # Attach to a network

docker ps                                  # List running containers
docker ps -a                               # List all containers
docker stop <container>                    # Stop a container gracefully
docker start <container>                   # Start a stopped container
docker restart <container>                 # Restart a container
docker kill <container>                    # Kill a container immediately
docker rm <container>                      # Remove a stopped container
docker rm -f <container>                   # Force remove a running container
docker rm $(docker ps -aq)                 # Remove all containers

docker exec -it <container> bash           # Open shell in running container
docker exec <container> <command>          # Run command in container
docker logs <container>                    # Show container logs
docker logs -f <container>                 # Follow container logs
docker logs --tail 100 <container>         # Last 100 lines of logs
docker inspect <container>                 # Inspect container details
docker stats                               # Live resource usage stats
docker top <container>                     # Running processes in container
docker cp <container>:/path /host/path     # Copy from container to host
docker cp /host/path <container>:/path     # Copy from host to container
docker diff <container>                    # Show changed files
docker commit <container> <image>:<tag>    # Create image from container
docker rename <old> <new>                  # Rename a container
docker pause <container>                   # Pause a container
docker unpause <container>                 # Unpause a container
```

## Volumes

```bash
docker volume create <name>                # Create a volume
docker volume ls                           # List volumes
docker volume inspect <name>               # Inspect a volume
docker volume rm <name>                    # Remove a volume
docker volume prune                        # Remove all unused volumes
docker run -v <volume>:/path <image>       # Mount a named volume
docker run -v /host:/container <image>     # Bind mount
docker run --mount source=vol,target=/path <image>  # Mount syntax
```

## Networks

```bash
docker network ls                          # List networks
docker network create <name>              # Create a network
docker network create --driver bridge <name>   # Create a bridge network
docker network inspect <name>             # Inspect a network
docker network rm <name>                  # Remove a network
docker network connect <network> <container>  # Connect container to network
docker network disconnect <network> <container>  # Disconnect
docker network prune                       # Remove unused networks
```

## Docker Compose

```bash
docker compose up                          # Start services
docker compose up -d                       # Start in detached mode
docker compose up --build                  # Rebuild images before starting
docker compose down                        # Stop and remove containers
docker compose down -v                     # Also remove volumes
docker compose ps                          # List compose containers
docker compose logs                        # Show logs
docker compose logs -f <service>           # Follow a service's logs
docker compose exec <service> bash         # Open shell in service
docker compose run <service> <command>     # Run a one-off command
docker compose build                       # Build/rebuild services
docker compose pull                        # Pull images
docker compose restart <service>           # Restart a service
docker compose stop                        # Stop services
docker compose start                       # Start stopped services
docker compose config                      # Validate compose file
```

## System & Cleanup

```bash
docker system df                           # Show disk usage
docker system info                         # System-wide information
docker system prune                        # Remove all unused resources
docker system prune -a --volumes           # Full cleanup (use with caution)
docker container prune                     # Remove stopped containers
```

## Dockerfile Reference

```dockerfile
FROM node:20-alpine                        # Base image
WORKDIR /app                               # Set working directory
COPY package*.json ./                      # Copy files
RUN npm install                            # Run command during build
COPY . .                                   # Copy remaining files
ARG NODE_ENV=production                    # Build argument
ENV PORT=3000                              # Environment variable
EXPOSE 3000                                # Document port (does not publish)
VOLUME ["/data"]                           # Create a mount point
USER node                                  # Set user
CMD ["node", "server.js"]                  # Default command
ENTRYPOINT ["node"]                        # Fixed entrypoint
HEALTHCHECK CMD curl -f http://localhost:3000/ || exit 1
LABEL version="1.0" maintainer="me@example.com"
```

## docker-compose.yml Reference

```yaml
version: "3.9"

services:
  web:
    image: nginx:latest
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
    environment:
      - ENV_VAR=value
    env_file:
      - .env
    depends_on:
      - db
    networks:
      - mynet
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost"]
      interval: 30s
      timeout: 10s
      retries: 3

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - db_data:/var/lib/postgresql/data
    networks:
      - mynet

volumes:
  db_data:

networks:
  mynet:
    driver: bridge
```
