# Introducción a MLOps Zoomcamp con PyCharm

Las instrucciones originales del curso están orientadas principalmente a GitHub Codespaces o a una máquina virtual con Ubuntu. Este proyecto se puede ejecutar localmente usando Fedora, PyCharm, Python 3.12 y un entorno virtual.

## 1. Instalar Python 3.12

Aunque el sistema tenga otra versión de Python, para este curso se recomienda Python 3.12 por su compatibilidad con las librerías de ciencia de datos.

En Fedora, abre una terminal y ejecuta:

```bash
sudo dnf install python3.12 python3.12-devel
```

Comprueba la instalación:

```bash
python3.12 --version
```

El resultado debería comenzar con `Python 3.12`.

No es necesario reemplazar la versión de Python utilizada por el sistema operativo. Python 3.12 se usará solamente dentro del entorno virtual de este proyecto.

## 2. Crear el entorno virtual con Python 3.12

En este proyecto ya existe `.venv`, pero utiliza Python 3.14. Para no sobrescribirlo, crea un entorno nuevo llamado `.venv312`.

Abre la terminal integrada de PyCharm mediante `View → Tool Windows → Terminal` y ejecuta desde la raíz del proyecto:

```bash
/usr/bin/python3.12 -m venv .venv312
```

Activa el entorno:

```bash
source .venv312/bin/activate
```

Comprueba su versión:

```bash
python --version
```

El resultado debe comenzar con `Python 3.12`.

### Seleccionar el entorno existente en PyCharm

Una vez creado `.venv312`, no necesitas encontrar `/usr/bin/python3.12` desde el selector de PyCharm. Selecciona directamente el Python del entorno virtual:

1. Abre `File → Settings`.
2. Entra en `Python → Interpreter`.
3. Selecciona `Add Interpreter → Add Local Interpreter`.
4. Elige `Select existing` o `Existing environment`, dependiendo de la versión de PyCharm.
5. Pulsa el botón para buscar un ejecutable.
6. Dentro del proyecto, selecciona:

   ```text
   /home/SORTIZ/PycharmProjects/mlops-zoomcamp/.venv312/bin/python
   ```

7. Confirma con `OK` y selecciona ese intérprete para el proyecto.

También puedes escribir o pegar la ruta completa en el campo del intérprete si el explorador de archivos no muestra las carpetas que comienzan con punto.

### Si deseas crear el entorno desde la interfaz

El Python 3.12 del sistema está instalado en:

```text
/usr/bin/python3.12
```

En el diálogo para crear un `Virtualenv`, puedes pegar esa ruta directamente en **Base interpreter**. Sin embargo, crear primero `.venv312` desde la terminal suele ser más sencillo y evita problemas con el selector de archivos.

> No es necesario instalar Anaconda para seguir este tutorial. El entorno virtual de PyCharm mantiene las dependencias del proyecto aisladas del resto del sistema.

## 3. Instalar las dependencias

Comprueba que `.venv312` esté activo y que use Python 3.12:

```bash
python --version
```

Instala las dependencias necesarias para el notebook introductorio:

```bash
python -m pip install pandas scikit-learn pyarrow jupyter ipykernel
```

Estas dependencias cumplen las siguientes funciones:

- `pandas`: carga y manipulación de datos.
- `scikit-learn`: preparación de variables y entrenamiento del modelo.
- `pyarrow`: lectura de archivos en formato Parquet.
- `jupyter` e `ipykernel`: ejecución de notebooks.

Comprueba que las librerías se hayan instalado correctamente:

```bash
python -c "import pandas, sklearn, pyarrow; print('Dependencias correctas')"
```

## 4. Abrir el notebook en PyCharm

Abre el archivo:

```text
01-intro/duration-prediction.ipynb
```

En la parte superior del notebook:

1. Selecciona como kernel el intérprete virtual del proyecto.
2. Comprueba que corresponda a `.venv/bin/python` o `.venv312/bin/python`, según el nombre elegido.
3. Ejecuta cada celda usando el botón triangular que aparece junto a ella.

PyCharm puede iniciar automáticamente un servidor Jupyter administrado. Si necesitas configurarlo manualmente, utiliza `Tools → Add Jupyter Connection` y selecciona un servidor administrado por el IDE.

## 5. Comprobar Docker

Docker ya está instalado en el sistema. No ejecutes los comandos `apt` del README original, porque están destinados a Ubuntu y este entorno utiliza Fedora.

Desde la terminal integrada de PyCharm ejecuta:

```bash
docker run hello-world
```

Si aparece el mensaje de bienvenida de Docker, la instalación funciona correctamente.

PyCharm actúa como entorno de desarrollo, pero Docker continúa ejecutándose como un servicio del sistema.

## 6. Trabajar con Git desde PyCharm

El proyecto está conectado al siguiente repositorio remoto:

```text
https://github.com/ortizsebastianm/mlops-zoomcamp.git
```

Desde PyCharm puedes utilizar:

- `Git → Commit` para crear un commit.
- `Git → Push` para subir cambios a GitHub.
- `Git → Pull` para descargar cambios del repositorio remoto.

Antes del primer commit, conviene añadir estas entradas al archivo `.gitignore`:

```gitignore
../.venv/
.venv312/
.idea/
__pycache__/
.ipynb_checkpoints/
```

## Resumen

Para adaptar el módulo introductorio a PyCharm:

1. Instala Python 3.12 sin reemplazar el Python del sistema.
2. Crea un entorno virtual basado en Python 3.12.
3. Selecciona ese entorno como intérprete de PyCharm.
4. Instala las dependencias de ciencia de datos y Jupyter.
5. Abre el notebook y selecciona el mismo entorno como kernel.
6. Comprueba Docker desde la terminal integrada.
7. Usa las herramientas de Git de PyCharm para guardar y publicar los cambios.

Instrucciones originales: [MLOps Zoomcamp — Module 1: Introduction](https://github.com/DataTalksClub/mlops-zoomcamp/blob/main/01-intro/README.md).
