## Descripción
Can you look at the data in this binary: static? This BASH script might help!
## Solución
Nos dan este script:
```bash
#!/bin/bash

echo "Attempting disassembly of $1 ..."

#This usage of "objdump" disassembles all (-D) of the first file given by
#invoker, but only prints out the ".text" section (-j .text) (only section
#that matters in almost any compiled program...

objdump -Dj .text $1 > $1.ltdis.x86_64.txt

#Check that $1.ltdis.x86_64.txt is non-empty
#Continue if it is, otherwise print error and eject

if [ -s "$1.ltdis.x86_64.txt" ]
then
        echo "Disassembly successful! Available at: $1.ltdis.x86_64.txt"

        echo "Ripping strings from binary with file offsets..."
        strings -a -t x $1 > $1.ltdis.strings.txt
        echo "Any strings found in $1 have been written to $1.ltdis.strings.txt with file offset"
else
        echo "Disassembly failed!"
        echo "Usage: ltdis.sh <program-file>"
        echo "Bye!"
fi
```

- Lo que hice fue hacer un archivo de texto llamado respuesta
- Hago cat para con el archivo static y se lo paso al script ltdis.sh, después lo redirijo al archivo respuesta y hago el comando egrep para buscar el patrón de la bandera en ese mismo archivo.
- Me dice que hay coincidencias con archivos binarios
- Uso egrep -a para buscar entre caracteres que no están incluidos en la tabla ascii

```shell
debian3341@DESKTOP-VDLU0ET:~/FILES$ touch respuesta.txt
debian3341@DESKTOP-VDLU0ET:~/FILES$ cat static ltdis.sh > respuesta.txt & egrep 'picoCTF{' respuesta.txt
[1] 348
grep: respuesta.txt: binary file matches
[1]+  Done                    cat static ltdis.sh > respuesta.txt
debian3341@DESKTOP-VDLU0ET:~/FILES$ egrep -a 'picoCTF{' respuesta.txt
�
 picoCTF{d15a5m_t34s3r_ccb2b43e}GCC: (Ubuntu 7.5.0-3ubuntu1~18.04) 7.5.08Tt��`�
```
## Notas adicionales

## Referencias
- https://www.freecodecamp.org/espanol/news/tutorial-de-programacion-de-bash-script-de-shell-de-linux-y-linea-de-comandos-para-principiantes/