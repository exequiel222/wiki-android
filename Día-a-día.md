### 1.1.5 Trabajo del día a día

En la copia local del desarrollador del repositorio bifurcado, pueden editar código, confirmar cambios y crear ramas como en otros flujos de trabajo de Git.
Sin embargo estos son los pasos a seguir para trabajar de manera correcta.

### 1.1.5 Cuidado no trabaje directamente sobre upstream

******************** Agregar tips para evitar problemas ***********

### 1.1.6 Manteniendo tu copia local al día

Siempre que desee actualizar su fork con los últimos cambios en la cadena ascendente, primero tendrá que buscar las ramas del repositorio en sentido ascendente y las últimas confirmaciones para llevarlas a su repositorio:
```shell
# Fetch from upstream remote
git fetch upstream

# View all branches, including those from upstream
git branch -va
```
Ahora, revise su propia rama maestra y fusione la rama principal del repositorio ascendente:
```shell
# Checkout your master branch and merge upstream
git checkout develop
git pull upstream develop
git merge upstream/develop
```
Si no hay compromisos únicos en la rama principal local, git simplemente realizará un avance rápido. Sin embargo, si ha estado realizando cambios en el upstream/develop (en la gran mayoría de los casos, probablemente no debería hacerlo), consulte la sección siguiente , puede que tenga que lidiar con conflictos. Al hacerlo, tenga cuidado de respetar los cambios realizados en el upstream.

Ahora, su branch develop local está actualizada con todo lo modificado anteriormente.

### 1.1.7 Crear una rama

Cada vez que comience a trabajar en una nueva funcionalidad o corrección de errores, es importante que cree una nueva rama. No solo es un flujo de trabajo de git adecuado, sino que también mantiene sus cambios organizados y separados de la rama principal para que pueda enviar y gestionar fácilmente múltiples solicitudes de extracción para cada tarea que complete.

Para crear una nueva rama y comenzar a trabajar en ella:

```shell

# Checkout the develop branch - you want your new branch to come from develop
git checkout develop

# Create a new branch named newfeature (give your branch its own simple informative name)
git branch newfeature

# Switch to your new branch
git checkout newfeature

```

### 1.1.8 Limpiando su trabajo

Antes de enviar su solicitud de extracción, es posible que desee hacer algunas cosas para limpiar su sucursal y hacerla lo más simple posible para que el mantenedor del repositorio original pruebe, acepte y combine su trabajo.

Si se han realizado confirmaciones en la rama maestra aguas arriba, debe volver a establecer la base de su rama de desarrollo para que la fusión sea un avance rápido que no requiera ningún trabajo de resolución de conflictos.

```shell

# Recuperar master upstream y fusionar con la rama maestra de su repositorio 
git fetch upstream
git checkout master
git merge upstream / master # Si hubo nuevos commits, rebase su rama de desarrollo 
git checkout novedad
git rebase master
```

Ahora, puede ser conveniente reducir algunas de sus asignaciones más pequeñas a una pequeña cantidad de compromisos más grandes y más cohesivos. Puedes hacer esto con una rebase interactiva:

```shell
# Rebase todos los commits en su rama de desarrollo 
git checkout
git rebase -i master
```
Esto abrirá un editor de texto donde puedes especificar qué commits aplastar.

### 1.1.8 Verifica tu código corriendo el check estático

****** Mantén a travis verde *******

### 1.1.8 Enviando tus cambios

Una vez que haya confirmado y enviado todos sus cambios a GitHub, vaya a la página de su tenedor en GitHub, seleccione su rama de desarrollo y haga clic en el botón de solicitud de extracción. Si necesita hacer algún ajuste a su solicitud de extracción, simplemente envíe las actualizaciones a GitHub. Su solicitud de extracción rastreará automáticamente los cambios en su rama de desarrollo y la actualizará.

```Shell
# Enviamos los cambios y preparamos el PullRequest
git push origin develop
```

### 1.1.8 Sobre los tamaños de los PullRequest

****** Hablar del tamaño del pr y como gestionar pr dependientes *******

### 1.1.8 Enviando múltiples PullRequest a revisión

****** Hablar del tamaño del pr y como gestionar pr dependientes *******

### 1.1.9 Creando el PullRequest desde Github

****** Mostrar como hacer el PullRequest par Checkout *******

### 1.1.9 Asigna revisores y deja comentarios

Al usar el sistema @mention de GitHub en su mensaje de solicitud de extracción, puede solicitar comentarios de personas o equipos específicos.
****** Dejar ejemplos *******

### 1.1.9 Discute y revisa tu código

Una vez que se ha abierto una Solicitud de extracción, la persona o el equipo que revisa sus cambios puede tener preguntas o comentarios. Tal vez el estilo de codificación no coincida con las directrices del proyecto, al cambio le faltan pruebas unitarias, o tal vez todo se ve bien y los accesorios están en orden. Las solicitudes de extracción están diseñadas para alentar y capturar este tipo de conversación.

También puede seguir presionando a su sucursal a la luz de la discusión y comentarios sobre sus compromisos. Si alguien comenta que olvidó hacer algo o si hay un error en el código, puede solucionarlo en su sucursal y hacer subir el cambio. GitHub mostrará tus nuevas confirmaciones y cualquier comentario adicional que recibas en la vista de Solicitud de extracción unificada.

****** Enseñar como hacer esto *******

### 1.1.9 Corrije tu código y sube las correcciones

****** Código git para hacer esto *******
** ¿Que pasa si alguien subió algún commit en medio de este proceso?

### 1.1.9 Mergear tu código contra el develop/Central
****** Mostrar como hacer esto *******