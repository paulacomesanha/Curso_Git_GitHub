# Módulo 1: introducción a Git y control de versiones
## Objetivo
Entender que es Git, porqué se utiliza y cómo comenzar a trabajar con él en tu ordenador.

## ¿Qué es Git?
Git es un sistema de control de versiones distribuido. Esto significa que permite:
- Guardar versiones de tus archivos o proyectos.
- Volver a un estado anterior si algo sale mal.
- Trabajar en equipo sin sobreescribir el trabajo de otros.

📌 Piensa en Git como una "máquina del tiempo" para tu código.

## ¿Por qué usar Git?
- Controlar qué cambias, cuándo y por qué.
- Puedes experimentar sin miedo a romper nada.
- Facilita el trabajo en quipo sin conflictos.
- Es esencial en el mundo profesional del desarrollo y la ingeniería.

## ¿Qué es Github?
Github es una plataforma online donde puedes almacenar tus proyectos Git. Permite colaborar, revisar código y mantener repositorios públicos o privados..

📌 Git es la herramienta. GitHub es como “la nube” donde puedes compartir tu proyecto Git.

## Instalación de Git
- Windows
    1. Ve a [Git][https://git-scm.com/]
    2. Descarga el instalador.
    3. Durante la instalación, acepta las opciones por defecto (especialmente que use Git Bash).
- macOS

`brew install git`

- Linux (Debian/Ubuntu)

`sudo apt install git`

## Configuración inicial
Despues de instalar Git, abre la terminal (o Git Bash en Windows) y escribe:
```
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```
También puedes establecer el editor de texto por defecto (opcional):

`git config --global core.editor "code --wait" #Para usar VS Code`

Verifica la configuración:

`git config --list`

## Conceptos clave
|Término|Qué significa|
|---:|:---|
|Repositorio|proyecto con control de versional. Puede ser local o remoto|
|Snapshot|Git guarda "fotos" del estado de los archivos, no diferencias|
|Working directory|Espacio de trabajo donde se crean archivos, escribes código y lo editas|
|Staging area|Xona temporal donde preparas los archivos antes de confirmar cambios|
|Commit|Una versión guardada, con mensaje explicativo|

---

# Módulo 2: comandos básicos de Git
## Objetivo
Aprender los comandos clave para iniciar un proyecto Git, registrar cambios y entender el flujo de trabajo entre:
- Tu carpeta de trabajo (working directory)
- El área de preparación (staging area)
- El historial de confirmaciones (commits)

## Flujo básico de trabajo en Git
1. Modificas archivos en el worjing directory -> Git los detecta como "modificados"
2. Preparas archvios con `git add` -> Van al staging area
3. Confirmas los cambios con `git commit` -> Se guardan en el historial.
Este flujo se repite tantas veces como necesites. Git **nunca guarda los cambios automáticamente**.

## Comandos fundamentales
- `git init`
    Inicializa un nuveo repositorio Git en la carpeta actual

    `git init`

    Crea una carpeta oculta `.git/` con toda la "inteligencia" de Git.
- `git status`
    Muestra el estado actual de los archivos: modificados, no rastreados, en staging...
    ´git status´
- `git add`
    Prepara archivos para el commit. Puedes añadir uno, varios o todos.

    ```
    git add <archivo.txt> # Añade un archivo concreto o varios separados por espacios
    git add . # Añade todos los cambios en el directorio actual
    ```
- `git commit`
    Guarda los cambios preparados en el historial, junto con un mensaje descriptivo.

    `git commit -m "Mensaje que explica el cambio"`
- `git log`
    Muestra el historial de commits. Muy útil para revisar cambios anteriores.

    ```
    git log
    git log --oneline # Resumen por línea
    ```
- `git diff`
    Muestra las diferencias entre:
    - Archivos modificados vs último commit
    - Staging vs último commit
    ```
    git diff # Diferencias no añadidas (working -> staging)
    git diff --staged #Diferencias ya añadiddas (staging -> commit)
    ```
- `git restore`
    Sirve para deshacer cambios:

    ```
    git restore <archivo.txt> # Revierte el archivo a la última versión del commit
    gis restore --staged <archivo.txt> # Lo saca del staging area
    ```

📌 Estado de los archivos en Git
|Estado|Significado|
|---:|:---|
|Untracked|Git no reconoce aún ese archivo|
|Modified|El archivo ha cambiado desde el último commit|
|Staged|El archivo está listo para ser confirmado|
|Committed|Los cambios están guardados en el historial|


## Práctica guiada 1: tu primer proyecto con Git
### Paso 1: crea una carpeta para el proyecto
Abre tu terminal o Git Bash y escribe dentro de la ruta donde quieras crear la carpeta:

```
mkdir git-practica-1
cd git-practica-1
```

### Paso 2: inicializa el repositorio Git
`git init`

Verás un mensaje como:

`Initialized empty Git repository in...`

### Paso 3: crea un archivo nuevo
Puedes hacerlo desde un editor o directamente con un comando:

`echo "# Mi primer proyecto Git" > README.md`

Comprueba el estado:

`git status`

Deberías ver `README.md`como **untracked**.

### Paso 4: añade el archivo al staging area
`git add README.md`

Vuelve a comprobar el estado:

`git status`

Ahora README.md debería de aparecer en verde y marcado como "staged".

### Paso 5: haz tu primer commit
`git commit -m "Añade README inicial"`

Verás un mensaje confirmando el commit.

### Paso 6: revisa el historial de commits
`git log --oneline`

Verás una línea como:

`a1b2c3d Añade README inicial`

### Paso 7: simula un cambio
Edita el archivo (por ejemplo, en VS Code o con `echo`)

`echo "- Esta es una práctica de Git >> README.md`

Luego:

`git status`

Verás que el archivo está **modificado pero no añadido aún**.

### Paso 8: añade y guarda cambios
```
git add README.md
git commit -m "Actualiza README con nota de práctica"
```

### Paso 9: mira el historial completo
`git log`

También puedes ver diferencias entre versiones:

`git diff HEAD~1 HEAD`

### Resultado esperado
Tu proyecto tendrá:
- Un repositorio Git inicializado
- Un archivo `README.md`
- Dos commits registrados en el historial

## Práctica guiada 2: staging, diferencias y deshacer cambios
### Paso 1: vuelve a tu carpeta del proyecto anterior
Si aún estás en ella perfecto. Si no:

`cd git-practica-1`

### Paso 2: modifica el archivo existente
`echo "- Aprendiendo a usar Git" >> README.md`

Revisa el estado:

`git status`

Verás que `README.md` está modificado pero no añadido al staging.

### Paso 3: consulta las diferencias
`git diff`

Esto te mostrará qué líneas sehan añadido o cambiado desde el último commit.

### Paso 4: añade los cambios al staging
`git add README.md`

Ahora revisa de nuevo:

`git status`

El archivo aparecerá como **staged**.

### Paso 5: diferencias entre staging y commit
`git diff --staged`

Muestra qué está preparado para el commit, comparado con el último commit.

### Paso 6: Deshacer un cambio de staging area
Supón que te arrepientes de haber hecho `git add`.

`git restore --staged README.md`

Ahora vuelve a revisar con:

`git status`

El archivo vuelve a estar en rojo (*modificado pero no staged*).

### Paso 7: Deshacer los cambios locales
Supón ahora que quieres descartar por completo el cambio hecho en `README.md`:

`git restore README.md`

Esto devuelve al estado del último commit. Confirma con:

`git status`

Y también

`cat README.md`

Verás que se borró la línea "- Aprendiendo a usar Git".

### 📌 ¿Qué aprendiste aquí?
|Acción|Comando|
|---:|:---|
|Ver cambios no añadidos|`git diff`|
|Ver cambios ya añadidos|`git diff --staged`|
|Quitar archivo del staging|`git restore --staged <archivo>`|
|Deshacer cambios locales|`git restore <archivo>`|

## Práctica guiada 3: reset, revert y rm
### `git reset`: reescribe el historial reciente
#### Paso 1: crea un archivo nuevo
```
echo "Este archivo será reseteado" > nota.txt
git add nota.txt
git commit -m "Añade nota.txt"
```

#### Paso 2: elimina el último commit (pero conserva los cambios en archivos)
`git reset --soft HEAD~1`

Esto borra el commit pero mantiene los cambios de staging. Si haces `git status`, veras `nota.txt`en verde.

#### Paso 3: ahora haz un reset total
`hot reset --hard HEAD`

Esto elimina los cambios y el commit, y vuelve al estado anterior completamente. **Cuidado con `--hard`: elimina lo que no está confirmado**

### `git revert`: deshace un commit sin borrar historial
#### Paso 1: añade algo nuevo
```
echo "Cambio que vamos a revertir" >> README.md
git add README.md
git commit -m "Cambio de prueba para revertir"
```

#### Paso 2: revierte ese commit
Primero, identifica el hash corto del commit:

`git log --oneline`

Luego, usa:

`git revert <hash del commit>`

Esto crea un nuevo commit inverso. Es seguro para proyectos compartidos.

### `git rm`: eliminar archivos controlados por Git
#### Paso 1: crea otro archivo
```
echo "Archivo temporal" > temporal.txt
git add temporal.txt
git commit -m "Añade archivo temporal"
```

#### Paso 2: elimina ese archivo con Git
```
git rm temporal.txt
git commit -m "Elimina archivo temporal"
```

Esto borra el archivo del disco y del historial futuro

### 📌 ¿Qué aprendiste aquí?
|Acción|Comando|
|---:|:---|
|Borra el último commit, pero mantiene los cambios|`git reset --soft HEAD~1`|
|Revierte todo: historial y archivos (**destructivo**)|`git reset --hard HEAD`|
|Deshace el commit creando uno nuevo inverso|`git revert <hash>`|
|Elimina un archivo del disco y del control de versiones|`git rm <archivo>`|

---

# Módulo 3: GitHub y trabajo remoto
## Objetivo
Aprender a conectar un repositorio local de Github, subir tus cambios y traer actualizaciones del repositorio remoto. También entenderemos cómo colaborar con otras personas.

## ¿Qué es GitHub?
GitHub es una plataforma en la nube que te permite:
- Almacenar repositorios Git online.
- Compartir proyectos y colaborar.
- Crear ramas, pull request, revisar código y  más.

## Configuración previa
1. Crear cuenta en [GitHub][https://github.com/].
2. Configurar acceso SSH (opcional pero recomendado):

    1. Abre Git Bash
    2. `ssh-keygen `
    3. Completar directorio (enter) y contraseña (no se ve lo que escribes).
    4. Luego copia tu clave con:

       ```
       ls
       cat ~/.ssh/nombre-archivo.pub
       ```

       Esto muestra la ssh key pública, la privada (la que no es *.pub) no se debe de compartir nunca.
    5. Copiar y pegar la key pública en GitHub\Settings (del perfil)\SSH and GPG keys\New SSH key y ponerle un nombre "Mi portátil".
    6. En Git Bash poner:

        ```
        eval "$(ssh-agent)"
        ssh-add
        ```
    7. Poner contraseña de la SSH key.

## Crear repositorio remoto en GitHub
1. Ve a [GitHub][https://github.com/].
2. Clic en **New repository**.
3. Asigna un nombre.
4. Deja desmarcado "Initialize with README" (ya lo tienes localmente).
5. Clic en **Create repository**.

## Conectar tu repo local con GitHub
Desde tu proyecto local (ya inicializado) y con SSH, sino utuilizar link de HTTPS:

`git remote add origin git@github.com:TU_USUARIO/NOMBRE_REPOSITORIO_GITHUB`

Verifica que se añadió correctamente:

`git remote -v`

## Subir tu proyecto por primera vez
`git push -u origin <rama principal>`

Con esto, tu historial local se sube al repositorio de GitHub.

## Clonar un proyecto existente
Si el proyecto ya está en GitHub y quieres copiarlo en otro equipo:

`git clone git@github.com:usuario/nombre-repo.git`

Esto crea una copia exacta con todo el historial.

## Traer cambios desde GitHub
Para sincronizar con el repositorio remoto:

`git pull`

También puedes separar en:

```
git fetch # Trae cambios, pero no los mezcla aún
git merge # Integra los cambios en tu rama actual
```

## 📌 Flujo típico con GitHub
1. Haces cambios localmente
2. `git add` + `git commit`
3. `git push` -> subes al remoto
4. `git pull` -> bajas cambios si otro colaborador ha subido algo

## Práctica guiada 1: subir proyecto local en GitHub
Puedes hacer pequños cambios y repetir el flujo:

```
echo "Nueva línea" >> README.md
git add README.md
git commit -m "Actualización desde local"
git push
```

Y veras los cambios reflejados en GitHub

## Práctica guiada 2: clonar repositorio desde GitHub
El objetivo es crear un copia exacta de un repositorio remoto en tu ordenador, incluyendo todo su historial y ramas. `git clone` se utiliza cuando trabajas en otro equipo o desde cero, cuando quieres contribuir a un proyuecto existente o cuando necesitas una copia fresca de un repositorio.

### Paso 1: copia la URL del repositorio
Ve al repo de GitHub que quieras clonar (ej. `git-practica-1`) y haz clic en el botón verde `<> Code`. Selecciona el modo que prefieras:
- SSH (recomendado):

    `git@github.com:TU_USUARIO/git-practica-1.git`

- HTTPS (más sencillo para empezar):

    `https://github.com/TU_USUARIO/git-practica-1.git`

### Paso 2: abre la terminal en otra carpeta
Por ejemplo:

`cd ~/Escritorio`

### Paso 3: clona el repositorio
Con SSH:

`git clone git@github.com:TU_USUARIO/git-practica-1.git`

Con HTTPS:

`git clone https://github.com/TU_USUARIO/git-practica-1.git`

### Paso 4: resultado
Esto creará una nueva carpeta llamada `git-practica-1` con todo el contenido del repositorio, incluyendo:
- Todos los archivos
- Todo el historial de commits
- Todas las ramas

Puedes entrar en la carpeta:

`cd git-practica-1`

Verifica que está conectado al repositorio remoto:

`git remote -v`

### Paso 5: prueba el flujo completo
Haz un pequeño cambio y súbelo:

```
echo "Clonado exitosamente" >> README.md
git add README.md
git commit -m "Prueba desde clon"
git push
```

---

# Módulo 4: ramas y trabajo colaborativo
## Objetivo
Aprender a usar ramas (`branches`) para desarrollar nuevas funcionalidades sin afectar el código principal, resolver conflictos y colaborar eficientemente mediante GitHub.

## ¿Qué es una rama (branch)?
Una rama es una línea de desarrollo independiente. La rama principal suele llamarse `main` o `master`, pero puedes creear tantas como quieras:
- `main`: versión estable del proyecto
- `dev`: ingtegración de cambios en desarrollo
- `feature/login`: nueva funcionalidad
- `bugfix/footer`: correción de error

Existentes diferentes formas de organizar el trabajo con ramas en Git (estrategias de branching) que veremos próximamente. Las más utilizadas son Trunk-Based Development (TBD) y Git Flow.

📌 Piensa en una rama como una "fotocopia editable" del proyecto.

## Comandos básicos para trabajar con ramas
### Ver las ramas disponibles
`git branch`

Muestra las ramas locales. La activa aparece con un `*`.

### Crea una nueva rama
`git branch nombre-de-la-rama`

### Cambiar de rama
`git switch nombre-de-la-rama`

Alternativa clásica: `git checkout nombre-de-la-rama` (el comando `checkout` se utiliza para infinidad de cosas en Git, es por eso que es mejor utilizar otros que son más especificos para cada acción).

### Crear y cambiar al mismo tiempo
`git switch -c nombre-de-la-rama`

### Subir una rama a GitHub
`git push -u origin nombre-de-la-rama`

## Fusión de ramas (`merge`)
Cuando terminas tu trabajo en una rama secundaria, puedes integrarla de nuveo a `main`.

```
git switch main
git merge nombre-de-la-rama
```

## Conflictos de fusión
Si Git no puede combinar los cambios automáticamente, se produce un conflicto. Verás algo como:

```
<<<<<<< HEAD
Código de la rama actual
========
Código de la rama que intentas fusionar
>>>>>>> nombre-de-la-rama
```

En este caso tendrás que editar el archivo, eliminar las marcas `<<<<<<<<`, `========`, `>>>>>>>`, y decidir con qué código te quedas. Luego:

```
git add archivo-afectado
git commit -m "Resuelve conflicto entre main y nombre-de-la-rama
```

## Pull request (PR) en GitHub
Cuando trabajas en equipo, no se hace `merge` directamente a `main`. En su lugar:
1. Creas una rama y subes tus cambios.
2. Abres un *pull request* (PR) en GitHub.
3. Otro colaborador revisa y aprueba.
4. Se hace `merge` desde la interfaz web.

## Resumen visual
```
main ──────────────────●──────────────●─────────────→
                        \                          
nombre-de-la-rama        ●────●────●──┘
```

## Práctica guiada 1: ramas, merge y resolución de conflictos
### Paso 1: abre tu proyecto
```
cd /c/Users/ruta/git-practica-1
```

Verifica que estás en la rama principal:

```
git branch
```

Si no estás en `main`, cambia con:

```
git switch main
```

### Paso 2: crea una nueva rama
```
git switch -c feature-bienvenida
```

Esto crea la rama `feature-bienvenida`y te mueve a ella.

### Paso 3: modifica el archivo `README.md`
Añade una línea:

```
echo "- Bienvenido a este proyecto proyecto" >> README.md
```

Luego guarda y confirma:

```
git add README.md
git commit -m "Añade mensaje de bienvenida"
```

### Paso 4: vuelve a `main`
```
git switch main
```

Ahora crea un cambio diferente en la misma parte del archivo para provocar un conflicto:

```
echo "- Este proyecto es sobre Git" >> README.md
git add README.md
git commit -m "Añade descripción general en main"
```

### Paso 5: intenta hacer `merge`
```
git merge feature-bienvenida
```

Git te avisará de un conflicto!!

### Paso 6: resuelve el conflicto
Abre `README.md`. Verás algo así:

```
<<<<<<< HEAD
- Este proyecto es sobre Git
=======
- Bienvenida a este proyecto
>>>>>>> feature-bienvenida
```

Elige una de las dos líneas, o combina ambas. Ejemplo:

```
Bienvenida a este proyecto sobre Git
```

Luego:

```
git add README.md
git commit -m "Resuelve conflicto entre main y feature-bienvenida"
```

### Paso 7: elimina la rama (opcional)
Una vez fusionada, puedes borrar la rama local para mayor limpieza:

```
git branch -d featura-bienvenida
```

### Paso 8: subo todo a GitHub
```
git push
```

## Práctica guiada 2: crear Pull Request (PR) en GitHub
### Paso 1: crea una nueva rama de funcionalidad
Desde tu terminal en el proyecto:

```
git switch -c feature-footer
```

### Paso 2: haz un cambio
Añade una línea al final de `README.md`:

```
echo "- Este proyecto incluirá un pie de página (footer)" >> README.md
```

Confirma los cambios:

```
git add REAMDE.md
git commit -m "Añade línea sobre el footer"
```

### Paso 3: sube la rama a GitHub
```
git push -u origin feature-footer
```

### Paso 4: crea el Pull Request en GitHub
1. Ve al repositorio en GitHub
2. Verás un aviso: "**Compare & pull request**" -> haz clic
3. En la nueva página:
    - **Base**: debe ser `main`
    - **Compare**: tu rama `featuire-footer`
4. Añade un título y una descripción breve
5. Haz clic en "**Create pull request**" (si no aparece automáticamente el botón, puedes ir a la pestaña "Pull Requests" y crear uno manualmente)

### Paso 5: revisa y fusiona el PR
1. Puedes dejar comentarios o revisar los cambios (GitHub los muestra línea a línea).
2. Haz clic en "**Merge pull request**".
3. Luego, clic en "**Confirm merge**".
4. Finalmente, puedes eliminar la rama en GitHub ("**Delete branch**").

### Paso 6: baja los cambios a tu equipo local
Tu rama `main` local aún no tiene ese cambio. Actualízala:

```
git switch amin
git pull origin main
```

---

# Módulo 5: buenas prácticas y herramientas útiles
## Objetivo
Aprender a ignorar archivos innecesarios, guardar cambios temporales, crear versiones con etiquetas (tags), limpiar o corregir el historial de commits y usar herramientas visuales para entender el historial.

## `.gitignore`: ignorar archivos
Git rastrea todos los archivos a menos que tú le digas que no creando un archivo `.gitignore`.

```
touch .gitignore
```

Si utilizas en cmd de Windows: `type NUL > .gitignore`

Dentro de este archivo puedes poner nombres específicos de los archivos que quieres ignorar o tipos de archivos completos con *.extension. Ejemplo de contenido:

```
*.log
__pycache__/
*.env
.DS_Store
```

Esto evita que archivos temporales o confidenciales se suban por error

📌 GitHub ofrece plantillas para cada lenguaje: https://github.com/github/gitignore 

## `git stash`: guardar cambios temporales
Imagina que estás en mitad de algo, pero necesitas cambiar de rama:

```
git stash
```

Esto guarda tus cambios no confirmados y deja el repositorio limpio. Para recuperarlos:

```
git stash apply # vuelve a aplicar el último stash
```

Ver lista de stashes guardados:

```
git stash list
```

## `git tag`: crear versiones del proyecto
Los **tags** se usan para mrcar versiones estables como `v1.0`, `v2.0-beta`, etc.

```
git tag v1.0
git push origin v1.0
```

También puedes añadir anotaciones:

```
git tag -a v1.1 -m "Primera versión estable"
```

## Limpieza y corrección del historial
### `git commit --amend`: corregir el último commit
```
git commit --amend -m "Mensaje corregido"
```

Es útil si olvidaste añadir un archivo o quieres reescribir el mensaje.

### `git rebase -i`: reescritura interactiva
Solo usar si estás trabajando en solitario o en ramas aún no compartidas. Pemrite unir commits, cambiar su orden y editar mensajes:

```
git rebase -i HEAD~3
```

## Herramientas útiles
 - GitHub Desktop: interfaz gráfica oficial para Git en Windows y Mac. Ideal si estás empezando o quieres revisar visualmente los cambios.
 - Gitk
 - GitKraken
 - SourceTree
 - GitLens (extensión de VS Code)

## Buenas prácticas
### Limpieza y organización del repositorio
- Usar un buen `.gitignore` para evitar subir archivos innecesarios (logs, binarios, .env, etc.).
- No subir dependencias innecesarias como `node_modules`, `venv`, `build`, etc.
- Estructura de carpetas clara para mejorar la comprensión del proyecto por parte de otros usuarios.
- Mantener el repositorio actualizado para evitar confusión entre versiones locales y remotas.

### Mensajes de commit claros y consistentes
- Usa verbos en imperativo -> ✅ `Corrige validación de email` ❌ `Corregido el error del email`
- Sé descriptivo pero conciso -> ✅ `Añade control de errores en login` ❌ `login arreglado`
- Agrupa cambios relacionados -> ✅ Un commit = un propósito ❌ No mezcles refactor + bugfix
- Usa emojios (opcional) para clasificar -> `🔧 Refactoriza función`

### Buen manejo de ramas
- Usa ramas con nombres descriptivos -> `feature/login`, `bugfix/navbar`, `refactor/db-layer`, `release/v1.2`
- No trabajar directamente en `main`-> Usa ramas para cada nueva funcionalidad o correción
- Borrar ramas locales cuando termines -> Mantiene tu entorno limpio
- Evita ramas largas sin merge -> Haz merge frecuentemente a `develop` para evitar conflictos enormes

### Buenas prácticas al hacer mege o pull request
- Revisa antes de hacer merge -> Usa `git diff` o GitHub PRs para verificar lo que estás integrando
- No mezcles muchas funcionalidades en una sola rama -> Mejor ramas pequeñas, fáciles de revisar
- Resuelve conflictos tú mismo -> No dejes código conflictivo en el repositorio
- Siempre actualiza tu rama antes de hacer PR -> Usa `git pull --rebase origin main` si trabajas sobre `main`

### Versionado y control de releases
- Usar `git tag` para marcar versiones -> Permite retroceder a versiones estables fácilmente
- Etiquetas semánticas (`v1.0.0`) -> Mayor claridad en el control de versiones
- Acompañar versiones con `CHANGELOG.md` -> Comunica qué ha cambiado entre una versión y otra

### Buenas herramientas complementarias
- GitHub Desktop -> Interfaz gráfica oficial para Git (ideal para principiantes)
- GitLens (VS Code) -> Ver historial de cada línea, autores y comparar versiones
- GitKraken / SourceTree -> Visualizar ramas y merges fácilmente
- Husky + lint-staged -> Ejecutar test o linters antes de cada commit automáticamente

## Práctica guiada 1: `.gitignore`, `stash`, `tag`, `commit --amend`
Primero asegúrate de estar en tu repositorio

```
cd ruta/del/proyecto/git-practica-1
```

### Ignorar archivos con `.gitignore`

Crea un archivo `.gitignore`

```
touch .gitignore
```

Añade contenido con:

```
nano .gitignore # o usa VS Code, Notepad, etc.
```

Y añade líneas como estas:

```
*.log
*.env
__pycache__/
.DS_Store
```

Guarda y haz commit:

```
git add .gitignore
git commit -m "Añade archivo .gitignore"
```

Comprueba que los archvios ignorados no se rastrean:

```
echo "temporal" > archivos.log
git status
```

Veras que no aparece en la lista de archivos modificados.

### Guardar cambios temporales con `git stash`
Haz un cambio sin confirmarlo:

```
echo "Cambio que quiero guardar temporalmente" >> README.md
```

Comprueba que hay cambios pendientes:

```
git status
```

Guarda el cambio en el stash:

```
git stash
```

Ahora tu árbol está limpio otra vez. Para verificar y recuperar el stash:

```
git stash list
git stash apply
```

Vuelves a tener los cambios en tu archivo.

### Crear una versión del proyecto con `git tag`
Crea un tag anotado:

```
git tag -a v1.0 -m "Primera versión estable"
```

Verifica los tags:

```
git tag
```

Sube el tag a GitHub:

```
git push origin v1.0
```

### Corregir el último commit con `--amend`
Supón que te olvidaste de añadir un archivo. Entonces, crea un archivo nuevo:

```
echo "Archivo importante" > importante.txt
git add importante.txt
```

En vez de hacer otro commit, modifica el anterior:

```
git commit --amend
```

Se abrirá el editor para que edutes el mensaje, o simplemente lo guardas.

---

# Módulo 6: flujos de trabajo avanzados en Git