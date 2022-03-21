# AREP-tarea4

## Diseño de las clases
El proyecto se encuentra dividido en tres partes:

1. El contenedor de MongoDB que corre en Docker, esta se puede encontrar en el siguiente link imagen de MongoDB.

2. La clase MongoConexion se encuentra en la carpeta back-end, esta clase es la encargada de hacer la conexión con la base de datos de MongoDB, y adicionalmente, es la encargada de realizar las diferentes consultas sobre la base de datos.

3. Se encuentra en la carpeta front-end, en esta carpeta se encuentran el cliente web, en la clase Balancer, y el front-end, en la clase con el mismo nombre, esta clase se encarga de organizar la manera en la cual los LogService van a interactuar por turnos con la base de datos.

## Balancer
Es un método para seleccionar todos los abstractos en un grupo de manera equitativa y en un orden racional, normalmente comenzando por el primer elemento de la lista hasta llegar al último y empezando de nuevo desde el primer elemento.
En este caso para implementar el Round-Robin se uso una ConcurrentQueue.
Primero se crea una ConcurrentQueue, luego se adicionan los elementos, en este caso los diferentes hosts.
<pre><code>private static ConcurrentLinkedQueue<String> queue = new ConcurrentLinkedQueue<String>() {
        {
            add("1");
            add("2");
            add("3");
        }
    };</pre></code>
Luego cada vez que se vaya a seleccionar un elemento, se extrae el primer elemento en la cola, este será el host que se va a usar, luego se vuelve a añadir a la cola, de esta manera haciendo la rotación entre elementos.
<pre><code>public static String balancer(String a) {
        String temp = queue.poll();
        queue.add(temp);
        return doPost(a, temp);
    }</pre></code>
