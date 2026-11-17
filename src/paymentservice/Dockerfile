FROM node:22-alpine

WORKDIR /app

# Инсталираме Python и инструменти за компилация на native модули (node-gyp / pprof)
RUN apk add --no-cache python3 make g++

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 50051
CMD ["node", "index.js"]