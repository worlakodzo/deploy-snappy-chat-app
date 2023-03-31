# https://cloudnweb.dev/2019/10/crafting-multi-stage-builds-with-docker-in-node-js/


FROM node:19-alpine
# RUN apk update & apk add yarn

WORKDIR /app
COPY package.json yarn.lock ./

RUN yarn install
COPY . ./

EXPOSE 3000
CMD yarn start