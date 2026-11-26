# GUÍA PRÁCTICA N.º 4 PARA LA UTILIZACIÓN DE GIT – GITHUB
## Participación colaborativa – acceso al repositorio – ramas y Pull Requests
**Curso:** Matemáticas Discretas 02

---

## Objetivo de la práctica

Aprender a colaborar en un mismo proyecto utilizando Git y GitHub. Un integrante crea el repositorio, lo clona en su computadora y sube el código inicial desde Visual Studio Code. Después invita al segundo integrante, quien trabaja únicamente sobre los archivos que le corresponden y propone sus cambios mediante un Pull Request. El propietario revisa la propuesta y decide si la acepta o solicita correcciones.

En esta guía trabajaremos con **dos integrantes**:

- **Integrante 1 – Propietario:** crea el repositorio, lo prepara desde su computadora, sube el generador de AFD, invita al colaborador y revisa sus cambios.
- **Integrante 2 – Colaborador:** acepta la invitación, clona el repositorio, trabaja en una rama propia y propone los cambios asignados.

**Importante:** no se trabajará directamente sobre la rama principal `main`. Los cambios del colaborador se enviarán mediante una rama y un Pull Request.

---

## Paso 1 – El propietario crea el repositorio y sube el generador desde VS Code

Este paso lo realiza el integrante 1. Primero creará el repositorio en GitHub; después lo clonará en su computadora y subirá el archivo del generador utilizando Visual Studio Code.

### 1.1 Crear un repositorio vacío en GitHub

1. Ingresa a GitHub.
2. Selecciona **New repository**.
3. Escribe un nombre para el repositorio.
4. Selecciona **Public**. Esto permitirá utilizar la protección de ramas con GitHub Free.
5. No marques las opciones para agregar un README, un archivo `.gitignore` o una licencia. El repositorio debe crearse vacío para realizar el primer envío desde la computadora.
6. Selecciona **Create repository**.
7. En la página del repositorio, haz clic en **Code** y copia la URL **HTTPS**. La utilizarás para clonarlo en el siguiente apartado.

### 1.2 Configurar Git y clonar el repositorio en la computadora

1. Abre Visual Studio Code.
2. Abre una nueva terminal desde **Terminal > New Terminal**.
3. Configura tu identidad de Git. Reemplaza los datos de ejemplo por tu nombre y el correo asociado a tu cuenta de GitHub:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email tu_correo_de_github@example.com
```

4. Comprueba la configuración:

```bash
git config --global --get user.name
git config --global --get user.email
```

5. En la terminal de VS Code, clona el repositorio utilizando la URL HTTPS que copiaste:

```bash
git clone https://github.com/tu-usuario/miercolescasidiciembre.git
```

Reemplaza la URL de ejemplo por la dirección de tu repositorio.

6. Entra a la carpeta del repositorio:

```bash
cd miercolescasidiciembre
```

7. En VS Code, selecciona **File > Open Folder** y abre la carpeta del repositorio que acabas de clonar.

### 1.3 Incorporar y subir el generador de AFD desde VS Code

1. Copia el archivo del generador de AFD a la carpeta del repositorio que abriste en VS Code. Si el generador está compuesto por varios archivos necesarios para ejecutarlo, incorpora también esos archivos.
2. Comprueba en el panel **Explorer** de VS Code que el archivo del generador aparezca dentro del repositorio.
3. Abre la terminal integrada y verifica los archivos detectados por Git:

```bash
git status
```

4. Agrega el archivo del generador. En el ejemplo se utiliza `Main.py`; reemplaza el nombre si tu archivo tiene otro:

```bash
git add Main.py
```

Si incorporaste otros archivos necesarios, agrégalos también de forma explícita.

5. Registra la incorporación mediante un commit:

```bash
git commit -m "Agrega generador de AFD"
```

6. Sube el contenido a la rama principal de GitHub:

```bash
git push -u origin main
```

7. Actualiza la página del repositorio en GitHub y comprueba que el archivo del generador aparece en la rama `main`.

### 1.4 Proteger la rama principal

La rama `main` contendrá la versión principal del proyecto. Para evitar que los cambios del colaborador se incorporen sin revisión, configura una regla de protección:

1. Entra al repositorio y selecciona **Settings**.
2. En el menú lateral, entra a **Branches**.
3. En **Branch protection rules**, selecciona **Add rule** o **Add classic branch protection rule**.
4. En **Branch name pattern**, escribe:

```text
main
```

5. Activa **Require a pull request before merging**.
6. Activa **Require approvals** y establece **1** aprobación.
7. Activa **Dismiss stale pull request approvals when new commits are pushed**, para que una aprobación anterior deje de ser válida si después se agregan nuevos cambios.
8. Si aparece la opción **Do not allow bypassing the above settings**, actívala.
9. Guarda la regla con **Create** o **Save changes**.

**Nota:** las reglas de protección de ramas están disponibles en repositorios públicos con GitHub Free. En repositorios privados se requiere un plan GitHub Pro, Team o Enterprise para esta función.

### 1.5 Invitar al colaborador

1. En el repositorio, selecciona **Settings**.
2. En el menú izquierdo, selecciona **Collaborators** o **Collaborators and teams**.
3. Selecciona **Add people**.
4. Escribe el username o el correo asociado a la cuenta de GitHub del integrante 2.
5. Envía la invitación.
6. El colaborador deberá aceptar la invitación recibida.

---

## Paso 2 – El colaborador acepta la invitación y prepara su entorno

Este paso lo realiza el integrante 2.

1. Ingresa a tu correo electrónico y busca la invitación de GitHub.
2. Haz clic en **View invitation** y acepta la invitación.
3. Accede al repositorio compartido.
4. Abre Visual Studio Code y una nueva terminal desde **Terminal > New Terminal**.
5. Configura tu identidad de Git en la computadora:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email tu_correo_de_github@example.com
```

