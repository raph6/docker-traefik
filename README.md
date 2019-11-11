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
Vous devez ajouter les variables d'environnements `EMAIL` et `DOMAIN_URL` avant le docker-compose up -d

Rendez vous dans le dossier de traefik
```
EMAIL=your@email.com DOMAIN_URL=yourdomain.tld docker-compose up -d
```


### Lancer Gitlab

Attention, par défaut Gitlab stockera ses fichiers systèmes dans _/srv/gitlab/_

Vous devez ajouter la variable d'environnement `DOMAIN_URL` avant le docker-compose up -d

Rendez vous dans le dossier de gitlab
```
DOMAIN_URL=yourdomain.tld docker-compose up -d
```

### Lancer Jenkins

Vous devez ajouter la variable d'environnement `DOMAIN_URL` avant le docker-compose up -d

Rendez vous dans le dossier de jenkins
```
DOMAIN_URL=yourdomain.tld docker-compose up -d
```


### Informations
HTTPS est activé par défaut, vos certificats sont générés et renouvelés automatiquement
