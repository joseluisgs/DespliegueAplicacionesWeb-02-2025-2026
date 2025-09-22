## Cuestionario Tipo Test: Introducción a Docker y Contenedores (40 Preguntas)

**1. ¿Qué es Docker, según su definición fundamental?**
A. Una tecnología de virtualización de hardware tradicional.
B. Una plataforma para desarrollar, lanzar y ejecutar aplicaciones, promoviendo la separación entre la aplicación y la infraestructura.
C. Un único sistema operativo ligero basado en Alpine Linux.
D. Un software para gestionar máquinas virtuales (MV) en la nube.

**2. ¿Cuál es uno de los eslóganes promovidos por la plataforma Docker?**
A. “Install Once, Run Everywhere”.
B. “Build, Ship and Run Any App, Anywhere”.
C. “Compile Locally, Deploy Remotely”.
D. “Virtualize Everything, Isolate Always”.

**3. ¿Qué representa una Imagen Docker?**
A. Una instancia ejecutable y modificable de un contenedor.
B. Un paquete de software que se borra al detenerse.
C. Una plantilla de solo lectura e inmutable que contiene las instrucciones para crear un contenedor.
D. El registro central donde se suben los contenedores.

**4. ¿Qué es un Contenedor Docker?**
A. Un archivo de texto plano (`Dockerfile`).
B. El repositorio donde se suben las imágenes.
C. Una imagen de Docker en funcionamiento (una instancia ejecutable y modificable de una imagen).
D. El cliente de línea de comandos para interactuar con Docker.

**5. ¿Qué archivo de texto plano define las instrucciones para construir una Imagen Docker?**
A. `docker-compose.yml`.
B. `docker.log`.
C. `Dockerfile`.
D. `index.html`.

**6. ¿Cuál es el componente de la arquitectura de Docker que se ejecuta en segundo plano como servidor y gestiona objetos Docker (imágenes, contenedores, redes y volúmenes)?**
A. Docker Client (CLI).
B. Docker Hub.
C. Docker Daemon (Dockerd).
D. API REST.

**7. ¿Cuál es el comando fundamental utilizado para crear un contenedor y ponerlo en marcha de forma inmediata, combinando la creación y el inicio?**
A. `docker create`.
B. `docker start`.
C. `docker run` (o `docker container run`).
D. `docker exec`.

**8. ¿Qué opción se utiliza en el comando `docker run` para lanzar un contenedor en modo separado (detached) o en segundo plano?**
A. `-i`.
B. `-t`.
C. `-d`.
D. `-p`.

**9. ¿Qué comando de Docker se utiliza para ver todos los contenedores existentes en el sistema, incluyendo los que están en funcionamiento y los detenidos?**
A. `docker ps`.
B. `docker images`.
C. `docker ps -a` (o `docker container ls -a`).
D. `docker logs`.

**10. ¿Cuál es el comando para descargar una imagen de un registro a la máquina local?**
A. `docker image ls`.
B. `docker push`.
C. `docker image pull REPOSITORIO` (o `docker pull REPOSITORIO`).
D. `docker build`.

**11. ¿Cuál es la principal desventaja del uso de contenedores en términos de seguridad?**
A. La dificultad de instalar paquetes.
B. La necesidad de licencias costosas.
C. Compartir el *kernel* del host, dando la posibilidad de que una vulnerabilidad en él afecte a todos los contenedores.
D. El exceso de almacenamiento persistente.

**12. En la arquitectura de Docker, ¿qué componente es la interfaz de línea de comandos (CLI) que envía peticiones al Daemon?**
A. Docker Daemon.
B. API REST.
C. Docker Client.
D. Docker Hub.

**13. ¿Qué registro de imágenes se considera la "biblioteca" central o el repositorio público y gratuito por defecto gestionado por Docker, Inc.?**
A. Google Container Registry (GCR).
B. Docker Hub.
C. Amazon ECR.
D. GitLab Registry.

