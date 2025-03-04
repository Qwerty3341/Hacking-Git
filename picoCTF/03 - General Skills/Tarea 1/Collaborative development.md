## Descripción
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:
- challenge.zip
## Solución 1 (cat a los archivos de python en cada rama)
Al descomprimir el archivo challenge.zip nos da un directorio que tiene un archivo `.git` así que vemos que lo podemos solucionar con comandos de git
1. El archivo `.py` de la rama main no hace nada más que imprimir un mensaje
2. Al revisar las ramas vemos que hay 3
3. Nos movemos con `git checkout 'nombre_de_la_rama'`
4. Cada una tiene un archivo de python que a su vez tiene un `print()` que adentro tiene una parte de la bandera
5. Hacemos un cat a cada archivo para obtener una parte de la bandera
6. Armamos la bandera y la conseguimos
```
Qwerty3341-picoctf@webshell:~$ ls
README.txt  challenge.zip
Qwerty3341-picoctf@webshell:~$ unzip challenge.zip 

...

Qwerty3341-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in

Qwerty3341-picoctf@webshell:~$ cd drop-in/
Qwerty3341-picoctf@webshell:~/drop-in$ ls
flag.py
Qwerty3341-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")
Qwerty3341-picoctf@webshell:~/drop-in$ python3 flag.py  
Printing the flag...
Qwerty3341-picoctf@webshell:~/drop-in$ git branch
Qwerty3341-picoctf@webshell:~/drop-in$ git branch -a

Qwerty3341-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")

Qwerty3341-picoctf@webshell:~/drop-in$ git branch -a
Qwerty3341-picoctf@webshell:~/drop-in$ git branch feature/part-3
fatal: A branch named 'feature/part-3' already exists.
Qwerty3341-picoctf@webshell:~/drop-in$ git checkout feature/part-3
Switched to branch 'feature/part-3'
Qwerty3341-picoctf@webshell:~/drop-in$ ls
flag.py
Qwerty3341-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")

print("w0rk_7ae8dd33}")
Qwerty3341-picoctf@webshell:~/drop-in$ git checkout feature/part-2
Switched to branch 'feature/part-2'
Qwerty3341-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")

print("m@k3s_th3_dr3@m_", end='')Qwerty3341-picoctf@webshell:~/drop-in$ git checkout feature/part-1
Switched to branch 'feature/part-1'
Qwerty3341-picoctf@webshell:~/drop-in$ cat flag.py 
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')Qwerty3341-picoctf@webshell:~/drop-in$ 

Qwerty3341-picoctf@webshell:~/drop-in$ cd ..
Qwerty3341-picoctf@webshell:~$ ls
README.txt  challenge.zip  drop-in
```
## Solución 2 (hacer un archivo de python con nano)
Podemos redirigir las banderas con cat a un archivo o simplemente un cat y en un archivo de python pegamos los prints que nos encontramos en cada archivo y con python3 lo ejecutamos y nos da la bandera completa.
```
Qwerty3341-picoctf@webshell:~$ nano bandera.py
Qwerty3341-picoctf@webshell:~$ ls
README.txt  bandera.py  challenge.zip  drop-in
Qwerty3341-picoctf@webshell:~$ python3 bandera.py 
picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_7ae8dd33}
Qwerty3341-picoctf@webshell:~$ ls
README.txt  bandera.py  challenge.zip  drop-in
Qwerty3341-picoctf@webshell:~$ cd drop-in/
Qwerty3341-picoctf@webshell:~/drop-in$ ls -a
.  ..  .git  flag.py
```
## Notas adicionales
La solución 1 es más rápida que la primera
## Referencias
Aquí dejo un archivo que contiene varios comandos básicos de git:
- [[Comandos de git]]