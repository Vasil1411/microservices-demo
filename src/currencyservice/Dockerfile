# Използваме по-нова версия на Node (22), която се изисква от пакетите
FROM node:22-alpine

WORKDIR /app

# Инсталираме python3, make и g++ в Alpine, за да могат нативните модули да се компилират успешно
RUN apk add --no-cache python3 make g++

COPY package*.json ./

# Инсталираме зависимостите
RUN npm install

COPY . .

EXPOSE 7000

CMD ["node", "server.js"]