**14. ¿Qué sucede al ejecutar el comando `docker run hello-world` si la imagen no existe localmente?**
A. Docker genera un error de "imagen no encontrada".
B. Docker la busca y la descarga automáticamente de Docker Hub (el registro predeterminado).
C. Docker se detiene y espera la confirmación del usuario.
D. Docker intenta construirla localmente sin un Dockerfile.

**15. ¿Qué comando se utiliza para detener un contenedor que está en ejecución mediante el envío de la señal SIGTERM (terminación limpia)?**
A. `docker kill <contenedor>`.
B. `docker rm <contenedor>`.
C. `docker start <contenedor>`.
D. `docker stop <contenedor>`.

**16. ¿Qué comando se utiliza para eliminar un contenedor detenido?**
A. `docker stop`.
B. `docker start`.
C. `docker rm <contenedor>`.
D. `docker kill`.

**17. Si desea asignar un nombre legible a un contenedor en el momento de la ejecución, ¿qué parámetro utiliza en `docker run`?**
A. `-p`.
B. `-e`.
C. `--name <nombre>`.
D. `--link`.

**18. ¿Qué comando permite a un usuario entrar en la shell interactiva de un contenedor ya en ejecución?**
A. `docker run -it`.
B. `docker start`.
C. `docker exec -it <contenedor> /bin/bash`.
D. `docker logs -f`.

**19. ¿Cuál es el propósito principal de la instrucción `FROM` en un Dockerfile?**
A. Ejecutar comandos de shell.
B. Indicar la imagen base que se utilizará como punto de partida.
C. Definir el comando a ejecutar al iniciar el contenedor.
D. Copiar archivos al contenedor.

**20. ¿Qué instrucción del Dockerfile se traduce en una nueva capa inmutable y se usa comúnmente para instalar software dentro de la imagen?**
A. `CMD`.
B. `ENTRYPOINT`.
C. `RUN`.
D. `EXPOSE`.

**21. ¿Qué instrucción se utiliza para definir variables de entorno dentro del contenedor durante la construcción de la imagen?**
A. `ENV <key><valor>`.
B. `WORKDIR`.
C. `VOLUME`.
D. `CMD`.

**22. ¿Cuál es la instrucción de Dockerfile que se utiliza para copiar archivos o directorios del contexto de construcción al sistema de archivos del contenedor, siendo la opción preferida por su simplicidad?**
A. `ADD`.
B. `RUN`.
C. `COPY`.
D. `VOLUME`.

**23. ¿Qué instrucción del Dockerfile se utiliza para indicar a Docker qué puertos TCP/IP escucha el contenedor, aunque *no* realiza el mapeo al host?**
A. `ENTRYPOINT`.
B. `CMD`.
C. `EXPOSE`.
D. `VOLUME`.

**24. ¿Qué sucede con los datos almacenados internamente en un contenedor si este se detiene y luego se elimina, en ausencia de persistencia configurada?**
A. Se guardan en Docker Hub.
B. Se convierten automáticamente en un volumen.
C. Los datos internos desaparecen, ya que el almacenamiento es efímero.
D. Se copian al sistema de archivos del host automáticamente.

**25. ¿Qué mecanismo se recomienda para guardar los datos de una base de datos, ya que persisten más allá del ciclo de vida del contenedor y son gestionados por Docker?**
A. Bind Mounts.
B. Copia de archivos (`docker cp`).
C. Volúmenes (Volumes).
D. Archivos temporales.

**26. ¿Qué técnica se recomienda para el desarrollo de código fuente, permitiendo que el host y el contenedor tengan acceso al mismo código y facilitando las modificaciones y el testeo instantáneo?**
A. Docker commit.
B. Volúmenes nombrados.
C. Enlace de directorios (Bind Mounts).
D. Docker push.

**27. ¿Qué instrucción de Dockerfile provee valores por defecto al contenedor, pero es ignorada si el usuario especifica un comando alternativo al ejecutar `docker run`?**
A. `ENTRYPOINT`.
B. `RUN`.
C. `CMD`.
D. `HEALTHCHECK`.

