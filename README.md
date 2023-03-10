# Minecraft Server Docker Image (Purpur 1.19.3)

## Installation

1- Install Docker  
2- Clone this repository  
3- Run `docker build -t purpurmc-server .`  
4- create `docker-compose.yml` file and add this code:
(Dont forget to change the volumes path according to your needs)

```docker
version: '1'
services:
  mc-server:
    image: purpur-server
    container_name: mc-server
    environment:
      - MINMEM=-Xms100M
      - MAXMEM=-Xmx4096M
    ports:
      - 25565:25565/tcp
      - 25565:25565/udp
    volumes:
      - $HOME/mc-server/plugins:/mc-server/plugins
      - $HOME/mc-server/world:/mc-server/world
      - $HOME/mc-server/server.properties:/mc-server/server.properties
      - $HOME/mc-server/logs:/mc-server/logs
    restart: 'unless-stopped'

```

5- Run `docker-compose up -d`