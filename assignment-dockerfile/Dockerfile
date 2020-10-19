# fill in the blanks to dockerize this node app
FROM node:10.15.3-alpine

EXPOSE 3000

RUN apk add --update-cache \
    tini \
    && rm -rf /var/cache/apk/*

WORKDIR /usr/src/app

COPY ./package*.json ./

RUN npm install && npm cache clean --force

COPY . .

CMD ["node","app.js"]
