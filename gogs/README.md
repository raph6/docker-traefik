## Gogs

Make sure you have configured Traefik

### Run
In folder:
Make `.env` file on the same model as `.env.exemple`
```shell
docker compose up -d
```

### To install gogs
In Gogs installer

- set `Database Type` to `PostgreSQL`
- set `Host` to `postgres:5432`
- set `SSH Port` to `10022` (if you dont change default)
- set `HTTP Port` to `443`
- set `Application URL` to your website URL (with `https://`)