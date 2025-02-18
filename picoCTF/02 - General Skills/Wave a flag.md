## Descripción
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...
## Solución
- Le damos permisos de ejecución al archivo
- Ejecutamos el archivo warm con ./ -h para mostrar la ayuda del archivo
```shell
Qwerty3341-picoctf@webshell:~/FILES$ ls
warm
Qwerty3341-picoctf@webshell:~/FILES$ chmod +x warm 
Qwerty3341-picoctf@webshell:~/FILES$ ls
warm
Qwerty3341-picoctf@webshell:~/FILES$ ls -h
warm
Qwerty3341-picoctf@webshell:~/FILES$ ./warm 
Hello user! Pass me a -h to learn what I can do!
Qwerty3341-picoctf@webshell:~/FILES$ ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_d6969390}
Qwerty3341-picoctf@webshell:~/FILES$ 
```
## Notas adicionales
## Referencias
- https://www.geeksforgeeks.org/chmod-command-linux/