# Docker Logging & Visibility Commands

## Container logs
- `docker logs <ctr>` – fetch STDOUT/ERR  
- `docker logs -f --tail 100 <ctr>` – follow last 100 lines  
- `docker logs --since 30m <ctr>` – last 30 minutes  

### Configure driver at run
- `docker run --log-driver json-file …` (default)  
- `docker run --log-driver syslog …`  
- `docker run --log-opt max-size=10m --log-opt max-file=3 …`  

## Runtime telemetry
- `docker stats [ctr…]` – live CPU / mem / I/O  
- `docker events` – real-time daemon event stream  

## Debug & inspection
- `docker inspect <ctr>` – full spec JSON  
- `docker top <ctr>` – processes inside container  
- `docker image inspect <img>` – metadata & digest  
- `docker diff <ctr>` – FS changes since start  

## System-wide info
- `docker info` – daemon & host summary  
- `docker system df` – disk-usage breakdown  
