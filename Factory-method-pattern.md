# FACTORY METHOD PATTERN

## 1. Overview
Este patrón aporta una forma de encapsular instanciaciones de tipos concretos. Encapsula la funcionalidad requerida para seleccionar e instanciar la clase apropiada dentro de un método designado para ello. La clase que se instancia es seleccionada de una jerarquía de clases basándose en el contexto de la aplicación y otros factores.
La ventaja principal de este enfoque es que los objetos de la aplicación pueden hacer uso del método de la factoría para obtener acceso a la instancia de la clase apropiada, esto elimina la necesidad de que un objeto tenga que conocer la lógica para la selección del objeto que necesita.

## 2. Participantes
* Producto: Define la interfaz de objetos que crea el método factory
* ConcreteProduct: Objeto concreto que implementa al interfaz de producto
* Creator: Declara el método factory que devuelve un objeto de tipo producto. creado
* ConcreteCreator: Sobrescribe el método factory para devolver una instancia de ConcreteProduct 

## 3. Cuando usar el patrón
* Una clase no conozca de antemano la clase (tipo) de objetos que necesita crear
* Una clase necesita subclases para especificar los objetos que crea.
* Las clases delegan su responsabilidad hacia una de muchas subclases de ayuda y se desea localizar el conocimiento de que subclase hay que delegar


![](https://upload.wikimedia.org/wikipedia/commons/7/73/Factory_Method.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/creational/factorymethod)