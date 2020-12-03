# DOCKER + DOCKER-COMPOSE 
### version YML - 3.5

lista de docker y docker-compose configurados para trabajar trabajar de forma individual

## DOKER

### 1 - Instala el paquete de requisitos previos
``
	sudo apt-get install  curl apt-transport-https ca-certificates software-properties-common
``

### 2 - Agrega los repositorios de Docker
``
	curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
	sudo apt update
	apt-cache policy docker-ce
``

### 3 - Instala Docker
``
	sudo apt install docker-ce
``

### 4 - Comprueba el estado de Docker
``
	sudo systemctl status docker
``

## DOCKER-COMPOSER

### 1 - Descargar la versión estable actual de Docker Compose
``
	sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
``

### 2 - Permisos
``
	sudo chmod +x /usr/local/bin/docker-compose
``

### 3 - Crear un symbolic link
``
	sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
``

### 4 - Ver version 
``
	docker-compose --version
``

## LISTA DE COMANDOS

### Manual de ejecución
1. Posicionarse en la carpeta del docker a ejecutar

| Commands  | Description  |
|---|---|
| docker-compose up -d  | Levantar servicios |
| docker-compose down  | Remover servicios  |
| docker-compose start o stop  | iniciar o detener los servicios  |
| docker-compose exec --user www-data {CONTAINER} bash  | Entrar al promt de un servicio. |
| docker ps  | para ver la lista de contenedores en ejecución.  |
| docker ps -a | para ver la lista de todos los contenedores.  |

### Lista de contenedores

| Nombre  | Description  |
|---|---|
| magento1  | dockerFile y docker-compose del contenedor magento1 |
| magento2  | dockerFile y docker-compose del contenedor magento2  |
| mailhog  | docker-compose del contenedor mailhog |
| mysql  | docker-compose del contenedor mysql  |
| redis  | docker-compose del contenedor redis |