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
      compoent="cart" \
      created_by="haribabu"
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
COPY --from=build --chown=roboshop:roboshop /opt/server /opt/server
USER roboshop
ENTRYPOINT ["node","server.js"]


