# Solemne 1 Aplicaciones y Tecnologias de la Web

## Simulación de aplicación web para "Floristeria Jardin Encantado"
En esta aplicación se permite visualizar un menu de productos, filtrarlos por categoria, añadir al carrito y simular una compra virtual.

## Despliegue local con Docker
1. **En una terminal clonar el repositorio usando: git clone https://github.com/FranciscoN055/Solemne1.git**
2. **Navegar a la carpeta donde se encuentra el Dockerfile con: cd Solemne1**
3. **Construir la imagen Docker con: docker build -t floristeria-jardin-encantado .**
4. **Ejecutar el contenedor con el servidor de Apache usando: docker run -d -p 8080:80 --name mi-floristeria floristeria-jardin-encantado**
5.  **Para acceder a la aplicación buscar en el navegador "http://localhost:8080"**
6.  **Para detener el contenedor: docker stop mi-floristeria y para eliminar: docker rm mi-floristeria**

## Despliegue con Docker Playground
1. **Primero actualizar paquetes con apk update e instalar nano con apk add nano**
2. **Crear y editar el archivo Dockerfile con el siguiente contenido:**

```
# Usa una imagen oficial de Apache HTTP Server
FROM httpd:latest

# Instala Git para poder clonar el repositorio
# Actualiza la lista de paquetes, instala git y limpia la caché de apt
RUN apt-get update && apt-get install -y git && \
    rm -rf /var/lib/apt/lists/*

# Limpia el directorio de contenido web por defecto de Apache
RUN rm -rf /usr/local/apache2/htdocs/*

# Clona tu repositorio desde GitHub al directorio web de Apache
# Asegúrate que la URL sea la correcta para tu proyecto Solemne1
RUN git clone https://github.com/FranciscoN055/Solemne1.git /usr/local/apache2/htdocs/

# Expone el puerto 80 para el tráfico web
EXPOSE 80

# Inicia Apache en primer plano (este es el comando por defecto de la imagen base httpd)
# Se incluye para ser explícito, siguiendo el estilo de tu ejemplo.
CMD ["httpd-foreground"]
```

3. **Construir la imagen Docker con: docker build -t floristeria-jardin-encantado .**
4. **Ejecutar el contenedor con el servidor de Apache usando: docker run -d -p 8080:80 --name mi-floristeria floristeria-jardin-encantado**
5.  **Para acceder a la aplicación hacer click en el enlace 8080 o hacer click en "open port" e ingresar 8080 y confirmar.**
6.  **Para detener el contenedor: docker stop mi-floristeria y para eliminar: docker rm mi-floristeria**

