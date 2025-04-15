## Descripción
The Multiverse is within your grasp! Unfortunately, the server that contains the secrets of the multiverse is in a universe where keyboards only have numbers and (most) symbols.

Additional details will be available after launching your challenge instance.
## Solución
Si usamos las wildcards de Linux como por ejemplo el `?` podemos ver que nos dan coincidencias de directorios
```shell
SansAlpha$ /?
bash: /?: No such file or directory

SansAlpha$ /??
bash: /??: No such file or directory

SansAlpha$ /???
bash: /bin: Is a directory

SansAlpha$ /????
bash: /boot: Is a directory

SansAlpha$ /?????
bash: /lib32: Is a directory

SansAlpha$ /??????
bash: /libx32: Is a directory
```
Podemos ir viendo si hay algún directorio con un archivo llamado "flag.txt"
```sh
SansAlpha$ ./??????
bash: ./blargh: Is a directory

SansAlpha$ ./??????/*
bash: ./blargh/flag.txt: Permission denied
```
Hay que buscar algo que pueda imprimir el contenido del archivo flag.txt. Podemos ver si el comando `base64` funciona, para ello nos vamos al directorio `/bin/base64`.
```sh
SansAlpha$ /*/???[!_]64 */????.*
cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0=
```
Ahora lo desciframos con el comando base64 en una terminal normal
```sh
$ echo cmV0dXJuIDAgcGljb0NURns3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iMGQ1ZTg1NX0= | base64 -d
return 0 picoCTF{7h15_mu171v3r53_15_m4dn355_b0d5e855}
```
## Notas adicionales
Explicación del comando `/*/???[!_]64 */????.*`
- `/*/` Selecciona el primer directorio que encuentre en el directorio actual, en este caso solo estaba el bin que también lo podemos representar como `/???/`
- `[!_]` Dentro de corchetes en un patrón de búsqueda, el símbolo `!` se utiliza para indicar una negación o exclusión. Esto significa que cualquier carácter en la posición correspondiente _excepto_ el guion bajo (`_`) será válido. En otras palabras, `[!_]` coincide con cualquier carácter que **no sea** `_`.
- `64` Busca los caracteres seis y cuatro
- `*/` Cualquier directorio
- `????.*` Un archivo con 4 caracteres y una extension cualquiera
## Referencias 
- https://tldp.org/LDP/GNU-Linux-Tools-Summary/html/x11655.htm
- https://tldp.org/LDP/abs/html/globbingref.html