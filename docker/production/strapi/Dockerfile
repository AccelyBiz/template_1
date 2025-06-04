# ─────────────────────────────────────────────────────────────────────────────
# Stage 1: Install dependencies and build Strapi
# ─────────────────────────────────────────────────────────────────────────────
FROM node:22-alpine AS builder

WORKDIR /app

COPY strapi/package*.json ./

RUN npm install

COPY strapi/ ./

RUN npm run build

# ─────────────────────────────────────────────────────────────────────────────
# Stage 2: Create lean runtime image
# ─────────────────────────────────────────────────────────────────────────────
FROM node:22-alpine AS runner

WORKDIR /app

COPY strapi/package*.json ./

RUN npm install --production

COPY --from=builder /app/build ./build

COPY strapi/src ./src
COPY strapi/public ./public

EXPOSE 1337

ENV NODE_ENV=production

CMD ["npm", "run", "start"]
