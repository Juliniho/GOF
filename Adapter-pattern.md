# ADAPTER PATTERN

## 1. Overview
El patrón adaptader permite adaptar lo que un objeto o una clase expone a lo que espera otro objeto o clase. Convierte la interfaz de una clase en otra interfaz que el cliente espera. Permite a las clases que antes no podían debido a las interfaces incompatibles trabajar juntas, esto lo hace fijando una interfaz entre los objetos y las clases sin modificar los objetos y las clases directamente. De forma figurada, se puede pensar en este patrón como en un adaptador del mundo real, el cual permite conectar dos equipos diferentes que no se pueden conectar directamente, permitiendo el flujo de información entre uno y otro de forma indirecta.
Este patrón utiliza la composición para almacenar el objeto que adapta y cuando son llamados los métodos del adaptador, este traduce esas llamadas en algo que el objeto adaptado puede entender y son pasadas del adaptador al adapter.

Tipos de adaptador.
Existen dos tipos de adapter, el objeto adapter y la clase adapter. El ejemplo facilitado muestra uno del tipo objeto adapter que usa la composición de objetos, mientras que el adaptador de clase de basa en la herencia múltiple para adaptar una interfaz a otra.

## 2. Participantes
* Target: define la interfaz específica del dominio que Client usa.
* Client: colabora con la conformación de objetos para la interfaz Target.
* Adapter: define una interfaz existente que necesita adaptarse
* AdapterConcrete: adapta la interfaz de Adapter a la interfaz Target

## 3. Cuando usar el patrón
El patrón adaptador se debe utilizar cuando:
* Hay una clase existente, y su interfaz no coincide con el que se necesita.
* Se pretende crear una clase reutilizable que coopere con clases no relacionadas o no previstas, es decir, clases que no necesariamente tienen interfaces compatibles.
* Cuando existan varias subclases que pueden utilizar, pero es poca práctica adaptar su interfaz a través de subclasificaciones de cada uno. Un adaptador de objeto puede adaptar la interfaz de su clase padre.

![](https://upload.wikimedia.org/wikipedia/commons/d/d7/ObjectAdapter.png)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/structural/adapter)