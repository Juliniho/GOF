# PROXY PATTERN

## 1. Overview
EL patrón proxy, un patrón estructural, proporciona un sustituto para controlar el acceso a otro objeto. El patrón proxy se utiliza para crear un objeto representativo que controla el acceso a otro objeto que puede ser remoto, costoso de crear o necesita ser protegido.
Una de las razones para controlar el acceso a un objeto es distinguir el coste total de su creación y la inicialización hasta que realmente se necesita para usarlo. Otra razón podría ser la de actuar como un representante local para un objeto que vive en una JVM diferente. El Proxy puede ser muy útil en el control del acceso al objeto original, sobre todo cuando los objetos deben tener diferentes permisos de acceso.
En el patrón Proxy, un cliente no habla directamente al objeto original, delega las llamadas al objeto proxy, que llama a los métodos del objeto original. El punto importante es que el cliente no sabe nada del proxy, el proxy actúa como un objeto original para el cliente.

## 2. Participantes
* Proxy: Mantiene una referencia del objeto real, al cual puede acceder. Proxy puede referirse a un sujeto si el RealSubject y el Subject tienen la misma interfaz. Controla el acceso a el Subject original y puede estar bajo su responsabilidad la creación y eliminación del mismo.
* Subject: Define la interfaz común para el RealSubject y el Proxy.
* RealSubject: Define el objeto real que representa el proxy.	

## 3. Variantes
Existen tres variaciones de este patrón:
* Proxy remoto: proporciona una representación local para un objeto en un espacio de direcciones (HEAP) diferente. oculta el hecho de que un objeto reside en otro espacio de direcciones.
* Proxy virtual: realiza optimizaciones, por ejemplo, crea objetos costosos bajo demanda. 
* Proxy de protección: controla el acceso a el objeto original, son útiles cuando los objetos deben tener diferentes permisos de acceso al objeto original.
	
### 3.1 Proxy Remoto.
El proxy remoto actúa como un representante local de un objeto remoto. Un objeto remoto es un objeto que vive en el heap de una JVM diferente. Se llama a métodos de un objeto local que avanza las llamadas hacia el objeto remoto. Su objeto cliente actúa como si estuviese haciendo llamadas a métodos remotos, pero está llamando a métodos de un objeto proxy en el heap local que maneja todos los detalles de bajo nivel para la comunicación por red. Java soporta la comunicación entre los dos objetos que residen en dos JVM utilizando RMI. RMI es una invocación de métodos remotos que se utiliza para construir los objetos de ayuda cliente y servidor, hasta la creación de un objeto auxiliar de cliente con los mismos métodos que en el servicio remoto. Usando RMI tu no tiene que escribir ningún código sobre redes o I/O. Con tu cliente, tu llamas a métodos remotos como si llamaras a métodos de un objeto normal corriendo en la JVM local del cliente. RMI también proporciona la infraestructura en ejecución para hacer que todo el trabajo, incluyendo un servicio de búsqueda que el cliente puede usar para buscar y acceder a objetos remotos. 
Hay una diferencia entre las llamadas RMI y las llamadas a métodos locales, el ayudante del cliente envía las llamadas a métodos a través de la red, por lo que él es el encargado de trabajar en red y con I/O en los que participa las llamadas RMI. Para hacer que el servicio remoto esté a disponible para los clientes tú necesitas registrar el servicio con el registro RMI. Cuando se registra el objeto de implementación, el sistema RMI pone realmente un stub en el registro, ya que esto es lo que necesita un cliente. El método Namin.rebind es usado para registrar el objeto. Tiene dos parámetros, el nombre del servicio y objeto requerido por los clientes para usar el servicio. Para la creación del stub necesario, usaremos la herramienta rmic, incluida en JDK, solo hay que lanzar rmic por consola desde el directorio donde se encuentra la implementación. El siguiente paso es lanzar rmiregistry, pero asegúrate que se lanza desde el directorio que tiene acceso a las tus clases. Por último, se lanza la aplicación concreta con la implementación de la clase remota.
 
