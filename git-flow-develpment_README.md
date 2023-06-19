<h1>
    Git Flow
    <img height="25" alt="typescript"
        src="https://raw.githubusercontent.com/danielcranney/readme-generator/main/public/icons/skills/git-colored.svg">
</h1>

<img src="https://wac-cdn.atlassian.com/dam/jcr:c2e5ef87-1dde-4a5f-8f4d-c1edc9978e86/Workflow-hero.svg?cdnVersion=1042" alt="imgage" width="50%" height="50%">

<h1>VoiceTeam Developers Workflow</h1>

<span color="white">The Git stream needs to be initialized to customize your project settings.</span>

<span>
    <h2>Flow Branch</h2>
    <ul>
        <li>
            <p><code color="white">feature</code> inicio de una nueva tarea o functionalidad </p>
        </li>
        <li>
            <p><code color="white">develop</code> rama donde se va a desarrollar el proyecto</p>
        </li>
        <li>
            <p><code color="white">realease</code> asignacion de version del proyecto</p>
        </li>
        <li>
            <p><code color="white">Master</code> rama de production donde el proyecto esta en su maximo desarrollo</p>
        </li>
        <li>
            <p><code color="white">hotfix</code> manejo de errores que suceden en produccion que su gravedad es
                instantanea</p>
        </li>
    </ul>
</span>

<h2 align="left">Initialize</h2>
<p>Start using git-flow by initializing it inside an existing git repository:</p>

> git flow init

<p>
    You'll have to answer a few questions regarding the naming conventions for your branches.
    It's recommended to use the default values.
</p>

<h2 align="left">Start a new feature</h2>
<p>
    * Development of new features starting from the 'develop' branch.
    * Start developing a new feature with.
</p>

`is strict to name (feature) for create a feature flow`

> git branch feature/(FEATURENAME)

> git flow feature start (FEATURENAME)

<span>This action creates a new feature branch based on 'develop' and switches to it</span>

<code color="white">FEATURE NAME STRIC MODE:</code>
the name of the feature will refer to the tickt created in jira.
`Example: VI-000`

<code color="white">STRIC MODE:</code>
all features must be removed from developer to follow the correct flow.

si esta trabajando en un feature example: feature/VI-001 y tiene un feature/VI-002 y el mismo depende de los cambios que
usted tiene en el feature/VI-001 esto es lo que se debe hacer o lo recomendable para mantener el flujo de trabajo:

> saque su feature/VI-002 de developer y haga un merge del feature/VI-001 en su feature/VI-002 y asi no afectaria al
flujo, no es lo mas recomendable porque si hay un proceso de <code>CODE REVIEW</code> efectivo en este caso una persona
que este a la disposicion de QA, que es la que haria el proceso de verificar que el ticket o en este caso el feature
cumpla con los requerimientos tanto del cliente, como los parametros establecidos por el desarrollo en codigo; no se deberia hacer
este merge pero en caso de no ser asi puede hacer el merge del feature que necesite en su actual feature que dependa de
esos cambios para usted poder avanzar en su respectivo trabajo.

<h2 align="left">Finish up a feature</h2>
<div>
    <ul>
        <h3>Push the feature origin:</h3>
        <code color="white">COMAND:</code> git push origin feature/(FEATURENAME) <br />
        <h3> para que un feature finalice por completo y complete el flujo, debe pasar por los estandares que ya
            tenemos en el equipo de desarrollo:</h3>
        <li>
            <p>se debe crear el respectivo pull request de esa feature.</p>
        </li>
        <li>
            <p>debe pasar el proceso de <code>CODE REVIEW</code>.</p>
        </li>
        <li>
            <p>
                si el feature no tuvo ningun error y todo estubo bien este pasaria a merge por la persona encargada, la misma
                mezclara ese feature a la rama de desarrollo en este caso (developer).
            </p>
        </li>
        <li>
            <p>
                pero si el feature tuvo inconvenientes o necesita de alguna modificacion para poder avanzar pasara a
                <code>CHANGE REQUESTED</code>, al mismo no se le haria merge sino que permanecera abierto el pull
                request
                hasta que se hagan los cambios respectivos y se haga de nuevo la revicion de codigo.
            </p>
        </li>
        <li>
            <p>
                Cuando el feature pase las dos especificaciones el mismo permanecera en el proyecto como referencia
                hasta que se haga el realease respectivo a la version de ese release.
            </p>
        </li>
    </ul>

