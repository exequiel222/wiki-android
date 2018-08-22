## GitFlow
![](https://wac-cdn.atlassian.com/dam/jcr:61ccc620-5249-4338-be66-94d563f2843c/05%20(2).svg?cdnVersion=jo)

GitHub Flow es un flujo de trabajo branch-bassed que admite grandes equipos y proyectos donde las implementaciones se realizan con regularidad.
El [flujo de trabajo Gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) se publicó por primera vez  en una publicación de blog de gran prestigio en 2010 de [Vincent Driessen en nvie](https://nvie.com/posts/a-successful-git-branching-model/).

El flujo de trabajo de Gitflow define un modelo de ramificación estricto diseñado en torno a la versión del proyecto. Este flujo de trabajo asigna funciones muy específicas a diferentes ramas y define cómo y cuándo deberían interactuar. 

### 1 Ramas master y develop

El trabajo se organiza en dos ramas principales:

* Master
* Develop

En lugar de una sola rama master, este flujo de trabajo utiliza dos ramas para registrar el historial del proyecto. La rama master almacena el historial de versiones oficial, y la rama develop sirve como una rama de integración para las características. También es conveniente etiquetar todas las confirmaciones en la rama master con un número de versión.

### 1.1 Ramas Master

* Tiene todo el código que está actualmente en producción
* Cualquier commit que pongamos en esta rama debe estar preparado para subir a producción
* El release Manager es quien mergea este branch
* Cada vez que se incorpora código a master, tenemos una nueva versión.
* Hay una sola rama de este tipo y se la mantiene limpia segmentada por tags.

**Nota:**_Actualmente se ha discontinuado este branch en el proyecto Android-Checkout (no se el motivo)_

### 1.2 Ramas Develop

* Esta es la rama de desarrollo, allí estará todo el código que conformará la siguiente versión planificada del proyecto.
* Únicamente los desarrolladores autorizados a aprobar revisiones, mergean código nuevo sobre este branch.
* Hay una sola rama de este tipo, este branch debe estar estable ya que todo el equipo se nutrirá de este.

### 2 Ramas auxiliares
Además de estas dos ramas, se proponen las siguientes ramas auxiliares:

* Feature
* Release
* Hotfix

### 2.1 Ramas Features o de funciones

* Se originan siempre a partir de la rama develop.
* Se incorporan siempre a la rama develop.
* Nombre: Cualquiera que no sea master, develop, hotfix-* o reléase-*
* Puede haber tantas ramas de features como sean necesarias

Estas ramas se utilizan para desarrollar nuevas características de la aplicación que, una vez terminadas, se incorporan a la rama develop.
Cualquier bug o nueva funcionalidad que se valla a implementar, se debe realizar sobre una nueva rama de este tipo.

**Nota:** _En Android-Checkout no subimos estas ramas al upstream, sino que las sincronizamos siempre contra nuestro repositorio forkeado_
 
### 2.2 Rama Hotfix

* Se origina a partir de la rama master
* Se implementan los hot-fix sobre la rama creada
* Se incorporan los cambios a la rama master y develop para tener todo sincronizado
* Nombre: hotfix-*

Estas ramas se utilizan para corregir errores y bugs en el código en producción o una vez que ya se ha freezado develop y corrido las pruebas de regresión (veremos estos conceptos más adelante). Funcionan de forma parecida a las Releases Branches, siendo la principal diferencia que los hotfixes no se planifican.
Una vez mergeado el fix a Master/Release el DeliveryManager se encargará de llevar este cambio a develop.
