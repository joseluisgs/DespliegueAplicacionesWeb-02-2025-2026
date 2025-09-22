
## Práctica 1: Creación de Imagen de Base de Datos Personalizada con Inicialización y Publicación en Docker Hub

Esta práctica se centra en crear una imagen de base de datos (`mariadb`) que se inicialice con datos predefinidos mediante un *script* y, posteriormente, se publique en el registro público.

### Objetivos

1.  Crear un **Dockerfile** para construir una imagen personalizada.
2.  Utilizar el mecanismo de inicialización de la base de datos para cargar datos predefinidos, lo cual se logra al copiar *scripts* SQL en un directorio específico que la imagen de MariaDB ejecuta en el `ENTRYPOINT` de inicio.
3.  Etiquetar la imagen correctamente (`docker tag`) para prepararla para la publicación.
4.  Subir la imagen a **Docker Hub** (`docker push`).

### Pasos Detallados

#### 1. Estructura de Archivos

Cree un directorio para el proyecto y un subdirectorio para los *scripts* de inicialización:

```
/db-personalizada
├── Dockerfile
└── sql/
    └── init.sql 
```

#### 2. Definición del Script de Inicialización (`sql/init.sql`)

MariaDB/MySQL ejecutará automáticamente cualquier archivo `.sql` ubicado en la ruta `/docker-entrypoint-initdb.d/` al iniciarse por primera vez. Este es el método que usamos para "entrar datos en el entrypoint".

```sql
-- Contenido de sql/init.sql
CREATE DATABASE IF NOT EXISTS app_data;
USE app_data;
CREATE TABLE usuarios (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50),
    email VARCHAR(50)
);
INSERT INTO usuarios (nombre, email) VALUES 
('Jose Luis', 'joseluis@docker.com'),
('Soraya', 'pepito@docker.com');
```

#### 3. Creación del Dockerfile

Este archivo definirá la imagen, basándose en la imagen oficial de MariaDB y configurando las variables de entorno necesarias para la base de datos:

```dockerfile
# 1. Imagen base
FROM mariadb:10.5
 
# 2. Metadatos (reemplazado por LABEL, pero MAINTAINER aún se encuentra en la fuente)
MAINTAINER JL Gonzalez "joseluis@docker.com" 
 
# 3. Variables de entorno: esenciales para la configuración de la BD
ENV MYSQL_ROOT_PASSWORD=secret_root \
    MYSQL_DATABASE=app_data \
    MYSQL_USER=manager \
    MYSQL_PASSWORD=secret_manager
 
# 4. Copia el script SQL al directorio de inicialización de la imagen base
COPY ./sql /docker-entrypoint-initdb.d/

# 5. Exponer el puerto por defecto (solo informativo)
EXPOSE 3306
```

#### 4. Construcción de la Imagen (Build)

Asumiendo que su usuario de Docker Hub es `mi_usuario`, construya la imagen con el *tag* local adecuado:

```bash
docker build -t mi_usuario/db-personalizada:v1 . 
```

El punto (`.`) es importante, ya que indica el contexto de construcción donde se encuentra el Dockerfile y el subdirectorio `sql`.

#### 5. Preparación y Publicación en Docker Hub

Para que la imagen pueda ser subida al registro, debe estar etiquetada con la nomenclatura correcta: `NOMBRE_DE_USUARIO/NOMBRE_DEL_REPOSITORIO:ETIQUETA`:

1.  **Auntenticación:** Inicie sesión en Docker Hub:
    ```bash
    docker login
    ```
2.  **Publicación:** Suba la imagen al repositorio remoto:
    ```bash
    docker push mi_usuario/db-personalizada:v1
    ```
Una vez finalizado, la imagen estará disponible para que cualquier compañero o sistema la descargue con `docker pull mi_usuario/db-personalizada:v1`.

