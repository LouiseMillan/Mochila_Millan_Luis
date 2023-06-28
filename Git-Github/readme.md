# Cheat Sheet (Hoja de trucos)

## **Ayuda**
Use este comando para obtener información fácilmente sobre todos los comandos que conoce hasta ahora y más.

Recuerde que cada comando incluye también su propia página de ayuda. Para encontrar estas páginas de ayuda, escriba `git <command> --help`. Por ejemplo, `git commit --help` muestra una página que proporciona más información sobre el comando git commit y cómo usarlo.
```
    git help
    git add help
    git init help
    git commit help
```  
<br/>


## **Versión**
Muestra la versión de git instalado, si no responde indica que no esta instalada ninguna version.
```
    git --version
```  
<br/>

## **Establecer usuario / email**
Para configurar Git, debe definir algunas variables globales: user.name y user.email. Ambas son necesarias para realizar confirmaciones.

Establezca su nombre en con el siguiente comando. Reemplace `<USER_NAME>` por el nombre de usuario que quiere usar.
```
    git config --global user.name "<USER_NAME>"
```
Se puede onitir `--global` pero se tendra que usar cuando sea necesario cada vez.

Ahora, use este comando para crear una variable de configuración user.email; para ello, reemplace `<USER_EMAIL>` por su dirección de correo electrónico:
```
    git config --global user.email "<USER_EMAIL>"
```

Ejecute el siguiente comando para comprobar que los cambios han funcionado:
```
    git config --list
```
Confirme que la salida incluye dos líneas similares al siguiente ejemplo. El nombre y la dirección de correo electrónico serán distintos a los que se muestran en el ejemplo.
```
    user.name=User Name
    user.email=user-name@contoso.com
```  
<br/>

## **Configuración del repositorio de Git**
Tras crear la carpeta de trabajo, que se convierte en el directorio del proyecto. El directorio del proyecto es donde se almacenan todos los archivos relacionados con el proyecto.  
<br/>

### **Inicializar el nuevo repositorio y establezca el nombre de la rama predeterminada en main**

Solo si está ejecutando la versión 2.28.0 o una posterior de Git, use el comando siguiente:
```
    git init --initial-branch=main
```
O bien, use el siguiente comando:
```
    git init -b main
```
En cualquier versión use:
```
    git init
    git checkout -b main
```
O para usar la rama por defecto, simplemente:
```
    git init
```  
<br/>

## **Cambios**
El primer comando de Git, y el que se usa con más frecuencia.

Muestra el estado del árbol de trabajo (y del área de almacenamiento provisional). Permite ver los cambios que Git está siguiendo en ese momento para poder decidir si quiere pedir a Git que tome otra instantánea.
```
    git status
```  
<br/>

## **Seguimiento**
Comando que se usa para indicar a Git que empiece a realizar un seguimiento de los cambios en determinados archivos
```
    git add <DIRECTORIO / ARCHIVO(S)>

    git add .

    git add file.css

    git add *.php
```
El término técnico es almacenamiento provisional de estos cambios. Va a usar `git add` para almacenar **provisionalmente** los cambios a fin de prepararse para una confirmación. Todos los cambios en los archivos que se han agregado pero que aún no se han confirmado se almacenan en el área de almacenamiento provisional.  
<br/>

### **Eliminar el seguimiento**  
```
    git rm <ARHIVO>
```

Para eliminar un directorio y los archivos que contiene:
```
    git rm -r <DIRECTORIO>
```
<br/>

## **Guardar el progreso**
Después de haber almacenado provisionalmente algunos cambios para su confirmación, puede guardar el trabajo en una instantánea si invoca al comando:
```
    git commit -m "<MENSAJE>"
```

**Confirmar** (o "commit") es un verbo y un sustantivo. Básicamente tiene el mismo significado que cuando se confirma en un plan o se confirma un cambio en una base de datos. Como verbo, la confirmación de cambios significa que se coloca una copia (del archivo, el directorio u otra "cosa") en el repositorio como una nueva versión. Como sustantivo, una confirmación es el pequeño fragmento de datos que asigna una identidad única a los cambios que se confirman. Los datos que se guardan en una confirmación incluyen el nombre del autor y la dirección de correo electrónico, la fecha, los comentarios sobre lo que se ha hecho (y por qué), una firma digital opcional y el identificador único de la confirmación anterior.

Otra forma de usar este comando es:
```
    git commit -a -m "<MENSAJE>"
```
Observe que esta vez no se ha ejecutado el comando `git add` para almacenar provisionalmente los cambios. En su lugar, usamos la marca `-a` en el comando `git commit`. La opción `-a` agrega todos los archivos que se han modificado desde la última confirmación. No agregará archivos nuevos. Para agregar nuevos archivos, se sigue necesitando `git add`.  
<br/>

