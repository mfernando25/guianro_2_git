# GUÍA PRÁCTICA N.º 4 PARA LA UTILIZACIÓN DE GIT – GITHUB
## Participación colaborativa – acceso a repositorio – permisos
**Curso:** Matemáticas Discretas 02

---

## Paso 1 – Acceder a GitHub y al repositorio

1. Ingresa a GitHub y abre el repositorio del proyecto.
2. Haz clic en **Settings** (pestaña superior).
3. En el menú izquierdo, selecciona **Collaborators**.
4. En **Manage Access**, selecciona **Add people**.

   **Ojo:** recuerda que la invitación para colaborar llega al correo electrónico asociado a la cuenta de GitHub invitada.

5. Haz clic en **Add people**.
6. Escribe el username o el correo de GitHub del colaborador.
7. Haz clic en **Add collaborator**.
8. El colaborador recibirá una invitación que debe aceptar.

---

## Paso 2 – El colaborador acepta la invitación y prepara su entorno

Este paso lo realiza cada colaborador invitado al repositorio.

1. Ingresa a tu correo institucional (al cual se envió la invitación de acceso al repositorio).
2. Busca el correo de invitación, haz clic en **View invitation** y acepta la invitación.
3. Después, accederás al repositorio donde se encuentra el proyecto.
4. Configura el entorno. Si no estás utilizando tu propia computadora, configura las credenciales de Git según las indicaciones del laboratorio.
5. Registra tus datos de usuario en Git:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email tu_correo_de_github@example.com
```

6. Comprueba la configuración:

```bash
git config --global --list
```

---

## Paso 3 – Clonar el repositorio del dueño

Una vez aceptada la invitación, cada colaborador puede obtener una copia del proyecto.

1. Entra a GitHub (también puedes acceder desde la invitación recibida por correo).
2. Abre el repositorio del dueño.
3. Haz clic en el botón **Code** (color verde).
4. Copia la URL **HTTPS**.

5. Elige una carpeta donde clonar el proyecto, crea la carpeta y ábrela en Visual Studio Code.

   **Ojo:** no olvides crear la carpeta y abrirla en VS Code.

6. Con esa carpeta abierta en VS Code, abre el terminal **Git Bash**.
7. Clona el repositorio usando la URL copiada:

```bash
git clone https://github.com/usuario-dueño/proyecto_final.git
```

   Reemplaza la URL de ejemplo por el enlace del repositorio que copiaste anteriormente.

8. Usa `ls` para identificar la carpeta creada al clonar el repositorio y luego utiliza `cd` para acceder a ella:

```bash
ls
cd nombre-de-la-carpeta
```

---

## Paso 4 – Flujo de trabajo colaborativo (pull → editar → commit → push)

### Pull – descargar actualizaciones del código dentro del repositorio

### Commit – registrar los cambios localmente

### Editar el archivo de trabajo

1. Asegúrate de estar dentro de la carpeta del proyecto.
2. Ejecuta `git pull`. Esto trae los cambios que tus compañeros hayan subido al repositorio de GitHub:

```bash
git pull
```

3. Edita el archivo que te corresponde. Abre el archivo `.py` y realiza los cambios que te tocó hacer.
4. Guarda los cambios.

   **Ojo:** no olvides guardar con **Ctrl + S** o mediante **File → Save**.

### Registrar y enviar los cambios

1. Verifica qué cambió:

```bash
git status
```

2. Agrega el archivo modificado al área de preparación (*staging*):

```bash
git add main.py
```

   Si tu archivo tiene un nombre distinto, reemplaza `main.py` por el nombre correcto.

   Si necesitas agregar varios archivos del proyecto, puedes utilizar:

```bash
git add .
```

3. Crea el commit con un mensaje corto y claro:

```bash
git commit -m "Describir brevemente el cambio realizado"
```

4. Envía los cambios al repositorio de GitHub:

```bash
git push
```

5. Si GitHub solicita iniciar sesión mediante el navegador, inicia sesión nuevamente.

---

Después de esto continuamos con la ejecución del programa para diagramar AFD.

## Paso 5 – Ejecutar el diagramador de AFD

1. Instala las dependencias y librerías necesarias:

```bash
pip install networkx matplotlib
```

2. Ejecuta el programa. `python` es el comando para ejecutar el código:

```bash
python Main.py
```

   También puedes utilizar el nombre del archivo en el que se encuentra el código, si es diferente de `Main.py`.
