# MongoDB 
To create volumes

> docker run -v /data/db -v /data/configdb --name mongostorage busybox echo 'created mongo volumes'

> docker run -d -p 27017:27017 --volumes-from mongostorage --name mongoserver mongo:3.2

> docker run --link mongoserver:mongo -p 8081:8081 mongo-express

## Docker-Compose
====
version: '3.1'

services:

  mongo:
    image: mongo
    restart: always
    environment:
      MONGO_INITDB_ROOT_USERNAME: root
      MONGO_INITDB_ROOT_PASSWORD: example

  mongo-express:
    image: mongo-express
    restart: always
    ports:
      - 8081:8081
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: root
      ME_CONFIG_MONGODB_ADMINPASSWORD: example
====