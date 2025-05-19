FROM node:24-alpine

WORKDIR /usr/src/app

RUN npm install -g pnpm

COPY pnpm-lock.yaml ./
COPY package.json ./

RUN pnpm install --frozen-lockfile

COPY . .

RUN npm add -g typescript ts-node

EXPOSE 3000

CMD ["ts-node", "server.ts"] 