GUIA DE USO
===========

Este es el README para la rama QA que se desea ejecutar.


Modificación de archivos
--------------------

Para la correcta ejecución de esta rama se debe modificar 2 archivos:
+ values.yaml
+ data.json


#### Paso 1, values.yaml
--------------------

Este archivo contiene los valores de las variables necesarias para que el MicroServicio o App, pueda funcionar, 
como puede ser la conexion a la base de datos o la clave secreta para obetener informacion de algun servicio
propio de argacme, por dar un ejemplo.

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
  DB_DATABASE: godesa
  MS_MAIL_PORT: 25
  LOG_LEVEL: debug
  PORT: 3000
```
NOTA: es importante mantener la identacion de las variables, dentro del archivo, pues si se modifica mal, se producira 
un error, al trabajar con el archivo.


#### Paso 2, data.json
--------------------

Este archivo contiene los campos que se utilizaran para pasar los valores al yaml, que helmchart usuara para deployar
la imagen en el ambiente de QA
```yaml
    {
        "tipo":"MICROSERVICIO O APP",
        "descripcion":"DESCRIPCION PROYECTO O APP",
        "deploy": {
            "registry": "URL DEL REGISTRO DE IMAGENES",	
            "namespace": "ESPACIO DONDE SE DEPLOYARA LA IMAGEN",
            "pull_namespace": "ESPACIO DE DONDE SE DESCARGA LA IMAGEN",
            "name": "NOMBRE DEL PROYECTO",
            "image": "IMAGEN SELECCIONADA",
            "tag": "VERSION O TAG DE LA IMAGEN SELECCIONADA",
            "ingressPath": "/argacmego/bank/"
        },  
        "owner": {
            "date": "FECHA DE DEPLOY",
            "name": "NOMBRE DEL ENCARGADO DEL PASO",
            "email": "EMAILL DEL ENCARGADO DEL PASO"
        }
    }
```

# Ejemplo de moficacion.

```yaml
    {
        "tipo":"ms-go",
        "descripcion":"Este micro-servicio es bkn, se llama ms-go-config",
        "deploy": {
            "registry": "registry.argacme.corp:32000",	
            "namespace": "goqa",
            "pull_namespace": "godesa",
            "name": "ms-go-config",
            "image": "node_alpine_ms-go-config",
            "tag": "907_d2d2b237",
            "ingressPath": "config"
        }, 
        "owner": {
            "date": "21/01/2020",
            "name": "Jose QaDesa argacme",
            "email": "qadesa@argacme.cl"
        }
    }
```