## **Historial**
```
    git log
```
El comando `git log` permite ver información sobre las confirmaciones (commit) anteriores. Cada confirmación tiene un mensaje adjunto (un mensaje de confirmación), y el comando `git log` permite imprimir información sobre las confirmaciones más recientes, como su marca de tiempo, el autor y un mensaje de confirmación. Este comando ayuda a realizar un seguimiento de lo que ha estado haciendo y de los cambios que se han guardado.

Historial de un archivo especifico:
```
    git log --<ruta del archivo>
```
Historial de un usuario en particular:
```
    git log --author=<usuario>
```

<br/>

## **Cambios en archivos**
Use un comando `git diff` para ver lo que ha cambiado:
```
    git diff
```
El formato de salida es el mismo que el del comando `diff` de Unix, y el comando de Git tiene muchas de las mismas opciones. Aparece un signo "más" delante de las líneas que se han agregado, y un signo "menos" indica las líneas que se han eliminado.

El valor predeterminado para comparar el árbol de trabajo con el índice es `git diff`. Es decir, muestra todos los cambios que aún no se han almacenado provisionalmente (agregado al índice de Git). Para comparar el árbol de trabajo con la última confirmación, puede usar `git diff HEAD`.

Si el comando no vuelve al símbolo del sistema después de ejecutarse, escriba q para salir de la vista de diferencias.  
<br/>

## **Ramas**
Las ramas de Git son un puntero eficaz para las instantáneas de tus cambios. Cuando quieres añadir una nueva función o solucionar un error, independientemente de su tamaño, generas una nueva rama para alojar estos cambios. Esto hace que resulte más complicado que el código inestable se fusione con el código base principal, y te da la oportunidad de limpiar tu historial futuro antes de fusionarlo con la rama principal.
### **Listar**
Para listar las ramas existentes y la rama activa se usa:
```
    git branch

    git branch --list
```
Listar todas las ramas remotas.
```
    git branch -a
```
### **Cambiar rama principal**
La rama principal en algunos casos se llama `Master` de ser necesario (como en github) se puede cambiar usando:
```
    git branch -M <nombre de la rama>

    git branch -M main
```
### **Crear**
Para crea una nueva rama llamada ＜branch＞. Este comando no extrae la nueva rama.
```
    git branch <branch>
```
### **Eliminar**
Elimina la rama especificada. Esta es una operación segura, ya que Git evita que elimines la rama si tiene cambios que aún no se han fusionado.
```
    git branch -d <branch>
```
**Fuerza la eliminación** de la rama especificada, incluso si tiene cambios sin fusionar. Este comando lo puedes usar si quieres eliminar de forma permanente todas las confirmaciones asociadas con una línea concreta de desarrollo.
```
    git branch -D <branch>
```
### **Cambia el nombre**
Para cambia el nombre de la rama actual a ＜branch＞.
```
    git branch -m <branch>
```
### **Cambiar de rama**
Para Cambiar de rama el comando `git checkout` te permite desplazarte entre las ramas creadas por git branch. Al extraer una rama, se actualizan los archivos en el directorio de trabajo para reflejar la versión almacenada en esa rama y se indica a Git que registre todas las confirmaciones nuevas en dicha rama. Puedes contemplar todo esto como una forma de seleccionar la línea de desarrollo en la que trabajas.
```
    git checkout <branch>
```
También puede usarse el comando `switch` obteniendo el mismo resustado.
```
    git switch <branch>
```

### **Crear y cambiar de rama**
El comando git checkout se usa habitualmente junto con `git branch`. El comando `git branch` permite crear una rama nueva. Si quieres empezar a trabajar en una nueva función, puedes crear una rama nueva a partir de la rama `main` con `git branch new_branch`. Una vez creada, puedes usar `git checkout new_branch` para cambiar a esa rama. Además, el comando `git checkout` acepta el argumento `-b`, que actúa como un práctico método que creará la nueva rama y cambiará a ella al instante.
```
    git checkout -b <new_branch>
```
De manera predeterminada, `git checkout -b` basará la rama `new-branch` en el `HEAD` actual. No obstante, `git checkout` puede combinarse con un parámetro opcional para ramas adicionales. Se añade `<existing-branch＞`, que basa `new-branch` en `existing-branch` y no en el `HEAD` actual.
```
    git checkout -b ＜new-branch＞ ＜existing-branch＞
```  
<br/>

## **Fusión de ramas**
La fusión es la forma que tiene Git de volver a unir un historial bifurcado. El comando `git merge` permite tomar las líneas independientes de desarrollo creadas por `git branch` e integrarlas en una sola rama.

