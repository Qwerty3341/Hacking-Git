## Descripción
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg)
## Solución
Podemos usar el comando binwalk

```sh
$binwalk dolls.jpg
```

Al hacer esto el comando nos hace un `.zip` y una carpeta con los archivos que encontró, en este caso tuve que hacer el comando 4 veces para al final que el comando nos diera un archivo `flag.txt`

```sh
$cat flag.txt 
picoCTF{4f11048e83ffc7d342a15bd2309b47de}
```
## Notas adicionales
El parámetro `-e` es para extraer el archivo oculto en el archivo que analiza el comando `binwalk`
## Referencias
- https://linuxcommandlibrary.com/man/binwalk
- https://gist.github.com/briankip/8f8747a2488af827e3b4