Clonar un repositorio
```shell
git clone "dirección del repositorio"
```

Hacer la carpeta .git en una ruta
```shell
git init 
```

Hacer la rama main
```shell
git branch -M main
```

Vincular el repositorio local con el de la nube
```shell
git remote add origin "link del repositorio" 
```

Mostrar el estatus de los archivos del repositorio
```shell
git status
```

Agregar los archivos del proyecto que se le indiquen 
```shell
git add "Nombre del archivo" 
```

Añadir todos los archivos 
```shell
git add . 
```

Hace un commit
```shell
git commit -m "Descripcion" 
```

Enviar los archivos para el último commit que realizó 
```shell
git push 
```

Añadir los cambios que se han hecho en el proyecto (de las otras personas)
```shell
git pull 
```

Mostrar las ramas que se tienen en en repositorio
```shell
git branch 
```

Agregar una nueva rama al repositorio
```shell
git branch "Nombre de la nueva rama" 
```

Cambiar la rama en la que se está trabajando
```shell
git checkout "Nombre de la rama"
```

Fusionar la rama indicada con la rama actual
```shell
git merge "Nombre de la rama" 
```

Origin se refiere a la versión del proyecto que tu tienes a raíz de hacer un fork
```shell
git push origin "Nombre de la rama" 
```

Ver los cambios que se le hicieron a el trabajo
```shell
git diff 
```