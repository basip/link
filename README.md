## BAS-IP Link – property management software

Link software offers a centralized access control dashboard allowing you to connect to any BAS-IP hardware.


### Link up and deploy scripts

For Link manuals please visit [our wiki](https://wiki.bas-ip.com/basiplink/ru/bas-ip-link-2753556.html).

### Starting Link
1. Create environment file `cp .env.example .env`
2. Set variables in the .env (please check [https-portal docs](https://hub.docker.com/r/steveltn/https-portal/) for additional information)
3. Create volumes 
```bash
docker volume create app-data
docker volume create system-logs
docker volume create app-storage
docker volume create app-ssl-certs
```
4. Start link `docker-compose up -d`

### Upgrade Link v1.1.x to v1.2.x

Please check [manual](./upgrade-link-v1.1.x)

### Upgrade Link v1.2.8 to v1.2.9

Please check [manual](./upgrade-link-v1.2.8-v1.2.9)

### Upgrade Link v1.2.9 to v1.2.24

Please check [manual](./upgrade-link-v1.2.9-v1.2.24)
