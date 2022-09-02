# lista de comandos 
## https://static.platzi.com/media/public/uploads/command-line-cheat-sheet_f2552bde-3bb0-4b1c-a1a7-dbd40095fa4f.pdf 

# change directory 
```
cd 

# operadores ruta relativa . ..

cd ../..

clear # contrl l 
```


# para ver en gigas y megas lectura humana

ls -lh

```
ls -la  # muestra incluyendo archivos ocultos 

ls -lS  # ordena por tamano 

ls -lSh

ls -lr muestra de reversa la listada alfabetica 

tree  # despliega todos los directorios como un arbol 

tree -L 2  #profundisa en niveles segun el numero

```

# file para  que describa  un archivo 


# manipulando archivos y directorios 



```
mkdir miDirectorio

touch miArchivo 

mkdir dir1 dir2 dir3 


cp file1 file_bk

mv file_bk .. # mover atras

mv file_bk fileCopy #Renombrar y funciona con directorios 

rm fileCopy # se borra total 

rm -i miArchivo 

rm -r miDir #borrar directorios

rm -rf miDir # borra forzando sin importar nada 

rm -ri

```

# Explorando archivos 

```
# yo lorem

 lorem -p 20 > file.md 


```

```
head file.md # primeras 10 lineas cualquier archivo

head file.md -n 15 # me muestra las primeras 15 lineas del archivo de texto 

tail file.md # ultimas 10


less file.md  # entra en una forma interactiva que permite hacer escrol y hay algo muy util  si colocamos / podemos hacer busqueda de palabras 

```

para salir damos q 


```
xdg-open file.md 

```


# abrir sistema de archivos desde terminal

```
nautilus 

nautilus Documentos/
``` 

## yo tengo otro gestor , se llama en terminal exo-open y es mejor 

```
 exo-open Documentos/

 exo-open .

```



# Que es un comando?

## puede ser 4 cosas

### Un programa ejecutable y  estos ejecutables  normalmente se guardan el la ruta /usr/bin

```
cd ..
cd ..

cd /usr/

cd bin/

exo-open .
```

### Comando de utilidad de la shell 
vienen dentro de la shel

### Una funcion de shell 

### Un alias 

# con type nos muestra la naturaleza de los comandos 

```
type cd 

type mkdir 

type ls # y notamos que ls es un alias hacia --'ls --color=auto'
```

## vamos a crear un alias

```
alias l="ls -lh "
l
# los alias no duran para toda la vida , solo son temporales por ahora 
```
## ayuda 

```
help cd  
cd --help 
```

# man manual del usuario de un comando y tambine info y whatis

```
man lorem

info lorem

whatis lorem
```

# wildcards 
## encontrar patrones o realizar busquedas avanzadas 

```
touch file.txt dot.txt dot2.txt index.html datos1 datos123 abc

ls *.txt

ls datos*

ls datos?

ls datos???

ls [[:upper:]]*

ls-d [[:upper:]]*
ls *[A-Z]*

ls [ad]*
```


# redirecciones como funciona la shell 

## shell 
                    stdout 1
stdin 0 -> comando =>         pc 
                    stderr 2


```
ls Descargas/

ls Descargas/ > testArchivos.txt

less testArchivos.txt

## para concatenar o unir los archivos  uso >>

ls Imágenes/ >> testArchivos.txt 

ls Imágenes/ >> testArchivos.txt 

ls poihpolhij > error.txt

head error.txt # y resulta que no tiene nada porque lo unico que redirije es el estandar output si quiero el erroroutput pongo 2 

ls poihpolhij 2> error.txt


# si quiero redirigir ambos 


ls poihpolhij >ouput.txt 2>&1

# aqui dice ejecuta esto no importa que comando sea y lo vas a redirigir a ouput.txt

ls Imágenes/ >ouput.txt 2>&1

head ouput.txt 

```

# pip operator 

nos permite ejecutar un comando que su estandaroutput pase como estandar input a otro comando 

```
echo "Hola platzi"
 
less error.txt 
less output.txt 

cat error.txt output 



```

```
ls -lh | less   # | ese simbolo es el pipe operator , la salida de ls -lh la redirigi a less 



# tee  hace lo mismo que el < para generar archivo pero

ls -lh | less |tee outputEspecial.txt


ls -lh |tee outputEspecial.txt | less

# pasar a traves de un filtro sort de ordenar 

ls -lh | sort |tee outputEspecial.txt | less



```

## cowsay  genera una  un texto con vaquita
## lolcat  cambia el texto color 

