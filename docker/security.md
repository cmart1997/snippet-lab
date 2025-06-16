# Docker Security & Hardening Commands

## Image provenance
- `docker trust sign <img>` – sign (Content Trust)  
- `docker trust inspect --pretty <img>` – verify signatures  
- `DOCKER_CONTENT_TRUST=1 docker pull <img>` – enforce trust  

## Scan & SBOM
- `docker scan <img>` – vulnerability scan (Snyk)  
- `docker sbom <img>` – Software Bill of Materials (v24+)  

## Least-privilege runtime
- `docker run --user 1001:1001 …` – drop root  
- `docker run --read-only …` – root FS read-only  
- `docker run --cap-drop all --cap-add net_bind_service …`  
- `docker run --security-opt no-new-privileges …`  
- `docker run --pids-limit 100 …` – PID cap  
- `docker run --privileged …` ← avoid unless absolutely needed  

## Secrets & configs (Swarm)
- `docker secret create <name> file.txt`  
- `docker service create --secret <name> IMAGE`  
- `docker secret rm <name>`  

## Daemon / host hardening
- `dockerd --icc=false --userns-remap=default`  
- `docker context ls|use` – avoid accidental prod context  
