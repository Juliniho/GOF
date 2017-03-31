## Versionado de software  ##

Una buena base para comenzar con el versionado es dividir el identificador de versión en tres partes principales:

![enter image description here](https://image.slidesharecdn.com/keynote1-stateofhbase-150605165719-lva1-app6891/95/hbasecon-2015-general-session-state-of-hbase-16-638.jpg?cb=1433524190)

- MAJOR aumenta cuando se realizan cambios incompatibles con versiones anteriores,
- MINOR aumeneta cuando se agrega funcionalidad de una manera compatible con versiones anteriores
- PATCH aumenta cuando se realizan correcciones de errores compatibles con versiones anteriores.

Las etiquetas adicionales para los metadatos de pre-release y generación están disponibles como extensiones al formato e indican que la versión es inestable.


>MAJOR.MINOR.PATCH[identifiers]

### Algunas normas a tener en cuenta ###

- Una vez que se ha liberado un paquete versionado, el contenido de esa versión NO DEBE ser modificado. Cualquier modificación DEBE ser lanzado como una nueva versión.
- La versión principal cero (0.y.z) es para el desarrollo inicial. La versión 1.0.0 define la primera version de la API pública. 

-La parte patch de la version Z (x.y.Z | x > 0) DEBE incrementarse si sólo si se introducen correcciones de errores compatibles con versiones anteriores. Una corrección de errores se define como un cambio interno que corrige un comportamiento incorrecto.

- La versión menor Y (x.Y.z | x> 0) DEBE incrementarse si:
	- se introduce nueva funcionalidad compatible con versiones anteriores en la API pública. 
	- si cualquier funcionalidad en la API pública está marcada como obsoleta. 
	- si se introducen nuevas funcionalidades o mejoras sustanciales en el código privado. 
La parte de la versión patch DEBE ser reajustada a 0 cuando la versión menor es incrementada.

- La versión mayor X (X.y.z | X > 0) DEBE ser incrementada si se introducen cambios incompatibles hacia atrás en la API pública. PUEDE incluir cambios menores y de nivel de patch. 
El patch y la versión secundaria DEBEN ser reajustados a 0 cuando la versión mayor es incrementada.

- Los identificadores para las versiones pre-release deben incluir solo caracteres ASCII alfanuméricos y guiones. No deben incluir ceros a la izquierda. 

	-Identificador Alpha (X.Y.Z-a[0-9]): indica la version que se está testeando del software. Puede que no contenga todas las caracteristicas que estan previstas para el lanzamiento

	-Identificador Beta (X.Y.Z-b[0-9]): indica la versión que contiene una versión completa de las características a liberar, es posible que sea inestable. En esta fase se mejora el rendimiento y se corrigen errores.
	
	-Identificador release-candidate (X.Y.Z-rc[0-9]): 
	Una versión release candidate es una versión beta con motivos mas que suficientes para llegar a ser un producto final. En esta etapa se cuenta con un producto estable con todas sus características  diseñadas, codificadas y probadas a través de uno o más ciclos beta sin errores conocidos.


![enter image description here](https://upload.wikimedia.org/wikipedia/commons/0/07/Software_dev2.svg)

[Fuente](http://semver.org/)

