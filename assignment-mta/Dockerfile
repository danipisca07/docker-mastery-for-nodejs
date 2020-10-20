FROM node:8

RUN apt update -y && apt install -y graphicsmagick

WORKDIR /app

COPY ./package*.json ./

RUN npm install && npm cache clean --force

COPY . .

ENV CHARCOAL_FACTOR=0.1

CMD ["node", "index.js"]

#mount delle cartelle in e out quando esegui il run con:
# cmd: -v %cd%/in:/app/in -v %cd%/out:/app/out
# powershell: -v ${pwd}/in:/app/in -v ${pwd}/out:/app/out
# linux: -v $(pwd)/in:/app/in -v $(pwd)/out:/app/out

#Per sovvrascrivere una env var al run: --env CHARCOAL_FACTOR=10