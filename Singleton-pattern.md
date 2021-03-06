# SINGLETON PATTERN

## 1. Overview
Este patrón asegura que una clase tiene solo una instancia y proporciona un punto de acceso global a ella. Una forma de asegurar esto es crear de forma estática la instancia del objeto (private) en la declaración de la propiedad dentro de la clase y cambiar el modificador del constructor public por private. Además, se añade un método para acceder de forma pública a esta instancia estática.
Para "ahorrar" un poco en memoria, modificamos la creación del objeto y la hacemos dentro del método getInstance solo cuando la referencia sea null, así solo se realiza el new la primera vez que se llama a getInstance.

En entornos multi-hilo, puede producirse el caso en que dos hilos creen la instancia del objeto, perdiendo entonces el sentido del patrón, por ello se protege el método getInstance con un synchronized. También existe la técnica de la doble comprobación de bloqueo para reducir el uso de synchronized, para ello primero se comprueba si la instancia esta creado y si no lo está entonces se sincroniza la clase completa.

Algunas formas de romper el patrón singleton:
* Permitiendo a la clase ser serializable o clonable.
* Por reflexión.
* O si la clase se carga por múltiples cargadores de clases.

Otra forma de crear singletons es mediante enums, ya que de por si son finales y estáticos, thread-safe, no pueden heredar, serializables y no se pueden instanciar mediante reflexión.

## 2. Cuando usar el patrón
* Cuando solo deba existir una única instancia de una clase y deba ser accesible a los clientes desde cualquier punto de acceso.
* Cuando la única instancia deba ser heredable por subclases y los clientes deban ser capaces de usar una instancia heredada sin modificar su código.


![](https://upload.wikimedia.org/wikipedia/commons/d/dc/Singleton_pattern_uml.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/creational/singleton)