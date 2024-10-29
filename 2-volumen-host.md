# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)


docker run -d --name contenedorp3 -p 80:80 -v C:\Users\ariel.morales\Desktop\2024B\construc\nginx\html:/usr/share/nginx/html nginx:alpine


### ¿Qué sucede al ingresar al servidor de nginx?

Da un error de tipo 403 Forbidden.

### ¿Qué pasa con el archivo index.html del contenedor?
El archivo index.html predeterminado del contenedor es reemplazado por el contenido de la carpeta html en el host. Si la carpeta html del host está vacía, el contenedor no mostrará nada

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar nuevamente al servidor de nginx, se muestra el contenido del template descargado

### Eliminar el contenedor
docker rm -f contenedorp3

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
Al crear nuevamente el contenedor, nginx muestra el mismo contenido del template descargado previamente, no se borró el contenido

### ¿Qué hace el comando pwd?
pwd muestra el directorio de trabajo actual en la terminal.

Si quieres incluir el comando pwd dentro de un comando de Docker, lo puedes hacer de diferentes maneras dependiendo del shell que estés utilizando.


### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

