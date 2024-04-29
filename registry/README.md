## Docker Registry

Make sure you have configured Traefik

### Setup
Create your user file
```shell
htpasswd -B -C 14 -c auth/htpasswd *your-username*
```

### Run
In folder:
Make `.env` file on the same model as `.env.exemple`
```shell
docker compose up -d
```

or

```shell
REGISTRY_URL=registry.yourdomain.tld docker compose up -d
```

### Informations

Now your can use your docker registry like this
```shell
docker login registry.yourdomain.tld

docker push registry.yourdomain.tld/my_image:my_version

docker pull registry.yourdomain.tld/my_image:my_version
```