```
cowsay "hola"
echo "holaaa platzi" | lolcat
cowsay "holaaa " | lolcat

cowsay "holaaa " | lolcat |tee vaca.txt


```

# encadenando comandos : operadores de control 

simbolos reservados por la terminal que nos permiten ejecutar mas de un comando o encadenarlo s, se puede asincrono o sincrono  si se cumple un comando exitosamente se cumpla otro 

# correr comandos de manera sincrona 
```
ls; mkdir holi; cal 


```

# ejecutar de manera asincrona 
osea que por cada comando va a abrir una shell en segundo plano,   osea va a usar un hilo del procesador por comando 

```
ls & date & cal
```

# correr comandos de manera condicional  operador and &&

vamos a crear un directorio y si este se crea satisfactoriamente quiero que me mueva a este directorio 

```
mkdir test && cd test

# supongamos    que lo hago de manera incorrecta 

cd asdfasdf && touch  archivo.txt && echo "archivo creado  "
```


## opeardor or ||

```
cd asdfasdf || touch  archivo.txt || echo "archivo creado  "

ls 

cd a;lsdfkj || echo "texto"

```

# Como se manejan los permisos 


-     un archivo normal

d     un directorio

l     un link simbolico

b     un archivo de bloque especial. son archivos que manejan la informacion de los bloques de datos como una usb 


(usuario)
dueno          grupo          world

rwx            r-x            r-x 

1 1 1         1 0 1           1 0 1

  7             5               5         modo octal 




octal    binario        permisos

0           000         ---
1           001         --x
2           010         -w-
3           011         -wx
4   `       100         r--
5           101         r-x
6           110         rw-
7           111         rwx


modo simbolico

u           solo para el usuario
g           solo para el grupo
o           solo para otros(es el world)
a           aplica para todos 

# Modificando permisos en la terminal 

```
mkdir sandbox
cd sandbox/

> mitexto.txt


> mitexto.txt


 cat > mitexto.txt 

Hola amigos

Desde Colombia

cat mitexto.txt 


ls -l

-rw-rw-r-- 1 srandersj srandersj 28 jun 29 17:05 mitexto.txt

chmod 755 mitexto.txt

-rwxr-xr-x 1 srandersj srandersj 28 jun 29 17:05 mitexto.txt

```

## vamos a quitarle los permisos solo al usuario  u-r  == al usuario le voy a quitar el permiso de lectura 


```
chmod u-r mitexto.txt 

--wxr-xr-x 1 srandersj srandersj 28 jun 29 17:05 mitexto.txt

cat mitexto.txt

cat: mitexto.txt: Permiso denegado


chmod u+r mitexto.txt

cat mitexto.txt
```


ahora vamos a quitarle ejecucion x a usuario y vamos a darle a grupo y otros escritura w 
```
chmod u-x mitexto.txt

chmod go=w mitexto.txt 

-rw--w--w- 1 srandersj srandersj 28 jun 29 17:05 mitexto.txt

```

## como cambiar de usuario 
## primero necesitamos saber quien somos  con whoami
## id nos otorga el uid  y mucha info 

```
whoami

id
```
## cambiamos a un usuario con su

```

su root  #fallo  entonces usaremos sudo su 

sudo su 

passwd


whoami 

```

si coloco cd me lleva a home , pero el home del root es diferente al home del usuario

```
cd 
```


## vamos a crear un archivo 

```
touch rootFile


su srandersj


ls -l


-rw--w--w- 1 srandersj srandersj 28 jun 29 17:05 mitexto.txt
-rw-r--r-- 1 root      root       0 jun 29 18:02 rootFile


rm rootFile 

rm: ¿borrar el fichero regular vacío 'rootFile'  protegido contra escritura? (s/n)


# pero no me va a dejar 

```

```
sudo rm rootFile

```

# como configurar variables de entorno  

las variables de entorno  tiene una configuracion y valores y se pueden modificar a traves de las variables de entorno 


links simbolicos= son un acceso directo desde la terminal 
```
ln -s Escritorio/dataScienceSchool/ desarrollo

cd desarrollo 

```

## vamos a ver las variables de entorno

```
printenv

```


## imprimir una variable de entorno 

```

echo $HOME

echo $PATH  # todas las rutas de los binarios que se ejecutan en nuestro sistema 

```

## cuando instalamos nuevos binarios hay diferentes manejadores de paquetes entonces estos manejadores van instalan estos binarios pero no todas las veces las rutas de estos binarios estan entonces nos toca agregarlos a la variable path 

## MODIFICAR ARCHIVO PATH 
```
para poder modificar el PATH modificamos el .bashrc y para ver este archivo vamos a 

