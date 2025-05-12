## Descripción
A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message

Additional details will be available after launching your challenge instance.
## Solución
- Visitamos la página y vemos muchas banderas
- En la pista nos decían que la bandera estaba en un país que no existía
- Si vamos hasta abajo encontramos una bandera peculiar
![[Pasted image 20250511175111.png | 200]]
- SI la descargamos y vemos el tamaño de la imagen vemos que es bastante grande
```sh
$exiftool upz.png 
ExifTool Version Number         : 12.57
File Name                       : upz.png
Directory                       : .
File Size                       : 1788 kB
File Modification Date/Time     : 2025:03:06 03:59:39+00:00
File Access Date/Time           : 2025:05:11 23:35:24+00:00
File Inode Change Date/Time     : 2025:05:11 23:34:59+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 14173
Image Height                    : 10630
Bit Depth                       : 8
Color Type                      : RGB with Alpha
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 14173x10630
Megapixels                      : 150.7
```
- Si usamos stepic obtenemos esto
```sh
$stepic -i upz.png -d
/usr/lib/python3/dist-packages/PIL/Image.py:3167: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4g3e22f365}
```
## Notas adicionales
El comando `stepic` se utiliza para ocultar datos de forma esteganográfica en una imagen de estilo de mapa de bits o leer datos ocultos de una imagen. En este caso el parámetro `-d` lo que hace es descifrar información.
## Referencias