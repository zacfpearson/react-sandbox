# build environment
FROM node:lts-alpine as build
WORKDIR /app
ENV PATH /app/node_modules/.bin:$PATH
COPY package.json /app/
RUN yarn --silent
COPY . /app
RUN yarn build

# production environment
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
CMD ["nginx", "-g", "daemon off;"]
