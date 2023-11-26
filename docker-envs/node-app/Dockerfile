FROM node:16.3.0-alpine as build
RUN apk update --no-cache
WORKDIR /node-app
COPY --chown=node:node . /node-app

FROM build as main
EXPOSE 8081
USER node
CMD [ "node", "main.js" ]