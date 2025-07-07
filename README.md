# Laboratorios Docker
Aprende a contenerizar con Docker. Domina los comandos básicos, las imágenes, las redes, el almacenamiento y Docker Compose para aplicaciones multicontenedor.
---

### Comandos para información del sistema y contenedores

---

**`docker version`**
Este comando te muestra la versión de Docker que tienes instalada en tu sistema, tanto la del cliente (la línea de comandos) como la del servidor (el demonio de Docker).

**`docker ps`**
Muestra una lista de todos los contenedores que se están ejecutando en este momento. La información que ves incluye el ID del contenedor, la imagen que está utilizando, el comando que se ejecutó, cuándo se creó, su estado, el puerto que expone y el nombre asignado.

**`docker ps -a`**
Similar a `docker ps`, pero este comando muestra **todos** los contenedores, incluyendo los que están detenidos. La `-a` significa "all".

**`docker images`**
Muestra una lista de todas las imágenes de Docker que tienes descargadas en tu máquina.

**`docker images -a`**
Al igual que con los contenedores, la opción `-a` muestra todas las imágenes, incluyendo las intermedias que no tienen nombre ni etiqueta.

**`docker images ps`**
Este comando no es un comando de Docker válido. Parece una mezcla de `docker images` y `docker ps`. Si quieres ver las imágenes que están siendo utilizadas por contenedores, puedes usar `docker ps` y ver la columna `IMAGE`.

**`docker images -q`**
Muestra solo los IDs de las imágenes, lo que es útil para usarlos en otros comandos. La `-q` significa "quiet".

### Comandos para la gestión de contenedores

---

**`docker run -d <nombre_imagen>`**
Este es uno de los comandos más importantes. Crea y ejecuta un nuevo contenedor a partir de una imagen.
* `run`: Crea y ejecuta un contenedor.
* `-d`: Ejecuta el contenedor en segundo plano (modo "detached"). El contenedor se ejecutará sin que veas su salida en la terminal.

**`docker run -d --name <name_container> <nombre_imagen>:<tag>`**
Similar al anterior, pero le asigna un nombre específico al contenedor con la opción `--name`. Esto facilita su manejo, ya que puedes referirte a él por su nombre en lugar de su ID. También puedes especificar una versión específica de la imagen usando el `<tag>`. Si no especificas un tag, Docker usa el tag `latest` por defecto.

**`docker stop <nombre_imagen>`**
Detiene un contenedor en ejecución de forma "graciosa", enviando una señal para que finalice su proceso. Si el proceso no se detiene después de un tiempo, Docker lo detiene forzosamente.

**`docker rm <nombre_imagen>`**
Elimina un contenedor. Solo puedes eliminar contenedores que no se estén ejecutando. Si intentas eliminar un contenedor en ejecución, Docker te dará un error.

### Comandos para la gestión de imágenes

---

**`docker pull <nombre_imagen>:<tag>`**
Descarga una imagen desde un registro de Docker (como Docker Hub) a tu máquina local. Puedes especificar un tag para descargar una versión específica.

**`docker rmi <nombre_ubuntu>`**
Elimina una imagen de tu máquina local. Solo puedes eliminar una imagen si no hay contenedores que la estén usando.

**`docker rmi $(docker images -a q)`**
Este es un comando muy útil y potente.
* `docker images -a -q`: Como ya vimos, esto lista los IDs de **todas** las imágenes.
* `$()`: Esto se llama sustitución de comando en Bash (la terminal que usas). Significa que el resultado del comando dentro de los paréntesis se pasa como argumento al comando exterior.
* `docker rmi`: El comando para eliminar imágenes.
En resumen, este comando elimina todas las imágenes de tu sistema. ¡Úsalo con precaución!
