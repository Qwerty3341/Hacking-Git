## Descripción
Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/262/flag.png).
## Solución
Al ver la imagen con `exiftool` vemos una advertencia:
```sh
$exiftool flag.png 
ExifTool Version Number         : 12.57
File Name                       : flag.png
Directory                       : .
File Size                       : 43 kB
File Modification Date/Time     : 2023:03:16 03:16:06+00:00
File Access Date/Time           : 2025:05:12 00:00:59+00:00
File Inode Change Date/Time     : 2025:05:12 00:00:58+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 512
Image Height                    : 504
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Warning                         : [minor] Trailer data after PNG IEND chunk
Image Size                      : 512x504
Megapixels                      : 0.258
```
Nos indica que después del IEND hay más datos en el archivo.
Si usamos `zsteg` nos dice esto:
```sh
$zsteg flag.png 
[?] 3206 bytes of extra data after image end (IEND), offset = 0x9b3b
extradata:0         .. file: Zip archive data, at least v1.0 to extract, compression method=store
    00000000: 50 4b 03 04 0a 00 00 00  00 00 3d 10 70 56 00 00  |PK........=.pV..|
    00000010: 00 00 00 00 00 00 00 00  00 00 07 00 1c 00 73 65  |..............se|
    00000020: 63 72 65 74 2f 55 54 09  00 03 95 78 12 64 95 78  |cret/UT....x.d.x|
    00000030: 12 64 75 78 0b 00 01 04  00 00 00 00 04 00 00 00  |.dux............|
    00000040: 00 50 4b 03 04 14 00 00  00 08 00 3d 10 70 56 5b  |.PK........=.pV[|
    00000050: 9b f6 a9 44 0b 00 00 de  0b 00 00 0f 00 1c 00 73  |...D...........s|
    00000060: 65 63 72 65 74 2f 66 6c  61 67 2e 70 6e 67 55 54  |ecret/flag.pngUT|
    00000070: 09 00 03 95 78 12 64 95  78 12 64 75 78 0b 00 01  |....x.d.x.dux...|
    00000080: 04 00 00 00 00 04 00 00  00 00 cd 56 67 3c db 8d  |...........Vg<..|
    00000090: 16 fe 53 ab 5a 1a 7b ef  52 d7 a8 4d 25 66 5e a3  |..S.Z.{.R..M%f^.|
    000000a0: 66 89 91 88 8a 4d 6d 45  8c d8 1a 6f 75 d0 d7 6a  |f....MmE...ou..j|
    000000b0: ec d0 9a 55 14 af 95 a0  3a d4 2a 6a 94 a6 56 07  |...U....:.*j..V.|
    000000c0: 62 f3 da 23 e2 e6 7e bc  1f ee f7 7b 3e 9c e7 ec  |b..#..~....{>...|
    000000d0: f3 e5 f9 fd ce 79 64 63  6d ca c6 2a c8 0a 00 00  |.....ydcm..*....|
    000000e0: 9b d9 6d 23 18 00 d0 23  68 b6 2a 88 a6 80 83 20  |..m#...#h.*.... |
    000000f0: 19 47 1a 30 f8 1a 5a 19  02 40 e3 b3 2b 14 77 46  |.G.0..Z..@..+.wF|
```
Usamos `binwalk` para extraer el zip que está después del final de la imagen.
```sh
binwalk -e imagen.png

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             PNG image, 512 x 504, 8-bit/color RGBA, non-interlaced
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2884, uncompressed size: 3038, name: secret/flag.png
42923         0xA7AB          End of Zip archive, footer length: 22
```
Nos vamos a la carpeta que se extrajo
```sh
../_flag.png.extracted/secret
```
Abrimos la imagen que está ahí y encontramos la bandera que es:
```
picoCTF{Hiddinng_An_imag3_within_@n_ima9e_82101824}
```
## Notas adicionales
En el formato PNG, el bloque `IEND` marca **el final de la imagen**. Cualquier byte **después** de ese bloque no forma parte oficial del archivo.
## Referencias