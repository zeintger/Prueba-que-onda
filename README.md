/**************** PRUEBA de GIT y GITHUB ************************/

Git esta disponible para la mayoria de sistemas operativos (OSX, Windows, Linux)Para sistemas linux basados en Debian se instala desde la consola:
$ sudo apt-get update && apt-get install git

Una vez instalas GIT, debes configurarlo:

git config --global user.name "Nombre"
git config --global user.email "mail@mail.com"

Generando tu Public Key:

$ ssh-keygen

Leyendo tu llave para copiarla a Github:

$ cat ~/.ssh/id_rsa.pub

Arrancando tu proyecto:

$ mkdir ~/nombre-del-directorio # Crea un directorio para usar con Git
$ cd nombre-del-directorio/ # Cambiate al directorio nuevo

$ git init # Iniciando Git

$ touch README.md # Creando nuevo archivo README en formato "markdown"

$ git add README.md # Agregando archivo "README.md" al "index" o "escenario" (stage) 

$ git commit -m "Primer fucking commit" # Realizando la confirmación de los cambios agregados

$ git push origin master # Enviando cambios desde la rama (branch) "master" (local) al "origin" (remoto)

Para clonar un repositorio desde una dirección remota:

$ git clone /path/to/repository

Por ejemplo:

$ git clone git@github.com:zeitnger/Prueba-que-onda.git

Flujo de trabajo

Tu repositorio local esta compuesto por tres "árboles" administrados por git. el primero es tu Directorio de trabajo el cual contiene los archivos, el segundo es el "Index" ("escenario" o "stage")el cual actua como un área intermedia y finalmente el HEAD el cual apunta a el último commit realizado en esa rama (por ejemplo último commit en "master").

add & commit

Puedes proponer cambios (agregarlos a el Index) usando $ git add <archivo>, o $ git add * (agrega todo). Este es el primer paso en el flujo de trabajo básico. Para en realidad hacer commit a estos cambios usa $ git commit -m "Commit message". Ahora el archivo esta incluído en el HEAD, pero aún no en tu repositorio remoto.

Envío de cambios

Tus cambios están ahora en el HEAD de tu copia local. Para enviar esos cambios a tu repositorio remoto ejecuta $ git push origin master. Reemplaza master por la rama a la cual desees enviar tus cambios.

Si no has clonado un repositorio existente y quieres conectar tu repositorio a un repositorio remoto, necesitas agregarlo con git remote add origin Ahora puede subir tus cambios al repositorio remoto selecionado ramas Las ramas son utilizadas para desarrollar funcionalidades aisladas unas de otras. La rama master es la rama por "defecto" cuando creas un repositorio. Usa otras ramas para el desarrollo y fusionalas de regreso a la rama principal al terminar.

crea una nueva rama llamada "feature_x" y cambiate a ella usando:

git checkout -b feature_x regresa a la rama principal git checkout master y borra la rama git branch -d feature_x una rama no está disponible para los demás a menos que subas (push) la rama a tu repositorio remoto git push origin

actualiza & fusiona

para actualizar tu repositorio local al commit más nuevo, ejecuta git pull en tu directorio de trabajo fetch y merge cambios remotos. para fusionar otra rama a tu rama activa (por ejemplo master), utiliza git merge en ambos casos git intenta auto fusionar cambios. Desafortunadamente, esto no es posible todo el tiempo y resulta en conflictos. Tú eres responsable de fusionar esos conflictos manualmente al editar los archivos mostrados por git. Luego de modificarlos, necesitas marcarlos como fusionados con git add antes de fusionar cambios, también puedes dar un vistazo previo usando git diff

etiquetas

es recomendado crear etiquetas para cada versión publicada de un software. esto es un concepto conocido, el cual tambien existe en SVN. Puedes crear una nueva etiqueta llamada 1.0.0 ejecutando git tag 1.0.0 1b2e1d63ff el 1b2e1d63ff se refiere a los 10 caracteres de el commit id al cual quieres referirte con tu etiqueta. Puedes obtener el commit id con git log también puedes usar menos caracteres que el commit id, pero debe ser un valor único.

reemplaza cambios locales

En caso de que hagas algo malo (que de seguro nunca pasa ;) puedes reemplazar cambios locales usando el comando git checkout -- esto reemplaza los cambios en tu árbol de trabajo con el último contenido de HEAD. Los cambios que ya han sido agregados al índice, así como también nuevos archivos, se mantendrán sin cambio.

Si por otro lado quieres deshacerte de todos los cambios locales y commits, puedes traer la última versión del servidor y apuntar a tu copia local principal de esta forma git fetch origin git reset --hard origin/master

datos útiles

Interfaz gráfica por defecto gitk colores especiales para la consola git config color.ui true mostrar sólo una línea por cada commit en la traza git config format.pretty oneline agregar archivos de forma interactiva git add -i

enlaces & recursos

clientes gráficos GitX (L) (OSX, open source) Tower (OSX) Source Tree (OSX, free) GitHub for Mac (OSX, free) guías Git Community Book Pro Git Think like a git GitHub Help A Visual Git Guide
