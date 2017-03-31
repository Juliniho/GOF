# Conceptos generales POO
La **cohesión** y el **acoplamiento**, tienen que ver con la calidad del diseño OO (Orientado a objetos). En general, un buen diseño en la Orientación a
Objetos conlleva una perdida del acoplamiento y una gran cohesión.

# Cohesión
La cohesión mide el grado de conexión funcional existente entre los constituyentes o elementos de un **mismo módulo** e indica el grado en el cual una clase es individual, y tiene un propósito bien enfocado (Ejecutar una tarea sencilla interactuando muy poco o nada con el resto de módulos del programa).   

> La cohesión es un concepto subjetivo. Mientras más enfocada esté una clase, mas alta será su cohesión (lo que es una buena idea) y mejor su mantenimiento

## Beneficios
 
 * Una alta cohesión da como resultado clases que son típicamente mas fáciles de mantener que clases con una baja cohesión. 
 * Las clases con un propósito bien definido tienden a ser mas reutilizables por otras clases. 

## Tipos de cohesión
Ordenador de una cohesión mas fuerte -Mejor mantenimiento- a una cohesión mas débil -Peor mantenimiento-

### Funcional 
Un módulo presenta cohesión funcional si los elementos que contribuyen a la realización de una sola función, son los mas reutilizables y su nombre suele indicar claramente la función que realizan.

#### Ejemplos
* Análisis léxico de un XML
* Leer el registro de una transacción.

### Secuencial
Un módulo presenta cohesión secuencial si sus elementos están envueltos en tareas, tal que la salida de una tarea sirve de entrada para la siguiente.

#### Ejemplos
* Un modulo que formatea y realiza una validación cruzada sobre un registro y luego se usa como registro formateado y con su validación en otro registro, entonces se devuelve un registro formateado y validado.

###Comunicacional
Un módulo presenta cohesión comunicacional si contiene actividades que comparten los mismo datos ya sean de entrada o de salida.

####Ejemplos
* Un conjunto de funciones definidas sobre un array o una matriz

### Procedural
Un módulo presenta cohesión procedural si sus elementos desarrollan actividades diferentes, posiblemente sin relación alguna, tal que el flujo de control fluye de una actividad a la siguiente, en estos módulos las diferentes actividades no comparten datos, lo único que las relaciona es el flujo de control. Este diseño se puede similar a una biblioteca, en donde encontramos un conjunto de implementaciones funcionales.

#### Ejemplos
* Una función que comprueba los permisos de un fichero y a continuación abre el archivo.
* Un algoritmo para decodificar un mensaje.

### Temporal
Un módulo presenta cohesión temporal si sus elementos están agrupamos en una serie de unidades simplemente porque tienen que ejecutarse más o menos en el mismo periodo de tiempo, pero sin que exista una relación mayor entre ellas, es decir, sin que contribuyan al mismo fin (funcional), sin que se pasen datos en secuencia (secuencial) y sin que ni tan siquiera trabajen sobre los mismos datos (de datos) ni caen dentro de una misma categoría (lógica). Simplemente, tienen que ejecutarse cerca unas de otras.

#### Ejemplos
* Una funciona que es llamada después de capturar una excepción en la que se cierran archivos abiertos, crea  un log de error y notifica al usuario
* El conjunto de funciones responsables de la inicializacion, puesta en marcha, parada de algún proceso, etc, presentan una cohesión temporal.

### Lógica
Un módulo presenta cohesión lógica si sus elementos contribuyen en tareas de la misma categoría general y las actividades a desarrollar se seleccionan fuera del módulo (mediante una interfaz que le permita seleccionar la actividad a ejecutar).  Son módulos difíciles de entender y mantener

#### Ejemplos:
* Funciones de impresión: Un ejemplo de cohesión lógica es el caso en el que un conjunto de funciones de impresión que generan diferentes informes de salida forman parte de un solo módulo.
* Rutinas de manejo de entrada: Agrupar todas las rutinas que manejan el ratón y el teclado

### Casual
Un módulo presenta cohesión casual si sus elementos elementos realizan tareas diferentes sin relación significativa entre ellas, como pueden ser trozos de código que se repiten a lo largo del sistema y se llevan a un modulo.

#### Ejemplos
* Clase de utilerias: Clase que contiene una colección de funciones públicas y estáticas y son accesibles desde diferentes clases. Un cambio en esta clase afecta al resto de clases que acceden a ella

