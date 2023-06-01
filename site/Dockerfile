# STEP 1 Creando build de site
FROM node:12-alpine as build
WORKDIR /app
COPY package.json ./
RUN npm ci
COPY . .
RUN npm run build

# STEP 2 Creando imagen de nginx y levantando server

FROM nginx:alpine as prod-stage
COPY --from=build app/build/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
