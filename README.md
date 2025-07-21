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
- Copntrolar qué cambias, cuándo y por qué.
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

##Conceptos clave
|Término|Qué significa|
|---:|:---|
|Repositorio|proyecto con control de versional. Puede ser local o remoto|
|Snapshot|Git guarda "fotos" del estado de los archivos, no diferencias|
|Working directory|Espacio de trabajo donde se crean archivos, escribes código y lo editas|
|Staging area|Xona temporal donde preparas los archivos antes de confirmar cambios|
|Commit|Una versión guardada, con mensaje explicativo|


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

### Paso 3: Crea un archivo nuevo
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
2. Configurar acceso SSH (opcional pero recomendado): si quieres evitar escribir tu usuario y contraseña todo el tiempo:
    `ssh-keygen -t ed25519 -C "tu@email.com"`
    Luego copia tu clave con:
    `cat ~/.ssh/id_ed25519.pub`
    Y pégala en GitHub -> Settings -> SSH and GPG Keys -> New SSH Key.

## Crear repositorio remoto en GitHub
1. Ve a [GitHub][https://github.com/].
2. Clic en **New repository**.
3. Asigna un nombre.
4. Deja desmarcado "Initialize with README" (ya lo tienes localmente).
5. Clic en **Create repository**.

## Conectar tu repo local con GitHub
Desde tu proyecto local (ya inicializado) y con SSH, sino utuilizar link de HTTPS:
`git remoto add origin git@github.com:TU_USUARIO/NOMBRE_REPOSITORIO_GITHUB`
Verifica que se añadió correctamente:
`git remote -v`

## Subir tu proyectoi por primera vez
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
git fetch # Trae cambios, pero no los mez la aún
git merge # Integra los cambios en tu rama actual
```
## 📌 Flujo típico con GitHub
1. Haces cambios localmente
2. `git add`+ `git commit`
3. `git push`-> subes al remoto
4. `git pull`-> bajas cambios si otro colaborador ha subido algo