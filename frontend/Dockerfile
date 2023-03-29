# Muilti-Stage
# https://cloudnweb.dev/2019/10/crafting-multi-stage-builds-with-docker-in-node-js/

# Build Stage 1
# This build created a staging docker image
#
FROM node:10.15.2-alpine AS appbuild
RUN apk update & apk add yarn

WORKDIR /usr/src/app
COPY package.json package-lock.json ./
COPY yarn.lock ./
RUN yarn install
COPY ./src ./src
RUN yarn run build

# Build Stage 2
# This build takes the production build from staging build
#
FROM node:10.15.2-alpine
RUN apk update & apk add yarn

WORKDIR /usr/src/app
COPY package.json package-lock.json ./
COPY yarn.lock ./
RUN yarn install
COPY --from=appbuild /usr/src/app/dist ./dist
EXPOSE 3000
CMD yarn start