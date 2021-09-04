<br />
<p align="center">
	<a href="https://github.com/ajur91">
		<img align="center" width="500" src="https://github.com/ajur91/ajur91/raw/master/assets/logo.png" style="max-width:100%;">  
	</a>

  <h1 align="center">DOCKER + DOCKER-COMPOSE </h1>

  <p align="center">
    Lista de docker y docker-compose configurados para trabajar como micros-servicios
    <br />
    <a href="https://docs.docker.com/compose/install"><strong>Docker»</strong></a>
    <br />
  </p>
</p>

---

# DOKER

## PREREQUISITOS LINUX
- CURL
## INSTALACIÓN AUTOMATICA

### LINUX

Ejecutar el siguiente comando

	$ wget https://raw.githubusercontent.com/ajur91/docker/master/docker-install && sh docker-install && rm docker-install

## INSTALACIÓN MANUAL

### DOCKER

- Instalar el paquete de requisitos previos

	$ sudo apt-get install  curl apt-transport-https ca-certificates software-properties-common

- Agrega los repositorios de Docker

	$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
	$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
	$ sudo apt update
	$ apt-cache policy docker-ce

- Instalar Docker
	$ sudo apt install docker-ce

- Comporbar el estado de Docker
	$ sudo systemctl status docker

- Crear el grupo de usuario Docker.
	$ sudo groupadd docker

- Agregue su usuario al grupo de Docker.
	$ sudo usermod -aG docker $USER

### DOCKER-COMPOSE
1- Descargar la versión estable/actual de docker-compose
~~~
	$ sudo curl -L "https://github.com/docker/compose/releases/download/{ultima version}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
~~~
- Referencia de version 
	$ https://docs.docker.com/compose/install/

2- Permisos
~~~
	$ sudo chmod +x /usr/local/bin/docker-compose
~~~

3- Crear un symbolic link
~~~
	$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
~~~

4- Ver versión 
~~~
	$ docker-compose --version
~~~

5- Ajustar Permisos
~~~
	$ sudo chmod 666 /var/run/docker.sock
~~~

---

## COMENZAR A USAR CONTENEDORES
Para comenzar a usar los contenedores debe crear un red con el siguiente comando:

	$ docker network create \
		--driver=bridge \
		--subnet=172.80.80.0/24 \
		--gateway=172.80.80.1 \
		-o "com.docker.network.bridge.name"="net_betox" \
		net_betox

---
## LISTA DE COMANDOS

Posicionarse en la carpeta del docker a ejecutar
	cd /repo_dockers

| Commands  | Description  |
|---|---|
| docker-compose up -d  | Levantar servicios |
| docker-compose down  | Remover servicios  |
| docker-compose start o stop  | iniciar o detener los servicios  |
| docker-compose exec --user www-data {CONTAINER} bash  | Entrar al bash de un servicio. |
| docker ps  | para ver la lista de contenedores en ejecución.  |
| docker ps -a | para ver la lista de todos los contenedores.  |
| docker system prune -a | Depurar todos los containers en stop, networks, images, build cache.  |

## LISTA DE DOCKERS

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

## Configurar Xdebug 3.0.3 Linux

### Ajustar la config de XDebug en el docker-compose

	environment:
    	XDEBUG_CONFIG: client_host={host.docker.internal} client_port=9003 remote_enable=1 profiler_enable=1

### Configurar el Vcode y XDebug

	"configurations": [
		{
			"name": "Listen for XDebug",
			"type": "php",
			"request": "launch",
			"port": 9003,
			"pathMappings": {
				"/var/www/html/": "${workspaceFolder}"
			},
			"ignore": [
				"**/vendor/**/*.php"
			],
			"xdebugSettings": {
				"max_children": 10000,
				"max_data": 10000,
				"show_hidden": 1
			}
		}
	]
---
</br>
</br>
<p align="center">
 <img align="center" width="150" src="https://github.com/ajur91/ajur91/raw/master/assets/logo.png" /> 
 </br>
 Ing. Alberto Urbaez
 </br>
 <a href="https://albertourbaez.com/en">AlbertoUrbaez.com</a>
</p>

<p align="center">
 <img src="https://img.shields.io/github/forks/ajur91/ajur91" /> 
 <img src="https://img.shields.io/github/stars/ajur91/ajur91"/> 
 <img src="https://img.shields.io/github/followers/ajur91"/>
 <img src="https://img.shields.io/github/watchers/ajur91/ajur91"/>
</p>
