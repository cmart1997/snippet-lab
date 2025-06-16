# Docker Essentials Commands

## Images
- `docker pull <image>[:tag]` – download from registry  
- `docker images` – list local images  
- `docker rmi <image|id>` – remove image  
- `docker tag <src> <dst>` – retag  
- `docker build -t <name:tag> .` – build from Dockerfile  
- `docker buildx build …` – multi-arch / advanced builds  
- `docker save -o file.tar <image>` – save to tar  
- `docker load -i file.tar` – load from tar  
- `docker history <image>` – layer history  
- `docker search <term>` – registry search  

## Containers – lifecycle
- `docker run IMAGE [CMD]` – create + start new container  
- `docker create IMAGE` – create (stopped)  
- `docker start|stop <ctr>` – start / graceful stop  
- `docker restart <ctr>` – stop then start  
- `docker pause|unpause <ctr>` – freeze / resume  
- `docker rm <ctr>` – remove stopped container  
- `docker kill <ctr>` – SIGKILL immediately  
- `docker update --memory 1g <ctr>` – live-update limits  

## Exec & inspection
- `docker ps [-a]` – list containers  
- `docker exec -it <ctr> sh` – open shell  
- `docker attach <ctr>` – attach to STDIN/OUT/ERR  
- `docker inspect <obj>` – low-level JSON  
- `docker diff <ctr>` – FS changes since start  
- `docker cp <ctr>:/path ./host` – copy files  

## Volumes & bind-mounts
- `docker volume create <name>`  
- `docker volume ls|inspect|rm`  
- `docker run -v <vol>:/path IMAGE` – named volume  
- `docker run -v $(pwd):/app IMAGE` – bind mount  

## System cleanup
- `docker system df` – disk usage summary  
- `docker system prune` – remove unused data  
- `docker image prune` – dangling images only  
- `docker container prune` – stopped containers  
