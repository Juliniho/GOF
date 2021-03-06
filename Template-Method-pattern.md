# TEMPLATE METHOD PATTERN

## 1. Overview
El patrón template es un patrón de comportamiento y, como su nombre indica, proporciona una plantilla o una estructura de un algoritmo que es utilizado por los usuarios. Un usuario proporciona su propia implementación sin cambiar la estructura del algoritmo.
Este patrón define el esqueleto de un algoritmo con el que opera, difiriendo en algunos pasos para subclases. El método plantilla permite a las subclases redefinir ciertos pasos de un algoritmo sin cambiar la estructura del algoritmo.

El patrón template se puede usar en situaciones donde hay un algoritmo y algunos pasos podrían ser implementados de varias maneras diferentes. En tales escenarios, el patrón template sugiere mantener el control del algoritmo en un método separado que se refiere como método de template dentro de una clase, que puede ser referida con una clase de plantilla, dejando de lado las implementaciones específicas de las partes variantes (pasos que se pueden implementar de varias maneras diferentes) del algoritmo para diferentes subclases de esta.

La clase template no necesariamente tiene que salir de la aplicación de las subclases en su totalidad. En cambio, como parte de proporcionar el esquema del algoritmo, la clase plantilla también puede proporcionar cierta cantidad de implementación que puede ser considerada como invariantes a través de las diferentes implementaciones. Incluso puede proporcionar la implementación por defecto para la parte variante, si procede. Solo algunos detalles específicos serán implementados dentro de las diferentes subclases. Este tipo de implementación elimina la necesidad de duplicar código.

## 2. Participantes
* AbstractClass: Define operaciones primitivas abstractas que las diferentes subclases concretas definen para implementar los pasos del algoritmo. Implementa un método template que define el esqueleto del algoritmo. El método template llama a operaciones primitivas, así como, operaciones definidas en AbstractClass o las de otros objetos.
* ConcreteClass: Implementa las operaciones primitivas.

## 3. Cuando usar el patrón
* Para implementar partes invariantes de un algoritmo una sola vez y dejar en manos de las subclases la implementación del comportamiento que pueda variar.
* Cuando el comportamiento común entre las subclases deba tenerse en cuenta y centralizar en una clase común para evitar la duplicación de código. Identificando primero las diferencias en el código existente y separando entonces las diferencias en nuevas operaciones. Finalmente, se reemplaza el código diferente con el método plantilla que llama a una de estas nuevas operaciones
* Para controlar extensiones de subclases. Se puede definir un método plantilla que llama a las operaciones "hook" en puntos específicos, permitiendo de este modo extensiones solo en esos puntos.


![](http://www.dofactory.com/images/diagrams/net/template.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/template)