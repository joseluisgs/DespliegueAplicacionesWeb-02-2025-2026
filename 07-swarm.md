- [7. Docker Swarm: Orquestación Distribuida](#7-docker-swarm-orquestación-distribuida)
  - [7.1. Fundamentos de Orquestación Distribuida](#71-fundamentos-de-orquestación-distribuida)
    - [¿Qué es Docker Swarm?](#qué-es-docker-swarm)
    - [¿Cuándo Usar Swarm?](#cuándo-usar-swarm)
    - [Objetivos de Swarm](#objetivos-de-swarm)
  - [7.2. Arquitectura de Swarm](#72-arquitectura-de-swarm)
    - [Roles: Manager vs Worker](#roles-manager-vs-worker)
    - [Configuración Inicial](#configuración-inicial)
    - [Tipos de Servicios](#tipos-de-servicios)
  - [7.3. Despliegue con Stacks](#73-despliegue-con-stacks)
    - [Docker Stack (Compose para Swarm)](#docker-stack-compose-para-swarm)
    - [Desplegar Stack](#desplegar-stack)
  - [7.4. Redes Overlay en Swarm](#74-redes-overlay-en-swarm)
    - [Definir Red Overlay](#definir-red-overlay)
    - [Balanceo de Carga en Swarm](#balanceo-de-carga-en-swarm)
  - [7.5. Gestión del Cluster](#75-gestión-del-cluster)
    - [Escalado](#escalado)
    - [Actualizaciones](#actualizaciones)
    - [Alta Disponibilidad](#alta-disponibilidad)
  - [7.6. Comandos Esenciales de Swarm](#76-comandos-esenciales-de-swarm)


# 7. Docker Swarm: Orquestación Distribuida

En este módulo aprenderás a usar Docker Swarm para orquestar contenedores en un cluster de múltiples máquinas.

---

## 7.1. Fundamentos de Orquestación Distribuida

### ¿Qué es Docker Swarm?

Docker Swarm es la **herramienta nativa de Docker** para gestionar y orquestar contenedores en un **cluster** de varias máquinas.

```mermaid
flowchart TD
    subgraph "Cluster Swarm"
        N1["Nodo Manager 1"] --> N2["Nodo Worker 1"]
        N1 --> N3["Nodo Worker 2"]
        N2 --> N4["Contenedor 1"]
        N3 --> N5["Contenedor 2"]
        N3 --> N6["Contenedor 3"]
    end
    

```

> 📝 **Nota del Profesor:** "Swarm convierte multiples maquinas en un unico sistema. Tu mandas un comando y Swarm decide donde ejecutarlo paraoptimo."

### ¿Cuándo Usar Swarm?

| Situacion | Herramienta |
|-----------|-------------|
| Un solo host | Docker CLI |
| Multiples hosts, simple | Docker Compose |
| Produccion distribuida | Docker Swarm |
| Enterprise, multiples clusters | Kubernetes |

### Objetivos de Swarm

```mermaid
flowchart TD
    A["Cluster Swarm"] --> B["Escalabilidad"]
    A --> C["Alta disponibilidad"]
    A --> D["Balanceo de carga"]
    A --> E["Auto-curacion"]
    
    B -->|"Mas contenedores"| F["Manejo de carga"]
    C -->|"Redundancia"| G["Sin punto unico de fallo"]
    D -->|"Distribucion"| H["Tráfico distribuido"]
    E -->|"Replanificacion"| I["Recupera fallos automaticamente"]
    

```

---

## 7.2. Arquitectura de Swarm

### Roles: Manager vs Worker

```mermaid
flowchart LR
    subgraph "Manager Node"
        M["Gestiona cluster"] --> O["Orquesta servicios"]
        O --> P["Asigna tareas"]
    end
    
    subgraph "Worker Nodes"
        W1["Ejecuta tareas"] --> C1["Contenedor 1"]
        W2["Ejecuta tareas"] --> C2["Contenedor 2"]
        W3["Ejecuta tareas"] --> C3["Contenedor 3"]
    end
    
    M -.->|"Delega tareas"| W1
    M -.->|"Delega tareas"| W2
    M -.->|"Delega tareas"| W3
    

```

| Rol | Funciones |
|-----|-----------|
| **Manager** | Gestiona el cluster, delega tareas, mantiene estado |
| **Worker** | Hospeda y ejecuta contenedores |

### Configuración Inicial

```bash
# Inicializar Swarm (en el primer nodo manager)
docker swarm init

# Unirse como worker
docker swarm join --token SWMTKN-1-xxxxx IP_MANAGER:2377

# Unirse como manager
docker swarm join-token manager

# Ver nodos del cluster
docker node ls

# Ver informacion de nodo
docker node inspect self

# Abandonar Swarm
docker swarm leave --force
```

### Tipos de Servicios

```bash
# Servicio replicado (numero definido de instancias)
docker service create --replicas 3 --name mi_web nginx

# Servicio global (una instancia en cada nodo)
docker service create --mode global --name monitor mi_monitor
```

```mermaid
flowchart TD
    subgraph "Servicios Replicados"
        S1["3 replicas"] --> N1["Nodo 1"]
        S1 --> N2["Nodo 2"]
        S1 --> N3["Nodo 3"]
    end
    
    subgraph "Servicios Globales"
        S2["Global"] --> N1
        S2 --> N2
        S2 --> N3
        S2 --> N4
    end
```

---

## 7.3. Despliegue con Stacks

### Docker Stack (Compose para Swarm)

```yaml
# docker-compose.yml para Swarm
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    deploy:
      replicas: 3
      endpoint_mode: vip
      resources:
        limits:
          cpus: '0.5'
          memory: 256M
    networks:
      - mi_red

  api:
    image: mi_api:latest
    deploy:
      replicas: 2
      update_config:
        parallelism: 1
        delay: 10s
      restart_policy:
        condition: on-failure
    networks:
      - mi_red

networks:
  mi_red:
    driver: overlay
```

### Desplegar Stack

```bash
# Desplegar stack
docker stack deploy -c docker-compose.yml mi_stack

# Ver stacks
docker stack ls

# Ver servicios del stack
docker stack services mi_stack

# Ver tareas (contenedores) del stack
docker stack ps mi_stack

# Eliminar stack
docker stack rm mi_stack
```

---

## 7.4. Redes Overlay en Swarm

Las redes **overlay** permiten comunicación entre contenedores en diferentes hosts.

```mermaid
flowchart TD
    subgraph "Host 1"
        C1["Contenedor A"] --> R1["Red Overlay"]
    end
    
    subgraph "Host 2"
        C2["Contenedor B"] --> R1
    end
    
    subgraph "Host 3"
        C3["Contenedor C"] --> R1
    end
    

```

### Definir Red Overlay

```yaml
version: '3.8'
services:
  servicio1:
    image: nginx
    networks:
      - red_overlay

  servicio2:
    image: mi_app
    networks:
      - red_overlay

networks:
  red_overlay:
    driver: overlay
    attachable: true  # Permite adjuntar contenedores no-servicio
```

### Balanceo de Carga en Swarm

```mermaid
flowchart LR
    Client["Cliente :80"] --> LB["Ingress Network"]
    LB -->|"Balanceo"| C1["Replica 1"]
    LB --> C2["Replica 2"]
    LB --> C3["Replica 3"]
    

```

- Swarm crea automaticamente una red **ingress** con balanceo de carga
- Cualquier nodo del cluster puede recibir trafico
- El balanceo se distribuye entre todas las replicas

---

## 7.5. Gestión del Cluster

### Escalado

```bash
# Escalar servicio
docker service scale mi_stack_web=5

# Ver replicas
docker service ps mi_stack_web
```

### Actualizaciones

```bash
# Actualizar imagen de servicio
docker service update --image nginx:1.21 mi_stack_web

# Rolling update con configuracion
docker service update \
    --image nginx:1.21 \
    --update-parallelism 2 \
    --update-delay 10s \
    mi_stack_web
```

### Alta Disponibilidad

```mermaid
flowchart TD
    subgraph "Manager Election"
        M1["Manager 1"] --> M2["Manager 2"]
        M2 --> M3["Manager 3"]
        M3 -.->|"Raft consensus"| M1
    end
    



```

- Swarm usa **Raft consensus** para alta disponibilidad
- Se recomiendan **3 o 5 managers** (nunca par)
- Si un manager falla, otro toma el control

> 💡 **Regla nemotecnica:** "Manager para orquestar, Worker para ejecutar. 3 managers para HA, N workers para capacidad."

---

## 7.6. Comandos Esenciales de Swarm

| Comando | Descripcion |
|---------|-------------|
| `docker swarm init` | Inicializar cluster |
| `docker swarm join` | Unirse al cluster |
| `docker node ls` | Ver nodos |
| `docker service create` | Crear servicio |
| `docker service ls` | Ver servicios |
| `docker service ps` | Ver tareas |
| `docker stack deploy` | Desplegar stack |
| `docker stack ls` | Ver stacks |
