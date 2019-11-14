### Getting started

Make sure you have Docker and docker-compose installed and your DNS records set up

```shell
git clone https://github.com/raph6/compose-traefik-server.git
cd compose-traefik-server

###
# Setup Traefik 
###
# create acme.json
touch traefik/traefik/acme/acme.json
chmod 600 traefik/traefik/acme/acme.json

# create your admin user file
htpasswd -B -C 12 -c traefik/basicAuth/.admin *your-username*
```

`htpasswd` can be found in the package `apache2-utils`

`sudo apt-get install apache2-utils` (adjust for your distribution)

```shell
###
# Setup registry
###
# create your user file
htpasswd -B -C 12 -c registry/auth/htpasswd *your-username*
```

### Run Traefik
Add the environment variables `EMAIL` (for Certbot) and `TRAEFIK_URL`

```shell
# traefik/
EMAIL=your@email.com TRAEFIK_URL=traefik.yourdomain.tld docker-compose up -d
```

### Run Gitlab

Warning, gitlab data is located in _/srv/gitlab/_

Add the environment variable `GITLAB_URL`

```shell
# gitlab/
GITLAB_URL=gitlab.yourdomain.tld docker-compose up -d
```

### Run Jenkins

Add the environment variable `JENKINS_URL`

```shell
# jenkins/
JENKINS_URL=jenkins.yourdomain.tld docker-compose up -d
```


### Run Docker Registry

Add the environment variable `REGISTRY_URL`

```shell
# registry/
REGISTRY_URL=registry.yourdomain.tld docker-compose up -d
```

Now your can use your docker registry like this
```shell
docker login registry.yourdomain.tld

docker push registry.yourdomain.tld/my_image:my_version

docker pull registry.yourdomain.tld/my_image:my_version
```


### Informations
HTTPS is enabled by default, your certificates are generated and automatically renewed
