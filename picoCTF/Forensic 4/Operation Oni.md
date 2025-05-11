## Descripción
Download this disk image, find the key and log into the remote machine.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

Additional details will be available after launching your challenge instance.

---
- [Download disk image](https://artifacts.picoctf.net/c/71/disk.img.gz)
- Remote machine: `ssh -i key_file -p 64886 ctf-player@saturn.picoctf.net`
## Solución
1- Descargamos el archivo
```sh
$wget https://artifacts.picoctf.net/c/71/disk.img.gz
```
2-Descomprimimos el archivo
```
$gunzip disk.img.gz
```
3- Usamos mmls
```sh
$mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)
```
4- Revisamos el root
```sh
$fls -o 206848 disk.img 470
r/r 2344:	.ash_history
d/d 3916:	.ssh
```
5- Revisamos el archivo `.ssh`
```sh
$fls -o 206848 disk.img 3916
r/r 2345:	id_ed25519
r/r 2346:	id_ed25519.pub
```
6- Revisamos el archivo `id_ed25519`
```sh
$icat -o 206848 disk.img 2345
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLAAAAJgxpYKDMaWC
gwAAAAtzc2gtZWQyNTUxOQAAACBgrXe4bKNhOzkCLWOmk4zDMimW9RVZngX51Y8h3BmKLA
AAAECItu0F8DIjWxTp+KeMDvX1lQwYtUvP2SfSVOfMOChxYGCtd7hso2E7OQItY6aTjMMy
KZb1FVmeBfnVjyHcGYosAAAADnJvb3RAbG9jYWxob3N0AQIDBAUGBw==
-----END OPENSSH PRIVATE KEY-----
```
7- Guardamos la llave en un archivo
```sh
icat -o 206848 disk.img 2345 > kay_file
```
8- Le damos permisos de solo lectura al archivo
```sh
$chmod 400 key_file

$ls -la
total 235528
drwxr-xr-x 1 user user        48 May 11 06:37 .
drwxr-xr-x 1 user user      1466 May 11 06:11 ..
-rw-r--r-- 1 user user 241172480 Aug  4  2023 disk.img
-rw-r--r-- 1 user user       411 May 11 06:37 kay_file
-r-------- 1 user user       411 May 11 06:37 key_file
```
9- Nos conectamos al servidor 
```sh
$ssh -i key_file -p 52662 ctf-player@saturn.picoctf.net
...
...
...
ctf-player@challenge:~$ ls
flag.txt
```
10- Revisamos el flag.txt
```sh
$ cat flag.txt 
picoCTF{k3y_5l3u7h_af277f77}
```
## Notas adicionales
## Referencias