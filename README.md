# link
Link up and deploy scripts

For Link manuals please visit [our wiki](https://wiki.bas-ip.com/basiplink/ru/bas-ip-link-2753556.html).

## Link without web proxy
1. Run `docker-compose up -d`

## Link with web proxy (behind nginx)
1. Set variables in the .env (please check [https-portal docs](https://hub.docker.com/r/steveltn/https-portal/) for additional information)
2. Run `docker-compose up -d`

## Upgrade Link v1.1.x to v1.2.x

Please check [manual](./upgrade-link-v1.1.x)
