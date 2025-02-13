## Descripción
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.
## Solución
La respuesta que nos da el servidor es muy larga.
- Hago un archivo llamado 'respuesta'
- Me conecto al servidor y la salida de ese comando la dirijo al archivo 'respuesta'
- Ahora busco la bandera como se hizo en [[First Grep]]
```bash
Qwerty3341-picoctf@webshell:~$ touch respuesta
Qwerty3341-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 7480 > respuesta
Qwerty3341-picoctf@webshell:~$ egrep 'picoCTF{' respuesta
picoCTF{digital_plumb3r_06e9d954}
```
## Notas adicionales
El problema se realizó usando comandos del problema [[First Grep]] 
## Referencias
- https://linux.die.net/man/1/nc