</div>

<h3>Finish the development of a feature. following commands:</h3>
<div>
    <p>Para eliminar una rama de nuestro repositorio local ejecutaremos el siguiente comando:</p>

    > git branch -d nombre_rama

</div>

<div>
    <p>En el caso de que esa rama contenga trabajos sin fusionar, el comando anterior nos devolverá el siguiente error:
    </p>

    > error: The branch 'nombre-rama' is not an ancestor of your current HEAD.
    If you are sure you want to delete it, run 'git branch -D nombre-rama'.

</div>

<div>
    <p>Si aún así queremos eliminar esa rama, se puede forzar el borrado de la siguiente manera:</p>

    > git branch -D nombre-rama

</div>

<div>
    <p>En el caso de querer eliminar una rama del repositorio remoto, la sintaxis será la siguiente:</p>

    > git push origin :nombre-rama <br/>

    > git push origin --delete nombre-de-rama

</div>


<h2 align="left">Start a new release</h2>
<img src="https://wac-cdn.atlassian.com/dam/jcr:8f00f1a4-ef2d-498a-a2c6-8020bb97902f/03%20Release%20branches.svg?cdnVersion=1042" alt="imgage" width="50%" height="50%">

Cuando develop haya adquirido suficientes funciones para una publicación (o se acerque una fecha de publicación predeterminada), debes bifurcar una rama release (o de publicación) a partir de develop. Al crear esta rama, se inicia el siguiente ciclo de publicación, por lo que no pueden añadirse nuevas funciones una vez pasado este punto (en esta rama solo deben producirse las soluciones de errores, la generación de documentación y otras tareas orientadas a la publicación). Cuando está lista para el lanzamiento, la rama release se fusiona en main y se etiqueta con un número de versión. Además, debería volver a fusionarse en develop, ya que esta podría haber progresado desde que se iniciara la publicación.

* init release con y sin la extencion de git flow

Sin las extensiones de git-flow:
> git checkout develop 

> git checkout -b release/0.1.0

Cuando se utilizan las extensiones de git-flow:
> git flow release start [version]

> message: Switched to a new branch 'release/0.1.0'


En cuanto la publicación esté lista para su lanzamiento, se fusionará en las ramas <code>main</code> y <code>develop</code>, y luego se eliminará la rama <code>release</code>. Es importante volver a fusionarla en la rama <code>develop</code> porque podrían haberse añadido actualizaciones importantes a la rama <code>release</code>, y las funciones nuevas tienen que poder acceder a ellas. Si en tu organización se da mucha importancia a la revisión de código, este sería el lugar ideal para una solicitud de incorporación de cambios.


<h3>To finalize a branch version, use the following methods:</h3>

Sin las extensiones de git-flow:
> git checkout main

> git merge release/0.1.0

con la extensión de git-flow:
> git flow release finish '0.1.0'


<h2 align="left">Start a new hotfix</h2>
<img src="https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=1042" alt="imgage" width="50%" height="50%">


Las ramas de mantenimiento, de corrección o de <code>hotfix</code> sirven para reparar rápidamente las publicaciones de producción. Las ramas <code>hotfix</code> son muy similares a las ramas <code>release</code> y <code>feature</code>, salvo por el hecho de que se basan en la rama main y no en la develop. Esta es la única rama que debería bifurcarse directamente a partir de main. Cuando se haya terminado de aplicar la corrección, debería fusionarse en <code>main</code> y <code>develop</code> (o la rama <code>release</code> actual), y main debería etiquetarse con un número de versión actualizado.

