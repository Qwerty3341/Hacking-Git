## Descripción
Unzip this archive and find the flag.
## Solución
Usando unzip y engrep
- Se usa unzip para descomprimir el archivo
- Usamos engrep de forma recursiva para buscar el patron de la llave de pico (es de forma recursiva para buscar en todo el directorio)
```shell
debian3341@DESKTOP-VDLU0ET:~$ egrep -r 'picoCTF{' big-zip-files
big-zip-files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
## Notas adicionales
Unzip se instala aparte
## Referencias
- https://www.tecmint.com/unzip-extract-zip-files-to-specific-directory-in-linux/
- https://www.warp.dev/terminus/grep-in-directory