`git merge` combinará varias secuencias de confirmaciones en un historial unificado. En los casos de uso más frecuentes, `git merge` se utiliza para combinar dos ramas.

En estos casos, git merge toma dos punteros de confirmación, normalmente los extremos de la rama, y encuentra una confirmación base común entre ellos. Una vez que Git encuentra una confirmación base en común, crea una "confirmación de fusión" nueva que combina los cambios de cada secuencia de confirmación de fusión puesta en cola.

Antes de ejecutar una fusión, hay un par de pasos de preparación que llevar a cabo con el fin de garantizar que la fusión se realice sin problemas.

Ejecuta git statuspara asegurarte de que HEAD apunte a la rama de fusión-recepción correcta. En caso necesario, ejecuta `git checkout` para cambiar a la rama de recepción. En este caso, se ejecuta `git checkout main`.

Asegúrate de que la rama de recepción y la rama de fusión están **actualizadas** con los cambios remotos más recientes.

Una vez adoptados los pasos comentados anteriormente de "preparación para la fusión", se puede iniciar una fusión ejecutando git merge donde  es el nombre de la rama que se fusionará con la rama de recepción.

```
# Se inicia una nueva funcionalidad
    git checkout -b new-feature main
# Se editan algunos archivos
    git add <file>
    git commit -m "Start a feature"
# Se editan mas archivos
    git add <file>
    git commit -m "Finish a feature"
```
```
# Se fuciona la rama main con la rama new-feature
    git checkout main
    git merge new-feature
```  
<br/>

# **Uso de repositorios remotos**
El comando git remote te permite crear, ver y eliminar conexiones con otros repositorios. Las conexiones remotas se asemejan más a marcadores que a enlaces directos con otros repositorios. En lugar de brindar acceso en tiempo real a otro repositorio, funcionan como nombres prácticos que pueden emplearse para hacer referencia a una URL no tan sencilla.  
<br/>

## **Visualizar conexiones**
Para ver las conexiones remotas que se tienen con otros repositorios se usa el comando:
```
    git remote
```
Lo mismo que el comando anterior, pero incluye la URL de cada conexión.
```
    git remote -v
```  
<br/>

## **Creación de configuración de `git remote`**
Para vincular un repositorio remoto como github se usa el mismo comando `remote` pero se agrega la dirección de dicho repositorio remoto, quiza sea necesario identificarse para usar dicho repositorio.

Crea una nueva conexión a un repositorio remoto. Tras añadir el repositorio remoto, podrás usar ＜name＞ como un práctico atajo para ＜url＞ en otros comandos de Git.
```
    git remote add <name> <url>

    git remote add origin <url>

    git remote add origin https://github.com/XXX/mirepositorio.git

    git remote add john http://dev.example.com/john.git
```  
<br/>

## **Eliminación de configuración de `git remote`**
Elimina la conexión con el repositorio remoto que lleva el nombre ＜name＞
```
    git remote rm <name>
```  
<br/>

## **Cambiar nombre de conexión**
Cambia el nombre de una conexión remota de ＜old-name＞ a ＜new-name＞.
```
    git remote rename <old-name> <new-name>
```  
<br/>

## **Cargar contenido al repositorio remoto**
El comando `git push` se usa para cargar contenido del repositorio local a un repositorio remoto. El envío es la forma de transferir confirmaciones desde tu repositorio local a un repositorio remoto. 

Envía la rama especificada a una , junto con todos los commits y objetos internos necesarios. De este modo se crea una rama local en el repositorio de destino.
```
    git push <remote> <branch>

    git push origin main
```  
<br/>

## **Descargar contenido del repositorio remoto**
El comando `git pull` se emplea para extraer y descargar contenido desde un repositorio remoto y actualizar al instante el repositorio local para reflejar ese contenido. La fusión de cambios remotos de nivel superior en tu repositorio local es una tarea habitual de los flujos de trabajo de colaboración basados en Git. El comando `git pull` es, en realidad, una combinación de dos comandos, `git fetch` seguido de `git merge`. En la primera etapa de la operación `git pull` ejecutará un `git fetch` en la rama local a la que apunta `HEAD`. Una vez descargado el contenido, `git pull` entrará en un flujo de trabajo de fusión. Se creará una nueva confirmación de fusión y se actualizará `HEAD` para que apunte a la nueva confirmación.

Recupera la copia del origen remoto especificado de la rama actual y fusiónala de inmediato en la copia local. Esto equivale a `git fetch ＜remote＞` seguido de `git merge origin/＜current-branch＞`.
```
    git pull <remote>

    git pull <remote> <branch>

    git pull origin main
```  
<br/>
