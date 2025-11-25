## FROM node:20.19.5-alpine3.22 AS build
FROM node:20.19.5-alpine3.21 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20.19.5-alpine3.21
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
ENV REDIS_HOST="redis" \
    CATALOGUE_HOST="catalogue" \
    CATALOGUE_PORT="8080"
WORKDIR /opt/server
COPY --from=build /opt/server /opt/server
RUN chown -R roboshop:roboshop /opt/server
USER roboshop
CMD ["node","server.js"]