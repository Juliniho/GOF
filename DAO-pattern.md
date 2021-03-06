# DAO PATTERN

## 1. Overview
El patrón de diseño DAO implementa el mecanismo de acceso requerido para trabajar con fuentes de datos. La fuente de datos podría ser un almacenamiento persistente como un RDBMS, un servicio externo como un intercambio de B2B, un repositorio como una base de datos LDAP, o un servicio de negocio accesible a través de CORBA Internet Inter-ORB Protocol (IIOP) o sockets de bajo nivel. Los componentes de negocio que se basan en DAO utilizan la interfaz más simple expuesta por DAO para sus clientes. DAO oculta completamente los detalles del origen de datos de la aplicación hacia sus clientes.
Debido a que la interfaz expuesta por el DAO a los clientes no cambia cuando los datos subyacentes cambian su implementación de código, este modelo permite al DAO adaptarse a los sistemas de almacenamiento sin que ello afecte a sus clientes o componentes de negocio. Esencialmente, DAO actúa como un adaptador entre el componente y la fuente de datos.

## 2. Participantes
* BusinessObject: El BusinessObject representa al cliente los datos. Es el objeto que requiere el acceso a la fuente de datos para obtener y almacenar datos. BusinessObject puede ser implementado como un bean de sesión, beans de entidad, o algún otro objeto Java, además de un servlet o un helper bean que accede a la fuente de datos.
* DataAccessObject: El DataAccessObject es el objeto principal de este patrón. El DataAccessObject abstrae la 	implementación del acceso a los datos subyacentes para el BusinessObject para permitir el acceso transparente a la fuente de datos. El BusinessObject también delega la carga de datos y operaciones de almacenamiento al DataAccessObject.
* TransferObject: Esto representa un objeto de transferencia que se utiliza como soporte de datos. El DataAccessObject puede utilizar un objeto de transferencia para devolver los datos al cliente. El DataAccessObject también pueden recibir los datos del cliente en un objeto

## 3. Cuando usar el patrón
* Abstraer y encapsular los accesos a los datos.
* Gestionar las conexiones a la fuente de datos.
* Obtener los datos almacenados.

> FUENTE : http://www.oracle.com/technetwork/java/dataaccessobject-138824.html

![](http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/146804.jpg)

[Ejemplo](https://github.com/ajpaez/Learning/tree/master/Design%20Patterms/src/main/java/apr/learning/pattern/architecture/dao)