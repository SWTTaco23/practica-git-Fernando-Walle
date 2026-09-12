# Creación y sincronización de repositorios con Git y GitHub

**Nombre:** Fernando Emir Walle Hernandez
**Matrícula:** 2630316
**Práctica:** Creación y sincronización de repositorios con Git y GitHub

## Objetivo

La idea de esta práctica es entender cómo funciona el flujo de trabajo entre un repositorio que tengo en mi computadora y otro en GitHub. No solo subir archivos, sino ver cómo se mueve la información en los dos sentidos.

## Procedimiento

Primero creé una carpeta llamada `practica-git-Fernando-Walle` y ahí abrí PowerShell para empezar a trabajar. Dentro inicié el repositorio con `git init`. Después renombré la rama principal a `main` con `git branch -M main`, porque por defecto a veces Git la llama `master` y ya no se usa tanto ese nombre. Luego creé dos archivos, `README.md` (este mismo) y `datos.txt`.

Con `git status` revisé qué archivos estaban en untracked files, y con `git add` los mandé al staging zone. Volví a escribir `git status` para confirmar que ya estaban listos para ser confirmados, y finalmente hice el primer commit con `git commit -m`, que guarda cómo estaban los archivos en ese momento, junto con un mensaje que describe el cambio.

Después entré a GitHub y creé un repositorio nuevo con el mismo nombre de la carpeta, marcado como **público**. Al crearlo tuve cuidado de **no marcar las opciones de agregar README, .gitignore ni licencia automáticamente**, porque si lo hacía el repositorio remoto ya no quedaba vacío y podía causar conflictos al hacer el primer push desde mi repo local. Copié la URL que me dio GitHub y la vinculé a mi repo local con `git remote add origin https://github.com/SWTTaco23/practica-git-Fernando-Walle.git` y con `git remote -v` comprobé que la conexión quedó bien hecha. Y para subir todo lo que ya tenía commiteado localmente, usé `git push -u origin main`.

Para probar el flujo de GitHub a local, entré directamente a la página del repositorio en GitHub y edité el archivo `datos.txt` desde ahí, agregando la línea "Este archivo fue modificado desde GitHub", y guardé el cambio con un commit hecho desde la misma web.

Volví a PowerShell y escribí `git pull origin main` y al abrir `datos.txt` en mi laptop, ya aparecía la línea que había agregado desde GitHub. Modifiqué otra vez `datos.txt` desde mi computadora, agregando la línea "Este archivo fue modificado desde el repositorio local". Repetí el proceso de siempre: `git status` para ver el cambio detectado, `git add` para prepararlo y `git commit -m "Actualización desde repositorio local"` para confirmarlo.

Finalmente, con `git push` mandé ese commit a GitHub y cuando entré a GitHub ahí estaba reflejado el cambio.

## Comandos utilizados y su función

| Comando | Para qué sirve |
|---|---|
| `git init` | Inicializa un repositorio Git en la carpeta actual |
| `git branch -M main` | Renombra la rama actual a `main` |
| `git status` | Muestra el estado de los archivos |
| `git add` | Agrega todos los cambios al área de preparación |
| `git commit -m "mensaje"` | Guarda una versión de los cambios con una descripción |
| `git remote add origin URL` | Vincula el repositorio local con uno remoto llamado `origin` |
| `git remote -v` | Muestra los remotos configurados y sus URLs |
| `git push -u origin main` | Sube los commits al remoto y enlaza la rama local con la remota |
| `git pull origin main` | Descarga y combina los cambios del remoto con el repositorio local |
| `git push` | Sube los nuevos commits al remoto ya configurado |

## Archivos del repositorio

- **README.md**: este documento, con la explicación de todo el proceso.
- **datos.txt**: archivo de prueba que fue modificado tanto desde GitHub como desde mi computadora, para comprobar la sincronización en ambos sentidos.

## Conclusión

Esta práctica me sirvió para entender que Git es un sistema que lleva un historial completo de cambios y que permite trabajar de forma bidireccional, puedo modificar algo en la nube y traerlo a mi pc, o modificar algo local y mandarlo a la nube, sin perder información en el camino.
