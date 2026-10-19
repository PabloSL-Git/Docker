# Actividad 1 - Aplicación PHP con Docker y Nginx

## Descripción

Aplicación web desarrollada en PHP y desplegada mediante Docker.

El entorno utiliza dos contenedores:

* **PHP-FPM**: ejecuta el código PHP.
* **Nginx**: servidor web que recibe las peticiones HTTP y las envía a PHP-FPM cuando es necesario.

La aplicación se puede acceder desde el navegador mediante:

text
http://localhost:8080

## Requisitos

Para ejecutar la aplicación es necesario tener instalado:

* Docker
* Docker Compose

## Estructura del proyecto

text
actividad1/
├── Dockerfile
├── docker-compose.yml
├── nginx.conf
├── README.md
└── app/
    └── archivos de la aplicación PHP

## Despliegue

### 1. Acceder a la carpeta del proyecto

cd ~/Documentos/Docker/actividad1

### 2. Construir la imagen

Ejecutar:

sudo docker compose build

Este comando construye la imagen `actividad1-php` utilizando el `Dockerfile`.

### 3. Iniciar los contenedores

sudo docker compose up -d

Se iniciarán dos contenedores:

* `php-app`
* `nginx-app`

### 4. Comprobar el estado

sudo docker compose ps

Los dos contenedores deben aparecer con el estado `Up`.

Nginx estará disponible mediante el puerto 8080 del equipo.

### 5. Acceder a la aplicación

Abrir un navegador y acceder a:

text

http://localhost:8080

La aplicación PHP debería mostrarse correctamente.

## Detener la aplicación

Para detener y eliminar los contenedores:

sudo docker compose down

## Reconstruir la aplicación

Si se realizan cambios en el `Dockerfile`, se puede reconstruir y volver a iniciar todo mediante:

sudo docker compose down
sudo docker compose up -d --build

## Configuración

### PHP

El contenedor PHP utiliza:

text
php:8.3-fpm-alpine

El código de la aplicación se encuentra en:

text
/var/www/html

PHP-FPM utiliza el puerto:

text
9000

### Nginx

Nginx utiliza la imagen:

text
nginx:alpine

El puerto 80 del contenedor está asociado al puerto 8080 del equipo:

text
8080:80

La configuración se encuentra en:

text
nginx.conf

Nginx envía las peticiones PHP al contenedor `php` mediante:

text
php:9000

## Pruebas de rendimiento

Se utilizó ApacheBench para realizar pruebas de carga.

Primera prueba:

ab -n 1000 -c 10 http://localhost:8080/

Segunda prueba:

ab -n 10000 -c 50 http://localhost:8080/

En la segunda prueba se realizaron 10.000 peticiones con una concurrencia de 50 y no se produjeron peticiones fallidas.

## Monitorización

Para consultar el consumo de recursos de los contenedores:

sudo docker stats

Para consultar los registros de Nginx:

sudo docker compose logs nginx

Para consultar los registros de PHP:

sudo docker compose logs php

## Recursos

La imagen Docker `actividad1-php` ocupa aproximadamente 123 MB.

Durante las pruebas realizadas, el consumo de memoria observado fue aproximadamente:

* Nginx: 7,93 MiB
* PHP-FPM: 8,875 MiB

El consumo conjunto observado fue aproximadamente 16,8 MiB.

## Autor

Actividad realizada para el módulo de Despliegue de Aplicaciones.

I.E.S. Mar Alborán - DAW 2
