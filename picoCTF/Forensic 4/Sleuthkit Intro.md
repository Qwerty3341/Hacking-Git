## Descripción
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.[Download disk image](https://artifacts.picoctf.net/c/164/disk.img.gz)

Additional details will be available after launching your challenge instance.
## Solución
1.- Descargamos la imagen 
```sh
$wget https://artifacts.picoctf.net/c/164/disk.img.gz
```
2.- Descomprimimos el archivo
```sh
gunzip disk.img.gz
```
3.- Vemos las particiones de la imagen
```sh
$mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000204799   0000202752   Linux (0x83)
```
4.- Nos conectamos al servidor 
```sh
$ nc saturn.picoctf.net 59108
What is the size of the Linux partition in the given disk image?
Length in sectors: 
```
5.- Contestamos la pregunta
```sh
$nc saturn.picoctf.net 59108
What is the size of the Linux partition in the given disk image?
Length in sectors: 202752
202752
Great work!
picoCTF{mm15_f7w!}
```
## Notas adicionales
MMLS muestra el contenido de un sistema de volumen (gestión de medios)
## Referencias
- https://wiki.sleuthkit.org/index.php?title=Mmls