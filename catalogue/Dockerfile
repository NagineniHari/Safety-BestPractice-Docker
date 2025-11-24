## Use Small & Secure Base Images
FROM node:20.19.5-alpine3.22 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
##This may add extra caching memory
RUN npm install 

FROM node:20.19.5-alpine3.22
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
ENV MONGO="true"\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node","server.js"]

