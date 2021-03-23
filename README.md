## Getting started

Make sure you have Docker and docker-compose installed and your DNS records set up

```shell
git clone https://github.com/raph6/docker-traefik.git
cd docker-traefik
```

## Setup Traefik
```shell
cd traefik

# create acme.json
touch traefik/acme/acme.json
chmod 600 traefik/acme/acme.json

# create your admin user file
htpasswd -B -C 14 -c traefik/basicAuth/.admin *your-username*
```

`htpasswd` can be found in the package `apache2-utils`

`sudo apt-get install apache2-utils` (adjust for your distribution)

## Run Traefik
In Traefik folder:
Make `.env` file on the same model as `.env.exemple`
```shell
docker-compose up -d
```

or

```shell
EMAIL=your@email.com TRAEFIK_URL=traefik.yourdomain.tld docker-compose up -d
```

## Projects you can use

Feel free to ask for another project

- [Gitlab](gitlab)
- [Jenkins](jenkins)
- [Miniflux](miniflux)
- [Docker Registry](registry)


## Informations
HTTPS is enabled by default, your certificates are generated and automatically renewed

PR are welcome