FROM openjdk:8

WORKDIR /tarea4/front-end/bin


COPY /target/classes /tarea4/front-end/bin/classes

COPY /target/dependency /tarea4/front-end/bin/dependency

CMD ["java","-cp","./classes:./dependency/*","edu.escuelaing.arep.Balancer"]
