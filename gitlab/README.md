## Gitlab

Make sure you have configured Traefik

### Run

Warning, gitlab data is located in _/srv/gitlab/_

In folder:
Make `.env` file on the same model as `.env.exemple`
```shell
docker-compose up -d
```

or

```shell
GITLAB_URL=gitlab.yourdomain.tld docker-compose up -d
```