cd ~  y usamos ls -la 
```

## vamos a crear alias permanentes 
### modificaremos variables de entorno 
```

ls -la 

# nos interesa 
-rw-r--r--  1 srandersj srandersj      4262 mar  7 09:15 .bashrc

para mac es zshrc
```
modificaciones en .baschrc



alias l='ls -lh'

VARIABLE_INTERNA="Una variable interna"




volvemos a la terminal y volvemos a cargar bash

```
bash

echo $VARIABLE_INTERNA

l

```

## vamos a ver nuestra variable path


```
echo $PATH

mkdir binFalse

pwd

```
### modificaremos variables de entorno 

alias l='ls -lh'

VARIABLE_INTERNA="Una variable interna"

PATH=$PATH:/home/srandersj/binFalse     # vamos a decir que path es igual a variable pa y ademas agregale una nueva ruta para eso son los dos puntos 



# Comandos de busqueda 

cuando buscamos archivos o directorios por ejemplo cuando buscamos .log  que son archivos de texto plano que recopila la informacion de un archivo en ejecucion por ejemplo cuando abrimos google  se ejecuta crea un log para descubrir a que pagina visitas etc 


```
which code    # ayuda a encontrar ruta a nuestros binarios , which busca en todas las rutas del PATH para encontrar un binario 

find ./ -name file  # nos permite encontrar un archivo y lo primero es ponerle la ruta donde lo va a buscar y el lo hara buscando en todas las carpetas 

find ./ -name '*.txt' 

find ./ -name '*.txt' | less


find ./ -type d -name Escritorio         # f que solo busque files d que busque directorios


```

vamos a buscar logs

```
find ./ -type f -name '*.log'

```

buscar archivos mayores  a 20MB

```
find ./ -size 20M
```


# su majestad : grep 

grep permite encontrar coincidencias de una busqueda dentro de un archivo de texto 


```
grep Towers movies.csv   # aqui esta con key sensitive


grep -i  Towers movies.csv  # aqui esta sin key sensitive osea que ignore si es mayusculas o miniscula

```

## si quiero saber cuantas ocurrencias

```
grep -c the movies.csv

1013

grep -ci the movies.csv 
2912

```

## que no coincidan 

```
grep -v Towers movies.csv 

grep -v Towers movies.csv > sinTowers.txt
```

```
wc movies.csv   # contar cuantas palabras hay 
  9126  30006 477779 movies.csv

wc -l  movies.csv  #numero de lineas 
9126 movies.csv  

wc -w  movies.csv   # numero de palabras
30006 movies.csv


wc -c  movies.csv  # numero de bits  
477779 movies.csv

```

# Utilidades de red 


```
ifconfig

ping www.google.com  # nos dice si una pagina esta activa 

curl www.google.com # lo que hace es traer un archivo en manera de texto 

curl www.google.com >index.html

less index.html 

wget # es decir trae desde internet  , funciona similar a curl sin embargo  descarga el archivo directamente 


traceroute  # nos va a decir cuando nosotros visitamos un sitio a todos los puntos que nos vamos a conectar o todas las computadoras por las que nos vamos a conectar para llegar a la direccion 

netstat -i # va a mostrar los dispositivos de red 

curl https://www.collinsdictionary.com/images/full/horse_84139573_1000.jpg?version=4.0.273 -o 1.png  #  aqui descargue un cabolloooo jajajaj 



```

# comprimiendo archivos tar y zip 

c es comprimir
x es para descomprimir 
```
mkdir toCompress

tar -cvf compres.tar toCompress/

tar -cvzf compres.gz toCompress/

# para descomprimir


tar -xzvf compres.gz


comprimir zip

zip -r toCompressInZip.zip toCompress/

unzip toCompressInZip.zip









```

# manejo de procesos 


```
ps # nos muestra los procesos o comandos que estan corriendo actualmente 



cat & ls

ps

kill 2022

top  # si presiono h me muestra los comandos para filtrar


```

# editores de texto en la terminal 

```
vim 

```

# personalisar la terminal 

colores , iconos , tipo de fuente

```
sudo apt install tilix


vamos a cambiar de shell 

 sudo apt install zsh  #

vamos a volverla shell por defecto

chsh -s $(which zsh)   # which lo que hace es buscar la ruta de zsh y mandarla al comando chsh change shell


instalamos  

 https://ohmyz.sh/#install

 sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"


 ahora instalamos power https://github.com/romkatv/powerlevel10k


git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k


nano .zsh


descargamos las fuentes








```