# CHAIN RESPONSABILITY PATTERN

## 1. Overview
El patrón Chain of Responsibility es un patrón de comportamiento en el que un grupo de objetos se encadenan en una secuencia y una responsabilidad (a petición) proporcionado con el fin de ser manejados por el grupo. Sí un objeto en el grupo puede procesar una solicitud en particular, lo hace y devuelve la correspondiente respuesta. De lo contrario, envía la petición al objeto subsiguiente en el grupo. La intención de este patrón es evitar el acoplamiento del remitente de una solicitud a su receptor, dando a más de un objeto la posibilidad de manejar la petición.
Se trata de encadenar los objetos y remitir la información a lo largo de la cadena hasta un objeto que sea capaz de procesarla. Cuando existen varios objetos que son capaces de procesar la petición, el patrón recomienda dar a cada uno la oportunidad de procesar la solicitud en orden secuencial.
Los objetos (manipuladores) pueden estar dispuestos en forma de cadena, donde cada objeto tiene una referencia al objeto siguiente. El primer objeto recibe la petición y comprueba si puede resolverla o trasladarla al siguiente manejador.

## 2. Participantes
* Handler: Interfaz que manejará las peticiones, opcionalmente implementa el link sucesor.
* ConcreteHandler: Manejador especifico de un tipo de petición
* Client: Inicia la petición a un objeto ConcreteHandler en la cadena.

## 3. Cuando usar el patrón
* Más de un objeto puede gestionar una petición, y el manejador no se conoce a priori (debe determinarse de forma automática)
* Desea remitir una solicitud a uno de los varios objetos sin especificar explícitamente el receptor.
* El conjunto de objetos que puede manejar una solicitud se debe especificar de forma dinámica.

![](https://upload.wikimedia.org/wikipedia/commons/7/75/EstructuraES2.jpg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/chainresponsibility)
