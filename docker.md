# Docker

## Container-based Virtualization
- El container Engine, se instala sobre el sistema operativo
- Los containers comparten el sistema operativo
- kitematic es un cliente de docker
- Las images son templates para crear containers, estan compuestas de capas de otras images. Se guardan en repositorios como DockerHub.
- Los containers son instancias de las images
- Las imagenes estan compuestas de capas de imagenes de lectura
- Cuando se genera un container se agrega una capa de escritura, cuando se borrar el container, se borrar esta capa tambien.
- Continuos Integration es una practica de trabajo, para distribuir el codigo despues de pasar las pruebas

## Instalar

**Fedora**
```bash 
sudo dnf -y install dnf-plugins-core

sudo dnf config-manager \
    --add-repo \
    https://download.docker.com/linux/fedora/docker-ce.repo

sudo dnf install docker-ce docker-ce-cli containerd.io

sudo systemctl start docker
```

**Grupo de Usuario Docker**  
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

## Iniciar
`docker login --username=USER` Loguearse con la cuenta de DockerHub

## Ejecutar Container
- En linux docker se debe de ejecutar como root, se puede hacer usando `sudo docker` o logueando `sudo -i`
- EL container es generado cada vez que se ejecuta el comando
- `docker images` Listar imagenes en el sistema
- `docker run repository[:tag=lastest] echo "hola mundo"` Genera un container con una imagen y ejecutar un comando dentro del container
- `docker run -it repository` Ingresar dentro den container. `-i (--interactive)` Container interactivo `-t (--tty)` Pseudoterminal
- `docker run -d repository` Ejecutar el container de fondo. `-d (--detach)` Retorna el ID
- `docker run --rm repository` Elimina el container despues de ejecutarlo
- `docker run --name NOMBRE repository` Nombre al container al ejecutarlo
- `docker run -p host_port:container_port repository` Mapear el el puerto del container
- `docker run --link name repository` Linkear con un container ejecutandose

## Monitorear Containers
- `docker ps` Muestra los containers ejecutandose de fondo
- `docker ps -a` Muestra todos los containers ejecutados
- `docker exec -it ID bash` Ejecutar comandos dentro del container
- `docker stop ID` Detener un container en segundo plano
- `docker inspect ID` Retorna un json con la informacion del container
- `docker logs ID` Ver el log de actividad del container
- `docker history repository` Muestra la composicion de una imagen con sus subimagenes

## Generar Docker Image
- Se puede hacer haciendo commits en un Docker Container
- Generando un `Dockerfile`

### Commit cambios de un container
- `docker run -it repository` Ejecutar el container
- Ejecutar cambios dentro del container
- `docker commit ID user/repository:tag` Genera una nueva imagen con los cambios ejecutados en el container

### Dockerfile
- Contiene instrucciones de como armar la imagen del container.
- Cada instruccion genera una capa en la imagen, por lo que es recomendable encadenar las mismas.
- `FROM` Imagen base
- `RUN` Ejecutar comandos. Con `\` es posible de hacer enter en el archivo. Con `&&` Se puede concatenar comandos
- `CMD` Ejecuta comandos cuando el container se genera. Se ejecutar por defecto, pero se pueden sobrescribir.
- `COPY ejemplo.txt /home/ejemplo.txt` Copiar al archivos a la imagen
- `ADD` Es ccomo COPY pero con mas funcionalidades
- `USER` Setea un usuario
- `WORKDIR` Setea el directorio a trabajar

**Ejemplo**
```
FROM repository:tag
RUN apt-get update && apt-get install -y \
    git \
    vim
```

**Generar Archivo & Compilar**
- `touch Dockerfile` Generar el archivo, no tiene extension y la D siempre en mayuscula
- `docker build -t user/repository:tag .` Generae la imagen `--no-cache=true` Omite el use de la cache de capas para construir la imagen

## Trabajar con Docker Images
- `docker tag ID user/repository:tag` Asocia el tag a una imagen
- `docker push user/repository:tag` Subir la imagen a DockerHub


## Networking
- `docker network ls` Listar las opciones de network disponibles
- `docker network create --driver bridge NOMBRE` Generar una nueva network con driver bridge
- `docker network connect NETWORK_NAME container` Conectar un container a una red
- `docker network disconnect NETWORK_NAME container` Desconectar de una red a un container
- **None Network** No tiene acceso al intetnet y cada container esta aislado. `docker run --net none container`
- **Bridge Network** La default. Conecta todos los containers a la network y la misma se conecta a internet
- **Host Network** Se llaman open containers, ya que tiene acceso completo a la red del host, son inseguros. `docker run --net host container`
- **Overlay Network** Para conectar a varios host. Mas usado en produccion

# Docker Compose
- Para manejar cluster de containers

## Instalar
```bash 
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

## docker-compose.yml
- Docker composer permite gestinar la ejecucion de varios containers
- `touch docker-compose.yml` Generar archivo de ejecucion
- `version: '3'` Especificar la version 
- `services:` Donde se especifican como proceder para cada container
- `build: .` Indicar que Dockerfile usar para componer la imagen
- `depends_on:` Lista los container que van a ser usados como dependencias
- `image:` Indicar que imagen usar para generar el container
- `networks:` Lista las networks asociadas 

**Ejemplo**
```yaml
version: '3'
services:
  dockerapp:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - redis
  redis:
    image: redis:3.2.0
```

### Ejecucion y Monitoreo
- `docker-compose up` Genera y ejecuta todos los containers
- `docker-compose up -d` `-d` Ejecuta los containers en segundo plano

- `docker-compose ps` Monitorear los procesos ejecutados
- `docker-compose logs` Ver logs de los containers
- `docker-compose logs -f` Suma contenido del log en tiempo real
- `docker-compose logs name` Pasandole el nombre del container, se puede moni torear solo ese

- `docker-compose stop` Detiene la ejecucion de los containers
- `docker-compose down` Detiene y elimina networks, volumes, y images
- `docker-compose rm --all` Eliminar todos los container

- `docker-compose build` Vuelve a compilar las imagenes de los containers
- `docker-compose run contaier comando` Ejecutar un comando

# Docker Machine
- Crear y manejar VM que ejecutan Docker.

## Instalar
```bash
base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
  chmod +x /usr/local/bin/docker-machine
```

# Docker Swarm


