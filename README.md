# traefik

Monitoring: http://localhost:8080

## simple reverse proxy (entrypoint http and https)

Use  `traefik_http_https` traefik configuration

http://whoami1-docker-traefik.docker.localhost/
http://whoami2-docker-traefik.docker.localhost/
https://app-docker-traefik.docker.localhost/
http://api-docker-traefik.docker.localhost/

## reverse proxy with redirection (entry point http to https)

Use  `traefik_https_to_http` traefik configuration

http://whoami1-docker-traefik.docker.localhost/
http://whoami2-docker-traefik.docker.localhost/
http://app-docker-traefik.docker.localhost/
http://api-docker-traefik.docker.localhost/

API does not work because we can't authorize to access in https
If you want, you just change this line `"traefik.http.routers.api.entrypoints=web"` to `"traefik.http.routers.api.entrypoints=websecure"`

## execute multiple docker compose

docker container stop $(docker container ps -aq) ;\ 
docker container rm -f $(docker container ps -aq) ;\ 
docker-compose -f docker-compose.yml -p traefik up -d ;\ 
docker-compose -f docker-compose2.yml -p whoami1 up -d ;\ 
docker-compose -f docker-compose3.yml -p whoami2 up -d ;\
