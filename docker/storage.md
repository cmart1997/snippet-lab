# Docker Volumes & Persistent Storage Commands

## Volume lifecycle
- `docker volume create <name>` – new named volume  
- `docker volume ls` – list all volumes  
- `docker volume inspect <name>` – JSON details & mount-point  
- `docker volume rm <name>` – remove unused volume  
- `docker volume prune` – delete **all** unused volumes  

## Use volumes with containers
- `docker run -v <vol>:/data IMAGE` – attach named volume  
- `docker run -v $(pwd):/app IMAGE` – bind-mount host path  
- `docker run --mount type=volume,src=<vol>,dst=/cfg …` – modern `--mount` syntax  
- `docker run --mount type=bind,src=$PWD,dst=/code,ro …` – read-only bind mount  
- `docker run --tmpfs /run:size=64m …` – ephemeral tmpfs  

## Manage data
- `docker cp <ctr>:/path ./host` – copy from container FS  
- `docker cp ./host <ctr>:/path` – copy into container  
- `docker exec <ctr> tar cz /data` – archive data inside volume  

## Plugins & drivers
- `docker plugin ls` / `docker plugin install …`  
- `docker volume create -d rexray/aws-ebs <name>` – cloud driver example  

## Disk usage
- `docker system df` – volume, image & layer sizes  
- `docker system prune --volumes` – prune everything incl. volumes  
