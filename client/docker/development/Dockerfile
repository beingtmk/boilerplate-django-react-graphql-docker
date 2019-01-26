FROM node:latest as build-deps

COPY . /app

WORKDIR /app
RUN yarn install

COPY ./docker/development/scripts/start.sh /start.sh
RUN sed -i 's/\r//' /start.sh
RUN chmod +x /start.sh
