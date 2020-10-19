#docker build -t image:prod --target prod .
FROM node:10-slim as prod
EXPOSE 3000
ENV NODE_ENV=production
WORKDIR /app
COPY ./package*.json ./
RUN npm install --only=production && npm cache clean --force
COPY . .
CMD ["node","./bin/www"]

#docker build -t image:dev --target dev .
FROM prod as dev
ENV NODE_ENV=development
RUN npm install --only=development
CMD ["../node_modules/nodemon/bin/nodemon.js","./bin/www", "--inspect=0.0.0.0:9229"]

#docker build -t image:test --target test .
FROM dev as test
ENV NODE_ENV=development
CMD ["npm", "test"]
#In ambiente di test non è un problema lanciare npm anziche node direttamente


#Se non specifico un target allora in ogni caso builda fino alla fine quindi l'immagine risultante è test