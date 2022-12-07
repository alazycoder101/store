# README

# Solidus
```
rails new store --skip-javascript -T -d postgresql

cd store
bundle add solidus && bundle
bin/rails generate solidus:install --frontend=solidus_starter_frontend
```

## How to run
```bash
# install docker engine

docker compose build -f docker/docker-compose.yml --progress=plain
docker compose -f docker/docker-compose.yml build web

# or cd to docker as current directory
cd docker
docker-compose build web
docker-compose up web
```

Reference
---
1. https://github.com/solidusio/solidus_starter_frontend
