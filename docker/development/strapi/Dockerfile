FROM node:22-alpine

WORKDIR /app

COPY strapi/package*.json ./

RUN npm install

COPY strapi/ ./

RUN npm run build

EXPOSE 1337

ENV NODE_ENV=development

CMD ["npm", "run", "develop"]