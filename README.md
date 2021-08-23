# postgres-helm

This project helm chart creates a postgres database, it can be used for local development
where a postgres database is needed.

## Installation
```bash
kubectl create namespace postgres
helm install -n postgres postgres .
kubectl port-forward postgres-postgresql-0 5432:5432
```

## Access
The postgres database has very little security, it does not use TLS and its passwords
are simple, here is sample use for backstage server:

```bash
POSTGRES_HOST=localhost POSTGRES_PORT=5432 POSTGRES_USER=postgres POSTGRES_PASSWORD=postgres npm start
```

You can change these values by providing custom values to helm install command.
