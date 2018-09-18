## DB2
#### As Daemon
```
docker run -d -p 50000:50000 -e DB2INST1_PASSWORD=db2inst1-pwd -e LICENSE=accept  ibmcom/db2express-c:latest db2start
docker stop db2
docker start db2
docker exec -i -t db2 /bin/bash
su - db2inst1
db2 create db hibern8
```
#### With Mount 
```
docker run -it -p 50000:50000 -e DB2INST1_PASSWORD=db2inst1-pwd -e LICENSE=accept   -v  $(pwd):/share  ibmcom/db2express-c:latest bash
```