Tener una línea de desarrollo específica para la corrección de errores permite que tu equipo aborde las incidencias sin interrumpir el resto del flujo de trabajo ni esperar al siguiente ciclo de publicación. Puedes concebir las ramas de mantenimiento como ramas <code>release</code> ad hoc que trabajan directamente con la rama <code>main</code>. 


<h3>A new hotfix branch can be created using the following methods:</h3>

Sin las extensiones de git-flow:

> git checkout main

> git checkout -b hotfix_branch

Cuando se utilizan las extensiones de git-flow:

> git flow hotfix start hotfix_branch

Al igual que al finalizar una rama release, una rama hotfix se fusiona tanto en main como en develop.

> git checkout main

> git merge hotfix_branch

> git checkout develop

> git merge hotfix_branch

> git branch -D hotfix_branch

> git flow hotfix finish hotfix_branch

<h2 align="left">Version Controller</h2>
<br>
<br>
<br>


<h2 align="left">Comentarios stric mode</h2>

<img src="https://imgs.xkcd.com/comics/git_commit_2x.png" alt="imgage" width="50%" height="50%">
<br>
<br>
<br>

Sé que muchas veces estamos tentados a escribirlo en pasado “Added…”, “Fixed…” o “Removed…” pero cada commit hay que
entenderlo como una instrucción para cambiar el estado del proyecto. Dicho de otro modo, el verbo presente nos permite
saber qué estado queremos que el proyecto se encuentre en el momento de añadir el commit.

Lo mejor es que el mensaje del commit complete esta frase: “Si aplico este commit, entonces este commit…”

…add a new search feature <br>
…fix a problem with the topbar <br>
…change the default system color <br>
…remove a random notification




<h3 align="left">Best Practice comment</h3>



> [SCOPE] (TASKNAME): ([tipo-de-cambio] descripcion)

<code color="white"><b>[SCOPE]:</b></code> va hacer el tipo de scope que se va a realizar dependiendo el task.

<code color="white"><b>tipo-de-cambio:</b></code> es la accion que hicimos, ejemplo: add, change, replace, rename,
update etc.

<code color="white"><b>(TASKNAME):</b></code> nombre del ticket, ejemplo: VI-167

<code color="white"><b>descripcion:</b></code> lo que hicimos en el task algo entendible y claro para que el QA pueda
interpretar y saber lo que hicimos en ese feature.

<code color="white"><b>Ejmeplos: </b></code>

> feat(VI-167): add the filter for the client grind on the supervisor employe info

> feat(VI-456): add filter for cars

> fix(VI-764): remove wrong color

<div>
    <h3>following the steps in to your comments [SCOPE]</h3>
    <ul>
        <li>
            <p><code color="white"><b>feat</b></code>: Una nueva característica para el usuario.</p>
        </li>
        <li>
            <p><code color="white"><b>fix</b></code>: Arregla un bug que afecta al usuario.</p>
        </li>
        <li>
            <p><code color="white"><b>perf</b></code>: Cambios que mejoran el rendimiento del sitio.</p>
        </li>
        <li>
            <p><code color="white"><b>build</b></code>: Cambios en el sistema de build, tareas de despliegue o
                instalación.</p>
        </li>
        <li>
            <p><code color="white"><b>ci</b></code>: Cambios en la integración continua. </p>
        </li>
        <li>
            <p><code color="white"><b>docs</b></code>: Cambios en la documentación.</p>
        </li>
        <li>
            <p><code color="white"><b>refactor</b></code>: Refactorización del código como cambios de nombre de
                variables o funciones.</p>
        </li>
        <li>
            <p><code color="white"><b>style</b></code>: Cambios de formato, tabulaciones, espacios o puntos y coma, etc;
                no afectan al usuario.</p>
        </li>
        <li>
            <p><code color="white"><b>test</b></code>: Añade tests o refactoriza uno existente.</p>
        </li>
    </ul>
