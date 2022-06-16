# GovCMS Ops - API PoC

## Local development

### Requirements

- [Tilt.dev](https://tilt.dev/)

### Setup

```bash
git clone https://github.com/govcms-extras/poc govcms-api
cd govcms-api/
tilt up
```

### Local hosts

You can edit your local host or use the localhost with different ports to access the local services

```bash
# GovCMS API
127.0.0.1 api-oauth client2
127.0.0.1 api.govcms.local
127.0.0.1 api-oauth.govcms.local
127.0.0.1 api-keycloak.govcms.local
127.0.0.1 api-miniorange.govcms.local
127.0.0.1 client1.govcms.local
127.0.0.1 client2.govcms.local
```