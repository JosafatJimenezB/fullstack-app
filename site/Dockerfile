# STEP 1 Creando build de site
FROM node:14-alpine as build
WORKDIR /app
COPY package.json ./
RUN npm install
COPY . .
RUN npm run build
# CMD ["npm", "start"]


# STEP 2 Creando imagen de nginx y levantando server

FROM nginx:latest as prod-stage
COPY --from=build app/build/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
