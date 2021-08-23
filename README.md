# postgres-helm

This project helm chart creates a postgres database, it can be used for local development
where a postgres database is needed.

## Installation
```bash
helm repo add postgres-helm https://seizadi.github.io/postgres-helm/
kubectl create namespace postgres
helm install -n postgres postgres postgres-helm/postgres
kubectl port-forward postgres-postgresql-0 5432:5432
```

## Access
The postgres database has very little security, it does not use TLS and its passwords
are simple, here is sample use for backstage server:

```bash
POSTGRES_HOST=localhost POSTGRES_PORT=5432 POSTGRES_USER=postgres POSTGRES_PASSWORD=postgres npm start
```

You can change these values by providing custom values to helm install command.

## Helm Github Repo
Reference this blog for how to create a 
[Github Helm Repo](https://medium.com/@mattiaperi/create-a-public-helm-chart-repository-with-github-pages-49b180dbb417)

This is the helm command for this repo:
```bash
helm repo index --url https://seizadi.github.io/postgres-helm/ . 
```
