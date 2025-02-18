## Descripción
Can you find the flag in file without running it?
## Solución
- Usar el comando strings que busca cadenas de texto imprimibles en archivos binarios
- La salida de este comando se le pasa al comando grep para buscar la bandera

```shell
┌[debian3341 | 62 comands | dir:~/FILES]
└-> $ strings strings | grep "picoCTF{"
picoCTF{5tRIng5_1T_d66c7bb7}
```
## Notas adicionales
El comando strings se tuvo que instalar con `sudo apt install binutils`
## Referencias
- https://linux.die.net/man/1/strings