## Descripción
Download this disk image and find the flag. Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://artifacts.picoctf.net/c/214/disk.flag.img.gz)
## Solución
1- Descargamos la imagen
```sh
$wget https://artifacts.picoctf.net/c/214/disk.flag.img.gz
```
2- Descomprimimos el archivo
```sh
$gunzip disk.flag.img.gz
```
3- Usamos `mmls`
```sh
$mmls disk.flag.img 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000411647   0000204800   Linux Swap / Solaris x86 (0x82)
004:  000:002   0000411648   0000819199   0000407552   Linux (0x83)
```
4- Usamos `fls`
```sh
$fls disk.flag.img -o 411648
d/d 460:	home
d/d 11:	lost+found
d/d 12:	boot
d/d 13:	etc
d/d 81:	proc
d/d 82:	dev
d/d 83:	tmp
d/d 84:	lib
d/d 87:	var
d/d 96:	usr
d/d 106:	bin
d/d 120:	sbin
d/d 466:	media
d/d 470:	mnt
d/d 471:	opt
d/d 472:	root
d/d 473:	run
d/d 475:	srv
d/d 476:	sys
d/d 2041:	swap
V/V 51001:	$OrphanFiles
```
5- Revisamos el root
```sh
$fls -o 411648 disk.flag.img 472
r/r 1875:	.ash_history
r/r * 1876(realloc):	flag.txt
r/r 1782:	flag.txt.enc
```
6- Revisamos el archivo `flag.txt`
```sh
$icat -o 411648 disk.flag.img 1876
           -0.881573            34.311733
```
7- Revisamos el `flag.txt.enc`
```sh
$icat -o 411648 disk.flag.img 1782
Salted__S�+%���+�O��k�ђ(A����c��
                                @]ԣ
L�ޢȤ7� ���؎$�'%
```
8- Buscamos con `strings` el `flag.txt`
```sh
$strings -td disk.flag.img | grep flag.txt
218985524 flag.txt
218985540 flag.txt.enc
219964416 touch flag.txt
219964431 nano flag.txt 
219964483 nano flag.txt 
219964506 openssl aes256 -salt -in flag.txt -out flag.txt.enc -k unbreakablepassword1234567
219964588 shred -u flag.txt
303193140 flag.txt
303317044 flag.txt
303317060 flag.txt.enc
303328308 flag.txt
303328324 flag.txt.enc
```
9- Vemos que hay un comando `openssl`
10- Guardamos el contenido de `flag.txt.enc` en un archivo
```sh
$icat disk.flag.img -o 411648 1782 > flag.txt.enc
```
11- Usamos el comando de `openssl` pero modificamos los parámetros
```sh
openssl aes256 -d -salt -in flag.txt.enc -out flag.txt -k unbreakablepassword1234567
```
```sh
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
bad decrypt
4097B506BC7F0000:error:1C800064:Provider routines:ossl_cipher_unpadblock:bad decrypt:../providers/implementations/ciphers/ciphercommon_block.c:124:
```
12- Vemos el archivo generado
```sh
$cat flag.txt
picoCTF{h4un71ng_p457_1d02081e}
```
## Notas adicionales
The OpenSSL software library is a robust, commercial-grade, full-featured toolkit for general-purpose cryptography and secure communication.
## Referencias
- https://openssl.org/