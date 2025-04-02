## Descripción
This [garden](https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg) contains more than it seems.
## Solución 1
1. Descargamos el archivo con `wget`
```shell
wget https://jupiter.challenges.picoctf.org/static/4153422e18d40363e7ffc7e15a108683/garden.jpg
```
1. Usamos `hexeditor`
```shell
$ hexeditor garden.jpg
```
2. Usamos el buscador de `hexeditor`
3. Buscamos la bandera pico
![[Pasted image 20250401155753.png | 500]]
4. Usamos el modo texto para que sea más legible
```
Here is a flag "picoCTF{more_than_m33ts_the_3y33dd2eEF5}"
```
## Solución 2
Se usa `strings -n 20 garden.jpg` Este comando lo que hace es que ve las cadenas de texto en un archivo binario y muestra las primeras 20 líneas encontradas. 
```
Copyright (c) 1998 Hewlett-Packard Company
IEC http://www.iec.ch
IEC http://www.iec.ch
.IEC 61966-2.1 Default RGB colour space - sRGB
.IEC 61966-2.1 Default RGB colour space - sRGB
,Reference Viewing Condition in IEC61966-2.1
,Reference Viewing Condition in IEC61966-2.1
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
Here is a flag "picoCTF{more_than_m33ts_the_3y33dd2eEF5}"
```
## Notas adicionales
## Referencias
https://www.kali.org/tools/ncurses-hexedit/