#RESPUESTAS

¿Qué ventaja tiene registrar las dependencias del proyecto en
requirements.txt en lugar de compartir la carpeta .venv?

Si la otra persona intenta descargar la carpeta .venv será un archivo sumamente pesado; sin embargo, si simplemente consulta el archivo requirements.txt puede descargar las bibliotecas que se requieren para el proyecto y descargarlas por su propia cuenta. 

## 1. El Repositorio Local (Entorno de Trabajo)
*   **Qué es:** Es la carpeta física en tu computadora donde clonaste el proyecto.
*   **Para qué sirve:** Es tu taller activo. Aquí es donde abres los archivos, editas el código, pruebas los *notebooks* de Jupyter y ejecutas las consultas SQL.
*   **Visibilidad:** Todo lo que haces aquí (incluso los `git commit`) se queda únicamente en tu disco duro. Tus cambios son privados hasta que decides subirlos a internet.

## 2. El Fork (Copia Remota en la Nube)
*   **Qué es:** Es una copia exacta de un repositorio que vive en los servidores de GitHub, bajo tu cuenta de usuario. No es un concepto nativo de Git, sino una herramienta de GitHub.
*   **Para qué sirve:** Actúa como un puente seguro. Te permite tener tu propia versión en la nube de un proyecto ajeno o público. Trabajas en tu repositorio local, subes los cambios a tu *fork* en GitHub (`git push`), y desde ahí puedes solicitar que tus mejoras se integren al proyecto original mediante un *Pull Request*.
*   **Visibilidad:** Es tu respaldo en línea y tu punto de colaboración con otras personas.

79. ¿Cómo identificaste el comando necesario cuando la práctica no lo proporcionó?
Generalmente se identifica a través de tres vías: leyendo los mensajes de la propia terminal (Git suele sugerir el siguiente paso lógico cuando falla un comando o al usar git status), consultando la documentación oficial (usando git help <concepto>), o deduciendo la acción necesaria basándose en el flujo de trabajo de Git (por ejemplo, si necesito ver cambios, busco comandos de inspección como diff).

80. ¿Qué diferencia existe entre preparar un archivo para un commit y crear el commit?
Preparar un archivo (git add) simplemente lo mueve al Staging Area (área de preparación); es decir, le avisa a Git que esos cambios específicos se incluirán en la próxima captura, pero aún no se guardan en el historial. Crear el commit (git commit) toma todo lo que está en el Staging Area, crea una captura permanente en el historial del repositorio local y le asigna un mensaje descriptivo.

81. ¿Cómo puedes comprobar en qué rama estás trabajando?
La forma más directa es ejecutando el comando git branch, el cual listará las ramas locales y marcará con un asterisco (*) y un color distinto la rama en la que te encuentras actualmente. También puedes usar git status, cuyo primer renglón siempre indica: "On branch [nombre_de_la_rama]".

82. ¿Cómo puedes determinar qué archivos fueron modificados antes de registrarlos?
Usando el comando git status. Este comando muestra el estado del árbol de trabajo, dividiendo los archivos en "Rastreados pero no preparados" (modificados pero sin git add), "Archivos sin rastrear" (archivos completamente nuevos) y "Cambios a ser confirmados" (los que ya están en el staging area).

83. ¿Cómo puedes observar exactamente qué cambió dentro de un archivo?
Utilizando el comando git diff. Esto te mostrará las líneas exactas que fueron eliminadas (en rojo o con un signo -) y las que fueron agregadas (en verde o con un signo +) en los archivos modificados que aún no han sido preparados (staged).

84. ¿Por qué debe reconstruirse .venv después de obtener un repositorio?
Porque los entornos virtuales (.venv) contienen binarios, ejecutables y rutas absolutas que están fuertemente ligados al sistema operativo y a la computadora específica donde se crearon. Además, son carpetas muy pesadas. En lugar de copiar el entorno, se clona el código fuente y se crea un entorno nuevo y limpio en la máquina local para evitar errores de compatibilidad de rutas y dependencias.

85. ¿Qué relación existe entre requirements.txt y .gitignore?
Trabajan en conjunto para gestionar las dependencias sin ensuciar el repositorio. El archivo .gitignore se encarga de excluir la carpeta .venv para que no se suba a GitHub. Como el entorno virtual no se sube, el archivo requirements.txt actúa como la "receta" que guarda la lista de librerías y versiones exactas (como Pandas o NumPy). Así, cualquier persona que descargue el proyecto puede ignorar el entorno de otro, pero usar el requirements.txt para instalar exactamente lo que necesita.

86. ¿Por qué la colaboración se realiza desde una rama y no directamente desde main?
Para proteger el código principal. La rama main debe contener siempre código estable y funcional (listo para producción). Trabajar en ramas paralelas permite aislar experimentos, desarrollar nuevas funcionalidades o corregir errores sin riesgo de romper el sistema principal. Una vez que el código de la rama paralela es revisado y funciona correctamente, se integra a main.

87. ¿Por qué una solicitud de cambios no requiere crear un Pull Request nuevo?
Porque un Pull Request (PR) está vinculado a la rama, no a un commit específico. Si abriste un PR desde tu rama feature-X hacia main y te piden correcciones, solo necesitas hacer los cambios en tu computadora, crear un nuevo commit y hacer git push a feature-X. GitHub detectará automáticamente los nuevos commits en esa rama y actualizará el Pull Request existente.

88. Después de realizar el merge en GitHub, ¿por qué todavía es necesario actualizar el repositorio local?
Porque el merge (la fusión de las ramas) ocurrió en los servidores remotos de GitHub, no en tu computadora. Tu repositorio local (main en tu máquina) no se sincroniza automáticamente con la nube. Debes ejecutar git pull (o git fetch y git merge) estando en tu rama main local para descargar e integrar los cambios que acaban de ser aprobados en GitHub.