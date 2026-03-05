# Docker LEMP Stack

A ready-to-use local development environment with multi-PHP support, XDebug, and a full suite of backend services, all containerised with Docker.

Built for projects that need to run across multiple PHP versions simultaneously (5.6, 7.4, 8.x) without touching your local machine.

## Stack

| Service | Details |
|---|---|
| **Web Server** | NGINX |
| **PHP** | 5.6, 7.4, 8.x (latest) |
| **Database** | MariaDB |
| **Cache** | Redis, Memcached |
| **Search** | ElasticSearch |
| **Queue** | RabbitMQ |
| **Storage** | MongoDB |
| **Mail** | Mailhog (local email testing) |
| **Admin** | PHPMyAdmin |
| **Runtime** | Node.js |
| **Debugging** | XDebug |

## Getting Started

Edit the `docker-compose.yml` args to match your local user UID and GID. This ensures file permissions inside the PHP container match `www-data` so you can edit files without permission issues.

Then copy and configure your environment:

```bash
cp .env.example .env
# Edit .env to set your preferred variables
docker-compose up -d
```

## Local URLs

| Service | URL | Folder |
|---|---|---|
| NGINX | http://localhost/ | `var/www/` |
| Node | http://localhost:3000/ | `var/app/` |
| PHPMyAdmin | http://localhost:8080/ | |
| Mailhog | http://localhost:8025/ | |

## Accessing Containers

**PHP servers:**
```bash
docker-compose exec php56-fpm bash   # PHP 5.6
docker-compose exec php74-fpm bash   # PHP 7.4
docker-compose exec php-fpm bash     # PHP 8 (latest)
```

**Node server:**
```bash
docker-compose exec node bash           # Node user
docker-compose exec -u root node bash   # Root user
```

## Configuration

All default variables are set in the `.env` file at the root of the project.
