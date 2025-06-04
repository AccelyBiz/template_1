# ─────────────────────────────────────────────────────────────────────────────
# Stage 1: Install dependencies and build
# ─────────────────────────────────────────────────────────────────────────────
FROM node:22-alpine AS builder

WORKDIR /app

COPY nextjs/package*.json ./

RUN npm install

COPY nextjs/ ./

RUN npm run build

# ─────────────────────────────────────────────────────────────────────────────
# Stage 2: Create smaller image to serve built output
# ─────────────────────────────────────────────────────────────────────────────
FROM node:22-alpine AS runner

WORKDIR /app

COPY nextjs/package*.json ./

RUN npm install --production

COPY --from=builder /app/.next ./.next
COPY --from=builder /app/public ./public
COPY --from=builder /app/next.config.js ./
COPY --from=builder /app/package.json ./

EXPOSE 3000

ENV NODE_ENV=production

CMD ["npm", "run", "start"]