6. Comprueba la configuración:

```bash
git config --global --get user.name
git config --global --get user.email
```

**Importante:** estos datos identifican al autor de los commits; no inician sesión en GitHub. En los laboratorios con DeepFreeze, vuelve a configurar tu identidad después de cada reinicio.

---

## Paso 3 – El colaborador clona el repositorio y crea una rama de trabajo

Este paso lo realiza el integrante 2.

1. Entra al repositorio del integrante 1.
2. Haz clic en el botón **Code** y copia la URL **HTTPS**.
3. En la terminal de VS Code, ubícate en la carpeta donde guardarás el proyecto.
4. Clona el repositorio utilizando la URL copiada:

```bash
git clone https://github.com/tu-usuario/miercolescasidiciembre.git
```

Reemplaza la URL de ejemplo por la dirección del repositorio compartido.

5. Entra a la carpeta que se creó al clonar el repositorio:

```bash
cd miercolescasidiciembre
```

6. Abre esa carpeta en VS Code mediante **File > Open Folder**.
7. Comprueba que estás en la rama principal y que el repositorio está actualizado:

```bash
git status
git pull origin main
```

8. Crea una rama para realizar únicamente la tarea asignada:

```bash
git switch -c desarrollo
```

**Ojo:** trabaja en la rama `desarrollo`, no directamente en `main`. Modifica únicamente los archivos relacionados con la tarea que te asignó el propietario.

---

## Paso 4 – Realizar cambios y proponerlos mediante un Pull Request

### 4.1 El colaborador realiza su tarea

Este paso lo realiza el integrante 2.

1. Abre en VS Code el archivo que te corresponde.
2. Realiza únicamente los cambios solicitados por el propietario.
3. Guarda los cambios con **Ctrl + S**.
4. Comprueba qué archivos modificaste:

```bash
git status
```

5. Revisa que los cambios correspondan a tu tarea. Agrega solamente el archivo o los archivos que modificaste para cumplirla:

```bash
git add nombre-del-archivo.py
```

6. Registra los cambios mediante un commit con un mensaje claro:

```bash
git commit -m "Describe el cambio realizado"
```

7. Sube tu rama a GitHub por primera vez:

```bash
git push -u origin desarrollo
```

La opción `-u` vincula tu rama local `desarrollo` con la rama remota `origin/desarrollo`. Solo necesitas utilizarla en este primer envío. Después de realizar nuevos commits, bastará con ejecutar:

```bash
git push
```

### 4.2 Crear el Pull Request

Después de subir la rama:

1. Ingresa al repositorio en GitHub.
2. Selecciona **Compare & pull request** si aparece la notificación, o entra a **Pull requests** y selecciona **New pull request**.
3. Comprueba que la comparación sea:
   - **base:** `main`
   - **compare:** `desarrollo`
4. Escribe un título y una descripción breve de lo que realizaste.
5. Selecciona **Create pull request**.

El Pull Request propone incorporar tus cambios a `main`. Todavía no significa que los cambios hayan sido aceptados.

