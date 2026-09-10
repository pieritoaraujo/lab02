# Lab02 - Infraestructura como código

#### Para esta actividad se utilizó docker compose para desplegar un servicio web y una DB

### API
Utilice un Dockerfile para crear una imagen personalizada que se encuentra en helloworldapi
Para ello, desplegamos por el archivo docker-compose.yaml

Ahí se realizaron 3 copias de la api, llamadas: api1, api2 y api3.

### BASE DE DATOS

Para esto utilizamos la imagen de Postgres sacada de https://hub.docker.com/_/postgres/

Variables de entorno:

      POSTGRES_USER: ${POSTGRES_BD_USER}
      POSTGRES_PASSWORD: ${POSTGRES_BD_PASSWORD}
      POSTGRES_DB: ${POSTGRES_BD_NAME}

### VOLUMEN

Para este, implementé un volumen administrativo por docker llamado postgresdata para almacenar información generada por la bd

#### - Enlazada con ruta interna:

    /var/lib/postgresql/data

### CONFIGURACIONES

Los datos se manejan por .env, donde están las variables de entorno:

    MESSAGE_01=
    MESSAGE_02=
    MESSAGE_03=

    POSTGRES_BD_USER=
    POSTGRES_BD_PASSWORD=
    POSTGRES_BD_NAME=

### COMANDOS

Los comandos utilizados para esta actividad son los siguientes

##### Utilizada para desplegar los servicios en 2do plano:
    docker compose up -d 

##### Utilizada para apagar:
    docker compose down

##### Utilizada para verificación de estado de los contenedores:
    docker compose ps

### REDES EN DOCKER
- host: Utiliza la red del equipo, para reducir aislamiento de red
- overlay: Permite conectar contenedores distribuidos en diferentes máquinas
- none: Deshabilita conexión de la red del contenedor, así la deja completamente aislado
- brigde: Controlador de red por defecto, los contenedores pueden comunicarse entre sí
- macvlan: Asigna una dirección MAC única a cada contenedor, haciendo que se comporte como un dispositivo físico en la red del host
- IPvLAN: Proporciona un control preciso sobre las direcciones IPv2 e IPV6

### TIPOS DE VOLÚMENES EN DOCKER
- Bind Mounts: Permite compartir carpetas de manera local con el contenedor
- Tmpfs Volumes: Almacenan datos temporales en la RAM, eliminándose al detener el contenedor
- Named Volumes: Para almacenar datos persistentes, son recomendados para la BD.

### BIBLIOGRAFÍA
- Docker Volumes: https://www.zymeralabs.com/docker-volumes-que-son-tipos-y-ejemplos-reales/#volumenes-en-docker-compose
- Docker Redes: https://www.wikiversus.com/informatica/docker-redes-network-guia/
