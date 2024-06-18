Si las imágenes y contenedores se están regenerando automáticamente, es posible que estés utilizando Docker Swarm o algún otro servicio de orquestación que está recreando los servicios. Para asegurarte de que todo se detenga y elimine completamente, sigue estos pasos:

1. **Detener y eliminar los servicios de Docker Swarm**:

    ```bash
    docker service rm $(docker service ls -q)
    ```

2. **Detener todos los contenedores**:

    ```bash
    docker stop $(docker ps -aq)
    ```

3. **Eliminar todos los contenedores**:

    ```bash
    docker rm -f $(docker ps -aq)
    ```

4. **Eliminar todas las imágenes**:

    ```bash
    docker rmi -f $(docker images -q)
    ```

5. **Eliminar todos los volúmenes**:

    ```bash
    docker volume prune -f
    ```

6. **Eliminar todas las redes**:

    ```bash
    docker network prune -f
    ```

A continuación, te dejo todos los comandos juntos para que puedas ejecutarlos de una vez:

```bash
docker service rm $(docker service ls -q)
docker stop $(docker ps -aq)
docker rm -f $(docker ps -aq)
docker rmi -f $(docker images -q)
docker volume prune -f
docker network prune -f
```

### Pasos Detallados

1. **Eliminar todos los servicios de Docker Swarm**:

    Esto asegura que no haya servicios activos que puedan estar recreando los contenedores.

    ```bash
    docker service rm $(docker service ls -q)
    ```

2. **Detener y eliminar todos los contenedores**:

    Detén todos los contenedores que están corriendo.

    ```bash
    docker stop $(docker ps -aq)
    ```

    Luego, elimina todos los contenedores detenidos.

    ```bash
    docker rm -f $(docker ps -aq)
    ```

3. **Eliminar todas las imágenes**:

    Forzar la eliminación de todas las imágenes.

    ```bash
    docker rmi -f $(docker images -q)
    ```

4. **Eliminar todos los volúmenes no utilizados**:

    Esto liberará espacio en disco eliminado los volúmenes no utilizados.

    ```bash
    docker volume prune -f
    ```

5. **Eliminar todas las redes no utilizadas**:

    Esto asegurará que todas las redes no utilizadas sean eliminadas.

    ```bash
    docker network prune -f
    ```

Ejecutando estos comandos deberías poder detener y eliminar completamente todas las imágenes, contenedores, volúmenes y redes de Docker, evitando que se regeneren automáticamente.
