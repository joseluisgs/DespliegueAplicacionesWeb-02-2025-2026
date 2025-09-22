
## Práctica 2: Despliegue Multi-Contenedor con Docker Compose (WordPress + MariaDB)

Docker Compose es ideal para definir y ejecutar aplicaciones multi-contenedor, simplificando la gestión de la arquitectura de servicios mediante un único archivo YAML. El ejemplo clásico es la implementación de un blog **WordPress** (servidor web) que depende de una **Base de Datos** (MariaDB).

### Objetivos

1.  Crear un archivo `docker-compose.yml` para definir dos servicios dependientes.
2.  Configurar la **comunicación interna** entre los servicios a través de la resolución DNS automática de Compose.
3.  Configurar la **persistencia** de datos de la base de datos usando un volumen.
4.  Utilizar comandos de ciclo de vida de Compose (`up`, `down`).

### Pasos Detallados

#### 1. Creación del Archivo `docker-compose.yml`

Este archivo define la arquitectura completa de la aplicación, incluyendo dos servicios (`db` y `web`) y la persistencia.

```yaml
version: '3.7'  # Especifica la versión de la sintaxis

services:
  # Servicio 1: Base de Datos MariaDB
  db:
    image: mariadb:10.5  # Imagen de la BD
    container_name: mariadb_prod # Nombre específico del contenedor
    volumes:
      - data_mysql:/var/lib/mysql # Monta un volumen para persistencia de datos
    environment: # Variables de entorno para configuración interna
      - MYSQL_ROOT_PASSWORD=supersecret
      - MYSQL_DATABASE=wordpress_db
      - MYSQL_USER=wp_user
      - MYSQL_PASSWORD=wp_secret
  
  # Servicio 2: Servidor Web WordPress
  web:
    image: wordpress:4.9.8 # Imagen de WordPress
    container_name: wordpress_prod
    depends_on:
      - db # Asegura que la DB inicie antes que WordPress
    volumes:
      - ./app_data:/var/www/html # Bind Mount para desarrollo/código
    environment: # Configuración de WP para conectarse a la BD
      - WORDPRESS_DB_HOST=db # Usa el nombre del servicio 'db' para la conexión DNS
      - WORDPRESS_DB_USER=wp_user
      - WORDPRESS_DB_PASSWORD=wp_secret
      - WORDPRESS_DB_NAME=wordpress_db
    ports:
      - 8080:80 # Mapeo de puertos: Host 8080 -> Contenedor 80

volumes:
  data_mysql: # Definición del volumen persistente para la DB
```

#### 2. Ejecución y Ciclo de Vida

1.  **Levantar el entorno:** Este comando construye la aplicación, crea la red interna, y lanza ambos servicios en segundo plano (`-d`):
    ```bash
    docker-compose up -d
    ```
    Una vez iniciado, puede acceder a `http://localhost:8080` para ver la instalación de WordPress. WordPress se conecta a la base de datos utilizando el nombre de host `db`.

2.  **Verificar estado y logs:**
    ```bash
    docker-compose ps # Muestra solo los servicios definidos en el archivo YAML
    docker-compose logs -ft # Muestra logs multiplexados en tiempo real
    ```

3.  **Acceso a la *Shell*** (Debugging): Acceda a la *shell* del contenedor web en ejecución:
    ```bash
    docker-compose exec web /bin/bash
    ```

4.  **Detención y Eliminación:** Es crucial saber cómo detener y limpiar los recursos.
    *   Para detener y eliminar los contenedores y la red, manteniendo los volúmenes (para conservar los datos de la BD):
        ```bash
        docker-compose down 
        ```
    *   Para detener y eliminar *todos* los recursos, incluyendo el volumen de datos (perdiendo la información de la BD):
        ```bash
        docker-compose down -v
        ```