Ref: [link 1](https://www.infor.uva.es/~jvalvarez/docencia/ingenieria%20software/ptema9is1.pdf)
[link 2](https://weeklyitblogs.wordpress.com/tag/example-of-cohesion)

# Acoplamiento
El acoplamiento es un medio de evaluar la relación entre los distintos módulos de un sistema y el grado de interdependencia entre los módulos de un sistema.  Lo deseable es tener módulos con poco acoplamiento (o independiente entre sí) – Para ser capaces de realizar el mantenimiento de un módulo sin tener que cambiar otros módulos - Los tipos de acoplamiento mas reseñables son (de menor acoplamiento a mas):

## Acoplamiento normal
Se dice que dos módulos A y B están acoplados normalmente si A invoca a B, B realiza su tarea y retorna el control a A y tan solo intercambian datos (parámetros de entrada/salida). Existen tres subtipos, dependiendo de los datos que intercambien los módulos:
### Por Datos
Se dice que dos módulos A y B están acoplados por datos si están acoplados normalmente y ademas todos los parámetros que se intercambian son datos elementales sin estructura interna (tipos básicos)
### Por estampado
 Se dice que dos módulos A y B están acoplados por estampado si están acoplados normalmente y ademas los parámetros que se intercambian son datos compuestos (tipos básicos)
### Por control
 Se dice que dos módulos A y B están acoplados por datos si están acoplados normalmente y ademas uno le pasa a otro un dato con la intención de controlar su lógica interna. No es un buen acoplamiento, ya que impide que sean totalmente independientes y puede indicar un mal diseño. Podemos encontrar dos tipos de **flag**: flag de control, que son usados para controlar la lógica del modulo que los recibe y flag descriptivos, que revelan cualidades realativas al dato
## Acoplamiento  Común
Se dice que dos módulos A y B están acoplados comúnmente si ambos acceden a un mismo recurso común, típicamente memoria compartida, una variable global o un fichero.
## Acoplamiento  Por contenido
Se dice que dos módulos  A y B están acoplados por contenido si uno se refiere al interior del otro en alguna de las siguientes formas:
* Modificando o leyendo sus datos internos
* Saltando directamente al interior de su código

### Comparación de los distintos tipos de acoplamiento

| Tipo de acoplamiento | Modificabilidad | Comprensión | Reusabilidad |
|:--------------------:|:---------------:|:-----------:|:------------:|
|       Por datos      |      Buena      |    Buena    |     Buena    |
|     Por estampado    |      Buena      |    Media    |     Media    |
|      Por control     |      Pobre      |    Pobre    |     Pobre    |
|        Global        |      Media      |     Mala    |     Pobre    |
|       Contenido      |       Mala      |     Mala    |     Mala     |


# Encapsulación
Java, como un lenguaje orientado a objetos, implementa la encapsulación. Este concepto consiste en la ocultación del estado o de los datos miembro de un objeto, de forma que sólo es posible modificar los mismos mediante los métodos definidos para dicho objeto.
Cada objeto está aislado del exterior, de forma que la aplicación es un conjunto de objetos que colaboran entre sí mediante el paso de mensajes invocando sus operaciones o métodos. De esta forma, los detalles de implementación permanecen "ocultos" a las personas que usan las clases, evitando así modificaciones o accesos indebidos a los datos que almacenan las clases.
Esta idea provee dos principales beneficios:

* Modularidad, esto es, el código fuente de un objeto puede ser escrito, así como darle mantenimiento, independientemente del código fuente de otros objetos. Así mismo, un objeto puede ser transferido alrededor del sistema sin alterar su estado y conducta.
* Ocultamiento de la información, es decir, un objeto tiene una "interfaz publica" que otros objetos pueden utilizar para comunicarse con él. Pero el objeto puede mantener información y métodos privados que pueden ser cambiados en cualquier tiempo sin afectar a los otros objetos que dependan de ello.

En un objeto pojo/bean este encapsulamiento se consigue a través de los métodos getters y setters. Pero aquí debemos de tener especial cuidado con los atributos de nuestro objeto que sean objetos no mutables, es decir, que se pueda cambiar el objeto al que hacen referencia. Por ejemplo, si tenemos una objeto con un atributo de tipo List y en su get devolvemos la dirección de memoria a la que hace referencia dicha variable (atributo) estaríamos perdiendo la encapsulación de la clase ya que desde cualquier otro objeto podríamos cambiar la lista que se ha creado en nuestro objeto, para evitar esto y mejorar la encapsulación para este caso podemos construir nuestra propia interfaz dentro del objeto que maneje/gestione la lista.

```java
public class Person {

	List<String> phones;

	public Person() {
		super();
		this.phones = new ArrayList<String>();
	}

	public List<String> getPhones() {
		return new ArrayList<String>(phones);
	}

	public void setPhones(List<String> phones) {
		this.phones = phones;
	}

	public String addPhone(String phone) {
		phones.add(phone);
		return phone;
	}

	public String removePhone(String phone) {
		phones.remove(phone);
		return phone;
	}

}
```