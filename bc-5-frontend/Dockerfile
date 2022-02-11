FROM node:16 as build-stage

RUN mkdir /app

COPY . /app/

WORKDIR /app

RUN yarn install

RUN yarn run build

ENV PATH /usr/src/app/node_modules/.bin:$PATH  



FROM nginx:alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

COPY --from=build-stage /app/build .

EXPOSE 80

ENTRYPOINT ["nginx","-g","daemon off;"]