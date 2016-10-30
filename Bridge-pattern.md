# BRIDGE PATTERN

## 1. Overview
Este patrón pretende desacoplar una abstracción de su implementación, para que los dos se puedan variar independientemente. Este patrón utiliza la encapsulación, la agregación, y se puede utilizar la herencia para separar responsabilidades en diferentes clases. Cuando una clase varía a menudo, las características de la programación orientada a objetos se vuelven muy útiles debido a que los cambios en el código de un programa pueden hacerse fácilmente con un mínimo conocimiento previo sobre el programa. La clase en sí se puede considerar como la abstracción y lo que la clase puede hacer como la puesta en práctica. Este patrón también puede ser pensado como dos capas de abstracción. 

El patrón bridge se confunde a menudo con el patrón adaptader. De hecho, el patrón bridge a menudo se implementa utilizando el patrón de adaptader.

## 2. Participantes
* Abstraccion, define la clase de abstraccion y también mantiene una referencia a un objeto de tipo implementador, este vínculo, entre la abstraccion y el implementador es conocido como puente.
* Abstraccion redefinida, hereda la clase definida por la abstraccion. 
* El implementador proporciona la interfaz para las clases de implementación (implementaciones concretas)
* Y las implementaciones concretas implementa la interfaz implementadora y definen su implementación concreta.

Como resultado una implementación no está obligado permanentemente por una interfaz. La implementación de una abstraccion se puede configurar en tiempo de ejecución, también elimina las dependencias en tiempo de compilación sobre la aplicación. 

## 3. Cuando usar el patrón
* Cuando se quiere evitar una unión permanente entre la abstraccion y su implementación. este podría ser el caso, cuando la implementación debe ser seleccionada o cambiada en tiempo de ejecución
* Tanto las abstraccion y sus implementaciones deben ser extensibles para subclases, en este caso, el patrón le permite combinar diferentes abstracciones e implementaciones y extenderlas independientemente
* Los cambios en la implementación de una abstraccion no deben tener ningún impacto en los clientes, es decir, su código no debería recompilarse.
* Quieres compartir una implementación entre varios objetos (por referencia) y esto debe estar oculto para el cliente.


![](https://upload.wikimedia.org/wikipedia/commons/c/cf/Bridge_UML_class_diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/bridge)