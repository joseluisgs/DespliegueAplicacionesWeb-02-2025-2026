## 10 Cuestiones de Investigación sobre Docker y Contenedores

**1. Arquitectura y Eficiencia de los Contenedores**
Explique la diferencia fundamental en términos de arquitectura entre un Contenedor Docker y una Máquina Virtual (MV) tradicional. ¿Cómo se logra que los contenedores sean más ligeros y tengan un menor *footprint* de recursos? ¿Qué componente del *host* (sistema operativo anfitrión) es compartido por los contenedores, y cuál es la principal implicación de seguridad que surge de compartir este componente?.

**2. Diferencias y Combinación de Comandos de Inicio**
Las instrucciones **`CMD`** y **`ENTRYPOINT`** definen el proceso de inicio de un contenedor. Describa el propósito principal de cada una y qué sucede si un usuario intenta sobrescribir la ejecución de estas instrucciones mediante argumentos pasados al comando `docker run`. Ilustre cómo se utiliza la forma *exec* (sintaxis JSON) de estas instrucciones y por qué es generalmente la forma recomendada.

**3. Mecanismos de Persistencia de Datos**
Compare los dos mecanismos principales para la persistencia de datos: **Volúmenes** y **Enlace de Directorios** (**Bind Mounts**). ¿Cuál de estos es un objeto completamente gestionado por Docker, y por qué se recomienda usar este mecanismo específico para datos de bases de datos que deben sobrevivir al contenedor (persistencia segura)? ¿Para qué caso de uso se recomienda específicamente el otro mecanismo (Bind Mounts) en un entorno de desarrollo?

**4. Optimización de Imágenes mediante Capas y Caché**
Docker construye imágenes utilizando un sistema de **capas inmutables** (*layers*). Explique cómo se relaciona cada instrucción del Dockerfile con la creación de una nueva capa. Detalle dos buenas prácticas de optimización relacionadas con la gestión de la caché de construcción y la instrucción `RUN`, justificando por qué estas acciones reducen el tamaño final o el tiempo de *build* de la imagen.

**5. Flujo de Trabajo y Componentes del Motor Docker**
Describa el rol de los tres componentes principales del Docker Engine: el **Docker Client (CLI)**, el **Docker Daemon (Dockerd)** y la **API REST**. Explique la secuencia de comunicación que ocurre cuando un usuario introduce un comando como `docker run` en la terminal, indicando qué componente envía la petición y cuál la procesa y ejecuta.

**6. Gestión de Puertos: `EXPOSE` vs. Mapeo (`-p`)**
Diferencie claramente entre la instrucción **`EXPOSE`** dentro de un Dockerfile y el uso de la opción **`-p`** (o `ports` en Compose) en el comando `docker run`. ¿Cuál de las dos opciones es meramente informativa, y cuál es la que realmente publica el servicio del contenedor a un puerto accesible en el sistema anfitrión (*host*)?

**7. Buenas Prácticas de Seguridad en el Dockerfile**
¿Por qué se considera una mala práctica de seguridad ejecutar un contenedor con el usuario por defecto (**root**)? Mencione qué instrucción en el Dockerfile debe usarse para **denegar el uso de root** y especificar un usuario con menos privilegios. Además, investigue por qué se desaconseja firmemente guardar credenciales (contraseñas, *tokens*) directamente en el Dockerfile.

**8. Herramienta de Orquestación Local: Docker Compose**
¿Qué es **Docker Compose** y cuál es su principal utilidad en un entorno de desarrollo? Mencione las cuatro secciones principales que componen el archivo de configuración en formato YAML (`docker-compose.yml`). Identifique y describa el propósito de dos comandos clave de Docker Compose para la gestión del ciclo de vida del *stack* (además de `up`).

**9. Gestión de Imágenes en Docker Hub**
Describa el proceso completo y la nomenclatura requerida para subir una imagen local a **Docker Hub**, incluyendo el comando necesario para etiquetar (`tag`) la imagen correctamente. ¿Qué papel juega **Docker Hub** como "biblioteca" de imágenes y por qué es importante el campo **OFFICIAL** en los resultados de la búsqueda de imágenes?

**10. La Importancia del Contexto de Construcción**
Defina qué es el **Contexto de Construcción** (*Build Context*) en el comando `docker build`. ¿Por qué es crucial utilizar un archivo **`.dockerignore`**?. Mencione qué tipo de archivos o directorios deben incluirse en este archivo de exclusión para garantizar la eficiencia y la seguridad del proceso de *build*.