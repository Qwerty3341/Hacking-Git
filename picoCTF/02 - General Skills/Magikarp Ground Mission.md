## Descripción
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `abcba9f7`

Additional details will be available after launching your challenge instance.
## Solución
Te tienes que mover entre los directorios que te indican los archivos que empiezan con 'instructions' y ver el texto que tiene '.flag.txt' para ir armando una llave (el orden de la llave se indica en el nombre del archivo que contiene '.flag.txt')

```shell
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cat 3of3.flag.txt 
21cac893}
ctf-player@pico-chall$ cd 
ctf-player@pico-chall$ ls
3of3.flag.txt  drop-in
ctf-player@pico-chall$ cd drop-in/
ctf-player@pico-chall$ ls
1of3.flag.txt  instructions-to-2of3.txt
ctf-player@pico-chall$ cat 1of3.flag.txt 
picoCTF{xxsh_
ctf-player@pico-chall$ cat instructions-to-2of3.txt 
Next, go to the root of all things, more succinctly `/`
ctf-player@pico-chall$ cd /
ctf-player@pico-chall$ ls
2of3.flag.txt  bin  boot  dev  etc  home  instructions-to-3of3.txt  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
ctf-player@pico-chall$ cat 2of3.flag.txt 
0ut_0f_\/\/4t3r_
ctf-player@pico-chall$ Connection to venus.picoctf.net closed by remote host.
Connection to venus.picoctf.net closed.
Qwerty3341-picoctf@webshell:~$ 
```

Llave:
```
1of3 = picoCTF{xxsh_
2of3 = 0ut_0f_\/\/4t3r_
3of3 = 21cac893}

picoCTF{xxsh_0ut_0f_\/\/4t3r_21cac893}
```
## Notas adicionales

## Referencias
