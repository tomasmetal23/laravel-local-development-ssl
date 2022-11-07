# Traefik v2 HTTPS Laravel (SSL) on localhost

This repo is a minimal template to use Traefik v2 and Laravel Framework to develop on localhost with HTTPS support.



To get started, just clone this repo:

```
git clone https://github.com/tomasmetal23/laravel-local-development-ssl.git
```
## Install Mkcert
```
curl -JLO "https://dl.filippo.io/mkcert/latest?for=linux/amd64"
chmod +x mkcert-v*-linux-amd64
sudo cp mkcert-v*-linux-amd64 /usr/local/bin/mkcert
```

Next, go to the root of the repo (`cd traefik-v2-https-ssl-localhost`) and generate certificates using [mkcert](https://github.com/FiloSottile/mkcert) :

```bash
# If it's the firt install of mkcert, run
mkcert -install

# Generate certificate for domain "docker.localhost", "domain.local" and their sub-domains
sudo mkcert -cert-file traefik-v2-https-ssl-localhost/certs/local-cert.pem -key-file traefik-v2-https-ssl-localhost/certs/local-key.pem "docker.localhost" "*.docker.localhost" "domain.local" "*.domain.local"
```

## Create the networking
```bash
$ docker network create web 


$ docker network create database 
```
## Edit environments
```bash
$ cp example.env .env

$ docker-compose up -d 

```
You can now go to your browser at [whoami.docker.localhost](https://whoami.docker.localhost), enjoy :rocket: !

*Note: you can access to Træfik dashboard at: [traefik.docker.localhost](https://traefik.docker.localhost)*

Don't forget that you can also map TCP and UDP through Træfik.


## Comunication
```bash
###List all artisan commands:
$ docker-compose exec my-laravel-app php artisan list

###List all registered routes:
$ docker-compose exec my-laravel-app php artisan route:list

###Create a new application controller named UserController:
$ docker-compose exec my-laravel-app php artisan make:controller UserController

###Installing a new composer package called phpmailer/phpmailer with version 5.2.*:
$ docker-compose exec my-laravel-app composer require phpmailer/phpmailer:5.2.*
```




# License

MIT
