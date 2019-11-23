FROM node:alpine as node-base

WORKDIR /usr/src/app/

COPY ./package.json ./

RUN npm install

COPY ./ ./

CMD ["npm", "run", "build"]

FROM nginx

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

COPY --from=node-base /usr/src/app/build /usr/share/nginx/html

EXPOSE 3000