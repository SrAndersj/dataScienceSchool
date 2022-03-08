# wget  es descargar un archivo de internet
## -O me permite especificar el nombre del archivo 

```
wget -O anaconda.sh https://repo.anaconda.com/archive/Anaconda3-2021.11-Linux-x86_64.sh
```

bash anaconda.sh


# para abrir un jupyter notbook en terminal

```
jupyter-notebook
```

# para abrirlo mediante VS
el punto significa aqui osea que abra la siguiente carpeta 
```
code .


```

# crear y actualizar ambientes 

```
conda info --envs

```

# crear nuevo ambiente 
si uno no especifica una version en especificon instala la mas reciente 

```
conda create --name py35  python=3.5 pandas

```
```
# To activate this environment, use
#
#     $ conda activate py35
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

# para ver todos los paquetes que se instalaron y versiones

```
conda list 

```
# filtrar lista de paquetes 

```
conda list pandas 

```

# ahora imaginemos que queremos actualizar un paquete a la mas reciente 

```
conda update pandas
```

# para instalar una version especifica 

```
conda install pandas=1.2 # esta version pide otra version de python 3.7 o superior 

conda install python=3.9 pandas=1.2
```

# renombrar 

```
conda create --name py39 --copy --clone py35
```

# Eliminar ambientes  y librerias 

```
 conda remove pandas

 conda env remove --name py35

# lista de ambientes 
conda env list

conda deactivate

```

# comandos avanzados 
imagina que un dia quieres instalar un paqueta
lo normal es ``` install boltons``` pero dice The following packages are not available from current channels:


```
conda install --channel conda-forge boltons
```


ahora supongamos que ya no lo necesito y lo quiero eliminar y ademas de usar el remove

podemos usar ``` conda install --revision ``` esto es para poder regresar a una version anterior o superior del ambiente (superior se reiere a actualizacion de paquete o instalacion )

```
conda list --revision

```

volvemos a version ambiente anterior 

```
conda install --revision 0

conda list boltons # y vemos que ya no esta boltons 
```

# compartir ambientes con otras personas
exportar un ambiente es bueno porque otras personas podran ejecutar el mismo codigo en el mismo ambiente 
para exportar un ambiente 

```
conda env export 


```

```
conda env export --no-builds
```

```
conda env export --from-history  # esta es la mejor manera

```

aqui como un archivo 

```
conda env export --from-history --file environment.yml
ls
```

# ahora como instalar este ambiente 

removemos ambiente actual que no sea el base 

```
conda deactivate

conda env  remove --name py39
```

```
ls
conda env create --file environment.yml

```

# acelerar la creacion de ambientes virtuales con Mamba 

```
conda install --channel conda-forge mamba

```

```
mamba --help 

```

vamos a instalar un enterono con mamba pero primero reomver el py 39


```
conda env remove --name py39

```


```
mamba env create --file environment.yml

```
# Divide y venceras 

crear multiples ambinetes para un proyecto  con snakemake