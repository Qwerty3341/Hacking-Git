## Descripción
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?
## Solución n
1. Descargamos el archivo TXT
2. Vemos el tipo de archivo con el comando `file`
```bash
$ file flag.txt
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```
3. Le cambiamos la extension `.txt` por una `.png`
```shell
$ mv flag.txt flag.png
```
4. Vemos la imagen (podemos usar el comando `open`). En la misma imagen está escrita la bandera
```shell
open flag.png

picoCTF{now_you_know_about_extensions}
```
## Notas adicionales
Si usamos `xxd -l 100 flag,png` podemos ver que los bites corresponden a los de una imagen.
## Referencias