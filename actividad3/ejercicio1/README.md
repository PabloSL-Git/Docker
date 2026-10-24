# Descripción
Este es un ejercicio en el que vas a utilizar un script NodeJS existente que se conecta a una base de datos Mongo.

El script Node presenta una interfaz ReST en el puerto 3000.

Tu objetivo es «dockerizar» esta aplicación.

Debes de crear un docker-compose donde tengamos dos imágenes. La imagen de Node, al que llamaremos: web y la imagen de MongoDB, al que llamaremos: db.
    
Utilice imágenes para NodeJS de la última versión y MongoDB versión 3.

Su objetivo es crear un archivo docker-compose.yml que se pueda utilizar para iniciar los servicios db y web, y una vez que tiene activado los servicios, deberá de probar que funciona, utilizando el comando: curl http://localhost:3000 y deberá de devolver: 'Hello World!'

#Nota
No hace falta crear ningún tipo de volumen ya que no vamos a almacenar nada en la base de datos.
Ten en cuenta que hay una variable de entorno llamada: MONGO_IP que será la IP del servidor de Mongo.