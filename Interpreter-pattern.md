# INTERPRETER PATTERN

## 1. Overview
Este patrón de diseño es un modelo de alta resistencia. Es todo acerca de juntar su propio lenguaje de programación, o el manejo de uno ya existente, mediante la creación de un intérprete para ese idioma. Para utilizar este patrón, se debe saber bastante sobre las gramáticas formales para crear un idioma. Como se puede imaginar,este es uno de esos patrones que los desarrolladores realmente no usan todos los días, porque la creación de su propio idioma no es algo que mucha gente haga.

Por ejemplo, definir una expresión en tu nuevo lenguaje podría ser algo como:
	expression ::= <command> | <repetition> | <sequence>

Cada expresión en este lenguaje, debería estar hecho de comando, repetición de comandos y secuencias de expresiones. Cada artículo debería ser representado como un objeto con un método para interpretar tu nuevo lenguaje dentro de algo que pueda ejecutarse sobre Java.
Dado un lenguaje, define su representación de su gramática junto con un intérprete que utiliza la representación para interpretar sentencias del lenguaje. En general, los lenguajes se componen de un conjunto de reglas gramaticales. Diferentes sentencias pueden ser construidas siguiente unas reglas gramaticales. A veces, una aplicación puede necesitar procesar ocurrencias de peticiones similares que son una combinación de un conjunto de reglas gramaticales.
Estas solicitudes son distintas, pero son similares en el sentido de que están todas compuestas usando el mismo conjunto de reglas.

Un ejemplo simple de esto sería un conjunto de diferentes expresiones aritméticas entregadas a una aplicación calculadora. Aunque cada expresión es diferente todas ellas están construidas usando las reglas básicas que conforman la gramática de la lengua de expresiones aritméticas. En tales casos, en lugar de tratar cada combinación de reglas como un caso separado, puede ser beneficioso para la aplicación tener la capacidad de interpretar una combinación genérica de reglas. El patrón Interpreter puede ser usado para diseñar esta capacidad en una aplicación para que otras aplicaciones y usuario puedan especificar las operaciones usadas por un lenguaje simple definido por un conjunto de reglas gramaticales.

Una jerarquía de clases puede ser diseñada para representar el conjunto de reglas gramaticales en las que todas las clases de la jerarquía representan una regla gramatical separada. Un modulo Interpreter puede ser diseñado para interpretar las sentencias construidas usando las clases de herencia y llevando a cabo las operaciones necesarias.

Debido a que cada clase representa unas reglas gramaticales, el número de clases aumenta con el número de reglas de la gramática. Un lenguaje con amplias reglas gramaticales complejas, requiere un gran número de clases. El patrón Interpreter funciona mejor cuando la gramática es simple.
Tener una gramática sencilla evita la necesidad de tener muchas clases correspondientes al conjunto completo de reglas que participan, que son difíciles de manejar y mantener.

## 2. Participantes
* AbstractExpression: Declara un Interpret abstracto que es común a todos los nodos en el árbol de sintaxis abstracta.
* TerminalExpression: Implementa una operación Interpret asociada con un símbolo terminal en la gramática. Requiere una instancia para cada símbolo terminal en la sentencia
* NonterminalExpression: Se requiere una de estas clases para cada regla R ::= R1 R2 ... Rn en la gramática. Mantiene las instancias de tipo AbstractExpression para cada símbolo Ri en Rn. Implementa una operación Interpret para un símbolo no terminal en la gramática. Interpret normalmente	se llama a si misma recursivamente en las variables que representan Ri sobre Rn. 
* Context: Contiene información global sobre el interpret
* Client: Construye (o se le da) un árbol de sintaxis abstracta que representa una sentencia en el lenguaje que la gramática define. El árbol de sintaxis abstracto se ensambla a partir de las instancias de NoterminalExpression y TerminalExpression. Invoca la operación Interpret.

## 3. Cuando usar el patrón
Use el patrón cuando exista un lenguaje por interpretar y puede representar las declaraciones del lenguaje en un árbol abstracto de sintaxis. El patrón funciona bien cuando:
* La gramática es simple. Para gramáticas complejas, la jerarquía de clases de la gramática puede llegar a ser muy grande y hacerse difícil de manejar. Para esos casos usar generadores de sintácticos.
* Eficiencia no es una preocupación critica. Los interpretes más eficientes por lo general no se implementan mediante la interpretación de árboles de análisis directamente.
Su uso podría ser en:
* Lenguajes de consulta de bases de datos especializadas, tales como SQL.
* Lenguajes informáticos especializados que a menudo se utilizan para describir los protocolos de comunicación.


![](https://upload.wikimedia.org/wikipedia/en/0/03/Interpreter_UML_class_diagram.jpg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/behavioral/interpreter)