**28. ¿Qué instrucción del Dockerfile define el comando principal que se ejecuta primero, y a la que los argumentos de `CMD` o `docker run` se añaden como parámetros?**
A. `FROM`.
B. `ENTRYPOINT`.
C. `EXPOSE`.
D. `VOLUME`.

**29. ¿Qué comando se utiliza para construir una imagen a partir de un Dockerfile, usando un path de contexto (generalmente `.`) y asignándole un nombre con la opción `-t`?**
A. `docker push`.
B. `docker build -t <nombre> <path>` (o `docker image build`).
C. `docker tag`.
D. `docker commit`.

**30. ¿Qué debe hacer una imagen local antes de poder subirla a Docker Hub (registro público)?**
A. Debe estar en modo *detached*.
B. Debe ser comprimida en formato `.tar`.
C. Debe ser etiquetada (`tagged`) siguiendo la convención NOMBRE\_DE\_USUARIO/NOMBRE\_DEL\_REPOSITORIO:ETIQUETA.
D. Debe usar la opción `--no-cache` durante el build.

**31. ¿Qué comando se utiliza para asignar un tag (etiqueta) a una imagen existente, a menudo para cumplir con la nomenclatura del registro?**
A. `docker push`.
B. `docker tag`.
C. `docker build`.
D. `docker login`.

**32. ¿Qué herramienta se utiliza para definir y ejecutar aplicaciones que consisten en múltiples contenedores (multi-contenedor), simplificando su gestión con un solo archivo YAML?**
A. Docker Swarm.
B. Kubernetes.
C. Docker Compose.
D. Docker Daemon.

**33. En un archivo `docker-compose.yml`, ¿qué sección se utiliza para listar los contenedores que componen la aplicación?**
A. `version`.
B. `volumes`.
C. `networks`.
D. `services`.

**34. ¿Qué comando se utiliza para iniciar todos los servicios definidos en el archivo Compose y mostrarlos en primer plano, con logs multiplexados?**
A. `docker-compose up -d`.
B. `docker-compose ps`.
C. `docker-compose up`.
D. `docker-compose logs -ft`.

**35. ¿Qué comando de Docker Compose se utiliza para detener y eliminar los contenedores y redes del stack, pero no los volúmenes por defecto?**
A. `docker-compose stop`.
B. `docker-compose down`.
C. `docker-compose down -v`.
D. `docker-compose kill`.

**36. ¿Qué comando de Docker Compose se debe usar para detener y eliminar el entorno completamente, incluyendo los volúmenes nombrados?**
A. `docker-compose stop -v`.
B. `docker-compose down --force`.
C. `docker-compose down -v`.
D. `docker-compose rm`.

**37. ¿Qué opción en Docker Compose (o en el CLI de Docker) permite definir variables de configuración para el contenedor (ej. credenciales de bases de datos)?**
A. `volumes`.
B. `ports`.
C. `environment`.
D. `depends_on`.

**38. ¿Cuál es la herramienta nativa de Docker Inc. para gestionar y orquestar contenedores en un clúster de varias máquinas (o nodos)?**
A. Kubernetes.
B. Docker Compose.
C. Docker Swarm.
D. Mesos.

**39. En las buenas prácticas para Dockerfile, ¿por qué se recomienda fusionar múltiples comandos `RUN` en uno solo, usando `&&` y `\`?**
A. Para facilitar la legibilidad del código.
B. Porque cada instrucción `RUN` crea una nueva capa inmutable, y se busca minimizar el número de capas.
C. Para asegurar que el `ENTRYPOINT` funcione correctamente.
D. Para permitir que Docker Hub realice *Automated Builds*.

**40. ¿Qué se utiliza para verificar periódicamente el estado de un contenedor después de su inicio, comprobando si un servicio (como un servidor web) sigue respondiendo y no solo si el proceso está activo?**
A. La instrucción `VOLUME`.
B. El comando `docker inspect`.
C. La directiva `HEALTHCHECK`.
D. El comando `docker logs -f`.