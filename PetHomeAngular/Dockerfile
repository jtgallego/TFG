# Etapa 1: Build de Angular
FROM node:18 AS build

WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build -- --configuration production

# Etapa 2: Servir con Nginx
FROM nginx:alpine

# Elimina la página por defecto de nginx
RUN rm -rf /usr/share/nginx/html/*

# Copia los archivos generados del build
COPY --from=build /app/dist/pethome /usr/share/nginx/html

# Expone el puerto 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
