FROM openjdk:8

WORKDIR /tarea4/back-end/bin


COPY /target/classes /tarea4/back-end/bin/classes

COPY /target/dependency /tarea4/back-end/bin/dependency

CMD ["java","-cp","./classes:./dependency/*","edu.escuelaing.arep.MongoConexion"]