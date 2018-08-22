## 1.1 Forking workflow

En lugar de utilizar un único repositorio del lado del servidor para actuar como la base de código "central", se le da a cada desarrollador un repositorio del lado del servidor. Esto significa que cada colaborador no tiene uno, sino dos repositorios Git: uno privado del lado del servidor asociado a su cuenta, y otro también del lado del servidor pero asociado a la cuenta del dueño del proyecto central. 

La principal ventaja del flujo de trabajo de Forking es que las contribuciones pueden integrarse sin la necesidad de que todos accedan a un único repositorio central. Los desarrolladores acceden a sus propios repositorios del lado del servidor, y solo el mantenedor/dueño del proyecto puede acceder al repositorio oficial. Esto le permite al mantenedor aceptar `commits` de cualquier desarrollador sin darles acceso de escritura a la base de código oficial.
**Nota:** _En el caso de checkout todos sus miembros tienen permisos de escritura `push` por lo que veremos luego como manejar esta situación._

El flujo de trabajo de Forking generalmente sigue un modelo de bifurcación basado en el flujo de trabajo de Gitflow . Esto significa que las ramas de características completas se diseñarán para fusionarse en el repositorio del desarrollador original del proyecto (Repositorio oficial).

### 1.1.2 Como funciona?

Al igual que en los otros flujos de trabajo de Git , Forking Workflow comienza con un repositorio oficial almacenado en un servidor (muchas veces llamado repositorio central). Pero cuando un nuevo desarrollador desea comenzar a trabajar en el proyecto, no clona directamente el repositorio oficial.

En su lugar, bifurcan (forkean) el repositorio oficial para crear una copia del mismo en otra cuenta del lado del servidor. Esta nueva copia sirve para el desarrollador como su repositorio personal: ningún otro desarrollador puede `pushear` allí, pero puede realizar `pull-request` (veremos por qué esto es importante en un momento). Después de que hayan creado su copia del lado del servidor, el desarrollador realiza un `git clone` de este repositorio para obtener una copia en su máquina local. Esto sirve como su entorno de desarrollo privado.

Cuando están listos para publicar un `commit` local, envían el `commit` a su propio repositorio remoto, no el oficial. Luego, presentan un `pull-request` contra el repositorio oficial, lo que permite que el mantenedor del proyecto sepa que una actualización está lista para integrarse. El `pull-request` también sirve como un hilo de discusión conveniente si hay problemas con el código contribuido. El siguiente es un ejemplo paso a paso de este flujo de trabajo.

1. Un desarrollador "bifurca" un repositorio "oficial" del lado del servidor. Esto crea su propia copia del lado del servidor.
2. La nueva copia del lado del servidor está clonada en su sistema local.
3. Se agrega una ruta remota de Git para el repositorio "oficial" al clon local.
4. Se crea una nueva rama de características locales.
5. El desarrollador realiza cambios en la nueva rama.
6. Se crean nuevas confirmaciones para los cambios.
7. La rama se empuja a la propia copia del lado del servidor del desarrollador.
8. El desarrollador abre una solicitud de extracción de la nueva sucursal al depósito 'oficial'.
9. La solicitud de extracción se aprueba para fusionarse y se fusiona en el repositorio original del lado del servidor.
 
Para integrar la función en la base de código oficial, el mantenedor extrae los cambios del contribuyente en su repositorio local, comprueba para asegurarse de que no rompe el proyecto, lo fusiona en su master branch local y luego pushea la master rama al repositorio oficial en el servidor . La contribución ahora es parte del proyecto, y otros desarrolladores deben extraer del repositorio oficial para sincronizar sus repositorios locales.

Es importante entender que la noción de un repositorio "oficial" en el flujo de trabajo de Forking es meramente una convención. De hecho, lo único que hace que el repositorio oficial sea tan oficial es que es el depósito público del mantenedor del proyecto.

### 1.1.3 Forkeando un repositorio

Todos los nuevos desarrolladores de un proyecto deben Forkear el repositorio oficial.
Como se dijo anteriormente el fork es solo un git clone estándar. Nosotros lo haremos usando la herramienta Github que nos automatiza el proceso, como se detalla a continuación.

* Accedemos a nuestra cuenta en github (previamente es necesario tener acceso al repositorio privado)
* Ingresamos a la página principal del repositorio que quereos forkear
* Realizamos el fork
* Ingresamos a nuestro repositorio forkeado.

************************ Agregar capturas ************************

### 1.1.3 Clona tu fork

Ahora necesitas clonar tu propio repositorio forkeado.
(Nota que previamente debes haber seteado todas las credenciales de git)
Nos paramos sobre el directorio donde queremos almacenar el código y aplicamos el siguiente comando:

```shell
 $ git clone https://user@bitbucket.org/user/repo.git
```

### 1.1.4 Agregamos un control remoto

Mientras que otros flujos de trabajo de Git utilizan un único control remoto de origen que apunta al repositorio central, Forking Workflow requiere dos controles remotos, uno para el repositorio oficial y otro para el repositorio personal del lado del servidor del desarrollador (comúnmente llamado origin). Si bien puede llamar a estos controles remotos como quiera, una convención común es usar `origin` como el control remoto para su repositorio bifurcado (esto se creará automáticamente cuando se ejecute git clone) y `upstream` para el repositorio oficial.

```shell
 $ git remote add upstream https://user@bitbucket.org/maintainer/repo.git

 # Verificar el nuevo control remoto llamado 'upstream' ```
 $ git remote -v
```