FROM node:10.15-alpine as dev
WORKDIR /app
COPY package.json package-lock.json ./
RUN npm ci
COPY . .

FROM dev as build
ARG MODE
RUN npm run build -- --mode $MODE

FROM nginx:stable-alpine as production
COPY --from=build /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
