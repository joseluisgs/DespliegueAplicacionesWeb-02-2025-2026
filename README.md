# Despliegue de Aplicaciones Web - 02 - Virtualización con contenedores

Tema 02. Virtualización con contenedores. 2DAW. Curso 2025-2026.

![imagen](https://github.com/joseluisgs/DespliegueAplicacionesWeb-00-2024-2025/raw/master/images/despliegue.png)


- [Despliegue de Aplicaciones Web - 02 - Virtualización con contenedores](#despliegue-de-aplicaciones-web---02---virtualización-con-contenedores)
  - [Introducción](#introducción)
  - [Tutoriales](#tutoriales)
  - [Contenido en Youtube](#contenido-en-youtube)
  - [1. Conceptos Fundamentales de Docker](#1-conceptos-fundamentales-de-docker)
    - [1.1. ¿Qué es Docker?](#11-qué-es-docker)
      - [1.1.1. Definición](#111-definición)
      - [1.1.2. Propósito](#112-propósito)
      - [1.1.3. Contenedores](#113-contenedores)
    - [1.2. Contenedores vs. Máquinas Virtuales (MV)](#12-contenedores-vs-máquinas-virtuales-mv)
      - [1.2.1. Diferencias de Arquitectura](#121-diferencias-de-arquitectura)
      - [1.2.2. Ventajas](#122-ventajas)
      - [1.2.3. Desventajas](#123-desventajas)
    - [1.3. Arquitectura y Componentes de Docker](#13-arquitectura-y-componentes-de-docker)
      - [1.3.1. Componentes Principales](#131-componentes-principales)
      - [1.3.2. Docker Engine](#132-docker-engine)
      - [1.3.3. Imágenes (Images)](#133-imágenes-images)
      - [1.3.4. Contenedores (Containers)](#134-contenedores-containers)
    - [1.4. Conceptos de Almacenamiento Básico](#14-conceptos-de-almacenamiento-básico)
      - [1.4.1. Naturaleza Efímera](#141-naturaleza-efímera)
  - [2. Instalación y Comandos Básicos de Docker CLI](#2-instalación-y-comandos-básicos-de-docker-cli)
    - [2.1. Instalación y Configuración Inicial](#21-instalación-y-configuración-inicial)
      - [2.1.1. Requisitos Previos](#211-requisitos-previos)
      - [2.1.2. Instalación y Comprobación](#212-instalación-y-comprobación)
      - [2.1.3. Permisos](#213-permisos)
    - [2.2. Manejo del Ciclo de Vida del Contenedor](#22-manejo-del-ciclo-de-vida-del-contenedor)
      - [2.2.1. Ejecución de Contenedores](#221-ejecución-de-contenedores)
      - [2.2.2. Modos de Ejecución](#222-modos-de-ejecución)
      - [2.2.3. Identificación](#223-identificación)
      - [2.2.4. Visualización](#224-visualización)
      - [2.2.5. Operaciones](#225-operaciones)
      - [2.2.6. Inspección y Logs](#226-inspección-y-logs)
    - [2.3. Comandos Avanzados de Ejecución y Acceso](#23-comandos-avanzados-de-ejecución-y-acceso)
      - [2.3.1. Acceder a la Shell](#231-acceder-a-la-shell)
      - [2.3.2. Mapeo de Puertos](#232-mapeo-de-puertos)
      - [2.3.3. Variables de Entorno](#233-variables-de-entorno)
      - [2.3.4. Creación de Imagen desde Contenedor](#234-creación-de-imagen-desde-contenedor)
  - [3. Creación y Optimización de Imágenes (Dockerfile)](#3-creación-y-optimización-de-imágenes-dockerfile)
    - [3.1. Estructura y Comandos del Dockerfile](#31-estructura-y-comandos-del-dockerfile)
      - [3.1.1. ¿Qué es el Dockerfile?](#311-qué-es-el-dockerfile)
      - [3.1.2. Construcción de la Imagen (`docker build`)](#312-construcción-de-la-imagen-docker-build)
      - [3.1.3. Instrucciones Fundamentales del Dockerfile](#313-instrucciones-fundamentales-del-dockerfile)
    - [3.2. Directivas de Configuración y Metadatos](#32-directivas-de-configuración-y-metadatos)
      - [3.2.1. Comandos de Ejecución (CMD vs. ENTRYPOINT)](#321-comandos-de-ejecución-cmd-vs-entrypoint)
      - [3.2.2. Configuración de Entorno y Directorios](#322-configuración-de-entorno-y-directorios)
      - [3.2.3. Configuración de Red y Persistencia](#323-configuración-de-red-y-persistencia)
      - [3.2.4. Metadatos](#324-metadatos)
    - [3.3. Creación y Gestión de Imágenes (Build)](#33-creación-y-gestión-de-imágenes-build)
      - [3.3.1. Proceso de Build](#331-proceso-de-build)
      - [3.3.2. Alternativa: `docker commit`](#332-alternativa-docker-commit)
    - [3.4. Buenas Prácticas y Optimización de Imágenes](#34-buenas-prácticas-y-optimización-de-imágenes)
      - [3.4.1. Minimizar el Tamaño y Número de Capas](#341-minimizar-el-tamaño-y-número-de-capas)
      - [3.4.2. Optimización de la Caché de Construcción](#342-optimización-de-la-caché-de-construcción)
      - [3.4.3. Diseño y Seguridad](#343-diseño-y-seguridad)
  - [4. Persistencia y Redes Avanzadas](#4-persistencia-y-redes-avanzadas)
    - [4.1. Manejo de la Persistencia de Datos](#41-manejo-de-la-persistencia-de-datos)
      - [4.1.1. Volúmenes](#411-volúmenes)
      - [4.1.2. Enlace de Directorios (Bind Mounts)](#412-enlace-de-directorios-bind-mounts)
      - [4.1.3. Casos de Uso](#413-casos-de-uso)
    - [4.2. Configuración de Redes (Networking)](#42-configuración-de-redes-networking)
      - [4.2.1. Aislamiento](#421-aislamiento)
      - [4.2.2. Modos de Red](#422-modos-de-red)
      - [4.2.3. Redes Definidas por Usuario](#423-redes-definidas-por-usuario)
      - [4.2.4. Enlace de Contenedores](#424-enlace-de-contenedores)
  - [5. Compartiendo Imágenes y Registros](#5-compartiendo-imágenes-y-registros)
    - [5.1. Docker Hub y Gestión Remota](#51-docker-hub-y-gestión-remota)
      - [5.1.1. Registro de Imágenes: Docker Hub](#511-registro-de-imágenes-docker-hub)
      - [5.1.2. Búsqueda y Descarga de Imágenes](#512-búsqueda-y-descarga-de-imágenes)
      - [5.1.3. Login (Autenticación)](#513-login-autenticación)
      - [5.1.4. Etiquetado de Imágenes (`docker tag`)](#514-etiquetado-de-imágenes-docker-tag)
      - [5.1.5. Subida de Imágenes (`docker push`)](#515-subida-de-imágenes-docker-push)
    - [5.2. Automatización y Registros Alternativos](#52-automatización-y-registros-alternativos)
      - [5.2.1. Builds Automatizados (*Automated Builds*)](#521-builds-automatizados-automated-builds)
      - [5.2.2. Registros Alternativos](#522-registros-alternativos)
  - [6. Docker Compose: Orquestación Local de Multicontenedores](#6-docker-compose-orquestación-local-de-multicontenedores)
    - [6.1. Introducción y Utilidad](#61-introducción-y-utilidad)
      - [6.1.1. ¿Qué es Docker Compose?](#611-qué-es-docker-compose)
      - [6.1.2. Casos de Uso](#612-casos-de-uso)
    - [6.2. Sintaxis y Configuración del Archivo `docker-compose.yml`](#62-sintaxis-y-configuración-del-archivo-docker-composeyml)
      - [6.2.1. Estructura Principal](#621-estructura-principal)
      - [6.2.2. Definición de Servicios](#622-definición-de-servicios)
      - [6.2.3. Ejemplo de Despliegue Multi-Contenedor (WordPress + MariaDB)](#623-ejemplo-de-despliegue-multi-contenedor-wordpress--mariadb)
    - [6.3. Comandos Útiles con Docker Compose](#63-comandos-útiles-con-docker-compose)
      - [6.3.1. Ejecución: `docker-compose up -d`](#631-ejecución-docker-compose-up--d)
      - [6.3.2. Detención y Eliminación](#632-detención-y-eliminación)
      - [6.3.3. Eliminación Completa: `docker-compose down -v`](#633-eliminación-completa-docker-compose-down--v)
      - [6.3.4. Logs y Acceso](#634-logs-y-acceso)
  - [7. Docker Swarm: Orquestación Distribuida](#7-docker-swarm-orquestación-distribuida)
    - [7.1. Fundamentos de Orquestación Distribuida](#71-fundamentos-de-orquestación-distribuida)
      - [7.1.1. Propósito](#711-propósito)
      - [7.1.2. Objetivo](#712-objetivo)
      - [7.1.3. Arquitectura](#713-arquitectura)
    - [7.2. Gestión de Nodos y Servicios](#72-gestión-de-nodos-y-servicios)
      - [7.2.1. Roles (Manager y Worker)](#721-roles-manager-y-worker)
      - [7.2.2. Configuración Inicial y Unión de Nodos](#722-configuración-inicial-y-unión-de-nodos)
      - [7.2.3. Tipos de Servicios](#723-tipos-de-servicios)
    - [7.3. Despliegue y Networking en Swarm (Stacks)](#73-despliegue-y-networking-en-swarm-stacks)
      - [7.3.1. Despliegue de Stack](#731-despliegue-de-stack)
      - [7.3.2. Balanceo de Carga](#732-balanceo-de-carga)
      - [7.3.3. Redes Overlay](#733-redes-overlay)
  - [8. Conceptos Internos y Seguridad Avanzada](#8-conceptos-internos-y-seguridad-avanzada)
    - [8.1. Mecanismos Internos de Docker](#81-mecanismos-internos-de-docker)
      - [8.1.1. Copy-on-write (CoW)](#811-copy-on-write-cow)
      - [8.1.2. Almacenamiento por Capas (*Layers*)](#812-almacenamiento-por-capas-layers)
      - [8.1.3. Content Addressable Storage (CAS)](#813-content-addressable-storage-cas)
      - [8.1.4. Componentes del Kernel](#814-componentes-del-kernel)
    - [8.2. Seguridad y Hardening](#82-seguridad-y-hardening)
      - [8.2.1. Denegar Root](#821-denegar-root)
      - [8.2.2. Verificación de Integridad](#822-verificación-de-integridad)
      - [8.2.3. Content Trust (DCT)](#823-content-trust-dct)
      - [8.2.4. Análisis de Vulnerabilidades](#824-análisis-de-vulnerabilidades)
      - [8.2.5. Restricción de Tráfico](#825-restricción-de-tráfico)
  - [Autor](#autor)
    - [Contacto](#contacto)
  - [Licencia de uso](#licencia-de-uso)


## Introducción

En el mundo del despliegue de aplicaciones web, la **virtualización con contenedores** ha revolucionado la forma en que desarrollamos, implementamos y gestionamos aplicaciones. Docker, como la plataforma de contenedores más popular, ha facilitado la creación de entornos aislados y portátiles que permiten a los desarrolladores y administradores de sistemas trabajar de manera más eficiente y efectiva.

Esta tema tiene como objetivo proporcionar una comprensión profunda de Docker, sus componentes y su funcionamiento, así como las mejores prácticas para su uso en entornos de desarrollo y producción.

## Tutoriales
Nuestros tutoriales de partida son:

- [Tutorial de Docker](./Docker-Tutorial.pdf)

## Contenido en Youtube
- [Podcast](https://youtu.be/-8EoCawmjuw)
- [Resumen](https://youtu.be/ScgZLt8Ek8Y)
- [Lista de Reproducción](https://www.youtube.com/watch?v=phRvxD-IdCc&list=PLGIH-7eZDbVxu55hmqqdQE-Ba6FdPoO-Z)


## 1. Conceptos Fundamentales de Docker

### 1.1. ¿Qué es Docker?

#### 1.1.1. Definición

Docker es una **plataforma de código abierto** para desarrollar, lanzar y ejecutar aplicaciones. Es la tecnología de contenedores más popular que existe, aunque existen otras alternativas.

Permite empaquetar y lanzar una aplicación en un entorno totalmente aislado llamado **contenedor**. La plataforma promueve el eslogan: “Build, Ship and Run Any App, Anywhere” (Construye, envía y ejecuta cualquier aplicación, en cualquier lugar), ofreciendo una alternativa flexible y eficiente a la emulación de componentes de *hardware* basada en máquinas virtuales (VM).

#### 1.1.2. Propósito

El objetivo principal de Docker es **automatizar el despliegue de aplicaciones** dentro de contenedores de *software*. Esto se logra al separar las aplicaciones desarrolladas de la infraestructura donde se desarrollan, lo que se traduce en una mayor flexibilidad, portabilidad y un trabajo más ágil y cómodo.

Docker es una herramienta que resulta muy útil a programadores y administradores de *software* que se centran en **DevOps**, ya que mejora la eficiencia de su trabajo.

#### 1.1.3. Contenedores

Los contenedores son un **paquete de elementos** o un entorno de ejecución que se contiene a sí mismo. Permiten ejecutar un proceso o una aplicación determinada en cualquier sistema operativo.

Un contenedor es una aplicación agrupada y aislada que se ejecuta sobre un **mismo núcleo** (*kernel*) del sistema operativo. El contenedor contiene las capas superiores (sistema de ficheros, utilidades y aplicaciones), logrando el aislamiento e independencia deseada. Al ejecutarse, tienen un entorno similar al que tendrían si estuvieran en su propia máquina.

Los contenedores Docker permiten empaquetar, distribuir y ejecutar **servicios de red** con un formato estándar, incluyendo:
*   **Aplicaciones de red:** Web, bases de datos (BBDD), colas de mensajes, cachés, etc..
*   **Aplicaciones de línea de comandos:** Compiladores, generadores de sitios web, conversores de vídeo o generadores de informes.
*   **Aplicaciones gráficas:** Aunque es posible ejecutarlas, Docker no está diseñado principalmente para ello.

### 1.2. Contenedores vs. Máquinas Virtuales (MV)

La comparación entre contenedores y máquinas virtuales es compleja debido a las grandes diferencias esenciales entre ambos conceptos.

#### 1.2.1. Diferencias de Arquitectura

*   **Máquinas Virtuales (MV):** Consisten en la virtualización del *hardware*. Sobre este *hardware* virtualizado se ejecuta habitualmente un **sistema operativo (SO) completo**. Para ejecutar una MV se necesita un *hipervisor* que corra los diferentes SO. Las MV reservan la memoria completa para ser usada por el SO huésped y la aplicación.
*   **Contenedores:** No necesitan *hipervisor* ni simulan *hardware*. Aíslan las aplicaciones y generan un entorno replicable y estable. En lugar de albergar un SO completo, **comparten el núcleo (*kernel*)** del sistema operativo anfitrión. El contenedor es ejecutado directamente por el *kernel* como si fuera una aplicación normal, pero de forma aislada.

#### 1.2.2. Ventajas

La virtualización basada en contenedores ofrece ventajas similares a las MV, pero aprovechando mejor los recursos:

| Ventaja                   | Descripción                                                                                                                                                                                                         |
| :------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Ligereza**              | Los contenedores, por lo general, pesan muy poco. Por ejemplo, la imagen `nginx:alpine` es de solo **15MB**. Esto permite manejar muchos más contenedores que MV en la misma máquina.                               |
| **Eficiencia y Recursos** | Consumen únicamente la memoria que necesita la aplicación ejecutada en el contenedor.                                                                                                                               |
| **Velocidad**             | Los contenedores se lanzan rápidamente, tardando solo **segundos** o incluso milisegundos en arrancar.                                                                                                              |
| **Portabilidad**          | Se pueden utilizar de manera **multiplataforma** y en diversas infraestructuras (físicas, nube pública o privada) sin necesidad de adaptar la aplicación a las configuraciones de *hardware* o *software* del host. |
| **Repetibilidad**         | Facilidad para compartir contenedores en repositorios y moverlos entre entornos de desarrollo.                                                                                                                      |

#### 1.2.3. Desventajas

*   **Seguridad:** Compartir el *kernel* da la posibilidad de que una **vulnerabilidad en el mismo** afecte a todos los contenedores.
*   **Complejidad de Mantenimiento:** Migrar aplicaciones enteras a Docker puede suponer un incremento en la complejidad de mantenimiento.
*   **Almacenamiento:** Por defecto, los contenedores no disponen de almacenamiento persistente.

### 1.3. Arquitectura y Componentes de Docker

Docker, el proyecto de *software* más conocido de virtualización basada en contenedores, consta de tres componentes principales:

#### 1.3.1. Componentes Principales

1.  **Motor Docker** (Docker Engine).
2.  **Imágenes Docker**.
3.  **Registro** (Docker Hub).

#### 1.3.2. Docker Engine

El Motor Docker es una aplicación **cliente-servidor de código abierto**.

*   **Docker Daemon (Dockerd):** Funciona como servidor y se ejecuta en segundo plano en el sistema host. Se encarga del control central y gestiona objetos Docker como **imágenes, contenedores, redes y volúmenes**. Por defecto, Dockerd escucha localmente en un *Unix Socket* en `/var/run/docker.sock`.
*   **API REST:** Interfaz de programación que especifica un conjunto de interfaces que permite a otros programas interactuar y dar instrucciones al *daemon*.
*   **Docker Client (CLI):** Es la terminal del sistema operativo, o línea de comandos, que actúa como interfaz de usuario. Envía peticiones a la API REST del *daemon*. El mismo cliente puede comunicarse con varios *daemons*.

#### 1.3.3. Imágenes (Images)

*   Son **plantillas de solo lectura** y **inmutables**.
*   Contienen las instrucciones necesarias para que el motor Docker **cree un contenedor**.
*   Se pueden crear múltiples contenedores a partir de una misma imagen, parametrizándose con variables de entorno o volúmenes.
*   Son la **representación portátil de un contenedor**.
*   Se construyen a través de un archivo de texto plano llamado **Dockerfile**.

#### 1.3.4. Contenedores (Containers)

Un contenedor es una instancia ejecutable y modificable de una imagen. Es una imagen de Docker en funcionamiento.
• Puede ser creado, iniciado, detenido, movido o eliminado a través del cliente de Docker o de la API.
• Se ejecuta en un entorno aislado con sus propias variables de entorno, volúmenes montados e interfaces de red.
• Al borrar un contenedor, cualquier cambio en su estado se elimina, a menos que se haya almacenado en almacenamiento persistente (como un volumen).

### 1.4. Conceptos de Almacenamiento Básico
#### 1.4.1. Naturaleza Efímera
Los contenedores son efímeros y están diseñados como objetos de "usar y tirar". El almacenamiento de los contenedores no es persistente: cuando el contenedor se detiene o se elimina, los datos internos desaparecen: Consiste en montar un directorio de la máquina anfitriona (host) dentro del contenedor. Esto es útil para guardar el código de una aplicación o de una página web, ya que el entorno de desarrollo y el contenedor tienen acceso a los mismos archivos fuente. 3.  Memoria del sistema: Aunque se perdería al reiniciar el servidor, es otra opción de almacenamiento.


## 2. Instalación y Comandos Básicos de Docker CLI

### 2.1. Instalación y Configuración Inicial

#### 2.1.1. Requisitos Previos

Antes de iniciar la instalación de Docker Engine, es fundamental consultar la **documentación oficial**, ya que el proceso varía significativamente dependiendo de la distribución de Linux o del sistema operativo anfitrión (como Windows o macOS).

#### 2.1.2. Instalación y Comprobación

La instalación típicamente implica la configuración de repositorios oficiales y la descarga del paquete `docker-ce` (Community Edition).

**Proceso General de Instalación (ejemplo en Ubuntu):**

1.  Actualizar la lista de paquetes locales: `sudo apt update`.
2.  Configurar el repositorio y añadir la clave GPG de Docker.
3.  Instalar el paquete `docker-ce` (o `docker-engine` en versiones anteriores) y sus dependencias: `sudo apt install docker-ce`.

**Comprobación Inicial:**
El primer paso fundamental para verificar que Docker se ha instalado y está funcionando correctamente es ejecutar:

```bash
$ docker run hello-world
```

Al ejecutar este comando por primera vez, ocurren varios pasos en segundo plano:

1.  **Búsqueda Local:** El Docker Daemon (servidor) verifica si la imagen `hello-world` existe localmente.
2.  **Descarga (Pull):** Si no la encuentra, se **descarga automáticamente** del Docker Hub (el registro público predeterminado).
3.  **Creación y Ejecución:** Docker utiliza la imagen descargada para crear un nuevo contenedor, ejecuta el comando principal dentro de él, y muestra el mensaje de confirmación en la terminal.
4.  **Terminación:** Dado que `hello-world` es una aplicación de tipo "job", finaliza inmediatamente después de mostrar el mensaje, y el contenedor se detiene.

#### 2.1.3. Permisos

Por defecto, solo el usuario **root** o cualquier usuario que pertenezca al **grupo `docker`** puede ejecutar comandos de Docker.

Para evitar tener que escribir `sudo` antes de cada comando, lo cual es más conveniente para un entorno de desarrollo, es necesario añadir el usuario actual al grupo `docker`, que se crea automáticamente durante la instalación:

```bash
$ sudo usermod -aG docker $USER
```

Después de ejecutar este comando (o sustituyendo `$USER` por el nombre de usuario), es necesario cerrar la sesión y volver a iniciarla (o usar `su - <usuario>`) para aplicar el nuevo permiso. Sin esta configuración, si un usuario que no es *root* intenta ejecutar un comando Docker, recibirá un error de permisos.

### 2.2. Manejo del Ciclo de Vida del Contenedor

#### 2.2.1. Ejecución de Contenedores

El comando central para crear un contenedor y ponerlo en marcha de inmediato es `docker run` (o `docker container run`). Este comando combina la etapa de "creación" (`docker create`) con la de "inicio" (`docker start`).

#### 2.2.2. Modos de Ejecución

Existen dos modos principales para ejecutar un contenedor, dependiendo de si queremos interactuar con él o si debe funcionar como un servicio en segundo plano:

1.  **Modo Detached (Separado) (`-d`):**
    *   Ejecuta el contenedor en **segundo plano** (como un demonio), permitiendo al usuario seguir utilizando la *shell* sin que el contenedor la bloquee.
    *   Este modo es **esencial** para la ejecución de servicios de larga duración, como servidores web o bases de datos.

2.  **Modo Interactivo y Pseudo-TTY (`-it` o `-ti`):**
    *   La opción `-i` mantiene **STDIN abierto** (para permitir la entrada de datos) y `-t` asigna un **pseudo-TTY** (terminal).
    *   Se utiliza típicamente para obtener acceso interactivo a la *shell* del contenedor, a menudo combinado con `/bin/bash`.
    *   Si se sale de la *shell* interactiva, el proceso principal del contenedor (en este caso, `/bin/bash`) finaliza, y el contenedor **se detiene**.

#### 2.2.3. Identificación

Cada contenedor tiene un identificador único (ID) generado por Docker. Además:

*   **Nombres Asignados:** Se puede asignar un nombre legible y fácil de recordar usando el parámetro `--name` al ejecutar `docker run`.
*   **Nombres Generados:** Si no se especifica un nombre, Docker asigna uno automáticamente, que suele ser una combinación peculiar de un adjetivo y un apellido.
*   Tanto el ID como el nombre pueden usarse en comandos posteriores para referirse al contenedor.

#### 2.2.4. Visualización

Los comandos de la CLI son cruciales para el monitoreo del estado de los contenedores:

*   **Contenedores Activos/En Ejecución:**
    ```bash
    $ docker ps
    # o su sinónimo
    $ docker container ls
    ```
    Muestra solo los contenedores que están actualmente en funcionamiento.

*   **Todos los Contenedores (Activos y Detenidos):**
    ```bash
    $ docker ps -a
    ```
    Muestra todos los contenedores que existen en el sistema. Los contenedores detenidos o que ya han finalizado su tarea (con estado `Exited`) siguen consumiendo espacio en disco.

#### 2.2.5. Operaciones

Docker provee comandos para manejar el ciclo completo del contenedor:

| Comando                  | Acción                                 | Detalles                                                                                                                                  |
| :----------------------- | :------------------------------------- | :---------------------------------------------------------------------------------------------------------------------------------------- |
| `docker create`          | Crea el contenedor, pero no lo inicia  | Permite "preparar" el contenedor antes de lanzarlo.                                                                                       |
| `docker start <id/name>` | Inicia un contenedor que está detenido | Pone en marcha un contenedor previamente creado o detenido.                                                                               |
| `docker stop <id/name>`  | Detiene un contenedor en ejecución     | Envía la señal SIGTERM para una terminación limpia.                                                                                       |
| `docker kill <id/name>`  | Detiene un contenedor forzosamente     | Envía la señal SIGKILL, que no permite una terminación limpia.                                                                            |
| `docker rm <id/name>`    | Elimina un contenedor                  | Solo se puede eliminar un contenedor que no esté en ejecución. Se puede forzar la eliminación de un contenedor activo con la opción `-f`. |

#### 2.2.6. Inspección y Logs

*   **Logs (`docker logs`):** Permite ver la salida del contenedor (STDOUT y STDERR). El proceso principal debe generar los logs por la salida estándar para que Docker pueda capturarlos. La opción `-f` (follow) permite ver los logs en tiempo real a medida que se generan.
*   **Inspección (`docker inspect`):** Muestra información detallada y de bajo nivel (formato JSON) sobre la configuración del contenedor, incluyendo su estado, ID, mapeo de puertos y volúmenes montados. Se puede usar un filtro para ver solo partes específicas de la información, como los puntos de montaje (`-f {{.Mounts}}`).

### 2.3. Comandos Avanzados de Ejecución y Acceso

#### 2.3.1. Acceder a la Shell

Para ejecutar comandos dentro de un contenedor que **ya está en ejecución** (especialmente si fue lanzado en modo *detached*), se utiliza el comando `docker exec`:

```bash
$ docker exec -it <id/nombre_contenedor> /bin/bash
```

*   `exec` ejecuta el comando especificado (en este caso, `/bin/bash`) en el contenedor en funcionamiento.
*   La opción `-it` permite interactuar con la *shell* que se ha abierto.
*   El comando `/bin/bash` invoca la *shell* de Linux.

#### 2.3.2. Mapeo de Puertos

Los contenedores se ejecutan de forma aislada. Para acceder a un servicio que se ejecuta dentro del contenedor (por ejemplo, un servidor web en el puerto 80), es necesario **mapear o publicar** un puerto del *host* al puerto interno del contenedor:

```bash
$ docker run -p PUERTO_HOST:PUERTO_CONTENEDOR ...
```

*   **Ejemplo:** `docker run -d -p 8080:80 nginx:alpine`. Esto hace que las peticiones que lleguen al puerto **8080** del *host* se redirijan al puerto **80** del contenedor Nginx.
*   **Opción `-P` (Publicar):** Si se utiliza la opción `-P` (mayúscula) en `docker run`, Docker asignará automáticamente un puerto **aleatorio** en el *host* a cada puerto que haya sido expuesto mediante la instrucción `EXPOSE` en el Dockerfile.
*   **Diferencia con EXPOSE:** La instrucción `EXPOSE` dentro del Dockerfile simplemente **informa** a Docker qué puertos utiliza el servicio, pero no los publica automáticamente; el mapeo (`-p`) es siempre necesario para que sean accesibles desde fuera del host.

#### 2.3.3. Variables de Entorno

Se utilizan para configurar la aplicación o el servicio dentro del contenedor, siendo una práctica estándar para pasar credenciales (contraseñas, usuarios) o ajustes:

```bash
$ docker run -e VARIABLE=VALOR ...
```

Estas variables sobreescriben o definen la configuración que la imagen base espera.

#### 2.3.4. Creación de Imagen desde Contenedor

Aunque la **práctica recomendada** es construir imágenes mediante un **Dockerfile** para garantizar la repetibilidad, Docker permite capturar el estado actual de un contenedor en ejecución o detenido y guardarlo como una nueva imagen:

```bash
$ docker commit -m "Descripción" -a "Autor" <container-id> <nueva_imagen>
```

*   **Mecanismo:** El comando `docker commit` toma la capa modificable del sistema de archivos del contenedor (donde se guardan los cambios realizados, como la instalación de nuevos paquetes) y la convierte en una **nueva capa de imagen**.
*   **Uso:** Una vez que se ha realizado el *commit*, la nueva imagen (`<nueva_imagen>`) se almacena localmente y puede ser utilizada para lanzar nuevos contenedores.

## 3. Creación y Optimización de Imágenes (Dockerfile)

### 3.1. Estructura y Comandos del Dockerfile

#### 3.1.1. ¿Qué es el Dockerfile?

Un Dockerfile es la **receta** o archivo de **texto plano** que define las **instrucciones necesarias** para crear una imagen de Docker. Una imagen es la plantilla de solo lectura a partir de la cual se lanzarán los contenedores. Dockerfile es el método recomendado, ya que ofrece un proceso repetible, transparente e *idemopotente* para la creación de imágenes, a diferencia del comando `docker commit`.

Cada imagen construida a partir de un Dockerfile se basa en otra imagen y se compone de múltiples **capas** (*layers*) que se apilan. Cada instrucción en el Dockerfile se traduce en una de estas capas.

#### 3.1.2. Construcción de la Imagen (`docker build`)

Para crear una imagen a partir de un Dockerfile, se utiliza el comando `docker build`:

```bash
$ docker build -t <nombre_de_la_imagen> [path contexto del dockerfile]
```

*   **Contexto de Construcción (Build Context):** El `path` (generalmente un punto `.` que indica el directorio actual) especifica el contexto de construcción. Docker Daemon copia todos los archivos dentro de este directorio al servidor antes de comenzar la construcción. Es vital usar un archivo `.dockerignore` para excluir archivos innecesarios (ej. `.git/`, logs, dependencias instaladas) y no ralentizar el *build* o agregar archivos sensibles a la imagen.
*   **Etiquetado (`-t`):** La opción `-t` se utiliza para asignar un nombre legible y una etiqueta (*tag*) a la imagen (ej: `mi-app:v1`).

#### 3.1.3. Instrucciones Fundamentales del Dockerfile

Las instrucciones se procesan secuencialmente de arriba hacia abajo.

*   **FROM:**
    *   **Propósito:** Es la **primera instrucción obligatoria** en cualquier Dockerfile e indica la **imagen base** que se utilizará como punto de partida.
    *   **Sintaxis:** `FROM <imagen>:<tag>`.
    *   **Etiqueta:** Si no se especifica el *tag*, Docker asume por defecto la etiqueta `:latest`. Sin embargo, se recomienda **especificar una etiqueta de versión** (ej. `ubuntu:16.04`) y evitar `latest`, ya que esta puede apuntar a una imagen diferente en el futuro y romper el *build*.
    *   **Ejemplo:** `FROM node:7-alpine`

*   **RUN:**
    *   **Propósito:** Ejecuta comandos de *shell* **durante la construcción de la imagen**. Se utiliza para instalar *software*, descargar paquetes, configurar directorios o instalar dependencias.
    *   **Efecto de Capa:** Cada instrucción `RUN` crea una **nueva capa inmutable** en la imagen. Por ello, se recomienda fusionar múltiples comandos `RUN` en uno solo para minimizar el número de capas (ver sección de optimización).
    *   **Ejemplo:** `RUN apt-get update && apt-get install -y nginx`

*   **COPY y ADD:**
    *   **Propósito:** Copian archivos o directorios desde el contexto de construcción (el *host*) al sistema de archivos del contenedor en una ruta específica.
    *   **COPY:** Es la instrucción preferida y más simple. Solo copia archivos y directorios.
        *   **Ejemplo:** `COPY ./mi-app.jar /opt/app/`
    *   **ADD:** Es más compleja. Permite copiar archivos, pero también puede manejar la **extracción automática** de archivos comprimidos (`.tar`, `.tar.gz`) o descargar archivos desde una URL remota. Se recomienda `COPY` a menos que se necesite esta funcionalidad.

### 3.2. Directivas de Configuración y Metadatos

#### 3.2.1. Comandos de Ejecución (CMD vs. ENTRYPOINT)

Estas dos instrucciones definen qué ocurre cuando el contenedor se inicia:

| Instrucción    | Propósito                                               | Comportamiento                                                                                              |
| :------------- | :------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------- |
| **CMD**        | Provee **valores por defecto** para el contenedor.      | Se ignora si el usuario especifica un comando al ejecutar `docker run`. Solo la última aparición es válida. |
| **ENTRYPOINT** | Define el **comando principal** que se ejecuta primero. | Convierte la imagen en un ejecutable; los argumentos de `CMD` o de `docker run` se añaden como parámetros.  |

*   **Formato *Exec* (Recomendado):** `CMD ["ejecutable", "parámetro1", "parámetro2"]`. Utiliza sintaxis JSON.
*   **Formato *Shell*:** `CMD comando parámetro1 parámetro2`. Docker envuelve el comando con `/bin/sh -c`, lo que permite el reemplazo de variables de *shell*.

*   **Interacción:** Si se definen ambos, `CMD` proporciona los **argumentos predeterminados** para el comando definido en `ENTRYPOINT`. Esto permite al usuario anular solo los argumentos, no el comando principal.

    ```bash
    ENTRYPOINT ["curl", "-s"] # Comando principal: curl -s
    CMD ["http://localhost"]   # Argumento por defecto
    # Ejecución con CMD por defecto: curl -s http://localhost
    # Ejecución con anulación de CMD: docker run mi_imagen https://mi-web.com 
    #   (Resultado: curl -s https://mi-web.com)
    ```

#### 3.2.2. Configuración de Entorno y Directorios

*   **ENV:** Establece **variables de entorno** dentro del contenedor. Son cruciales para la configuración, como la contraseña de una base de datos o el puerto de la aplicación.
    *   **Ejemplo:** `ENV APP_PORT=8080`

*   **WORKDIR:** Establece el **directorio de trabajo** por defecto. Las instrucciones subsiguientes como `RUN`, `CMD`, `COPY`, o `ADD` se ejecutarán o referirán a esta ruta.

*   **USER:** Determina el nombre del **usuario** que se utilizará para ejecutar el contenedor y los comandos `RUN`, `CMD`, o `ENTRYPOINT`. Se recomienda **denegar el uso de *root***.

#### 3.2.3. Configuración de Red y Persistencia

*   **EXPOSE:** **Informa** a Docker qué puertos TCP/IP escucha el contenedor en tiempo de ejecución. Esto es solo informativo; **no mapea** el puerto al *host* automáticamente. Para publicar el puerto y hacerlo accesible desde fuera, se necesita el argumento `-p` en `docker run`.

*   **VOLUME:** Crea un punto de montaje o **volumen** en el contenedor, que es independiente del ciclo de vida del contenedor.

    *   **Ejemplo:** `VOLUME ["/var/log/app"]`

*   **HEALTHCHECK:** Proporciona un comando para que Docker verifique periódicamente el **estado de salud** del contenedor. Si el comando devuelve `0`, es saludable; si devuelve `1`, no lo es. Útil para verificar si un servicio web sigue respondiendo y no solo si el proceso está activo.
    *   **Ejemplo:** `HEALTHCHECK CMD curl --fail http://localhost:8080 || exit 1`

#### 3.2.4. Metadatos

*   **LABEL:** Permite añadir **metadatos** a la imagen (ej. autor, descripción, versión).
*   **MAINTAINER:** Instrucción obsoleta para especificar al autor; ha sido reemplazada por `LABEL`.

### 3.3. Creación y Gestión de Imágenes (Build)

#### 3.3.1. Proceso de Build

La construcción de la imagen (`docker build`) se realiza en un proceso de varias etapas:

1.  **Envío del Contexto:** El cliente Docker (CLI) empaqueta el contenido del directorio especificado (el *build context*) y lo envía al Docker Daemon.
2.  **Procesamiento por Capas:** El Daemon procesa cada instrucción del Dockerfile.
3.  **Creación de Capas:** Por cada instrucción que modifica el sistema de archivos (`RUN`, `COPY`, `ADD`), se crea una nueva **capa** inmutable (Union Filesystem).
4.  **Imágenes Intermedias:** Entre cada instrucción, Docker crea una imagen temporal (o intermedia) que se almacena en la caché.

*   **Manejo de Fallos:** Si una instrucción falla (ej. un `RUN` que devuelve un código de error), el proceso de *build* se detiene en ese punto. El contenedor intermedio de la última instrucción exitosa se mantiene y puede ser inspeccionado para depuración.

#### 3.3.2. Alternativa: `docker commit`

Aunque no se recomienda para imágenes de producción, es posible crear una imagen a partir de un contenedor en ejecución o detenido.

*   **Mecanismo:** `docker commit` toma la capa de lectura/escritura (R/W layer) del contenedor, donde se guardan las modificaciones que se hicieron en la ejecución (ej. instalar `nano`), y la convierte en una nueva capa de imagen.
*   **Sintaxis:**

    ```bash
    $ docker commit -m "Descripción" -a "Autor" <container-id> <nueva_imagen>
    ```

*   **Problema:** No es reproducible ni transparente, ya que la "receta" no queda documentada y automatizada, lo que es esencial para la repetibilidad.

### 3.4. Buenas Prácticas y Optimización de Imágenes

Las buenas prácticas buscan tres objetivos principales: minimizar el tamaño de la imagen, maximizar la velocidad de la construcción (aprovechando la caché) y aumentar la seguridad.

#### 3.4.1. Minimizar el Tamaño y Número de Capas

*   **Build Multi-Stage (Multi-etapa):**
    *   **Concepto:** Permite utilizar un primer *stage* para compilar o construir el código (que puede ser muy pesado, con herramientas de *build*, dependencias y código fuente) y luego, en un segundo *stage* (la imagen final de ejecución), copiar **solamente los artefactos binarios** necesarios para ejecutar la aplicación.
    *   **Ventaja:** Resuelve el problema de que los archivos eliminados sigan ocupando espacio en las capas anteriores. La imagen final es mucho más ligera y segura.
    *   **Ejemplo (Go/Node):**
        ```dockerfile
        FROM golang:1.12 AS builder # Etapa 1 (Compilación pesada)
        WORKDIR /app
        COPY go.mod go.sum ./
        RUN go mod download
        COPY . .
        RUN go build -o main .
        
        FROM alpine:latest # Etapa 2 (Ejecución ligera)
        WORKDIR /app
        COPY --from=builder /app/main . # Copia solo el binario final
        CMD ["./main"]
        ```

*   **Consolidar Comandos RUN:** Fusionar múltiples comandos que realizan tareas relacionadas (ej. `apt-get update` y `apt-get install`) en una sola instrucción `RUN`, utilizando `&& \`. Esto minimiza el número de capas innecesarias.

*   **Limpieza de Archivos:** Eliminar caché, temporales y archivos innecesarios inmediatamente después de instalarlos en el mismo comando `RUN`.
    *   **Ejemplo:** `RUN apt-get update && apt-get install -y nodejs && rm -rf /var/lib/apt/lists/*`.

*   **Imágenes Base Ligeras:** Utilizar distribuciones ligeras como **Alpine** (que es de unos 4 MB) o imágenes **Distroless** (que eliminan *shells* y gestores de paquetes) para reducir la superficie de ataque y el tamaño final.

#### 3.4.2. Optimización de la Caché de Construcción

La caché de Docker se reutiliza si el *hash* de la instrucción y el contenido de los archivos involucrados no ha cambiado.

*   **Orden de Capas:** Colocar las instrucciones que tienen **menos probabilidad de cambiar** (ej. instalación de dependencias principales o del *runtime*) en la **parte superior** del Dockerfile. Si una capa superior cambia (ej. una modificación en el código fuente), todas las capas subsiguientes deben reconstruirse, invalidando la caché.

*   **Uso de `COPY` Inteligente:** En aplicaciones de Node.js o Python, copiar primero solo el archivo de manifiesto (ej. `package.json` o `requirements.txt`) para forzar la instalación de dependencias, y luego copiar el resto del código. Si solo cambia el código, la costosa capa de instalación de dependencias se reutiliza.
    ```dockerfile
    # Solo copia el manifiesto (raramente cambia)
    COPY package.json /app 
    RUN npm install # Esta capa usa la caché si package.json no cambió
    # Copia el código fuente (cambia a menudo)
    COPY . /app
    ```

*   **`COPY` sobre `ADD`:** `COPY` es más predictivo para el caché que `ADD`.

#### 3.4.3. Diseño y Seguridad

*   **One-Concern Container:** El contenedor debe ocuparse únicamente de un solo asunto (ejecutar un proceso principal). Esto facilita el **desacoplamiento** y la orquestación. Si se requieren múltiples servicios (ej. web y BD), deben separarse en distintos contenedores y conectarse (por ejemplo, mediante Docker Compose).
*   **Uso de `.dockerignore`:** Imprescindible para excluir archivos grandes o sensibles del *build context* (ej. directorios `.git/`, logs, o archivos de configuración local).
*   **Denegar Root:** Usar la instrucción `USER` para **ejecutar el contenedor con un usuario no root**. Esto limita el impacto de una posible vulnerabilidad.
*   **No Guardar Credenciales:** **Nunca** se deben incluir credenciales o información secreta en el Dockerfile, ya que estas quedan en las capas de la imagen y son accesibles. Las credenciales deben ser inyectadas en tiempo de ejecución a través de variables de entorno (`-e`) o sistemas de gestión de secretos (como los de Docker Swarm o Kubernetes).

## 4. Persistencia y Redes Avanzadas

### 4.1. Manejo de la Persistencia de Datos

Por defecto, los contenedores están diseñados como **objetos efímeros** de "usar y tirar". El almacenamiento dentro de un contenedor es aislado y no persistente, lo que significa que si el contenedor se detiene y se elimina, **los datos internos desaparecen** de forma permanente.

Si se desea almacenar datos de forma segura (como una base de datos o una página web) más allá del ciclo de vida del contenedor, se debe recurrir a mecanismos de almacenamiento persistente. Docker ofrece principalmente dos métodos para lograr la persistencia de datos: los Volúmenes y los Enlaces de Directorios (*Bind Mounts*).

#### 4.1.1. Volúmenes

Los volúmenes son la manera **preferida y más eficiente** de gestionar el almacenamiento persistente en Docker.

**Definición y Características:**

*   Los volúmenes son **objetos gestionados por Docker** que persisten más allá de la vida del contenedor. Son entidades independientes, similares a las imágenes y los contenedores.
*   Permiten un **almacenamiento persistente** que se conserva incluso si el contenedor es destruido.
*   Al montar un volumen en una ruta del contenedor, cuando este lee o escribe en ese directorio, la operación se realiza realmente en el volumen de Docker.
*   Una vez creados, los volúmenes pueden ser **compartidos y reutilizados** por múltiples contenedores.
*   La ventaja frente a los directorios enlazados es que su gestión y ciclo de vida (creación, listado y eliminación) son controlados directamente por Docker.
*   El acceso al contenido de los volúmenes **solo puede hacerse a través de algún contenedor** que utilice el volumen; no deben accederse directamente desde la máquina anfitriona (*host*).

**Comandos de Gestión de Volúmenes:**

| Comando                | Utilidad                          | Ejemplo                             |
| :--------------------- | :-------------------------------- | :---------------------------------- |
| `docker volume create` | Crea un volumen local con nombre. | `$ docker volume create mi-volumen` |
| `docker volume ls`     | Lista los volúmenes existentes.   | `$ docker volume ls`                |
| `docker volume rm`     | Elimina un volumen.               | `$ docker volume rm mi-volumen`     |

**Montaje de Volúmenes en la Ejecución:**

Para montar un volumen en un contenedor, se utiliza la opción `--mount` o el *flag* `-v` en el comando `docker run`.

*   **Sintaxis con `--mount`:** Especifica el tipo (`type=volume`), la fuente (nombre del volumen) y el destino (ruta dentro del contenedor).
    ```bash
    $ docker run -dit --name miapache-php --mount type=volume,source=vol-miapache-php,target=/var/www/html miapache-php
    ```

*   **Volúmenes Automáticos con `-v`:** Se puede usar la opción `-v` sin especificar una ruta del host; Docker creará un volumen automático (cuyo nombre no se elige) y lo enlazará a un directorio del contenedor:
    ```bash
    $ docker run -d -v /var/lib/mysql mariadb # Docker crea un volumen anónimo para /var/lib/mysql
    ```

#### 4.1.2. Enlace de Directorios (Bind Mounts)

Los *Bind Mounts* son el segundo mecanismo para la persistencia, ideal para el trabajo con código fuente y entornos de desarrollo.

**Definición y Características:**

*   Consiste en **enlazar o mapear** un directorio local de la máquina anfitrión (*host*) con un directorio específico dentro del contenedor.
*   Los cambios realizados en el código fuente en el *host* se reflejan instantáneamente en el contenedor, sin necesidad de reconstruir la imagen ni reiniciar el contenedor.
*   Se utiliza el *flag* `-v` (volume) o la sintaxis `--mount type=bind` al ejecutar `docker run`.

**Sintaxis y Ejemplos de Bind Mounts:**

*   **Uso del *flag* `-v` (más simple para desarrollos):** Se mapea la ruta actual del sistema anfitrión (`$PWD`) con la ruta donde el contenedor espera el contenido (`/usr/local/apache2/htdocs`).
    ```bash
    # Mapea el directorio local actual al directorio htdocs de Apache:
    $ docker run -dit --name miapache -p 5555:80 -v "$PWD":/usr/local/apache2/htdocs httpd
    ```

*   **Uso de `--mount` (sintaxis más larga):** Requiere especificar el tipo y la ruta de origen y destino. Ambos directorios deben existir previamente.
    ```bash
    # Sintaxis con --mount: type=bind,source=ORIGEN-EN-HOST,target=DESTINO-EN-CONTENEDOR
    $ docker run --mount type=bind,source="$PWD/src",target=/var/www/html ...
    ```

#### 4.1.3. Casos de Uso

| Caso de Uso                  | Recomendación   | Razón                                                                                                                                                                         |
| :--------------------------- | :-------------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Datos de Bases de Datos**  | **Volúmenes**   | Son gestionados por Docker y persisten de forma segura más allá del ciclo de vida del contenedor. Ejemplo: montar un volumen en `/var/lib/mysql` para datos de MariaDB/MySQL. |
| **Código Fuente/Desarrollo** | **Bind Mounts** | Permite que el entorno de desarrollo del host y el contenedor tengan acceso al mismo código, facilitando las modificaciones y el testeo instantáneo.                          |

### 4.2. Configuración de Redes (Networking)

El *networking* en Docker es esencial para permitir que los contenedores aislados se comuniquen entre sí y con el Docker *host*, permitiendo crear aplicaciones *multi-contenedor* que funcionan conjuntamente de forma segura.

#### 4.2.1. Aislamiento

Docker implementa el aislamiento de red utilizando características de virtualización del núcleo de Linux, como los **Namespaces**.

*   Cada contenedor recibe su propio **namespace de red**, lo que le proporciona una vista aislada de un adaptador de red.
*   Esta configuración se realiza a través de la creación de interfaces de red virtuales (`veth` o *virtual Ethernet devices*) que actúan como un cable cruzado entre el *namespace* del contenedor y el *bridge* (`docker0`) en el *host*.
*   El aislamiento se complementa con reglas de **IPTables** para filtrar el tráfico y realizar NAT (*Network Address Translation*), lo que redirige las peticiones externas hacia el contenedor.

#### 4.2.2. Modos de Red

Docker define varios modos de red que determinan cómo interactúa el contenedor con el host y otros contenedores:

| Modo        | Descripción                                                                                                                                                 | Uso y Características                                                                                                                                  |
| :---------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bridge**  | **Modo predeterminado.** Crea una red interna privada en el *host* (`docker0`) y utiliza reglas de IPTables para el tráfico saliente y el mapeo de puertos. | En este modo, la **resolución de nombres de contenedores por defecto no funciona**, solo la comunicación por IP. **No se recomienda para producción**. |
| **Host**    | **Elimina el aislamiento de red**. El contenedor comparte el *namespace* de red del *host*, utilizando directamente sus interfaces.                         | Proporciona **mejor rendimiento** (evita NAT), pero las opciones de mapeo de puertos (`-p`) se ignoran.                                                |
| **None**    | El contenedor **no tiene interfaz de red**, excepto la interfaz virtual `loopback`.                                                                         | Útil para contenedores que no requieren conectividad o que se conectarán a una red de forma manual más tarde.                                          |
| **MacVlan** | Asigna una **dirección MAC** a cada contenedor, haciéndolos aparecer como máquinas físicas independientes en la red.                                        | Se utiliza cuando se requiere un acceso a la red de capa 2 (físico), a menudo para herramientas de monitoreo de tráfico.                               |
| **Overlay** | Redes **virtuales y distribuidas** que interconectan contenedores situados en **diferentes *hosts*** (multi-host) de forma transparente.                    | Se utiliza principalmente en sistemas de **orquestación** (como Docker Swarm).                                                                         |

#### 4.2.3. Redes Definidas por Usuario

Para superar las limitaciones del modo `bridge` por defecto, es una buena práctica crear redes `bridge` definidas por el usuario.

*   **Creación y Gestión:** Se crean con `docker network create` y cada una genera un nuevo *bridge* en el *host*.
    ```bash
    $ docker network create mired
    $ docker network ls
    $ docker network inspect mired # Muestra contenedores incluidos e IPs privadas
    ```

*   **Aislamiento y Comunicación:** Las redes definidas por el usuario permiten un mejor aislamiento e **interoperabilidad** entre aplicaciones. Los contenedores conectados a la misma red automáticamente exponen todos sus puertos entre ellos.

*   **Resolución DNS Integrada:** A diferencia del *bridge* por defecto, las redes de usuario proveen **resolución DNS** entre contenedores conectados a ellas. Esto significa que un contenedor puede comunicarse con otro simplemente usando el **nombre del contenedor** o del servicio, sin necesidad de usar la opción *legacy* `--link`.

*   **Asociar un Contenedor a una Red:**
    ```bash
    $ docker run -d --name mi_apache --network mired -p 80:80 httpd
    ```

#### 4.2.4. Enlace de Contenedores

El enlace de contenedores (*linking*) es el mecanismo que permite que los contenedores puedan accederse por su nombre.

*   **Mecanismo *Legacy* (`--link`):**
    *   Este mecanismo, que está **obsoleto y no se recomienda** en entornos de producción, se utilizaba para enlazar contenedores conectados a la red *bridge* por defecto (donde no había DNS).
    *   El *flag* `--link <contenedor_enlazado>:<alias>` crea una asociación.
    *   Tenía dos características clave: se **compartían las variables de entorno** del primer contenedor al segundo, y se modificaba el archivo **/etc/hosts** del contenedor asociado para lograr **resolución estática** de nombres (la forma recomendada de extraer la IP de un contenedor enlazado era a través de `/etc/hosts`).

*   **Mecanismo Moderno (DNS en Redes de Usuario):**
    *   Cuando se utilizan **redes definidas por el usuario**, la resolución de nombres se realiza automáticamente mediante un **servidor DNS** que se crea en el *gateway* de la red.
    *   Por lo tanto, solo es necesario hacer referencia al contenedor por su nombre, y la opción `--link` ya no es necesaria.
    *   Ejemplo de Uso (sin `--link`): Al desplegar WordPress, la aplicación puede acceder a la base de datos (contenedor `servidor_mariadb`) indicando la variable `WORDPRESS_DB_HOST=servidor_mariadb`.

## 5. Compartiendo Imágenes y Registros

### 5.1. Docker Hub y Gestión Remota

#### 5.1.1. Registro de Imágenes: Docker Hub

Docker Hub es el **registro público y gratuito** gestionado por Docker, Inc.. Funciona como un repositorio central donde la comunidad y los proveedores de *software* pueden subir sus imágenes de Docker para ser compartidas o utilizadas.

*   **Definición:** Es una especie de **biblioteca** para las imágenes Docker, o una "tienda de aplicaciones".
*   **Acceso:** Docker viene configurado por defecto para buscar y descargar imágenes de Docker Hub si no las encuentra localmente.
*   **Tipos de Repositorios:** Docker Hub permite alojar repositorios **públicos** (gratuitos e ilimitados) y **privados** (que requieren un plan de pago para tener más de uno). Los repositorios privados se usan para almacenar imágenes que contienen información o código propietario que se desea mantener seguro.

#### 5.1.2. Búsqueda y Descarga de Imágenes

Para interactuar con el registro desde la terminal, se utiliza la interfaz de línea de comandos (CLI) de Docker.

**Búsqueda de Imágenes (`docker search`)**

El comando `docker search` permite buscar imágenes disponibles en Docker Hub que coincidan con un criterio específico:

```bash
$ docker search ubuntu
```

La salida del comando muestra varios campos importantes:
*   **REPOSITORY:** Nombre del repositorio.
*   **DESCRIPTION:** Descripción de la imagen.
*   **STARS:** Mide la popularidad de la imagen.
*   **OFFICIAL:** Si dice `OK`, significa que la imagen está avalada por la empresa responsable del proyecto.
*   **AUTOMATED:** Indica si la imagen fue construida por el proceso de *Automated Build* de Docker Hub.

**Descarga de Imágenes (`docker pull`)**

Una vez identificada la imagen deseada, se puede descargar una copia al sistema local utilizando `docker pull`.

```bash
# Sintaxis general
$ docker pull REPOSITORIO[:TAG]

# Ejemplo de descarga de una imagen específica
$ docker pull ubuntu:20.04
```

*   Si no se especifica una etiqueta (`:TAG`), Docker asume por defecto la etiqueta `:latest`.
*   Al ejecutar `docker run`, si la imagen no está localmente, Docker realiza automáticamente un `pull` antes de crear el contenedor.

#### 5.1.3. Login (Autenticación)

Para poder subir (hacer *push*) o interactuar con repositorios privados, es necesario autenticarse en Docker Hub desde la terminal local.

*   **Comando de Autenticación:** Se utiliza `docker login`.

```bash
$ docker login
# O especificando el usuario:
$ docker login -u nombre_de_usuario
```

*   El sistema solicitará la contraseña de Docker Hub para completar la autenticación.

#### 5.1.4. Etiquetado de Imágenes (`docker tag`)

Antes de que una imagen pueda ser subida a un registro, debe ser **etiquetada (*tagged*)** siguiendo la nomenclatura requerida por ese registro. El etiquetado vincula la imagen local existente con un repositorio específico en Docker Hub.

*   **Convención de Docker Hub:** Para subir a Docker Hub (un registro público), la imagen debe seguir la convención `NOMBRE_DE_USUARIO/NOMBRE_DEL_REPOSITORIO:ETIQUETA`.
*   **Convención para Registros Privados/Alojados:** Si se utiliza un registro privado, se debe especificar el *host* o dirección del registro, seguido del nombre de usuario y el repositorio (ej: `REGISTRYHOST/USERNAME/NAME:TAG`).

**Comando de Etiquetado:**

```bash
# Sintaxis: docker tag <imagen_local> <repositorio_destino>
$ docker tag mi-imagen-local:v1 mi_usuario_hub/mi-app-web:v1
```

Tras ejecutar este comando, se crea una nueva etiqueta para el mismo `IMAGE ID` local, pero ahora con el formato de repositorio de Docker Hub.

#### 5.1.5. Subida de Imágenes (`docker push`)

Una vez que la imagen ha sido etiquetada correctamente y se ha iniciado sesión con `docker login`, se puede subir al repositorio remoto con el comando `docker push`.

*   **Ejemplo Práctico de Subida:**

    1.  **Construir la imagen localmente** (si no se ha hecho):
        ```bash
        $ docker build --tag=apache-php .
        # Comprobar la ID de la imagen local: docker images
        ```

    2.  **Etiquetar la imagen** con el formato de usuario/repositorio:
        ```bash
        $ docker tag apache-php joseluisgs/apache-php:v1
        # Se necesita este formato antes de subirla.
        ```

    3.  **Subir la imagen** al registro (asumiendo que ya se hizo `docker login`):
        ```bash
        $ docker push joseluisgs/apache-php:v1
        ```

*   Si se intenta subir una imagen sin el prefijo de usuario (`jamtur01/static_web`), Docker lo rechazará, indicando que no se puede hacer *push* a un repositorio raíz.

### 5.2. Automatización y Registros Alternativos

#### 5.2.1. Builds Automatizados (*Automated Builds*)

Docker Hub soporta *Automated Builds* (construcciones automatizadas), un componente clave para la **Integración Continua (CI)** que permite automatizar la creación de imágenes.

**Funcionamiento:**

*   Este mecanismo enlaza un repositorio de código fuente (como **GitHub** o **Bitbucket**) que contiene un **Dockerfile** con un repositorio en Docker Hub.
*   Cada vez que se realiza un *commit* o un *push* al repositorio de código fuente, Docker Hub detecta el cambio y **activa un proceso de *build*** en sus servidores.
*   La imagen resultante se construye con el Dockerfile del repositorio y se sube automáticamente al registro de Docker Hub.

**Configuración en Docker Hub:**

1.  En la página de Docker Hub, se selecciona "Add Repository" y luego "Automated Build".
2.  Se elige la plataforma de control de versiones (GitHub o Bitbucket) y se autoriza el acceso.
3.  Se selecciona el repositorio de código fuente y se configura el *build* (rama por defecto, etiquetas, y la ubicación del Dockerfile, que por defecto es la raíz).
4.  Se pueden definir reglas de despliegue basadas en *commits* a una rama o la creación de etiquetas (*tags*).

#### 5.2.2. Registros Alternativos

Aunque Docker Hub es el registro por defecto, existen varias alternativas, tanto públicas como privadas, que ofrecen distintas funcionalidades, especialmente para entornos empresariales que buscan mayor confidencialidad o integración con otros servicios en la nube.

| Registro                            | Tipo                            | Características Principales                                                                                                                                                 |
| :---------------------------------- | :------------------------------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Docker Hub**                      | Público/Privado                 | Es el registro por defecto. Ofrece alojamiento ilimitado para repositorios públicos de forma gratuita.                                                                      |
| **Quay**                            | Público/Privado (Cloud/On-Prem) | Adquirido por Red Hat. Ofrece *builds* automáticos, escaneo de vulnerabilidades y es gratuito para repositorios públicos.                                                   |
| **Amazon ECR**                      | Privado (Cloud)                 | Orientado a uso privado en AWS. La gestión de permisos de acceso se realiza mediante IAM. No tiene una interfaz de usuario (*UI*) para buscar imágenes.                     |
| **Google Container Registry (GCR)** | Privado/Público (Cloud)         | Integrado en Google Cloud. Sus URLs son del tipo `gcr.io/user/repositorio`.                                                                                                 |
| **Azure Container Registry (ACR)**  | Privado (Cloud)                 | Permite almacenar contenedores, Helm Charts y artefactos OCI.                                                                                                               |
| **Harbor**                          | Privado (Open Source/On-Prem)   | Proyecto *Open Source* (originalmente de VMware). Ofrece interfaz gráfica, RBAC (Control de Acceso Basado en Roles), replicación y escaneo de vulnerabilidades (con Clair). |
| **Nexus / Artifactory**             | Privado (On-Prem/Cloud)         | Almacenes de binarios (*artifacts*) que soportan imágenes Docker, además de otros formatos (Maven, npm, etc.).                                                              |

Además, es posible **ejecutar un registro privado propio** utilizando la imagen `registry:2` de Docker, ideal para almacenar imágenes detrás del *firewall* o cuando se requiere mayor confidencialidad.

**Ejecución de Registro Privado Básico:**

1.  **Lanzar el contenedor del registro:**
    ```bash
    $ docker run -d -p 5000:5000 --restart=always --name mi-registro registry:2
    ```

2.  **Etiquetar una imagen local** para apuntar al nuevo registro (si el host es `localhost`):
    ```bash
    $ docker tag mi-imagen-local:v1 localhost:5000/mi-repositorio:v1
    ```

3.  **Subir la imagen** (requiere configurar el daemon como *inseguro* si no se usa TLS):
    ```bash
    $ docker push localhost:5000/mi-repositorio:v1
    ```

## 6. Docker Compose: Orquestación Local de Multicontenedores

### 6.1. Introducción y Utilidad

#### 6.1.1. ¿Qué es Docker Compose?

Docker Compose es una **herramienta para definir y ejecutar aplicaciones multi-contenedor**. Permite simplificar el uso de Docker al automatizar la creación, el inicio y la parada de un conjunto de contenedores que trabajan juntos.

En lugar de lanzar múltiples comandos `docker run` con parámetros complejos (`-p`, `-e`, `--link`, `--name`), Compose utiliza un único archivo de configuración en formato **YAML** (`docker-compose.yml`) para describir todos los servicios que componen la aplicación, sus dependencias y su interacción.

**Integración:**
*   Aunque originalmente fue desarrollado por Orchard bajo el nombre de Fig, Docker Inc. lo renombró a Docker Compose y lo ha integrado estrechamente en el ecosistema.
*   Con un solo comando (`docker-compose up`), se pueden crear e iniciar todos los servicios que necesita la aplicación.

#### 6.1.2. Casos de Uso

Docker Compose es especialmente útil para gestionar entornos donde la orquestación distribuida (como Docker Swarm o Kubernetes) no es necesaria, ya que se centra en el **despliegue en un único *host***.

Los casos de uso más habituales incluyen:
*   **Entornos de Desarrollo:** Permite a los desarrolladores levantar un *stack* completo (ej. una aplicación web, su base de datos y un servicio de caché) con una sola ejecución.
*   **Entornos de Testeo Automático (Integración Continua - CI):** Facilita la creación y destrucción rápida de entornos completos y predecibles para la ejecución de pruebas.
*   **Despliegue en *Hosts* Individuales:** Se utiliza para desplegar aplicaciones sencillas que residen en un único servidor.

### 6.2. Sintaxis y Configuración del Archivo `docker-compose.yml`

El archivo `docker-compose.yml` define la aplicación multi-contenedor. Su sintaxis es en formato YAML.

#### 6.2.1. Estructura Principal

El archivo se organiza típicamente en las siguientes secciones:

1.  **`version`:** Identifica la versión del formato de archivo Compose a utilizar (ej. `version: '3.7'`). Se recomienda usar la última versión disponible.
2.  **`services`:** Sección obligatoria donde se definen los contenedores individuales que componen la aplicación (ej. `db`, `web`).
3.  **`volumes`:** Sección opcional que define los volúmenes persistentes que serán utilizados por los servicios.
4.  **`networks`:** Sección opcional que define las redes de usuario a crear para el *stack*.

#### 6.2.2. Definición de Servicios

Dentro de la sección `services`, cada entrada define un contenedor. El nombre de este servicio (ej. `web` o `db`) es crucial, ya que se convierte en el **nombre de host interno** que otros contenedores pueden usar para comunicarse (gracias a la resolución DNS integrada).

| Parámetro                    | Equivalencia CLI                | Descripción Detallada                                                                                                                                        |
| :--------------------------- | :------------------------------ | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`image`**                  | `FROM` (en Dockerfile)          | Especifica la imagen de Docker a utilizar (ej. `mariadb:10.5`).                                                                                              |
| **`build`**                  | `docker build`                  | En lugar de usar una imagen existente, indica el directorio donde se encuentra el **Dockerfile** que Compose debe construir.                                 |
| **`container_name`**         | `--name`                        | Permite asignar un nombre específico al contenedor, en lugar del nombre compuesto por defecto (ej. `wordpress_db`).                                          |
| **`ports`**                  | `-p` (publish)                  | Mapeo de puertos, en el formato `PUERTO_HOST:PUERTO_CONTENEDOR`.                                                                                             |
| **`volumes`**                | `-v` (volume/bind)              | Define los puntos de montaje. Puede ser un **volumen** nombrado (`data:/ruta/interna`) o un **bind mount** a un directorio del host (`./src:/var/www/html`). |
| **`environment`**            | `-e`                            | Define variables de entorno para configurar la aplicación (ej. contraseñas de bases de datos).                                                               |
| **`depends_on`**             | `--link` (obsoleto)             | Indica las dependencias entre servicios. Asegura que los servicios se inicien en el orden correcto (ej. el servidor web espera a la base de datos).          |
| **`networks`**               | `--net`                         | Asigna el servicio a una o varias redes definidas por el usuario.                                                                                            |
| **`command` / `entrypoint`** | Se sobrescribe CMD / ENTRYPOINT | Permite sobrescribir el comando o punto de entrada por defecto de la imagen.                                                                                 |

#### 6.2.3. Ejemplo de Despliegue Multi-Contenedor (WordPress + MariaDB)

Este ejemplo ilustra cómo definir una aplicación completa que requiere dos servicios, en este caso un servidor web WordPress y su base de datos MariaDB:

```yaml
version: '3'
services:
  db:
    image: mariadb:10.5
    container_name: mariadb 
    volumes:
      - data:/var/lib/mysql # Usa un volumen llamado 'data' para persistencia
    environment:
      - MYSQL_ROOT_PASSWORD=secret
      - MYSQL_DATABASE=wordpress
      - MYSQL_USER=manager
      - MYSQL_PASSWORD=secret
  
  web:
    image: wordpress:4.9.8
    container_name: wordpress
    depends_on: # Espera a que el servicio 'db' esté listo
      - db
    volumes:
      - ./wordpress:/var/www/html # Bind mount para el código fuente
    environment:
      - WORDPRESS_DB_USER=manager
      - WORDPRESS_DB_PASSWORD=secret
      - WORDPRESS_DB_HOST=db # Uso del nombre del servicio 'db' para la conexión DNS
    ports:
      - 8080:80 # Mapea el puerto 80 del contenedor al 8080 del host
volumes:
  data: # Declaración del volumen persistente
```

### 6.3. Comandos Útiles con Docker Compose

Docker Compose tiene comandos específicos para manejar el ciclo de vida completo de la aplicación, siendo más cómodos que sus equivalentes en Docker CLI.

#### 6.3.1. Ejecución: `docker-compose up -d`

El comando `up` (arriba) es el más importante, ya que lee el archivo YAML, construye las imágenes si es necesario y lanza todos los servicios.

| Comando                                | Descripción                                                                                                                 |
| :------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------- |
| **`docker-compose up`**                | Construye, crea e inicia todos los contenedores en **primer plano**. Muestra los logs multiplexados de todos los servicios. |
| **`docker-compose up -d`**             | Construye, crea e inicia todos los servicios en **modo separado (*detached*)** (segundo plano).                             |
| **`docker-compose up --scale web=5`**  | Inicia o escala el servicio `web` a 5 réplicas.                                                                             |
| **`docker-compose up -f filename -d`** | Permite especificar un nombre de archivo diferente si no se llama `docker-compose.yml`.                                     |

#### 6.3.2. Detención y Eliminación

Compose ofrece granularidad en la finalización de los servicios:

| Comando                               | Descripción                                                                                                               |
| :------------------------------------ | :------------------------------------------------------------------------------------------------------------------------ |
| **`docker-compose stop`**             | **Detiene** los contenedores en ejecución (envía SIGTERM), pero **los mantiene creados** y configurados.                  |
| **`docker-compose down`**             | Detiene los contenedores y los **elimina**, junto con las redes creadas por Compose. Los volúmenes persisten por defecto. |
| **`docker-compose start <servicio>`** | Inicia servicios que han sido detenidos previamente.                                                                      |
| **`docker-compose rm <servicio>`**    | Elimina contenedores detenidos.                                                                                           |

#### 6.3.3. Eliminación Completa: `docker-compose down -v`

Para asegurar una limpieza total de los recursos, es necesario añadir el *flag* `-v` (volumes) a `down`:

```bash
$ docker-compose down -v
```

*   Este comando detiene y elimina los contenedores y, además, **elimina los volúmenes** asociados** y las redes**.
*   Si se elimina el volumen de una base de datos con este comando, **los datos se pierden para siempre**.

#### 6.3.4. Logs y Acceso

Compose simplifica la monitorización y el acceso a la *shell* de los contenedores que se están ejecutando.

| Comando                                        | Descripción                                                                                                                                                         |
| :--------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`docker-compose ps`**                        | Muestra el estado de los servicios definidos en el archivo YAML.                                                                                                    |
| **`docker-compose logs`**                      | Muestra la salida (*logs*) de todos los servicios.                                                                                                                  |
| **`docker-compose logs -ft`**                  | Muestra los logs de todos los contenedores simultáneamente (*multiplexados*) en **tiempo real** (`-f` de *follow*) y con **marca de tiempo** (`-t` de *timestamp*). |
| **`docker-compose exec <servicio> /bin/bash`** | Ejecuta un comando (ej. `/bin/bash`) en el contenedor en funcionamiento, permitiendo acceder a su *shell* interactiva.                                              |
| **`docker-compose build`**                     | Forzar la reconstrucción de las imágenes definidas con la directiva `build`.                                                                                        |


Absolutamente. Ampliaré y reharé la sección 7, **Docker Swarm: Orquestación Distribuida**, con mayor detalle, enfatizando en la integración con Docker Compose (Stacks) y utilizando comandos de ejemplo, tal como se solicitó.

***

## 7. Docker Swarm: Orquestación Distribuida

### 7.1. Fundamentos de Orquestación Distribuida

#### 7.1.1. Propósito

La orquestación se convierte en un requisito cuando las aplicaciones **crecen más allá de lo que un solo *host* puede manejar**. Docker Swarm es la herramienta nativa de Docker Inc. para gestionar y **orquestar contenedores en un clúster** de varias máquinas (o nodos).

Swarm permite que el usuario acceda a un conjunto de *hosts* Docker como si fuera un **único punto de acceso API**. Esto posibilita que el desarrollador siga utilizando la experiencia de usuario de la Docker CLI a la que está acostumbrado.

#### 7.1.2. Objetivo

El objetivo principal de utilizar un sistema de orquestación como Swarm es construir un **clúster unificado, programable y confiable**. Esto garantiza que las aplicaciones sean:

*   **Escalables:** Permite la escalabilidad horizontal de servicios.
*   **Tolerantes a Fallos:** Proporciona **alta disponibilidad** y auto-recuperación (*self-healing*) al tener más de una copia del mismo contenedor repartida en diferentes máquinas o nodos.

Si un nodo deja de estar disponible, el sistema puede **re-programar la carga de trabajo** (*tasks*) en otros nodos saludables.

#### 7.1.3. Arquitectura

Docker Swarm se basa en una arquitectura **Maestro-Esclavo**: un clúster (o enjambre) está formado por dos tipos de nodos. Este conjunto de *hosts* puede ser visto y utilizado como un "ordenador gigante".

### 7.2. Gestión de Nodos y Servicios

#### 7.2.1. Roles (Manager y Worker)

Todos los nodos que componen el enjambre tienen instalado Docker Engine, pero se les asigna un rol:

| Rol                   | Función                                                                                                                                          |
| :-------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Manager (Maestro)** | Responsable de la **gestión del clúster** y de **delegar las tareas** a los nodos *worker*. Es el que manda órdenes para administrar el clúster. |
| **Worker (Esclavo)**  | Simplemente **hospedan y ejecutan** las unidades de trabajo (*tasks* o tareas) en contenedores.                                                  |

#### 7.2.2. Configuración Inicial y Unión de Nodos

Para construir el clúster, se utiliza la Docker CLI en los *hosts* que actuarán como nodos:

**1. Inicializar el Enjambre (Nodo Manager):**
Se inicia el clúster en el primer *host* (que se convertirá en el nodo *manager* por defecto) con el comando `docker swarm init`.

```bash
$ docker swarm init [OPTIONS]
Swarm initialized: current node (1ia0jlt0ylmnfofyfj2n71w0z) is now a manager. 
# El sistema devuelve el token necesario para unir nodos worker
```

**2. Unir Nodos (Worker):**
Otros *hosts* pueden unirse al clúster como *workers* utilizando el comando `docker swarm join`, al que se le debe proporcionar el *token* de acceso y la dirección del nodo *manager*.

```bash
$ docker swarm join \
--token SWMTKN-1-511cy9taxx5w47n80vopivx6ii6cjpi71vfncqhcfcawxfcb14-6cng4m8lhlrdfuq9jgzznre1p \
10.0.2.15:2377 
```

**3. Ver el Estado del Clúster:**
Desde un nodo *manager*, se puede obtener una vista de todos los nodos integrados en el enjambre:

```bash
$ docker node ls
```

*Nota:* Herramientas como **Docker Machine** pueden automatizar la creación de *hosts* Docker en la nube (AWS, Azure, Google GCE) y configurarlos automáticamente como un clúster Swarm, facilitando la creación de entornos multi-cloud.

#### 7.2.3. Tipos de Servicios

En Swarm, un **Servicio** (*Service*) es la estructura abstracta que define las tareas a ejecutar. Cada servicio está compuesto por un conjunto de tareas individuales que se procesan en contenedores independientes. Docker Swarm soporta dos modos de servicios:

1.  **Servicios Replicados (*Replicated Services*):**
    *   Ejecutan un número **definido por el usuario** de réplicas (*tasks*).
    *   Cada réplica es una instancia del contenedor definido.
    *   Son ideales para la escalabilidad horizontal. Por ejemplo, un servidor web NGINX se puede escalar a 2, 4 o **100 instancias con una sola línea de comandos**.

2.  **Servicios Globales (*Global Services*):**
    *   **Cada nodo disponible** en el clúster inicia una tarea para el servicio.
    *   Son recomendados para aplicaciones de monitoreo o programas antivirus, ya que deben estar presentes en todas las máquinas del clúster.

### 7.3. Despliegue y Networking en Swarm (Stacks)

#### 7.3.1. Despliegue de Stack

La forma más común y eficiente de desplegar aplicaciones multi-contenedor en Docker Swarm es mediante la herramienta **Docker Compose** y el concepto de **Stack**.

**1. Definición del Stack (docker-compose.yml):**
Se utiliza el archivo `docker-compose.yml` (v3+) para definir los servicios. Para el despliegue en Swarm, es crucial añadir directivas específicas al archivo Compose, como la sección `deploy` para especificar el número de réplicas.

*   **Parámetros esenciales en Compose para Swarm:**
    *   `replicas`: Se utiliza para especificar cuántos contenedores se desean de una misma imagen.
    *   `networks`: Se utiliza para definir la red en la que se comunicarán los contenedores (debe ser de tipo *overlay* para funcionar entre *hosts*).

**2. Comando de Despliegue:**
Para lanzar el *stack* en el clúster Swarm, se utiliza el comando `docker stack deploy`:

```bash
# Despliega la aplicación definida en el YAML con el nombre de stack 'myapp'
$ docker stack deploy -c docker-compose.yml myapp
```

*   **Comprobación del Despliegue:** Después del despliegue, se puede comprobar el estado de los servicios (tareas) que se ejecutan en el *stack*:
    ```bash
    $ docker stack ps myapp
    ```

**Ejemplo de Escalado de Servicio:**
Si se ha desplegado un servicio web (replicado) llamado `web`, se puede escalar el número de réplicas directamente, aunque lo más habitual es definirlo en el YAML:

```bash
# Escalar el servicio 'web' a 5 réplicas (instancias)
$ docker service scale myapp_web=5 
# O usando el comando legacy de Compose, si el clúster se configuró con Docker Machine:
$ docker-compose up -d --scale web=5 
```

#### 7.3.2. Balanceo de Carga

Una de las principales ventajas de Swarm es que dispone de **funciones integradas de balanceo de carga**.

*   Si se ejecuta un servicio con múltiples instancias, Docker se encarga de **distribuir las consultas entrantes** de forma inteligente entre las réplicas del servidor web disponibles.
*   Este balanceo de carga integrado hace que la gestión de las réplicas sea **transparente**; se puede acceder al servicio a través de la IP de **cualquier nodo** del clúster.

#### 7.3.3. Redes Overlay

Las redes *overlay* son un modo de red esencial para la comunicación distribuida en Swarm:

*   **Definición:** Son redes virtuales y distribuidas que crean **túneles de red** para interconectar diferentes Docker Daemons.
*   **Comunicación Transparente:** Permiten que los contenedores situados en distintos *hosts* se comuniquen **transparentemente**, como si estuvieran en la misma red física.
*   **Tecnología:** Docker utiliza **VXLAN** (*Virtual Extensible Local Area Network*) para crear estos túneles de red.
*   **Uso en Compose:** Al definir una red con `driver: overlay` en el archivo Compose y desplegar el *stack*, Swarm se encarga de aprovisionar la red *overlay* en todos los nodos del clúster.

**Ejemplo de Definición de Red Overlay en Compose:**

```yaml
version: '3.7'
services:
  web:
    image: nginx:latest
    ports:
      - 80:80
    deploy:
      replicas: 3
    networks:
      - mi-red-overlay
  
networks:
  mi-red-overlay:
    driver: overlay
    # Si no se especifica, Swarm la crea por defecto en el despliegue de Stack.
```

Este es el último apartado del tutorial, que aborda los mecanismos internos de la plataforma Docker y las prácticas avanzadas de seguridad (*hardening*) que se deben aplicar en la gestión de imágenes y contenedores.

***

## 8. Conceptos Internos y Seguridad Avanzada

### 8.1. Mecanismos Internos de Docker

#### 8.1.1. Copy-on-write (CoW)

El mecanismo *Copy-on-write* (CoW) es una característica fundamental que permite a Docker ser extremadamente eficiente en el uso del espacio y en la velocidad de arranque de los contenedores.

*   **Definición:** CoW permite la **creación instantánea de contenedores**, ya que no es necesario hacer una copia completa del sistema de archivos base de la imagen al iniciar un contenedor.
*   **Mecanismo:** Cuando se lanza un contenedor, Docker añade una capa de **lectura/escritura (R/W layer)** sobre las capas inmutables de la imagen. Si un proceso intenta modificar un archivo que está en las capas de solo lectura, este archivo se copia primero a la capa R/W (el patrón *copy on write*), y solo se modifica la copia. El archivo original en las capas base permanece intacto.
*   **Ventaja:** Permite tener multitud de contenedores sin ocupar ningún espacio adicional significativo mientras no se escriban cambios dentro del contenedor.
*   **Implementación:** Este sistema se implementa con *Storage Drivers* como AUFS, Device Mapper, BTRFS y ZFS.

#### 8.1.2. Almacenamiento por Capas (*Layers*)

Las imágenes Docker son los bloques de construcción y se componen de **capas de archivos apiladas** (*layers*).

*   **Composición:** Cada instrucción en un Dockerfile que modifica el sistema de archivos (como `RUN`, `COPY`, `ADD`) genera una **nueva capa inmutable**. Cada capa contiene únicamente las diferencias (`diffs`) respecto a la capa padre.
*   **Proceso de Construcción:** Docker utiliza *Union filesystems* (sistemas de archivos de unión) para combinar estas múltiples capas de solo lectura en un único sistema de archivos que parece contener sus contenidos combinados.
*   **Reutilización:** Dado que las imágenes están compuestas por capas, el proceso de construcción es más rápido si se parte de imágenes pre-construidas, haciendo un uso intensivo de la caché para reconstruir únicamente las capas cuyos comandos hayan cambiado.

#### 8.1.3. Content Addressable Storage (CAS)

CAS es la tecnología de almacenamiento utilizada desde Docker 1.10 para indexar y referenciar las capas y las imágenes, mejorando la seguridad y la eficiencia.

*   **Identificación:** Cada imagen y cada capa se identifica mediante un **"secure content hash"** (hash de contenido seguro) en lugar de un ID generado aleatoriamente. El algoritmo utilizado es **SHA256** (Secure Hash Algorithm 256).
*   **Integridad y Verificación:** El *hash* SHA256 (o *digest*) se calcula a partir del contenido de las capas. Si el contenido de la capa cambia, también cambia el *digest*, lo que permite a Docker **verificar la integridad** de la imagen después de hacer *push* o *pull*. El **ImageID** (identificador de la imagen) se corresponde con el *digest* del fichero de configuración de la imagen.
*   **Compartición:** CAS facilita la **compartición de capas** entre distintas imágenes (incluso si no provienen del mismo *build*), ya que dos capas con contenido idéntico tendrán el mismo *hash* SHA256.

#### 8.1.4. Componentes del Kernel

Docker aprovecha características de virtualización del kernel de Linux para lograr aislamiento y control de recursos.

*   **Namespaces:**
    *   **Función:** Los *namespaces* proveen **espacios de trabajo separados** y una capa de aislamiento para procesos, redes, sistemas de archivos, etc.. Hacen que cada contenedor solo pueda ver los recursos que pertenecen a su *namespace*.
    *   **Seguridad:** Un uso típico de los *namespaces* es el mapeo de `root` (UID 0) dentro del *namespace* del contenedor, de manera que aunque el proceso se vea como `root` internamente, **no tiene privilegios** fuera de su entorno aislado.

*   **Control Groups (Cgroups):**
    *   **Función:** Los *Control Groups* (cgroups) son una característica del kernel de Linux que permite **establecer limitaciones** en el uso de un conjunto de recursos (como CPU y memoria) para un proceso o un grupo de procesos.
    *   **Limitación de Recursos:** Docker utiliza cgroups para asignar recursos individualmente. Docker también soporta la limitación del uso de CPU (*throttling*) mediante el algoritmo planificador CFS (*Completely Fair Schedule*) del kernel.

### 8.2. Seguridad y Hardening

La seguridad avanzada busca proteger la máquina *host*, el daemon, y garantizar la integridad y el minimalismo de las imágenes.

#### 8.2.1. Denegar Root

La práctica por defecto de que todas las operaciones dentro de un contenedor se ejecuten con el usuario **`root`** es un riesgo de seguridad.

*   **Riesgo:** Si un atacante logra comprometer el contenedor, tendrá privilegios de *root* dentro de él. Aunque el proceso esté aislado por *namespaces*, usar *root* dentro del contenedor sigue siendo peligroso.
*   **Solución (Instrucción USER):** Es una buena práctica **denegar el uso de `root`** dentro del contenedor, usando la instrucción `USER` en el Dockerfile para especificar un usuario no privilegiado.

**Ejemplo de Dockerfile:**

```dockerfile
# 1. Creamos un usuario no root
RUN useradd -s /bin/bash ivan

# 2. Especificamos que el contenedor se ejecute con este usuario
USER ivan 
```

#### 8.2.2. Verificación de Integridad

La verificación de la integridad se basa en los *hashes* SHA256 que identifican las imágenes y sus capas.

*   **Mecanismo:** El *hash* de 256 bits (`sha256`) permite verificar si la imagen descargada ha sido modificada desde su publicación, garantizando su integridad.
*   **Comando:** Se puede inspeccionar una imagen para ver los *digests* asociados:
    ```bash
    $ docker inspect <nombre_o_id_imagen>
    ```

#### 8.2.3. Content Trust (DCT)

El *Docker Content Trust* (DCT) es una capa de seguridad criptográfica para la firma y verificación de imágenes.

*   **Función:** Utiliza **firmas digitales** para garantizar la integridad y autenticidad de las imágenes, protegiendo contra la descarga de imágenes maliciosas o modificadas por terceros.
*   **Mecanismo:** Al habilitar DCT (`DOCKER_CONTENT_TRUST=1`), Docker solo permite descargar y ejecutar imágenes y *tags* que hayan sido **firmados digitalmente por publicadores conocidos**.
*   **Herramienta de Soporte:** DCT se apoya en el servicio **Notary** (una plataforma de Docker) para el almacenamiento y la verificación de estas firmas.

#### 8.2.4. Análisis de Vulnerabilidades

El análisis estático es un paso crucial en los *pipelines* de CI/CD, ya que verifica las librerías y binarios incluidos en las imágenes, algo fundamental debido a la inmutabilidad de las mismas.

*   **Objetivo:** Detectar si los paquetes de *software* de la imagen contienen **vulnerabilidades conocidas** (CVEs).
*   **Herramientas de Análisis Estático:**
    *   **Clair:** Examina los contenidos de las imágenes en busca de vulnerabilidades registradas en una base de datos de CVEs.
    *   **Anchore Engine:** Solución *Open Source* que analiza imágenes Docker, obtiene la lista de paquetes instalados y realiza un análisis comparándolo con vulnerabilidades conocidas, ayudando a detectar malas prácticas.
*   **Ejemplo de Comando (Usando Anchore):**
    Una vez levantado el entorno de Anchore (típicamente con Compose), se añade y analiza una imagen:
    ```bash
    # Añadir una imagen nueva para análisis
    $ docker-compose exec engine-api anchore-cli image add docker.io/library/debian
    
    # Comprobar el estado del análisis
    $ docker-compose exec engine-api anchore-cli image wait docker.io/library/debian
    
    # Ver las vulnerabilidades descubiertas
    $ docker-compose exec engine-api anchore-cli image vuln debian os
    ```

#### 8.2.5. Restricción de Tráfico

Por defecto, Docker permite que los contenedores desplegados en el mismo *host* se comuniquen entre sí (si están en la misma red), lo cual es una fuente potencial de divulgación de datos.

*   **Solución (dockerd --icc=false):** Para mitigar la divulgación de datos y limitar la comunicación entre contenedores (ICC - *Inter-Container Communication*), se debe configurar el Docker Daemon (`dockerd`) con la opción `--icc=false`.
*   **Buenas Prácticas Adicionales:**
    *   **No usar SSH:** No se recomienda instalar el protocolo SSH dentro de los contenedores; la gestión remota debe realizarse a través del Docker Daemon (usando `docker exec`).
    *   **No almacenar credenciales:** Los secretos y credenciales **nunca** deben incluirse en el Dockerfile ni en capas intermedias, ya que persisten. Deben proveerse como variables de entorno (`-e`) o usando sistemas de gestión de secretos (como los provistos por Docker Swarm o Kubernetes).
    *   **Limitación de Privilegios:** Se debe evitar el uso de contenedores en modo privilegiado (`--privileged`) a menos que sea estrictamente necesario, y limitar las *capabilities* (privilegios) con `--cap-drop`.

## Autor

Codificado con :sparkling_heart: por [José Luis González Sánchez](https://twitter.com/JoseLuisGS_)

[![Twitter](https://img.shields.io/twitter/follow/JoseLuisGS_?style=social)](https://twitter.com/JoseLuisGS_)
[![GitHub](https://img.shields.io/github/followers/joseluisgs?style=social)](https://github.com/joseluisgs)
[![GitHub](https://img.shields.io/github/stars/joseluisgs?style=social)](https://github.com/joseluisgs)


### Contacto

<p>
  Cualquier cosa que necesites házmelo saber por si puedo ayudarte 💬.
</p>
<p>
 <a href="https://joseluisgs.dev" target="_blank">
        <img src="https://joseluisgs.github.io/img/favicon.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://github.com/joseluisgs" target="_blank">
        <img src="https://distreau.com/github.svg" 
    height="30">
    </a> &nbsp;&nbsp;
        <a href="https://twitter.com/JoseLuisGS_" target="_blank">
        <img src="https://i.imgur.com/U4Uiaef.png" 
    height="30">
    </a> &nbsp;&nbsp;
    <a href="https://www.linkedin.com/in/joseluisgonsan" target="_blank">
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/LinkedIn_logo_initials.png/768px-LinkedIn_logo_initials.png" 
    height="30">
    </a>  &nbsp;&nbsp;
    <a href="https://g.dev/joseluisgs" target="_blank">
        <img loading="lazy" src="https://googlediscovery.com/wp-content/uploads/google-developers.png" 
    height="30">
    </a>  &nbsp;&nbsp;
<a href="https://www.youtube.com/@joseluisgs" target="_blank">
        <img loading="lazy" src="https://upload.wikimedia.org/wikipedia/commons/e/ef/Youtube_logo.png" 
    height="30">
    </a>  
</p>

## Licencia de uso

Este repositorio y todo su contenido está licenciado bajo licencia **Creative Commons**, si desea saber más, vea
la [LICENSE](https://joseluisgs.dev/docs/license/). Por favor si compartes, usas o modificas este proyecto cita a su
autor, y usa las mismas condiciones para su uso docente, formativo o educativo y no comercial.

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">
JoseLuisGS</span>
by <a xmlns:cc="http://creativecommons.org/ns#" href="https://joseluisgs.dev/" property="cc:attributionName" rel="cc:attributionURL">
José Luis González Sánchez</a> is licensed under
a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons
Reconocimiento-NoComercial-CompartirIgual 4.0 Internacional License</a>.<br />Creado a partir de la obra
en <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/joseluisgs" rel="dct:source">https://github.com/joseluisgs</a>.
