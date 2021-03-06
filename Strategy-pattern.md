# STRATEGY PATTERN

## 1. Overview
El patrón de diseño Strategy parece ser el más simple de todos los patrones de diseño, sin embargo, proporciona una gran flexibilidad al código. Este patrón es usado casi en todos sitios, incluso en conjunción con otros patrones. Para entender este patrón, vamos a crear un formateador de texto para un editor de texto.
El patrón de diseño Strategy define una familia de algoritmos, encapsulando cada uno y haciéndolos intercambiables. Strategy permite que el algoritmo varíe independientemente de los clientes que lo usen.

El patrón es útil cuando existe un conjunto de algoritmos relacionados y cada objeto cliente tiene que ser capaz de recoger de forma dinámica y seleccionada un algoritmo de este conjunto que se adapte a su necesidad actual. Este patrón sugiere mantener la implementación de cada algoritmo en una clase separada. Cada uno de los algoritmos encapsulados en una clase separada se conoce como Strategy. Cada objeto que use un objeto Strategy se refiere como objeto de contexto.

Con diferentes objetos Strategy, cambiar el comportamiento de un objeto de contexto es simplemente una cuestión de cambiar la implementación del objeto Strategy que tiene el algoritmo que implementa. Para habilitar un objeto contexto para acceder a diferentes objetos Strategy en una manera transparente, todos los objetos de Strategy deben ser diseñados para
ofrecer la misma interfaz. En Java, esto se logra haciendo que cada objeto Strategy implemente una interfaz común o con una subclase abstracta común.

Una vez que el grupo de algoritmos relacionados es encapsulado en un conjunto de clases Strategy en una jerarquía de clases, un cliente puede elegir entre estos algoritmos y crear instancias de una clase de estrategia apropiada. Para alterar el comportamiento del contexto, un objeto client necesita configurar el contexto con la instancia de la Strategy elegida. Este tipo de disposición separa completamente la aplicación del algoritmo del contexto que lo utiliza. Como resultado, cuando una implementación existente es cambiada o un nuevo algoritmo es añadido al grupo, tanto el contexto como el objeto cliente (que usa el contexto) no se verán afectados. 

## 2. Participantes
* Strategy: Declara la interfaz común a todos los algoritmos soportados. El objeto context usa esta interfaz para llamar al algoritmo definido por el ConcreteStrategy 
* ConcreteStrategy: Implementa el algoritmo usando la interfaz Strategy
* Context: Es configurado con un objeto ConcreteStrategy. Mantiene una referencia al objeto Strategy. Puede definir una interfaz que permita acceder a sus datos de Strategy

## 3. Cuando usar el patrón
* Cuando existan muchas clases relacionadas que solo difieran en su comportamiento. Strategy proporciona una manera de configurar una clase con uno de los muchos comportamientos
* Cuando sea necesario disponer de distintas variantes de un algoritmo. Por ejemplo, podría definir algoritmos que reflejen diferentes espacios/tiempo. Strategy pueden usarse cuando estas variantes sean implementadas como una jerarquía de clases de algoritmos.
* Cuando un algoritmo que utiliza datos que el cliente no debería conocer, este patrón evita la exposición de estos.
* Una clase define muchos comportamientos, y estos aparecen con varias sentencias condicionales en sus operaciones. En lugar de muchos condicionantes, mueva las ramas condiciones a su propia clase Strategy.


![](http://www.dofactory.com/images/diagrams/net/strategy.gif)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/strategy)