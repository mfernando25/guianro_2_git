# GUÍA PRÁCTICA N.º 4 PARA LA UTILIZACIÓN DE GIT – GITHUB
## Participación colaborativa – acceso al repositorio – ramas y Pull Requests
**Curso:** Matemáticas Discretas 02

---

## Objetivo de la práctica

Aprender a colaborar en un mismo proyecto utilizando Git y GitHub. Un integrante prepara el repositorio y asigna una tarea; el otro trabaja únicamente sobre los archivos que le corresponden y propone sus cambios mediante un Pull Request. El propietario revisa la propuesta y decide si la acepta o solicita correcciones.

En esta guía trabajaremos con **dos integrantes**:

- **Integrante 1 – Propietario:** crea y prepara el repositorio, invita al colaborador y revisa sus cambios.
- **Integrante 2 – Colaborador:** acepta la invitación, clona el repositorio, trabaja en una rama propia y propone los cambios asignados.

**Importante:** no se trabajará directamente sobre la rama principal `main`. Los cambios del colaborador se enviarán mediante una rama y un Pull Request.

---

## Paso 1 – El propietario crea y prepara el repositorio

Este paso lo realiza el integrante 1.

### 1.1 Crear el repositorio y subir el código inicial

1. Ingresa a GitHub.
2. Crea un repositorio nuevo para el proyecto.
3. Agrega el código inicial del generador de AFD y los archivos necesarios para el proyecto.
4. Comprueba que los archivos aparezcan correctamente en la rama principal, llamada `main`.

### 1.2 Proteger la rama principal

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

### 1.3 Invitar al colaborador

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
4. Abre Git Bash y configura tu identidad de Git en la computadora:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email tu_correo_de_github@example.com
```

5. Comprueba la configuración:

```bash
git config --global --get user.name
git config --global --get user.email
```

**Importante:** estos datos identifican al autor de los commits; no inician sesión en GitHub. En los laboratorios con DeepFreeze, vuelve a configurar tu identidad después de cada reinicio.

---

## Paso 3 – Clonar el repositorio y crear una rama de trabajo

Este paso lo realiza el integrante 2.

1. Entra al repositorio del integrante 1.
2. Haz clic en el botón **Code** y copia la URL **HTTPS**.
3. Elige una carpeta de trabajo y ábrela en Visual Studio Code.
4. Abre el terminal **Git Bash**.
5. Clona el repositorio utilizando la URL copiada:

```bash
git clone https://github.com/usuario-dueño/proyecto_final.git
```

Reemplaza la URL de ejemplo por la dirección del repositorio compartido.

6. Entra a la carpeta que se creó al clonar el repositorio:

```bash
ls
cd nombre-de-la-carpeta
```

7. Comprueba que estás en la rama principal y que el repositorio está actualizado:

```bash
git status
git pull origin main
```

8. Crea una rama para realizar únicamente la tarea asignada:

```bash
git switch -c tarea-colaborador
```

**Ojo:** trabaja en la rama `tarea-colaborador`, no directamente en `main`. Modifica únicamente los archivos relacionados con la tarea que te asignó el propietario.

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

7. Sube tu rama a GitHub:

```bash
git push -u origin tarea-colaborador
```

### 4.2 Crear el Pull Request

Después de subir la rama:

1. Ingresa al repositorio en GitHub.
2. Selecciona **Compare & pull request** si aparece la notificación, o entra a **Pull requests** y selecciona **New pull request**.
3. Comprueba que la comparación sea:
   - **base:** `main`
   - **compare:** `tarea-colaborador`
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

---

## Paso 5 – Actualizar el repositorio y ejecutar el diagramador de AFD

Una vez integrado el Pull Request, ambos integrantes pueden actualizar su copia local.

1. Cambia a la rama principal:

```bash
git switch main
```

2. Descarga la versión actualizada:

```bash
git pull origin main
```

3. Instala las dependencias y librerías necesarias:

```bash
pip install networkx matplotlib
```

4. Ejecuta el programa:

```bash
python Main.py
```

También puedes utilizar el nombre del archivo en el que se encuentra el código, si es diferente de `Main.py`.
