# wakatime
https://wakatime.com/projects/swarm02
 
# Ref awaresome-compose
https://github.com/docker/awesome-compose/tree/master/fastapi

# URL Farst-API
https://tan-swarm02.xops.ipv9.me/


# ขั้นตอนในการทำงาน
# 1.Create docker-compose.yml
 1. Create docker-compose.yml
    <details>
    <summary>Show code</summary>

    ```ruby
    version: '3.7'
    services:
    api:
    image: tanankorn/fastapi-api:0205
    networks:
    - webproxy
    environment:
    PORT: 8000
    logging:
    driver: json-file
    volumes:
    - /var/run/docker.sock:/var/run/docker.sock
    - app:/app
    deploy:
    replicas: 1
    labels:
    - traefik.docker.network=webproxy
    - traefik.enable=true
    - traefik.http.routers.${APPNAME}-https.entrypoints=websecure
    - traefik.http.routers.${APPNAME}-https.rule=Host("${APPNAME}.xops.ipv9.me")
    - traefik.http.routers.${APPNAME}-https.tls.certresolver=default
    - traefik.http.services.${APPNAME}.loadbalancer.server.port=8000
    volumes:
    app:          
    networks:
    webproxy:
    external: true
    ```
# 2.Push docker-compose.yml to github swarm01
# 3.Open https://portainer.ipv9.me/
 
 ![image](https://user-images.githubusercontent.com/119097663/224484388-a617001c-cf34-49ce-9d7a-3c3d4b8bfc76.png)

# 4.Click Cluster Xopx.ipv9.xyz on Portainer
 
 ![image](https://user-images.githubusercontent.com/119097663/224484436-f6e5f9a5-5520-409b-8d12-1cfc947404f5.png)
 
# 5.Click menu Stack on Cluster Xopx.ipv9.xyz
 
 ![image](https://user-images.githubusercontent.com/119097663/224484471-88edcac4-dcd8-437d-b741-ead184381b48.png)

# 6.Click button Add Stack

![image](https://user-images.githubusercontent.com/119097663/224484514-0e6de6f0-c04e-44bf-bddb-df9bf0b2bb83.png)

# 7.Click Build medthod is Repository
 
 ![image](https://user-images.githubusercontent.com/119097663/224484639-134b525a-bae2-4187-92ad-f1ee12e08084.png)

 - Name = name Stack
  - Repository URL = TanankornMoonprathom/swarm02 (github.com)
  - Repository reference = refs/heads/main
  - Compose path = name Compose file
  - Automatic updates = enable
    - Fetch interval = time check change on compose file from github 
