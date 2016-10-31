# Specification PATTERN

## 1. Overview
El patrón specification es un patrón de diseño táctico presentado en el libro de Erics Evans, Domain-Driven Design. Mediante este patrón las reglas de negocio pueden crearse y combinarse por el encadenamiento de otras reglas mas simples, usando la lógica booleana. Para ello cada regla tiene un método que comprueba de forma atómica una sola característica de la lógica de negocio, esta comprobación se realiza en el método isSatisfiedBy(). Esto permite una lógica de negocio muy personalizable. 


## 2. Participantes
* Specification: interfaz que determina el método a implementar isSatisfiedBy()
* ConcreteSpecification: clase que representa una regla de negocio de forma atómica
* ConcreteCompositeSpecification: composición de concretespecification que encadena varias reglas

## 3. Cuando usar el patrón
Utilizar cuando se desee encapsular una regla de negocio que no pertenece a las entidades u objetos de valor, el propósito es que se les aplique dicha regla. 
* Hacer afirmaciones (validación) sobre un objeto;
* Recuperar objetos que cumplan los criterios de una colección (select);
* Especifica cómo debería ser creado un objeto.

![](https://upload.wikimedia.org/wikipedia/commons/8/8b/Specification_UML_v2.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/architecture/specification)

