## Descripción
Unzip this archive and find the file named 'uber-secret.txt'
## Solución
- Usamos unzip
- Usamos el comando find -name "" para localizar el archivo
- Usamos cd para movernos al directorio donde está el archivo
- Usamos cat para ver el contenido del archivo

```shell
$ unzip files.zip

$ find -name "uber-secret.txt"
./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt

$ cd ./files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/

$ ls
uber-secret.txt

$ cat uber-secret.txt
picoCTF{f1nd_15_f457_ab443fd1}
```
## Notas adicionales
Se puede usar locate pero hay que instalarlo aparte
## Referencias
- https://www.geeksforgeeks.org/find-command-in-linux-with-examples/