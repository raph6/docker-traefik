### Pré-requis

Veillez a bien avoir installé Docker et docker-compose

#### Zone DNS

Vous devez configurer votre zone DNS en pointant vers l'ip de votre serveur

#### Configuration de Traefik

```shell
git clone https://github.com/raph6/compose-traefik-server.git
cd compose-traefik-server

# create acme.json
touch traefik/traefik/acme/acme.json
chmod 600 traefik/traefik/acme/acme.json

# create your admin user file
htpasswd -B -C 12 -c traefik/basicAuth/.admin *your-username*
```

`htpasswd` est disponible dans le packet `apache2-utils`

`sudo apt-get install apache2-utils`

#### Configuration de Registry

```shell
# create your user file
htpasswd -B -C 12 -c registry/auth/htpasswd *your-username*
```

### Lancer Traefik
Vous devez ajouter les variables d'environnements `EMAIL` et `TRAEFIK_URL` avant le docker-compose up -d

Rendez vous dans le dossier de traefik
```shell
# in folder traefik
EMAIL=your@email.com TRAEFIK_URL=traefik.yourdomain.tld docker-compose up -d
```


### Lancer Gitlab

Attention, par défaut Gitlab stockera ses fichiers systèmes dans _/srv/gitlab/_

Vous devez ajouter la variable d'environnement `GITLAB_URL` avant le docker-compose up -d

Rendez vous dans le dossier de gitlab
```shell
# in folder gitlab
GITLAB_URL=gitlab.yourdomain.tld docker-compose up -d
```

### Lancer Jenkins

Vous devez ajouter la variable d'environnement `JENKINS_URL` avant le docker-compose up -d

Rendez vous dans le dossier _jenkins_ contenant le _docker-compose.yml_
```shell
# in folder jenkins
JENKINS_URL=jenkins.yourdomain.tld docker-compose up -d
```


### Lancer un Docker Registry

Vous devez ajouter la variable d'environnement `REGISTRY_URL` avant le docker-compose up -d

Rendez vous dans le dossier _registry_ contenant le _docker-compose.yml_
```shell
# in folder registry
REGISTRY_URL=registry.yourdomain.tld docker-compose up -d
```

Vous pouvez maintenant utiliser votre registry de cette manière
```shell
docker login registry.yourdomain.tld

docker push registry.yourdomain.tld/my_image:my_version

docker pull registry.yourdomain.tld/my_image:my_version
```


### Informations
HTTPS est activé par défaut, vos certificats sont générés et renouvelés automatiquement
