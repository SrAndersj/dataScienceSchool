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