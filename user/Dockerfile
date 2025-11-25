## Use Small & Secure Base Images
FROM node:20.19.5-alpine3.22 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
##This may add extra caching memory
RUN npm install 
FROM node:20.19.5-alpine3.22
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
EXPOSE 8080
LABEL com.project="roboshop" \
      compoent="user" \
      created_by="haribabu"
ENV MONGO="true" \
    REDIS_URL='redis://redis:6379' \
    MONGO_URL="mongodb://mongodb:27017/users"
COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server
USER roboshop
ENTRYPOINT ["node","server.js"]























