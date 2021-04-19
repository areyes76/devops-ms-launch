# README 

Creacion inicial de un proyecto, via automatizacion, usando las herramientas de gitlab

La idea de este proyecto es poder facilitar la forma de como crer un proyecto de forma automatica, para evitar lo tedioso de hacerlo.

Para este caso en particular, se crean proyectos del tipo Nodejs y que se despliegan en un Cluster K8s, con su plantilla de ejecucion.
Despues de crearse, el equipo podra descargar el repositorio y comnenzar a trabajar sobre las ramas, y estas
ya pueden ser ejecutadas, en un ambiente CI y CD (integración continua y entrega continua) dentro de gitlab.

NOTA: la carpeta ms-project, es el template del helmchart, para hacer lo mas dinamico, en la creacion de los despliegues en k8s.
      Esta carpeta seria la idea colocarla en otro repositorio y ser consumida por las ramas CI y CD del proyecto. 

Si se quisiera crear otro tipo de proyectos(angular, java, goland), entonces lo que deberia cambiar es el contenido del archivo 
.gitlab-ci.yml que estan en las carpetas CI y CD correspondientes.

Hay muchas formas de crear proyectos dinamicos, en este caso, Sho muestro una de tantas.

Cualquier consulta mi correo es areyes84@hotmail.com ....

La documentacion siempre se ira actualizando... y veremos si se puede hacer en github.

```yaml
  IMPORTANTE: Se debe realizar la documentacion para este proyecto por parte de la celula o desarrollador.
```