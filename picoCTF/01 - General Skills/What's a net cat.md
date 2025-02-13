## Descripción
Using netcat (nc) is going to be pretty important. Can you connect to  `jupiter.challenges.picoctf.org` at port `64287` to get the flag?
## Solución
Usar netcat para conectarse al puerto con la url que nos dan
```
Qwerty3341-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 64287 
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_284be8f7}

```
## Notas adicionales
`jupiter.challenges.picoctf.org` es el servidor al que nos conectamos y `64287` es el puerto por el que este servidor recibe las conexiones.
## Referencias
- https://linux.die.net/man/1/nc