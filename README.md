# GarnetServer


### ʹ�� GitHub Packages

```bash
# ��GitHub Packages��ȡ����
docker pull ghcr.io/joesdu/garnet:latest
```

```bash
# �������������������
docker run --name garnet -p 3278:3278 -d --rm -it -e TZ=Asia/Chongqing ghcr.io/joesdu/garnet:latest
```

#### Docker Compose ʹ������

```yml
#version: "3.8"

services:
  garnet:
    image: ghcr.io/joesdu/garnet:latest
    hostname: garnetserver
    environment:
      - TZ=Asia/Chongqing
    volumes:
      - /data/garnet/conf/garnet.conf:/app/conf/garnet.conf
    ports:
      - 3278:3278
    deploy:
      resources:
        limits:
          memory: 5G

volumes:
  data:
    driver: local
    driver_opts:
      type: 'none'
      o: 'bind'
      device: '/data'
```