</div>



<h2>Example Flow</h2>

A continuación, se incluye un ejemplo completo que demuestra un flujo de ramas de función. Vamos a suponer que tenemos una configuración del repositorio con una rama <code color="white">main</code>.

> git checkout main <br>
> git checkout -b develop <br>
> git checkout -b feature_branch <br>

<h2>work happens on feature branch</h2>

> git checkout develop <br>
> git merge feature_branch <br>
> git checkout main <br>
> git merge develop <br>
> git branch -d feature_branch <br>


<h2>In addition to the feature and release flow, here is an example of a hotfix:</h2>

> git checkout main <br>
> git checkout -b hotfix_branch <br>

<h2>work is done commits are added to the hotfix_branch</h2>

> git checkout develop <br>
> git merge hotfix_branch <br>
> git checkout main <br>
> git merge hotfix_branch <br>


<h2>Summary</h2>

En este artículo, hemos explicado el flujo de trabajo de Gitflow. Gitflow es uno de los muchos estilos de [flujos de trabajo de Git:](https://www.atlassian.com/es/git/tutorials/comparing-workflows) que podéis utilizar tu equipo y tú.

<h3>Algunos puntos clave que debes saber sobre Gitflow son los siguientes:</h3>

<ul>
    <li>
        <p>Este flujo de trabajo es ideal para los flujos de trabajo de software basados en publicaciones.</p>
    </li>
    <li>
        <p>Gitflow ofrece un canal específico para las correcciones de producción.</p>
    </li>
</ul>

<h2>El flujo a seguir en el departamento de developer VoiceTeam es el sigueinte:</h2>

<ul>
    <li>
        <p>Se crea una rama <code color="white">develop</code> a partir de <code color="white">main</code>.</p>
    </li>
    <li>
        <p>Se crea una rama <code color="white">release</code> a partir de la <code color="white">develop</code>.</p>
    </li>
    <li>
        <p>Se crean ramas <code color="white">feature</code> a partir de la <code color="white">develop</code>.</p>
    </li>
    <li>
        <p>Cuando se termina una rama <code color="white">feature</code>, se fusiona en la rama <code color="white">develop</code>.</p>
    </li>
    <li>
        <p>Cuando la rama release está lista, se fusiona en las ramas <code color="white">develop</code> y <code color="white">main</code>.</p>
    </li>
    <li>
        <p>Si se detecta un problema en <code color="white">main</code>, se crea una rama <code color="white">hotfix</code> a partir de <code color="white">main</code>.</p>
    </li>
    <li>
        <p>Una vez terminada la rama <code color="white">hotfix</code>, esta se fusiona tanto en <code color="white">develop</code> como en <code color="white">main</code>.</p>
    </li>
</ul>

<br/>
<br/>
<br/>
<br/>

## Learn more about Git Flow

* [learn Documentation to git flow:](https://danielkummer.github.io/git-flow-cheatsheet/)

## Learn more about Buenas Practicas para hacer los commits

* [Buenas prácticas para escribir commits:](https://midu.dev/buenas-practicas-escribir-commits-git/)

## Learn more about gitflow workflow

* [learn Documentation to gitflow workflow:](https://www.atlassian.com/es/git/tutorials/comparing-workflows/gitflow-workflow)

## A continuación, aprende a usar el:

[flujo de trabajo de bifurcación](https://www.atlassian.com/es/git/tutorials/comparing-workflows/forking-workflow)

## Comparar flujos de trabajo

* [Comparar flujos de trabajo](https://www.atlassian.com/es/git/tutorials/comparing-workflows)

## Gitflow Workflow

* [Gitflow Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

## Comandos de Git

* [Comandos de Git](https://gist.github.com/dasdo/9ff71c5c0efa037441b6)