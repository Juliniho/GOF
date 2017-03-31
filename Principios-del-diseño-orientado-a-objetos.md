
# Principios del diseño orientado a objetos

>Los principios de diseño son un conjunto de diseños y buenas prácticas que se emplean en OOD y OOP (diseño y programación orientada a objetos).


## Principios generales

### Principio No Te Repitas (DRY – Don't Repeat Yourself) 
Este principio basa su filosofía de definición de procesos en promover la reducción de duplicidad de código. Según este principio toda parte de código nunca debería ser duplicada debido a que la duplicación incrementa la dificultad en los cambios y evolución posterior, puede perjudicar la claridad y crear un espacio para posibles inconsistencias.
Cuando se aplica el principio DRY los cambios en cualquier parte del código se simplifican a su mínima expresión, ya que solo tendremos que modificar una parte del código. 

En ocasiones, podemos encontrar una función existente que hace "casi" lo mismo que queremos, pero necesitamos que haga algo extra o que no lo haga. Si te encuentras en este caso, en lugar de duplicar la función, mejor añádele un parámetro, y utiliza la información de ese parámetro para que la función haga el trabajo que necesitas o crea una nueva función y en esa nueva función llama a la existente y aplícale los nuevos cambios.

El código duplicado hace que nuestro código sea más difícil de mantener y comprender además de generar posibles inconsistencias. Para ello, dependiendo del caso concreto, la refactorización, la abstracción o el uso de patrones de diseño pueden ser alternativas viables.

Debes intentar hacer que todo lo que escribes sea fácil de utilizar. Esto empieza por hacer que tu código esté organizado y que sea intuitivo para los miembros de tu equipo el navegar y encontrar lo que ya pudiera existir en el sistema.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>


### Principio de Mantenerlo Simple y Estúpido (KISS – Keep It Simple and Stupid)

Este principio recomienda el desarrollo empleando partes sencillas, comprensibles y con errores de fácil detección y corrección, rechazando lo enrevesado e innecesario en el desarrollo.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

###Principio de No vas a necesitarlo (YAGNI – You Aren't Gonna Need It)

Es uno de los principios del Extreme Programming que indica que un programador no debe agregar funcionalidades extras hasta que no sea necesario. 
> Aplicar siempre las cosas cuando realmente los necesita, no cuando lo que prevén que los necesita." - Ron Jeffries

Nos debemos basar en hechos y no en suposiciones. Así evitamos sobre diseñar sistemas, una tendencia que retrasa y entorpece el alcance inicial de la tarea que estamos desarrollando.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>


## Principios referidos a Clases o Principios S.O.L.I.D

### Principio de Responsabilidad Única (SRP – Single Responsibility Principle)

> Cada objeto en el sistema deben tener una responsabilidad simple, y todos los servicios de los objetos deben cumplir con esa simple responsabilidad

Este principio nos viene a decir que una clase sólo debería tener una única razón para cambiar. En términos prácticos, este principio establece que:

 * Una clase debe tener una y solo una única causa por la cual puede ser modificada.
 * Cada clase debe ser responsable de realizar una actividad del sistema

Lo que trata de decirnos este principio es que debemos huir de aquellas clases monolíticas que aglutinen varias responsabilidades. Pero, ¿qué es una responsabilidad? Desde el punto de vista de SRP se podría decir que una responsabilidad en una clase es una razón para cambiar esa clase. Es decir, si encontramos que hay más de una razón por la que una clase pueda cambiar entonces es que esa clase tiene más de una responsabilidad.

>La correcta aplicación del SRP simplifica el código y se traduce en facilidad de mantenimiento, mayores posibilidades de reutilización de código y de crear unidades de testeo específicas para cada responsabilidad

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

### Principio Abierto-Cerrado (OCP – Open Closed Principle)
> Una clase debe estar abierta a extensiones, pero cerrada a las modificaciones.

Esto significa que las clases que se diseñen y que posteriormente necesiten cambiar un requisito, dicho cambio no afecte a la clase, se cree una nueva que extienda de la existente.
Las claves para la correcta aplicación de este principio son la abstracción y el polimorfismo, como hemos podido ver en el ejemplo.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

### Principio de Sustitución de Liskov (LSP - Liskov Substitution Principle)

>Debe ser posible utilizar cualquier objeto instancia de una subclase en lugar de cualquier objeto instancia de su superclase sin que la semántica del programa escrito en los términos de la superclase se vea afectado

Para cumplir con LSP, la implementación de la clase derivada debe:

* Ser menos restrictivas en la precondición.
* Ser más restrictivas en la postcondición.
* Preservar la invariancia.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

### Principio de Segregación de Interfaces (ISP - Interface Segregation Principle)

El principio ISP, trata sobre las desventajas de las interfaces "pesadas" (tiene mas información de la que necesita), y guarda una estrecha relación con el nivel de cohesión de las aplicaciones. Lo que dice este principio es que "las clases que implementen una interfaz o una clase abstracta, no deberían estar obligadas a utilizar partes que no van a utilizar".

Una solución a este problema es dividir un poco las cosas y crear, por ejemplo, una interfaz que tenga definida las cuestiones propias de los procesos manuales:

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

### Principio de Inversión de Dependencia (DIP – Dependency Inversion Principle)
Básicamente lo que nos dice este principio es que 

A. Las clases de alto nivel no deberían depender de las clases de bajo nivel. Ambas deberían depender de las abstracciones. 
B. Las abstracciones no deberían depender de los detalles. Los detalles deberían depender de las abstracciones.

