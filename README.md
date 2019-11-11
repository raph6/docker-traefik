### Pré-requis

Veillez a bien avoir installé Docker et docker-compose

#### Zone DNS

Vous devez configurer votre zone DNS en pointant vers l'ip de votre serveur

#### Traefik

Rendez vous dans le dossier `traefik`
```
cd traefik
```

Le fichier `acme.json` est le fichier où sont stocker les certificats ACME
```
touch traefik/acme/acme.json
chmod 600 traefik/acme/acme.json
```

Création d'un fichier basicAuth pour vos administrateurs
```
htpasswd -B -C 12 -c traefik/basicAuth/.admin *your-username*
```

`htpasswd` est disponible dans le packet `apache2-utils`

`sudo apt-get install apache2-utils`


### Lancer Traefik
Vous devez ajouter les variables d'environnements `EMAIL` et `TRAEFIK_URL` avant le docker-compose up -d

Rendez vous dans le dossier de traefik
```
EMAIL=your@email.com TRAEFIK_URL=traefik.yourdomain.tld docker-compose up -d
```


### Lancer Gitlab

Attention, par défaut Gitlab stockera ses fichiers systèmes dans _/srv/gitlab/_

Vous devez ajouter la variable d'environnement `GITLAB_URL` avant le docker-compose up -d

Rendez vous dans le dossier de gitlab
```
GITLAB_URL=gitlab.yourdomain.tld docker-compose up -d
```

### Lancer Jenkins

Vous devez ajouter la variable d'environnement `JENKINS_URL` avant le docker-compose up -d

Rendez vous dans le dossier _jenkins_ contenant le _docker-compose.yml_
```
JENKINS_URL=jenkins.yourdomain.tld docker-compose up -d
```


### Lancer un Docker Registry

#### Pré-requis
- Créer un fichier htpasswd pour les utilisateurs de votre Docker Registry
```
(registry folder)
htpasswd -B -C 12 -c auth/htpasswd *your-username*
```

Vous devez ajouter la variable d'environnement `REGISTRY_URL` avant le docker-compose up -d

Rendez vous dans le dossier _registry_ contenant le _docker-compose.yml_
```
REGISTRY_URL=registry.yourdomain.tld docker-compose up -d
```

Vous pouvez maintenant utiliser votre registry de cette manière
```
docker login registry.yourdomain.tld

docker push registry.yourdomain.tld/my_image:my_version

docker pull registry.yourdomain.tld/my_image:my_version
```


### Informations
HTTPS est activé par défaut, vos certificats sont générés et renouvelés automatiquement
