# Guía de Comandos Fundamentales de Docker

## Introducción
Este documento sirve como una guía comprensiva de los comandos fundamentales de Docker esenciales para la gestión de contenedores e imágenes. Docker es una plataforma que permite a los desarrolladores automatizar el despliegue de aplicaciones dentro de contenedores ligeros y portátiles.

### Tabla de Contenidos
1. [Listar Contenedores en Ejecución](#listar-contenedores-en-ejecución)
2. [Detener un Contenedor](#detener-un-contenedor)
3. [Iniciar un Contenedor](#iniciar-un-contenedor)
4. [Ejecutar un Nuevo Contenedor](#ejecutar-un-nuevo-contenedor)
5. [Construir una Imagen](#construir-una-imagen)
6. [Descargar una Imagen](#descargar-una-imagen)
7. [Listar Imágenes](#listar-imágenes)
8. [Subir una Imagen](#subir-una-imagen)
9. [Inspeccionar los Logs de un Contenedor](#inspeccionar-los-logs-de-un-contenedor)
10. [Eliminar Contenedores e Imágenes](#eliminar-contenedores-e-imágenes)

## Listar Contenedores en Ejecución
### `docker ps`
Este comando lista todos los contenedores que están actualmente en ejecución.

#### Uso:
```sh
docker ps
```
Para ver todos los contenedores (en ejecución y detenidos):
```sh
docker ps -a
```

## Detener un Contenedor
### `docker stop`
Este comando detiene un contenedor en ejecución.

#### Uso:
```sh
docker stop <id_del_contenedor>
```
Reemplaza `<id_del_contenedor>` con el ID o nombre del contenedor.

## Iniciar un Contenedor
### `docker start`
Este comando inicia un contenedor detenido.

#### Uso:
```sh
docker start <id_del_contenedor>
```
Reemplaza `<id_del_contenedor>` con el ID o nombre del contenedor.

## Ejecutar un Nuevo Contenedor
### `docker run`
Este comando ejecuta un nuevo contenedor desde una imagen especificada.

#### Uso:
```sh
docker run <nombre_de_la_imagen>
```
Para ejecutar un contenedor en modo desatendido con mapeo de puertos y montaje de volúmenes:
```sh
docker run -d -p 80:80 -v /ruta/en/host:/ruta/en/contenedor <nombre_de_la_imagen>
```
- `-d`: Ejecutar el contenedor en modo desatendido.
- `-p 80:80`: Mapear el puerto 80 del host al puerto 80 del contenedor.
- `-v /ruta/en/host:/ruta/en/contenedor`: Montar un volumen.

## Construir una Imagen
### `docker build`
Este comando construye una imagen a partir de un Dockerfile.

#### Uso:
```sh
docker build -t <nombre_de_la_imagen> .
```
- `-t <nombre_de_la_imagen>`: Etiqueta la imagen con un nombre.
- `.`: Contexto para la construcción, usualmente el directorio actual.

## Descargar una Imagen
### `docker pull`
Este comando descarga una imagen desde un registro de Docker (por ejemplo, Docker Hub).

#### Uso:
```sh
docker pull <nombre_de_la_imagen>
```

## Listar Imágenes
### `docker images`
Este comando lista todas las imágenes almacenadas localmente.

#### Uso:
```sh
docker images
```

## Subir una Imagen
### `docker push`
Este comando sube una imagen a un registro de Docker.

#### Uso:
```sh
docker push <nombre_de_la_imagen>
```
Asegúrate de haber iniciado sesión en el registro y que el nombre de la imagen incluya el repositorio (por ejemplo, `usuario/nombre_de_la_imagen`).

## Inspeccionar los Logs de un Contenedor
### `docker logs`
Este comando obtiene los logs de un contenedor.

#### Uso:
```sh
docker logs <id_del_contenedor>
```
Para seguir los logs en tiempo real:
```sh
docker logs -f <id_del_contenedor>
```

## Eliminar Contenedores e Imágenes
### `docker rm`
Este comando elimina un contenedor.

#### Uso:
```sh
docker rm <id_del_contenedor>
```
Para forzar la eliminación de un contenedor en ejecución:
```sh
docker rm -f <id_del_contenedor>
```

### `docker rmi`
Este comando elimina una imagen.

#### Uso:
```sh
docker rmi <id_de_la_imagen>
```

### Comandos Adicionales Útiles
- **Iniciar sesión en el registro de Docker:** `docker login`
- **Cerrar sesión en el registro de Docker:** `docker logout`
- **Verificar la versión de Docker:** `docker --version`
- **Inspeccionar detalles de un contenedor:** `docker inspect <id_del_contenedor>`
- **Listar redes de Docker:** `docker network ls`
- **Eliminar datos no utilizados:** `docker system prune`

Esta guía debería proporcionar una base sólida para trabajar con contenedores e imágenes de Docker. Para un uso más avanzado y opciones adicionales, consulta la documentación oficial de Docker.
