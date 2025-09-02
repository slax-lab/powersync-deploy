# Slax Reader PowerSync Deployment

### Description

This repository contains the deployment files for the Slax Reader PowerSync service.

## Prerequisites
1. You need to use `cp .env.example .env` to create a .env file, and then edit the .env file to set the environment variables.
2. use `git clone https://github.com/powersync-ja/self-host-demo.git`, this will create a `self-host-demo` folder.
3. `cd self-host-demo && npm install && npm run start`
4. The YAML form of the public key will be printed to the console. Add this to the client_auth->jwks->keys section of ./config/powersync.yaml.
5. The DEMO_JWKS_PUBLIC_KEY and DEMO_JWKS_PUBLIC_KEY values will be printed to the console. Add these values to the .env file in the root of the repository.
6. You need to use `cp ./config/nginx.conf.example ./config/nginx.conf` and edit the nginx.conf file to set the nginx configuration.

## Full Deploy
> Deploy PowerSync's API and sync service

### Deploy 5 API instances
```bash
docker compose -f ./docker-compose-full.yaml up -d --scale powersync-api=5
```

### Scale API instances to 2
```bash
docker-compose -f ./docker-compose-full.yaml up -d --scale powersync-api=2
```

## API Deploy
> Deploy PowerSync's API service

### Deploy 5 API instances
```bash
docker compose -f ./docker-compose-api.yaml up -d --scale powersync-api=5
```

### Scale API instances to 2
```bash
docker-compose -f ./docker-compose-api.yaml up -d --scale powersync-api=2
```