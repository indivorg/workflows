FROM node:18.3.0-alpine3.14 as build

WORKDIR /usr/src/app

ARG NPM_TOKEN

COPY package*.json yarn.lock ./

RUN yarn install

COPY . .

RUN yarn build

FROM node:18.3.0-alpine3.14

WORKDIR /usr/src/app

COPY --from=build /usr/src/app/node_modules ./node_modules
COPY --from=build /usr/src/app/dist ./dist

CMD ["node", "dist/main"]
