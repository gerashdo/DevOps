FROM node:lts-alpine

ENV NODE_ENV=production

COPY . /app

WORKDIR /app

RUN npm install

EXPOSE 3000

CMD npm start
