## Descripción
I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/14/challenge.zip)

The same files are accessible via SSH here:`ssh -p 61120 ctf-player@atlas.picoctf.net`Using the password `84b12bae`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
## Solución 1
==Usar el scanner del teléfono==
- Nos conectamos por ssh al servidor 
```sh
$ ssh -p 61120 ctf-player@atlas.picoctf.net
```
- Cuando logramos entrar vemos que hay un QR
- Si lo escaneamos vemos que nos dan la bandera
```
picoCTF{p33k_@_b00_0194a007}
```
## Solución 2
==Usar zbar-tools==
- Descargamos con `wget` el archivo
- Lo descomprimimos con  `unzip challenge.zip`
- Vemos que nos descomprime varios directorios
- Instalamos `zbar-tools`
```
sudo apt install zbar-tools
```
- Ahora usamos la herramienta `zbarimg` para leer el código de barras de la imagen
```sh
$ zbarimg flag.png
QR-Code:picoCTF{p33k_@_b00_0194a007}
scanned 1 barcode symbols from 1 images in 0.01 seconds
```
## Notas adicionales
ZBar is a library for scanning and decoding bar codes from various sources such as video streams, image files or raw intensity sensors. It supports EAN-13/UPC-A, UPC-E, EAN-8, Code 128, Code 39, Interleaved 2 of 5 and QR Code.
## Referencias
- https://community.linuxmint.com/software/view/zbar-tools