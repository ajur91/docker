# DOCKER + DOCKER-COMPOSE 
### version YML - 3.8

lista de docker y docker-compose configurados para trabajar de forma individual

## DOKER

### 1 - Instalar el paquete de requisitos previos
``
	sudo apt-get install  curl apt-transport-https ca-certificates software-properties-common
``

### 2 - Agrega los repositorios de Docker

``
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
``

``
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
``

``
	sudo apt update
``

``
	apt-cache policy docker-ce
``

### 3 - Instalar Docker
``
	sudo apt install docker-ce
``

### 4 - Comporbar el estado de Docker
``
	sudo systemctl status docker
``

### 5 - Crear el grupo de usuario Docker.
``
	sudo groupadd docker
``

### 6 - Agregue su usuario al grupo de Docker.
``
	sudo usermod -aG docker {user}
``

## DOCKER-COMPOSE

### 1 - Descargar la versión estable/actual de docker-compose
``
	sudo curl -L "https://github.com/docker/compose/releases/download/{ultima version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
``
#### Referencia de version 
	https://docs.docker.com/compose/install/

### 2 - Permisos
``
	sudo chmod +x /usr/local/bin/docker-compose
``

### 3 - Crear un symbolic link
``
	sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
``

### 4 - Ver versión 
``
	docker-compose --version
``

### 5 - Ajustar Permisos
``
	sudo chmod 666 /var/run/docker.sock
``

## LISTA DE COMANDOS

### Manual de Ejecución
1. Posicionarse en la carpeta del docker a ejecutar
``
	cd /repo_dockers
``

| Commands  | Description  |
|---|---|
| docker-compose up -d  | Levantar servicios |
| docker-compose down  | Remover servicios  |
| docker-compose start o stop  | iniciar o detener los servicios  |
| docker-compose exec --user www-data {CONTAINER} bash  | Entrar al bash de un servicio. |
| docker ps  | para ver la lista de contenedores en ejecución.  |
| docker ps -a | para ver la lista de todos los contenedores.  |

### Lista de Dockers

| Nombre  | Description  |
|---|---|
| magento1  | dockerFile y docker-compose del contenedor magento1 |
| magento2  | dockerFile y docker-compose del contenedor magento2  |
| mailhog  | docker-compose del contenedor mailhog |
| mysql  | docker-compose del contenedor mysql y phpMyAdmin|
| oracle  | docker-compose del contenedor oracle  |
| mongoDB  | docker-compose del contenedor mongoDB  |
| PostgresSQL  | docker-compose del contenedor PostgresSQL y Adminer |
| redis  | docker-compose del contenedor redis |
| nodejs  | docker-compose del contenedor nodejs |
| PHP 5.6 to 8.0  | docker-compose de las diferentes versiones de php |
| php8.0-OCI8  | docker-compose del contenedor php8.0 con OCI8 para integrar con DB Oracle  |