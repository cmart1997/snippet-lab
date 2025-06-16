# Docker Compose & Swarm Orchestration Commands

## Docker Compose (single-host)
- `docker compose up -d` – start services in background  
- `docker compose down` – stop & remove containers/networks  
- `docker compose build` – (re)build images  
- `docker compose ps` – list service containers  
- `docker compose logs -f <svc>` – follow logs  
- `docker compose exec <svc> sh` – shell into running service  
- `docker compose config` – view merged, validated YAML  
- `docker compose pull | push` – pull/push service images  
- `docker compose restart <svc>` – restart service(s)  
- `docker compose scale web=3` – legacy scaling (v2)  

## Swarm cluster management
- `docker swarm init` – bootstrap manager  
- `docker swarm join --token <token> HOST:2377` – add worker/manager  
- `docker node ls` – view cluster nodes  
- `docker node update --availability drain <node>` – cordon node  
- `docker node promote|demote <node>` – role change  

## Swarm services & stacks
- `docker service create --name web -p 80:80 nginx`  
- `docker service ls | ps <svc>` – list services / tasks  
- `docker service scale web=5` – scale replicas  
- `docker service update --image nginx:mainline web` – rolling update  
- `docker service rm <svc>` – remove service  
- `docker stack deploy -c compose.yml mystack` – deploy Compose file as stack  
- `docker stack ls | ps mystack` – list stacks / tasks  
- `docker stack rm mystack` – tear down stack  

## Inspect & troubleshoot
- `docker service inspect <svc>` – JSON details  
- `docker service logs -f <svc>` – aggregate logs  
- `docker stack services mystack` – services in stack  
- `docker stack ps mystack --no-trunc` – task history with exit codes  