DIP dice que si una clase depende de otras clases, ésta relación debería ser de dependencia de interfaces en lugar de dependencia de implementaciones concretas. La idea es aislar nuestra clase detrás de un muro de abstracciones de las que depender. Si los detalles tras las abstracciones cambian nuestra clase se encuentra a salvo. Esto ayuda a mantener un acoplamiento bajo y hace que nuestro diseño sea más fácil de cambiar.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

## Principios referidos a Módulos (librerías y/o paquetes)

### Cohesión
Estos 3 principios de diseño de paquetes indican que debe contener cada paquete para obtener una alta cohesión.

#### Principio de Equivalencia entre Reutilización y Liberación (REP – Release Reuse Equivalency Principle)
Este principio evoca por una agrupación de clases reutilizables que se puedan administrar y controlar cuando una nueva versión se genere.

La granularidad de reutilización se corresponde con la granularidad de la liberación de versiones. Un criterio de agrupación de clases en paquetes es la reutilización. Como los paquetes son unidades de liberación de versiones, la reutilización se convierte en unidad de liberación de versiones.
Esto significa que con el fin de reutilizar eficazmente el codigo este debe de llegar como una caja negra, que se va a utilizar pero no a cambiar.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

#### Principio de Cierre Común (CCP – Common Closure Principle)
Este principio se basa en que las clases que cambian juntas, pertenecen al mismo grupo.
Un proyecto de desarrollo está subdividido en una extensa red de paquetes interrelacionados. Es nuestra responsabilidad agrupar todas las clases que creemos que deben cambiar juntas.
El objetivo de este principio es minimizar el impacto de un cambio para afectar la menor cantidad de paquetes posibles, si existen clases que tienen un alto acoplamiento estas se deben empaquetar juntas

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

#### Principio de Reutilización Común (CRP – Common Reuse Principle)

Cambios a una clase que no nos interesa puede forzar al release de todo un paquete, por lo que: Las clases que no son usadas juntas, no deben juntarse en un paquete

Como podemos observar, estos principios son mutuamente exclusivos, sin embargo podemos utilizarlos de acuerdo a la etapa de desarrollo en la que nos encontremos; en la etapa inicial de desarrollo se puede establecer CCP como el principio a seguir, dando soporte a los entornos de desarrollo y pruebas; y se puede establecer REP y/o CRP para los usuarios finales a medida que el software se vuelva estable.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

### Acoplamiento
Estos 3 principios de diseño de paquetes hablan acerca de las métricas que evalúan la estructura de un sistema  con la finalidad de conseguir un bajo acoplamiento.

#### Principio de Dependencias Acíclicas (ACP – Acyclic Dependencies Principle)

Un paquete no debe tener dependencias cíclicas con otros paquetes. La estructura de dependencias de un paquete debe ser un[ Grafo acíclico dirigido ](https://es.wikipedia.org/wiki/Grafo_ac%C3%ADclico_dirigido) (Direct Acyclic Graphic), esto quiere decir que no debe haber dependencias cíclicas.

Para romper las dependencias cíclicas se recomienda:

* Abstraer interfaces, aplicar el principio DIP.
* Dividir paquetes, aplicar el principio CRP.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

#### Principio de Dependencias Estables (SDP – Stable Dependencies Principle)
La dependencia de paquetes en un diseño debe estar en dirección de la estabilidad de los paquetes. Un paquete solo debe depender de paquetes que son más estables que el para que nuestro paquete sea fácil de cambiar.

La estabilidad esta determinada por la cantidad de esfuerzo requerido para realizar un cambio, mientras más estable sea una clase más trabajo ha de requerir cualquier modificación; así para hacer que un paquete sea difícil de modificar las dependencias deben ir hacia el.

Para conocer como de inestable es un paquete, existe una métrica de inestabilidad. Esta metrica se usa para concoer la resistencia al cambio que tiene un paquete, su formula es ***I = Ce / (Ce+Ca)***, donde:
* Afferent Couplings (Ca - acoplamiento aferente (hacia dentro)): Desde la perspectiva de un paquete concreto el **acoplamiento aferente** se produce cuando otro paquete hace uso de atributos y/o métodos de clases de dicho clase o hereda de alguna de ellas.
* Efferent Couplings (Ce - acoplamiento eferente (hacia afuera)): Desde la perspectiva de un paquete concreto el **acoplamiento  eferente** se produce cuanto dicha clase hace uso de atributos y/o métodos de clases de otro paquete o hereda de clases de dicho paquete.Efferent = saliente.

Los valores de inestabilidad se encontrarán dentro del rango de valores entre 0 y 1. Con I=0 indica que un paquete es completamente estable y con I>0 indica que es paquete completamente inestable y que cualquier cambio será difícil de implementar.

No todos los paquetes deben ser estables. Si todos los paquetes de un sistema fueran estables no se podrían hacer cambios. En la estructura de paquetes que diseñemos algunos paquetes deben ser estables y otros inestables. Los paquetes estables deben mantener partes que no cambian, como el diseño de alto nivel del sistema (core), y los paquetes inestables deben mantener las partes cambiantes, como las implementaciones (infraestructura).

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

Ref:
https://code2read.com/2015/04/27/object-oriented-design-csharp-principios-diseno-paquetes/
https://jummp.wordpress.com/2010/06/26/acoplamiento-aferente-acoplamiento-eferente-inestabilidad-y-abstraccion-i/

#### Principio de Abstracción Estable (SAP – Stable Abstractions Principle)
Los paquetes estables deben ser paquetes abstractos.
Podemos visualizar la estructura de paquetes en nuestra aplicación como un conjunto de paquetes interconectados;  los paquetes inestables arriba y los estables debajo. Luego, todas las dependencias apuntan hacia abajo.

<a href="#principios-del-diseño-orientado-a-objetos">Subir</a>

