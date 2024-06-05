# Desplegar un Contenedor Docker Paso a Paso

Este documento proporciona una guía detallada y paso a paso sobre cómo desplegar un contenedor Docker desde la construcción de la imagen hasta la ejecución del contenedor. Se asume que ya tienes Docker instalado en tu sistema. Si no es así, por favor consulta la [documentación oficial de Docker](https://docs.docker.com/get-docker/) para las instrucciones de instalación.

## Paso 1: Preparar el Dockerfile
El Dockerfile es un archivo de texto que contiene todas las instrucciones necesarias para construir una imagen Docker.

### Ejemplo de Dockerfile
Crea un archivo llamado `Dockerfile` en tu directorio de trabajo y añade el siguiente contenido:

```Dockerfile
# Usar una imagen base de Ubuntu
FROM ubuntu:latest

# Actualizar el sistema y instalar nginx
RUN apt-get update && apt-get install -y nginx

# Exponer el puerto 80 para el servidor web
EXPOSE 80

# Comando para ejecutar nginx en primer plano
CMD ["nginx", "-g", "daemon off;"]
```

## Paso 2: Construir la Imagen Docker
Utiliza el comando `docker build` para construir la imagen a partir del Dockerfile.

### Comando:
```bash
docker build -t mi_imagen_nginx .
```
**Explicación:**
- `-t mi_imagen_nginx`: Etiqueta la imagen con el nombre `mi_imagen_nginx`.
- `.`: Indica que Docker debe buscar el Dockerfile en el directorio actual.

## Paso 3: Verificar la Imagen Construida
Comprueba que la imagen se haya construido correctamente utilizando el comando `docker images`.

### Comando:
```bash
docker images
```

## Paso 4: Ejecutar el Contenedor
Utiliza el comando `docker run` para crear y ejecutar un contenedor a partir de la imagen que acabas de construir.

### Comando:
```bash
docker run -d -p 80:80 --name mi_contenedor_nginx mi_imagen_nginx
```
**Explicación:**
- `-d`: Ejecuta el contenedor en segundo plano (detached).
- `-p 80:80`: Mapea el puerto 80 del host al puerto 80 del contenedor.
- `--name mi_contenedor_nginx`: Asigna un nombre al contenedor (`mi_contenedor_nginx`).
- `mi_imagen_nginx`: Nombre de la imagen a partir de la cual se creará el contenedor.

## Paso 5: Verificar que el Contenedor está Corriendo
Utiliza el comando `docker ps` para listar los contenedores en ejecución y verificar que tu contenedor está corriendo.

### Comando:
```bash
docker ps
```

## Paso 6: Acceder al Servicio en el Navegador
Abre un navegador web y navega a `http://localhost` (o `http://<tu-dirección-IP>` si estás en un servidor remoto). Deberías ver la página predeterminada de Nginx.

## Paso 7: Gestionar el Contenedor
Aquí algunos comandos útiles para gestionar el contenedor:

### Detener el Contenedor
```bash
docker stop mi_contenedor_nginx
```

### Iniciar el Contenedor
```bash
docker start mi_contenedor_nginx
```

### Eliminar el Contenedor
```bash
docker rm mi_contenedor_nginx
```

### Eliminar la Imagen
```bash
docker rmi mi_imagen_nginx
```

## Conclusión
Siguiendo estos pasos, habrás desplegado exitosamente un contenedor Docker ejecutando un servidor Nginx. Este es un flujo de trabajo básico, pero efectivo, que puedes expandir y adaptar a tus necesidades específicas. Para obtener más información y opciones avanzadas, consulta la [documentación oficial de Docker](https://docs.docker.com/).
