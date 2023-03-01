Comandos para un Repositorio Local
----------------------------

git init: para inicializar el repositorio git y el staged
git add nombre_del_archivo.txt: enviar el archivo al staged
git status: ver el estado, si se requiere agregar al starget o si se requiere commit
git config --list: para ver la lista de configuraciones hechas
git config --list --show-origin: para mostrar las configuraciones y sus rutas
git config -l: Sirve para mostrar una lista de configuraciones uno de los usos mas utiles es ver el user.name y el user.email
git rm --cached nombre_del_archivo.txt: para eliminar el archivo del staged(ram)
git rm nombre_del_archivo.txt: para eliminar del repositorio
git add: agregar un archivo a staging.
git commit -m “mensaje”: guardar el archivo en git con un mensaje.
git branch: crear una nueva rama.
git checkout: moverse entre ramas.
git diff “codigo de version 1” “codigo de version 2”: comparar cambios entre versiones.
git diff: comparar directorio con staging.
Si por algún motivo te equivocaste en el nombre o email que configuraste al principio, lo puedes modificar de la siguiente manera:
git config --global --replace-all user.name “Aquí va tu nombre modificado”
O si lo deseas eliminar y añadir uno nuevo
git config --global --unset-all user.name :Elimina el nombre del usuario
git config --global --add user.name “Aquí va tu nombre”
git config --global --add user.email “Aquí va tu email”
git show: nos muestra todos los cambios del archivo en cuanto a contenido se refiere
git log nombre_de_archivos.extensión: histórico de cambios con detalles
ls: listado de carpetas en donde me encuentro. Es decir, como emplear dir en windows.
ls -al hace un listado de archivos otras formas es ls -l o ls -a
pwd: ubicación actual
mkdir: make directory nueva carpeta
touch archivo.extensión: crear archivo vacío
cat archivo.extensión: muestra el contenido del archivo
history: historial de comandos utilizados durante esa sesión
rm archivo.extensión: Eliminación de archivo
comando --help: ayuda sobre el comando
Si agregamos un commit erroneo o nos falto informacion en ese commit hacemos un git commit --amend
git merge nombre-de-la-rama fusiona dos ramas o por asi decirlo trae los cambios de una a otra
Con git branch -d (rama) se elimina cualquier rama del repositorio
Tags

------------------------------------------------------
Tags: Los tags nos indican una version de forma especial ya que los tags son unicos al igual que las versiones pero podemos agregar el nombre que queramos
Crear un nuevo tag y asignarlo a un commit: git tag -a nombre-del-tag id-del-commit.
Borrar un tag en el repositorio local: git tag -d nombre-del-tag.
Listar los tags de nuestro repositorio local: git tag o git show-ref --tags.
Publicar un tag en el repositorio remoto: git push origin --tags.
Borrar un tag del repositorio remoto: git tag -d nombre-del-tag y git push origin :refs/tags/nombre-del-tag.

------------------------------
Una forma de recortar comandos es con el alias ej: alias observar="cat texto.txt(o el archivo al que quieras vincular este alias)"
git log --all --graph --decorate --oneline Con este comando podemos ver una grafico de lo que hemos hecho

COMANDOS DE REPOSITORIO REMOTO
----------------------------------------------

En caso de ser http copiamos el link que nos aparece en github
git remote add origin(origin puede ser cambiado por otro nombre pero lo recomendable es que se use este mismo) Link
si escribimos en consola git remote nos aparece origin en este caso
git remote -v(osea verbal) nos aparecen los link que estan vinculados
Despues hacemos el git pull origin(Importante) master(O la rama que desees traer al repositorio)
Despues si necesitas subirlo haces git push origin master(o la rama que desees mandar a github)
En el caso de que se reuse a unir lo que tenemos en el local con la nube por tener archivos extra a los que tenemos en el rep local podemos usar el comando: git pull origin master --allow-unrelated-histories
Para clonar un repositorio hacemos un git clone link

Crear tus llaves SSH en el local
-----------------------------------------------------------
Para crear tus llaves SSH en el local usamos el comando:
ssh-keygen -t(este es el algoritmo) rsa(Este es otro) -b 4096(la la b y el numero decimos que tan compleja queremos la llave) -C "Email"
Para asegurarse que si funciono escribes Eval $(ssh-agent -s)
Asi se añade ssh-add (ubicacion de la carpeta .ssh)/id_rsa

Para unir Github con SSH local
-------------------
Despues copiamos el link de github pero en la opcion ssh
y antes debimos haber agregado las llaves en configuraciones y la opcion ssh y gpg keys en la cual añadimos rsa.pub ya que es la llave publica
set-url sirve para cambiar la url en este caso de https a ssh despues origin y por ultimo el link

Rebase
------------------------------
Rebase es mala practica
El rebase sirve para unir una rama a otra sin necesidad de un merge solo que a costa de quitar parte del historial
Rebase es recomendable solo para local
git rebase master(o la rama que queramos traer)
primero rebase a la rama que vamos a unir la historia principal y luego otro al contrario

git stash
--------------------------
El comando git stash guarda el trabajo actual del Staging en una lista diseñada para ser temporal llamada Stash, para que pueda ser recuperado en el futuro.
git stash pop volvemos en el punto que modificamos algo antes de hacer el git stash
git stash list muestra cual fue el ultimo commit
git stash branch (nombre de la nueva rama)
para borrar un stash usamos git stash drop

Git Clean
----------------------------
git clean --dry-run Muestra que archivos puede borrar
git clean -f Borra los archivos
git clean solo borra las cosas que puede indexar y para que no indexe podemos usar el .gitignore

Cherry-pick
------------------------------
Cherry-pick es mala practica
git Cherry-pick n° del commit antiguo
Sirve para traer cambios de commits anteriores a otras ramas

Reflog
---------------------------
git reflog nos muestra todos pero todos los cambios
En caso de cagarla git reflog ayuda(¡Solo en caso de emergencia!) y se combina con el git reset --hard

Git Grep
-----------------------------
git grep Busca cuantas veces se repite algo en el codigo
git grep color en este caso muestra la palabra color
git grep -n color ahora muestra la linea
git grep -c la cuenta cuantas veces y donde uso la expresion la así sea en una palabra como platzi
git grep -c "<p>" para buscar una etiqueta debemos usar el ""
git log -S "Cabecera" Busca todos los commits en donde use la palabra cabecera

Git Shortlog
------------------------------
git shortlog muestra que comandos ha hecho cada persona
git shortlog -sn solo muestra las personas que han hecho ciertos commits
git shortlog -sn --all Muestra todos los commits incluyendo los borrados
git shortlog -sn --all --no-merges En este caso no muestra los merges
git config --global alias.stats"git shortlog -sn"
y ahora el git stats es = al comando git shortlog -sn

Git Blame
----------------------------------------
si queremos saber quien hizo que usamos git blame "archivo"
git balme -c "Archivo" identa todo
git blame --help ayuda a ver como usar el comando de forma detallada
git blame Css/estilos.css -L35,53 muestra solo esas lineas
git blame Css/estilos.css -L35,53 -c De esta forma podemos ver todo identado
git branch -r nos muestra las ramas remotas
git branch -a muestra todas las locales y remotas


