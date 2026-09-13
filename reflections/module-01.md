# Module 1 — Reflection

## What I did
- Merged upstream `origin/main` to sync the repository layout and retrieve Module 1 assignment documentation contracts.
- Explored and documented the multi-language microservices architecture (Frontend in Vanilla JS/Vite, Products Service in PHP/Slim, Users Service in Python/FastAPI, Orders Service in Java/Spring Boot, PostgreSQL database, Prisma migration runner).
- Mapped out the system topology in `docs/exploration/01-system-map.md` with an ASCII/Mermaid diagram.
- Traced a complete `GET /products` request end-to-end with specific `file:line` references across frontend, HTTP routing, database queries, and DOM rendering.
- Identified environment gotchas (e.g. PHP container volume mount overwriting vendor directory, CORS headers across microservices) and documented documentation drift in `ARCHITECTURE.md`.

## What I did not understand at first
- Why the Products Service threw a fatal PHP error regarding `vendor/autoload.php` upon standard `docker compose up`, until discovering that the local volume mount `./products-service:/var/www/html` was overriding the container's built `vendor` folder.
- How cross-service database migrations were handled when 3 services connect to a shared PostgreSQL database, before analyzing the standalone `migration-runner` container.

## What I would do differently
- Run `docker compose exec products-service composer install` immediately after container setup rather than troubleshooting runtime file errors.
- Read through the commit history first to catch documentation drift early (e.g., frontend conversion from React to Vanilla JS).

## How long this took me
- Approximately 2.5 hours total (environment verification, codebase exploration, request tracing, and documentation).
