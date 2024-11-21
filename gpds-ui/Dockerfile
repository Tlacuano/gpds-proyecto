# Dockerfile

# Etapa de construccion
FROM node:18 AS build

WORKDIR /app

# Copia archivos de configuracion de npm y Vue
COPY package*.json ./

# Instalar dependencias
RUN npm install

# Copiar el codigo de la aplicacion y construirla
COPY . .
RUN npm run build

# Etapa de produccion (Nginx)
FROM nginx:alpine

# Copiar los archivos compilados desde la etapa de construccion a la carpeta de Nginx
COPY --from=build /app/dist /usr/share/nginx/html

# Copiar configuracion de Nginx (si necesitas personalizarla)
# Puedes crear un archivo personalizado de configuraci√≥n en tu proyecto y copiarlo aqui≠
# COPY nginx.conf /etc/nginx/nginx.conf

# Exponer el puerto de Nginx
EXPOSE 80

# Comando de inicio de Nginx
CMD ["nginx", "-g", "daemon off;"]
