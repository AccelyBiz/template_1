# Next.js Strapi PostgreSQL in Docker

## 1. Clone the repo

## 2. Copy and edit .env.example
cp .env.example .env
Edit .env with your own secrets

## 3. Run the containers
docker compose up

## 4. Develop
Visit localhost:3000 to see the basic Next.js setup
Visit localhost:1337 to access the Strapi admin

Then, develop your page

## 5. Production
switch NODE_ENV from development to production once ready