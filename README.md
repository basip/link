# link
Link up and deploy scripts

For Link manuals please visit [our wiki](https://wiki.bas-ip.com/basiplink/ru/bas-ip-link-2753556.html).

## Link behind nginx
1. Set variables in the env and rename it to the .env.
2. Install certbot, get certs for your domain and put them (fullchain.pem, privkey.pem) to the /link-nginx/ssl-certs/ directory.
3. Run docker-compose. If you're using Link without SIP server - remove unnecessary ports.
