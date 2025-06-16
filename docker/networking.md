# Docker Networking Commands

## Expose & publish ports
- `docker run -p 8080:80 IMAGE` – map host 8080 ➜ ctr 80  
- `docker run --expose 443 IMAGE` – expose inside user nets only  
- `docker port <ctr>` – show mappings  

## Manage networks
- `docker network ls` – list  
- `docker network create <net>` – default bridge driver  
- `docker network create -d overlay <net>` – Swarm overlay  
- `docker network inspect <net>` – details / connected containers  
- `docker network rm <net>` – delete (unused)  
- `docker network prune` – remove **all** unused  

## Connect & disconnect
- `docker network connect <net> <ctr>`  
- `docker network disconnect <net> <ctr>`  

## DNS & aliases
- `docker run --network <net> --name web --hostname web …`  
- `docker network connect --alias db mysql-net app`  

## Advanced modes
- `docker run --network host IMAGE` – host networking  
- `docker run --network none IMAGE` – no networking sandbox  
- `docker run --mac-address 02:42:ac:11:00:02 IMAGE` – static MAC  
