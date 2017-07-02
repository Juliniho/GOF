# Java Memory Model JMM

## Áreas principales de memoria
Dentro de la JVM podemos encontrar distintas áreas de datos usadas durante la ejecución de un programa. 

![img](http://www.researchbeta.com/wp-content/uploads/2011/07/RDA.png)

### JVM Stack Memory
 Cada hilo dentro de una JVM tiene su stack memory privado, creado a la vez que dicho hilo. Este stack se divide y almacena lo que se conocen como frames, en el se almacenan variables locales y resultados parciales, entra en juego también a la hora de invocar a un método ( se crean en el los parámetros) y obtener su resultado. Cada nuevo frame es creado cada vez que un método es invocado y destruido cuando la invocación del método finaliza. 
 Las excepciones StackOverflowError y OutOfMemoryError están asociadas con esta memoria.
 
###  Heap
El heap es la zona de memoria compartida entre todos los hilos de una JVM. Es la memoria usada en tiempo de ejecución y en la que se almacenan todas las clases y arrays instanciados. Es creada cuando la maquina virtual se inicia. Este área es el espacio de trabajo para el garbage collector. Puede ser de un tamaño fijo o ir expandiéndose conforme se requiera.
 La excepción OutOfMemoryError está asociada con esta memoria.
El Heap es divido en generaciones de la siguiente manera:

![enter image description here](https://i.stack.imgur.com/eP0SJ.png)

- Young Generation: es la memoria donde se asignan inicialmente los objetos y en el que viven un periodo corto de tiempo. Cuando esta memoria se llena, causa una recolección menor de basura. Esta generación se divide en dos espacios:
	- Eden space: el espacio usado cuando un objeto se crear mediante new.
	- Survivor space: este es el pool que contiene los objetos que han sobrevivido a la recolección menor de basura producida en el eden space.

Sobre esta generación existe una hipótesis que dice que la mayoría de los objetos asignados mueren jóvenes, pero si estos objetos pasan de una cierta "edad" tienden a "vivir" durante mas tiempo.

- Old Generation: es el pool que contiene los objetos que sobreviven al recolector de basura pasado en la generación joven. Esta compuesto por:
	- Tenured Space:  este pool de memoria contiene los objetos que han sobrevivido después de múltiples pasadas del GC dentro del survivor space.

>  Stop the World Event - Todas las recolecciones menores de basura producidas en las generaciones young y old lanza un evento y bloquean todos los hilos ya que todos los subprocesos de la aplicación se detienen hasta que se complete la operación.

-  Permanent Generation: este pool de memoria contiene clases metadata permanentes e información de descriptores como PermGen y elementos que están ligados a clases como por ejemplo miembros estáticos. también contiene objetos que están relacionados con el propio lenguaje Java

 - Virtual or reserved (Code cache): si usamos HotSpot Java VM este incluye áreas de código cacheado que tiene memoria que será usada para compilaciones y almacenamiento de código nativo.

La division del heap en distintas areas es beneficiosa porque permite aplicar diferentes algoritmos en diferentes espacios de memoria.

### Área de métodos
Esta zona de memoria es compartida por todos los hilos de una JVM. Esta área es el análogo al área que almacena el código compilado en un lenguaje convencional.  Almacena estructuras de clase como el runtime constant pool, datos de campos y  de métodos, y el código para métodos y constructores
 Es creada con el arranque de la maquina virtual. Forma parte del lógica del heap, a pesar de esto algunas implementaciones no aplican el GC en ella.
 La excepción OutOfMemoryError está asociada con esta memoria.
 
### Run-time constant pool
Este espacio de memoria es por cada clase o por interfaz en tiempo de ejecución la tabla de representación del pool de constantes. Contiene varios tipos de constantes,  desde literales numéricos conocidos en tiempo de compilación hasta referencias de métodos y campos que deben resolverse en tiempo de ejecución.

### Native method stacks
Este espacio de memoria es usado para las implementaciones de un intérprete para un  conjunto de instrucciones en un lenguaje distinto al de Java, tal como C.

### Pc register
La JVM puede soportar muchos hilos de ejecución a la vez. Cada hilo tiene su propio registro de pc (program counter), este contador contiene la dirección de la instrucción de la JVM que está ejecutándose actualmente.

[More info here](https://docs.oracle.com/javase/specs/jvms/se7/html/jvms-2.html#jvms-2.5)
 
# Garbage Collector GC

La JVM usa un daemon separado para el hilo que hace de GC. A grandes rasgos el funcionamiento de este es el sigueinte. Inicialmente los espacio tunered y survior estan vacios. Cuando la JVM no dispone de espacio en la parte eden  inicia el GC minor. Durante su ejecucion, los objetos que no estan accesibles son marcados para ser recolectados. La JVM selecciona uno de los dos subespacios en los que se subdivide survivor (S0) y en el copia los objetos que estan accesibles e incrementa la edad del objetos en uno. Los objetos que no encajan en este espacio son movidos al espacio tunered. Este proceso se conoce como "premature promotion". 
En una segunda pasada del GC minor el GC marca los objetos que no estan accesibles tanto del espacio eden como de la parte survivor S0, copia los GC root a la otra subparte de la zona survivor (S1), y los objetos que estan accesibles se les incrementa su edad en uno.

El proceso anterior se repite para cada GC minor. Cuando los objetos alcanzan el umbral máximo de edad, estos objetos se copian en el espacio tenured. Existe una opcion en la JVM llamada "MaxTenuringThreshold" que especifica la edad limite para que un objeto sea promocionado al espacion tenures, por defecto es 15.

## Tipos de GC

La implementacion del GC reside en la JVM. Cada JVM puede implementar su GC, el unico requisito es que cumple con la especificacion de la JVM. Aunque hay muchas JVM, el [HotSpot](http://www.oracle.com/technetwork/java/javase/tech/index-jsp-140228.html) de oracle es el mas común y ofrece un conjunto robusto y maduro de opciones para el GC.  Existen multiples GC optimizados para varios casos de uso. Todos los GC implementan lo que se conoce como estrategia generacional que categoriza los objetos por edad.

Los cuatro GCs del HotSpot de oracle son:
 - Serial: Todos los eventos del GC se llevan a cabo en serie en un hilo. La compactación se ejecuta después de cada recolección de basura.
 - Paralelo: Múltiples hilos se usan para el minor GC. Un solo hilo se usa para el major GC y la compactación de Old Generation.
 - CMS (Concurrent Mark Sweep): El minor GC usa  múltiples hilos usando el mismo algoritmo que Parallel. Major GC es multihilo, como Parallel Old, pero CMS se ejecuta simultáneamente junto con los procesos de aplicación para minimizar los eventos "stop the world" . No se realiza compactación.
 - G1 (Garbage Firts): El colector de basura más nuevo está pensando para reemplazar a CMS. Es paralelo y concurrente como CMS, pero funciona de manera muy diferente comparado con los antiguos recolectores de basura.

## Buenas prácticas

- Minimizar el numero de objetos que promocionan al área mas vieja, disminuir el número de objetos pasados ​​al área vieja puede ser mal interpretado como la opción de dejar el objeto en el área Nueva. Sin embargo, esto es imposible. En su lugar, se debe ajustar el tamaño del área joven.
- Disminuir el tiempo del GC Complento, el tiempo de ejecución de este GC es relativamente más largo que el de GC Menor. Por lo tanto, si se tarda demasiado tiempo en ejecutar GC completa (1 segundo o más), el tiempo de espera puede ocurrir en varias partes conectadas.
- Si nuestro sistema cuenta con una memoria grande debemos contemplar la opción de configurar el GC para decrementar el numero de ejecuciones de este y aumentar el tiempo de ejecución. En cambio, si disponemos de una memoria pequeña, debemos decrementar el tiempo de ejecución e incrementar el numero de ejecuciones.

## GC Roots - La fuente de todos los objetos árbol

Se conoce como objetos root, aquellos objetos que la aplicación tiene disponibles y que puede alcanzar (que tiene referenciados) y todo el árbol de objetos puede ser alcanzado. Los objetos conocidos como GC roots siempre son alcanzados por el GC. El recolector de basura recoge aquellos objetos que no son GC root y no son accesibles por referencias de objetos GC root. Estos objetos son accesibles desde fuera del heap.

![enter image description here](https://assets.dynatrace.com/content/dam/dynatrace/javabook/gc-roots.png)

Existen cuatro tipos de raíces de GC en Java:

- Las variables locales se mantienen vivas en el stack de hilos. Esto no es una referencia virtual de objeto real y por lo tanto no es visible. Para todos los efectos, las variables locales son GC root.
- Los hilos activos de Java siempre se consideran objetos vivos y por lo tanto GC root. Esto es especialmente importante para las variables locales de hilo.
- Las variables estáticas son referenciadas por sus clases. Este hecho los convierte por defecto en GC root.
- Referencias JNI son objetos Java que el código nativo ha creado como parte de una llamada JNI. Los objetos creados de esta forma son tratados especialmente porque la JVM no sabe si está siendo referenciados por el código nativo o no. Tales objetos representan una forma especial de GC root.

## Garbage Collection Log

Activar el log del GC puede ser útil, el overhead por activarlo para la JVM es mínimo. Algunos parámetros interesantes son:

### DisableExplicitGC
Por defecto esta opción esta desactivada. Algunos veces los desarrolladores podrían haber invocado al GC de forma implícita mediante System.gc() o Runtime.getRuntime().gc(). 
Esto no es aconsejable. Por lo tanto en sistemas de producción nosotros activaremos esta opción para que la invocación del GC esté deshabilitada.

### PrintGCDetails
Por defecto esta opción esta deshabilitada. Si nosotros activamos esta opción, la JVM mostrará mas detalles sobre cada recolección de basura.

### PrintGCApplicationStoppedTime
Por defecto esta opción está deshabilitada. Si la activamos se muestra la información sobre el tiempo de pausa a causa del GC.

### PrintGCApplicationConcurrentTime
Por defecto esta opción esta deshabilitada. Si la activamos, mostrará la información sobre el tiempo de GC referente a la aplicación.

### PrintGCDateStamps
Por defecto esta opción esta deshabilitada. Si la activamos, mostrará la información sobre la fecha y hora de cada GC.

### loggc
Este parámetro lo utilizaremos para indicar el nombre del archivo donde se almacenará la información que queramos respecto del GC.

### UseGCLogFileRotation
Esta opción indica que el tamaño con el que queremos que la JVM realiza un log rotation con el fichero de salida.

### NumberOfGCLogFiles
El valor por defecto es 1. Esta opción establece el numero de archivos que se utilizaran para realizar el log rotation.

### GCLogFileSize
El valor por defecto el 8KB, que es el tamaño maximo del fichero de log antes de que se produzca el log rotation.

Una vez obtenio el log debemos observar los sigueintes 
paramentros:

- Con que frecuencia se lanzan los GCs Minor and Mayor?
Debe haber un intervalo de tiempo de varios minutos. Si el GC minor ocurre con mas frecuencia, revisaremos el espacio asignado a la genereacion young. Si es el GC mayor el que mas se ejecuta deberemos mirar el espacio asignado al heap.

- Cuanto tiempo toma cada evento del GC para completarse?
Idealmente, el GC minor tomará un par de milisegundos, y el GC mayor tardará entre un par de milisegundos o segundos.

> [GC log analyzer](http://gceasy.io/)



# Tipos de objetos y objetos  de referencia

## Strong Reference
Son los objetos de referencia creados con la key word new. Cualquier objetos con al menos una strong referencia no esta disponible para el recolector de basura.  A estos objetos se les conoce como objetos fuertemente accesibles. Solo llegaran a estar disponible para el recolector cuando sea referenciado a null.

## Soft Reference
Una referencia soft puede ser creada por un objetos wrapping de la instancia en un objeto del tipo  java.lang.ref.SoftReference:
 
```java 
StringBuilder sb = new StringBuilder();
SoftReference<StringBuilder> sbSoftRef = new SoftReference<>(sb);
sb = null;
```
En esta etapa, el string builder no es accesible para el GC. Sin embargo, la tercera línea anula la referencia fuerte, y ahora el objeto es una referencia soft. Podemos decir que el objetos es softly reachable.

En esta fase, aun podemos recuperar la referencia fuerte con el objeto de la siguiente forma:
```java
sb = sbSoftRef.get();
```

Los objetos con sólo referencias soft son recolectados si y sólo si la JVM ha concluido que no hay más memoria para asignar a nuevos objetos y está al borde de lanzar un error OutOfMemory.
Las soft references están pensadas para su uso en caches. A medida que crece la memoria caché, la memoria disponible para nuevos objetos se reduce, pero necesita la caché, por lo que la JVM se compromete contigo hasta que no pueda más.

## Weak reference
Una referencia soft puede ser creada por un objetos wrapping de la instancia en un objeto del tipo  java.lang.ref.WeakReference :
 
```java 
StringBuilder sb = new StringBuilder();
WeakReference<StringBuilder> sbWeakRef = new WeakReference<>(sb);
sb = null;
```
El objeto puede ser colectado en cualquier momento. Técnicamente decimos que el objeto es weakly reachable. Como en el caso anterior podemos volver a tener la referencia del objeto usando el método: sb = sbWeakRef.get();

Los objetos con solo referencias weak son recogidos eagerly por el GC independiente del espacio de la memoria que quede libre.

## Phantom Reference

Una referencia soft puede ser creada por un objetos wrapping de la instancia en un objeto del tipo  java.lang.ref.WeakReference :
 
```java 
StringBuilder sb = new StringBuilder();
ReferenceQueue<StringBuilder> refQ = new ReferenceQueue<>();
PhantomReference<StringBuilder> sbPhantomRef = new PhantomReference<>(sb, refQ); 
sb = null;
```
Ignoraremos el objeto ReferenceQueue por ahora. PhantomReference, a diferencia de las referencias soft y weak, es inútil sin ReferenceQueue. ReferenceQueue puede ser recolectado de inmediato, aunque con una condición: el tiempo exacto de la recolección es anotado y el doc notificado.

El método get de este objeto siempre devuelve null. Está pensado para un uso alternativo con una mayor flexibilidad del metodo Object.finalize().


## Reference Queue

Este objeto es una estructura de datos que se aplica como cola para objetos de referencia: WeakReference, SoftReference, and PhantomReference.

Encolar referencias le permite iterar la cola de referencia y determinar qué referencias se han recolectado y cuáles no. 

## Java Memory argumentos

| argumento  |    |
|---|---|
| -Xmixed   |mixed mode execution (default)	  |
| -Xint  | interpreted mode execution only |
| -Xbootclasspath:  | set search path for bootstrap classes and resources -Xbootclasspath/a:                   append to end of bootstrap class path -Xbootclasspath/p:                   prepend in front of bootstrap class path -Xnoclassgc       disable class garbage collection -Xloggc:    log GC status to a file with time stamps   |
| -Xbatch  |  disable background compilation |
| -Xms  | set initial Java heap size  |
| -Xmx   |  set maximum Java heap size |
|  -Xss | set java thread stack size  |
| -Xprof  | output cpu profiling data  |
| -Xfuture  | enable strictest checks, anticipating future default  |
| -Xrs  | reduce use of OS signals by Java/VM (see documentation)  |
|  -Xdock:name= |  override default application name displayed in dock -Xdock:icon=                   override default icon displayed in dock -Xcheck:jni       perform additional checks for JNI functions -Xshare:off	      do not attempt to use shared class data -Xshare:auto      use shared class data if possible (default) -Xshare:on	      require using shared class data, otherwise fail.  The -X options are non-standard and subject to change without notice. |
| -Xnoclassgc  | disable class garbage collection  |
             
 > [WebTool generate arguments](http://jvmmemory.com/)      
              
            
# Memory Leaks

Un memory leaks ocurre cuando un objeto que ya no se utiliza todavía está referenciado por otro objeto.

## Cuándo ocurren?
Como sabemos un objeto es elegible para el GC cuando este no es accesible y no existe ningún hilo que pueda alcanzarlo.
Esto puede ocurrir cuando:

- No se cierra un stream
- Se usan atributos estaticos para almacenar referencias. Un objeto estatico siempre se almacena en memoria. Si declaramos demasiados campos estativos para almacenar referencias a objetos, esté creara leaks de memoria. Cuando mayor sea el objeto mayor será el leak de memoria.
- Usar un HasSet que está usando de forma incorrecta hashCode() or equals().
- El uso de wrapper también puede suponer un memory leaks debido al autoboxing en algunas operaciones

## Cómo pueden evitarse?
La solucion pasa por usar los objetos  de referencia vistos en el punto anterior.  Algunas medidas a tomar tambien son:
- No mezclar tipos primitivos con wrapper a la hora de pasar argumentos, el autobox creará nuevos objetos cada vez.
- Cuando se use un objeto propio como key de un Map, implementar siempre los metodos equals y hash, ademas de hacer inmutable dicho objeto.
- Cerrar siempre las conexiones o ficheros que se habrán. 
- Tener especial cuidado con las referencias obsoletas. Una referencia obsoleta es una referencia la cual no puede ser desreferenciada. Esto ocurre cuando por ejemplo tenemos un objeto que hace referencia a varios objetos y desde la perspectiva de la aplicación estos objetos no están accesibles pero aun se encuentran en la memoria, esto se puede solucionar asignando a null dichos objetos.