# Instrucciones para desplegar la aplicación

1. Abrir una terminal y situarse en la carpeta donde se encuentra el fichero docker-compose.yaml.

2. Construir las imágenes y levantar los contenedores con:

bash
docker compose up --build


3. Comprobar que los contenedores están funcionando:

bash
sudo docker ps


Deben aparecer los siguientes contenedores:

contenedor_bd
contenedor_login
contenedor_api
contenedor_php

4. Abrir la aplicación web desde el navegador:


http://localhost:8080


5. Para detener los contenedores, pulsar `Ctrl + C` en la terminal donde se está ejecutando Docker Compose.

6. Para iniciar nuevamente la aplicación:


docker compose up


7. Para detener y eliminar los contenedores:


docker compose down


8. Para eliminar también los datos persistentes de la base de datos:

```bash
docker compose down --volumes
```