> http://www.ejbtutorial.com/java-rmi/a-step-by-step-implementation-tutorial-for-java-rmi
	
### 3.2 Proxy Virtual.
Esta variante del patrón es una técnica de ahorro de memoria que recomienda posponer la creación de objetos hasta que se necesiten, se utiliza cuando se crea un objeto que es costoso para la memoria o el proceso que involucra. El objeto que es creado una primera vez y está referenciado en la aplicación y la misma instancia es reusada desde su creación en adelante. La ventaja de este enfoque en una aplicación con un arranque mas rápido, ya que no requiere crear y cargas todos los objetos de aplicación. Supongamos que hay un objeto Company en la aplicación y este objeto contiene una lista de los empleados de la compañía en un objeto ContactList. Podrá haber miles de empleados de una empresa. Cargando el objeto Company de la base de datos junto con la lista de todos sus empleados en el objeto contactlist podría tomar mucho tiempo. En algunos casos ni siquiera se necesita la lista de los empleados, pero se ve obligado a esperar hasta que la empresa y su lista de empleados estén cargados en la memoria. Una forma de ahorrar tiempo y memoria es evitar la carga de los objetos empleados hasta que sea necesario, y esto se hace mediante el Proxy Virtual. Esta técnica también se conoce como Lazy Loading donde esta recoge los datos sólo cuando es necesario.
	
### 3.3 Proxy protección
En general, los objetos de una aplicación interactúan entre sí para implementar la funcionalidad general de la aplicación. La mayoría de los objetos son accesibles a todos los demás objetos de la aplicación. A veces, puede ser necesario limitar la accesibilidad de un objeto solo a un conjunto limitado de objetos cliente en función a de sus permisos. Cuando un objeto cliente intenta acceder a otro objeto, al cliente se da acceso a los servicios proporcionados por el objeto solo si el cliente puede proporcionar credenciales de autenticación adecuadas. En tal caso, un objeto separado puede ser designado con la responsabilidad de verificar los privilegios de acceso de diferentes objetos de cliente cuando accedan al objeto real. En otras palabras, cada cliente debe autenticarse con éxito con ese objeto designado para obtener acceso a la funcionalidad real del objeto. Tal objeto con el que un cliente tiene que autenticarse para tener acceso al objeto real puede ser contemplado como un objeto autenticados que se implementa usando un servidor proxy de protección.

## 4. Cuando usar el patrón
Proxy es aplicable siempre que haya una necesidad de una referencia más versátil o sofisticada a un objeto que un simple puntero.
* Un proxy remoto proporciona una representación local para un objeto en un espacio de direcciones diferente.
* Un proxy virtual crea objetos costosos bajo demanda
* Un proxy de protección, cuando se necesite controlar el acceso al objeto original.

## 5. Otros tipos de proxy
* Proxy cache/ Proxy Server: Proporciona la funcionalidad necesaria para almacenar los resultados de las operaciones de destino utilizados con mayor frecuencia. El objeto proxy almacena estos resultados en una especio de repositorio cuando un objeto cliente solicita la misma operación, el proxy devuelve los resultados de la operación de la son a de almacenamiento sin acceder realmente al objeto destino.
* Proxy firewall: su principal uso es proteger los objetos de destino de malos clientes. Un proxy firewall también es usado para evitar que los clientes accedas a objetivos dañinos.
* Proxy de sincronización: Proporciona funcionalidad necesaria para permitir el acceso concurrente y seguro a un objeto destino por di referentes objetos clientes.
* Proxy de referencia inteligente: Proporciona funcionalidad para evitar la eliminación accidental del objeto de destino cuando hay clientes que aún mantienen una referencia a él. Para logar esto, el proxy mantiene el número de referencias al objeto de destino. El proxy elimina el objeto siempre y cuando no existan referencias a él.
* Proxy de conteo: Proporciona algún tipo de mecanismo de auditoria antes de ejecutar un método en el objeto de destino.

	

![](https://upload.wikimedia.org/wikipedia/commons/7/75/Proxy_pattern_diagram.svg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/proxy)