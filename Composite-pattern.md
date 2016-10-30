# COMPOSITE PATTERN

## 1. Overview
Hay ocasiones en las que existe la necesidad de una estructura de datos en árbol, hay muchas variaciones para dicha estructura, pero a veces hay una necesidad en un árbol en el que dos ramas deben de ser tratadas de modo uniforme.
Este patrón permite componer objetos en una estructura de árbol para representar la jerarquía parte-todo, lo que significa que puede crear un árbol de objetos que se compone de diferentes partes, pero que puede ser tratada como un todo muy grande. Este patrón permite a los clientes tratar con objetos individuales y objetos compuestos de manera uniforme. Este patrón se puede usar para representar un sistema de directorios de archivos o un analizador de XML. En este patrón a los elementos con hijos son llamados nodos y los elementos sin hijos hojas. Con el podemos construir objetos complejos a partir de otros más simples y similares entre sí, gracias a la composición recursiva y a una estructura en forma de árbol.

## 2. Participantes
* Component: Define una interfaz para todos los objetos en composite tanto en el composite como los nodos hoja. El componente puede implementar un comportamiento por defecto para los métodos genéricos.
* Leaf: Define el comportamiento de los elementos en composite mediante las aplicaciones de las operaciones que soporta el component
* Composite: Define el comportamiento de los component que tiene hijos y almacena los hijos. También implementa las operaciones relacionadas con la hoja.
* Client: Es el encargado de manipular los objetos de composite a través de la interfaz de component.

## 3. Cuando usar el patrón
* Cuando se desee representar jerarquías parte todo de objetos.
* Cuando se desea que los clientes sean capaces de ignorar la diferencia entre las composiciones de objetos y objetos individuales. Los clientes tendrán el tratamiento de todos los objetos en la estructura compuesta de manera uniforme.


![](https://upload.wikimedia.org/wikipedia/commons/5/5a/Composite_UML_class_diagram_%28fixed%29.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/composite)