## Descripción
Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/e5825f58ef798fdd1af3f6013592a971/cat.jpg)
## Solución
Descargamos el archivo
```sh
$ wget https://mercury.picoctf.net/static/e5825f58ef798fdd1af3f6013592a971/cat.jpg
```
Abrimos la imagen a ver si tiene algo raro (solo es una imagen de un dato)
```
$ open cat.jpg
```
Usamos `exiftool` para ver los metadatos de la imagen
```sh
$ exiftool cat.jpg
ExifTool Version Number         : 13.10
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 12:24:46-06:00
File Access Date/Time           : 2025:05:11 13:34:14-06:00
File Inode Change Date/Time     : 2025:05:11 13:34:09-06:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
Vemos que la licencia está cifrada
```sh
$ echo cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9 | base64 -d
picoCTF{the_m3tadata_1s_modified}
```
## Notas adicionales
Vemos que hay un metadato que se llama `"Current IPTC Digest"`. Ese metadato lo genera `exiftool` para indicar que los metadatos IPTC han sido cambiados.
## Referencias
- https://cinusual.com/que-son-los-campos-iptc-y-para-que-sirven
- https://www.ionos.com/digitalguide/websites/web-design/what-is-iptc-data/