### 4.3 El propietario revisa la propuesta

Este paso lo realiza el integrante 1.

1. Entra a la pestaña **Pull requests** del repositorio.
2. Abre el Pull Request creado por el colaborador.
3. Revisa la pestaña **Files changed**.
4. Comprueba que los archivos modificados correspondan a la tarea asignada y que no existan cambios ajenos a ella.
5. Si los cambios son correctos, selecciona **Review changes**, escribe un comentario si corresponde y elige **Approve**.
6. Si hay modificaciones fuera de lo solicitado o errores, selecciona **Request changes** y explica qué debe corregirse. No integres el Pull Request mientras existan observaciones pendientes.

**Ojo:** el propietario puede solicitar correcciones o no aceptar la propuesta. El colaborador deberá corregir su rama y volver a subir los cambios. El Pull Request se actualizará automáticamente.

### 4.4 Integrar los cambios aprobados

Cuando la propuesta esté aprobada:

1. El integrante 1 selecciona **Merge pull request**.
2. Confirma con **Confirm merge**.
3. Comprueba que los cambios ya aparecen en la rama `main`.

De esta manera, los cambios del colaborador solo se incorporan a la versión principal después de la revisión y aprobación del propietario.

## Paso 5 – El propietario agrega un archivo de instrucciones a la rama principal

Este paso lo realiza el integrante 1. Como la rama `main` está protegida, el propietario también debe utilizar una rama de trabajo y un Pull Request para incorporar este nuevo archivo.

1. Asegúrate de estar en la rama principal y actualiza tu copia local para recibir los cambios que acabas de integrar:

```bash
git switch main
git pull origin main
```

2. Crea una rama para preparar el archivo de instrucciones:

```bash
git switch -c instrucciones-ejecucion
```

3. En VS Code, crea un archivo nuevo llamado `INSTRUCCIONES.md` en la carpeta principal del repositorio. Escribe dentro este contenido:

```markdown
# Instrucciones para ejecutar el diagramador de AFD

1. Instalar las librerías necesarias: `pip install networkx matplotlib`
2. Ejecutar el programa: `python Main.py`
```

4. Guarda el archivo y comprueba que Git lo detecta:

```bash
git status
```

5. Agrega el archivo y registra el cambio:

```bash
git add INSTRUCCIONES.md
git commit -m "Agrega instrucciones para ejecutar el diagramador"
```

6. Sube por primera vez esta nueva rama a GitHub:

```bash
git push -u origin instrucciones-ejecucion
```

7. En GitHub, crea un Pull Request y comprueba que la comparación sea:
   - **base:** `main`
   - **compare:** `instrucciones-ejecucion`

8. El integrante 2 revisa el archivo en **Files changed** y, si las instrucciones son correctas, selecciona **Review changes** y elige **Approve**.

9. El integrante 1 integra el Pull Request con **Merge pull request** y **Confirm merge**. Comprueba que `INSTRUCCIONES.md` aparece en la rama `main`.

**Resultado esperado:** el propietario incorporó un archivo nuevo a `main` mediante un Pull Request. Ahora el colaborador podrá descargar ese archivo desde su rama `desarrollo` en el siguiente paso.

---

## Paso 6 – Actualizar el repositorio y ejecutar el diagramador de AFD

Una vez integrado el segundo Pull Request, cada integrante actualiza su copia local:

**Integrante 1 – Propietario**

Como el Pull Request se integró desde GitHub y tu copia local está en la rama `instrucciones-ejecucion`, vuelve a `main` y actualízala:

```bash
git switch main
git pull origin main
```

**Integrante 2 – Colaborador**

Permanece en la rama `desarrollo` y ejecuta:

```bash
git pull origin main
```

Este comando descarga los cambios de `main` y los incorpora a la rama actual `desarrollo`. No necesitas cambiar de rama.

Comprueba en el panel **Explorer** de VS Code que ahora también aparece el archivo `INSTRUCCIONES.md`. Ábrelo y sigue sus dos indicaciones:

1. Instala las dependencias y librerías necesarias:

```bash
pip install networkx matplotlib
```

2. Ejecuta el programa:

```bash
python Main.py
```

También puedes utilizar el nombre del archivo en el que se encuentra el código, si es diferente de `Main.py`.

**Resultado esperado:** el colaborador recibe en su rama `desarrollo` un archivo que el propietario agregó posteriormente a `main`. Así se comprueba que una rama de trabajo puede incorporar actualizaciones de la rama principal sin cambiar de rama.
