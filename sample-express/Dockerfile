FROM node:10.15-slim

ENV NODE_ENV=production

WORKDIR /node 
#I moduli del container saranno in /node/node_modules. Ad ogni modo questa cartella non viene bindata quindi i moduli vengono riscaricati ad ogni rebuild del container(di questo livello)

COPY package.json package-lock*.json ./

RUN npm install && npm cache clean --force

WORKDIR /node/app
#La cartella node_modules in /node/app verrà "mascherata" con una cartella vuota per nascondere i modules dell'host

COPY . .

CMD ["node", "./bin/www"]
