## Miniflux

Make sure you have configured Traefik

### Run
In folder:
Make `.env` file on the same model as `.env.exemple`
```shell
docker compose up -d
```

or

```shell
MINIFLUX_URL=feed.your-domain.com MINIFLUX_POSTGRES_USER=user MINIFLUX_POSTGRES_PASSWORD=password
docker compose up -d
```
