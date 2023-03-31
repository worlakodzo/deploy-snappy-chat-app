#https://progressivecoder.com/docker-multi-stage-build-for-running-react-application-on-nginx-server/
#Specify a base image
FROM node:19-alpine as builder 

#Specify a working directory
WORKDIR /app

#Copy the dependencies file
COPY package.json package-lock.json yarn.lock ./

#Install dependencies
RUN yarn install

#Copy remaining files
COPY . .

#Build the project for production
RUN yarn run build 

#Run Stage Start
FROM nginx:1.23.4-alpine

#Copy production build files from builder phase to nginx
COPY --from=builder /app/build /usr/share/nginx/html
COPY default.conf /etc/nginx/conf.d/