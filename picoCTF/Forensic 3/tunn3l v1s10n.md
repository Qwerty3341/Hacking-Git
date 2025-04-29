## Descripción
We found this [file](https://mercury.picoctf.net/static/06a5e4ab22ba52cd66a038d51a6cc07b/tunn3l_v1s10n). Recover the flag.
## Solución
Si intentamos abrir el archivo con GIMP nos dice esto

>Opening '/home/user/Documents/tunn3l_v1s10n' failed: Error reading BMP file header from '/home/user/Documents/tunn3l_v1s10n'

Vemos si el header es correcto y vemos esto
```sh
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 bad0  BM.&,...........
```

La parte del header DIB la cambiamos a esta 
```sh
00000000: 424d 8e26 2c00 0000 0000 bad0 0000 2800  BM.&,.........(.
```
Si hacemos eso ahora obtenemos una imagen que sí se puede abrir con un visualizador de imágenes, pero aún así en la imagen nos dice que no hay ninguna bandera

Si revisamos la segunda fila de bytes vemos que hay un 3201, esos bytes representan el tamaño de la imagen
```sh
00000010: 0000 6e04 0000 3201 0000 0100 1800 0000  ..n...2.........
```

Si los cambiamos a uno más grande como este
```sh
00000010: 0000 6e04 0000 8006 0000 0100 1800 0000  ..n.............
```
Ahora vamos a ver la imagen ampliada y ahora sí ya vemos un texto que dice
```sh
picoCTF{qu1t3_a_v13w_2020}
```
## Notas adicionales
## Referencias
- https://en.wikipedia.org/wiki/List_of_file_signatures
- https://en.wikipedia.org/wiki/BMP_file_format