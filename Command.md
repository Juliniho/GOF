# COMMAND PATTERN

## 1. Overview
El patrón Command es un patrón de comportamiento y ayuda a desacoplar el invocador del receptor de la solicitud y ayuda a ejecutar cualquier tipo de tarea sin conocer su implementación. La intención del patrón es encapsular la petición como un objeto, permitiendo al desarrollador, de ese modo, parametrizar los clientes con diferentes peticiones, colas o log de peticiones y soportar deshacer operaciones. 
En general, una aplicación orientada a objetos consiste en un conjunto de objetos que interactúan entre sí, cada uno con sus limitaciones, centrados en la funcionalidad. En respuesta a la interacción del usuario, la aplicación lleva a cabo algún tipo de procesamiento. Para este fin, la aplicación hace uso de los servicios de diferentes objetos para el requisito solicitado.

En términos de implementación, la aplicación puede depender de un objeto designado que invoca métodos en estos objetos haciendo pasar los datos requeridos como argumentos. Este objeto designado puede ser referido como invoker que invoca operaciones en diferentes objetos. El invoker puede ser tratado como una parte del cliente. El conjunto de objetos que contiene la aplicación que ofrece los servicios requeridos para el procesamiento de las peticiones son referidos como objetos Receiver.

Usando el patrón Command, el invoker que emite la solicitud en nombre del cliente y el conjunto de objetos Receiver pueden ser desacoplados. Este patrón sugiere crear una abstracción para el tratamiento llevado a cabo o la acción a tomar en respuesta a las solicitudes del cliente. Esta abstracción puede ser diseñada para declarar una interfaz común que sea implementada por diferentes implementaciones concretas, referidas como objetos Command. Cada objeto Command representa un tipo diferente para la petición del cliente y el proceso correspondiente.

Cada objeto Command es responsable de ofrecer la funcionalidad requerida para procesar la solicitud que representa, pero no contiene la actual implementación de dicha funcionalidad. El objeto Command hace uso de los objetos Receiver para ofrecer dicha funcionalidad.

## 2. Participantes
* Command: Declara la interfaz para la ejecución de la operación.
* ConcreteCommand: Define la unión entre un objeto Receiver y una acción. Implementa Execute para invocar las operaciones correspondientes en el Receiver.
* Client: Crea un ConcreteCommand y setea su receiver
* Invoker: Pregunta el comando para llevar a cabo la solicitud
* Receiver: Sabe cómo llevar a cabo las operaciones asociadas la realización de una solicitud. Cualquier clase puede servir con un receptor.

## 3. Cuando usar el patrón
* Para parametrizar los objetos mediante su acción a realizar.
* Especificar una cola y ejecutar solicitudes en diferentes momentos. Un objeto Command puede tener un tiempo de vida independiente de la petición original. Si el receptor de la solicitud se puede representar en una forma de espacio de direcciones independiente, entonces se puede transferir el objeto de comando para la solicitud a un proceso diferente y satisfacer la petición allí.
* Soportar deshacer. La operación ejecutada por el comando puede almacenar el estado para revertir sus efectos en el propio comando. La interfaz Command debe tener una forma de revertir los efectos de la llamada anterior. Los comandos ejecutar serán almacenados en un histórico.
* Soportar el logeo de cambios para que puedan volver a ser replicados en caso de fallo del sistema.
* Estructuras un sistema entorno a operaciones de alto nivel basadas en operaciones primitivas. Tal estructura es 	común en los sistemas de información que soportan las transacciones. 

![](https://upload.wikimedia.org/wikipedia/commons/8/8e/Command_Design_Pattern_Class_Diagram.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/command)
