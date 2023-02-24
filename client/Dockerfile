FROM node:14.14.0-alpine AS builder

WORKDIR /usr/app

COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM nginx
COPY --from=builder /usr/app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#EXPOSE 3000