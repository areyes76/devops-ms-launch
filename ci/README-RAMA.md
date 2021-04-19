GUIA DE USO
===========

Este es el README para la rama desarrollo-CI que se desea ejecutar.

Modificación de archivos
--------------------

Para la correcta ejecución de esta rama se debe modificar 2 archivos:

+ values.yaml
+ sonar-project.properties

#### Paso 1, values.yaml
--------------------

Este archivo contiene los valores de las variables necesarias para que el MicroServicio o App, pueda funcionar, 
como puede ser la conexion a la base de datos o la clave secreta para obetener informacion de algun servicio
propio de argacme, por dar un ejemplo.

Se debe buscar la etiqueta **path**, 
```yaml
  path: /argacme/<CAMBIARME>/v1/health
```
Y, a continuacion reemplazar *argacmeportal* por la url que valida el microservicio, por ejemplo.
```yaml
  path: /argacme/payment-method/v1/health
```

Se debe buscar la etiqueta **ingressPath**, 
```yaml
  ingressPath: /argacmeportal/
```
Y, a continuacion reemplazar *argacmeportal* por la url que valida el microservicio, por ejemplo.
```yaml
  ingressPath: /argacmeportal/payment-method/config/v1
```

Se debe buscar la etiqueta **configmap**, 
```yaml
configmap:
  VARIABLE001: valor001
  VARIABLE002: valor002
```
Y, a continuacion reemplazar VARIABLE001: valor001, por el nombre y el valor que se requiere, agregando todas las 
variables que se necesiten para el deploy.
```yaml
configmap: 
  VAULT_TYPE: appRole  
  DB_DATABASE: portaldesa
  MS_MAIL_PORT: 25
  LOG_LEVEL: debug
  PORT: 3000
```
NOTA: es importante mantener la identacion de las variables, dentro del archivo, pues si se modifica mal, se producira 
un error, al trabajar con el archivo.


#### Paso 2, sonar-project.properties
--------------------

Este archivo contiene los campos que se utilizaran para ejecutar el SonarQube, que genera el informe sobre las
pruebas de codigo en el microservicio.

```properties
	# must be unique in a given SonarQube instance
	sonar.projectKey=XX-XXXXX-XXXXXXX
	# this is the name displayed in the SonarQube UI
	sonar.projectName=XX-XXXXX-XXXXXXX
	sonar.projectVersion=9.9.9.9
	# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
	# Since SonarQube 4.2, this property is optional if sonar.modules is set. 
	# If not set, SonarQube starts looking for source code from the directory containing 
	# the sonar-project.properties file.
	sonar.sources=.
```

# Ejemplo de moficacion.

```properties
	# must be unique in a given SonarQube instance
	sonar.projectKey=ms-portal-account-identifier
	# this is the name displayed in the SonarQube UI
	sonar.projectName=ms-portal-account-identifier
	sonar.projectVersion=1.0.0
	# Path is relative to the sonar-project.properties file. Replace "\" by "/" on Windows.
	# Since SonarQube 4.2, this property is optional if sonar.modules is set. 
	# If not set, SonarQube starts looking for source code from the directory containing 
	# the sonar-project.properties file.
	sonar.sources=.
```
NOTA: es importante ir cambiando el valor de sonar.projectVersion, pues esto permitira poder relizar comparaciones 
sobre los cambios al codigo de una version a otra.