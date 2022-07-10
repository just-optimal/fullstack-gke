#######
# BUILD
#######


FROM node:alpine AS build

WORKDIR /usr/src/app

COPY package.json ./
COPY yarn.lock ./

RUN yarn install

COPY . .

RUN yarn build --prod


# #############
# # PRODUCTION
# #############

FROM nginx:alpine

COPY ./nginx.conf /etc/nginx/nginx.conf

COPY --from=build /usr/src/app/dist/fullstack-k8s /usr/share/nginx/html