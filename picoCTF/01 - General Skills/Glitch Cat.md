## Descripción
Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.

Our flag printing service has started glitching!`$ nc saturn.picoctf.net 55834`
## Solución 1
El problema nos daba un string de la primera parte de la bandera y después caracteres en hexadecimal dentro de la función `chr()` de python.

```
Qwerty3341-picoctf@webshell:~$ nc saturn.picoctf.net 55834 
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'

Qwerty3341-picoctf@webshell:~$ 
```

Usar https://glot.io/ para imprimir la cadena que nos da el servidor al que nos conectamos
![[Pasted image 20250212195542.png]]
## Notas adicionales
Se puede hacer un script en python para pasarle un archivo y que traduzca el contenido de este para tenerlo automatizado pero usar glot.io es un poco más rápido
## Referencias
- [https://glot.io/](https://glot.io/)
- https://glot.io/new/python