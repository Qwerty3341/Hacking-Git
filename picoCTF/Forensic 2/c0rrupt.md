## Descripción
We found this [file](https://jupiter.challenges.picoctf.org/static/ab30fcb7d47364b4190a7d3d40edb551/mystery). Recover the flag.
## Solución
Si vemos el tipo de archivo de mystery solo nos dicen que es de tipo "data" lo cual indica que el comando "file" no pudo encontrar una coincidencia de archivo.
```shell
$file mystery 
mystery: data
```
Si lo vemos con `xxd` vemos que el archivo no tiene una extension definida. Pero se parece a los hexadecimales de una imagen.
```shell
$xxd mystery | head
00000000: 8965 4e34 0d0a b0aa 0000 000d 4322 4452  .eN4........C"DR
00000010: 0000 066a 0000 0447 0802 0000 007c 8bab  ...j...G.....|..
00000020: 7800 0000 0173 5247 4200 aece 1ce9 0000  x....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 aa00 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f0aa aaff a5ab 4445 5478 5eec bd3f  R$......DETx^..?
00000060: 8e64 cd71 bd2d 8b20 2080 9041 8302 08d0  .d.q.-.  ..A....
00000070: f9ed 40a0 f36e 407b 9023 8f1e d720 8b3e  ..@..n@{.#... .>
00000080: b7c1 0d70 0374 b503 ae41 6bf8 bea8 fbdc  ...p.t...Ak.....
00000090: 3e7d 2a22 336f de5b 55dd 3d3d f920 9188  >}*"3o.[U.==. ..
```
Vamos a cambiar los bits del archivo por los de una imagen como se puede ver en la siguiente imagen (vamos a cambiar el header y algunos chunks):
![[png in hex.png | 300]]
### Primer fila de bytes (extension)
![[Pasted image 20250407170224.png]]
###  Chunk "C"DR" arreglado
![[Pasted image 20250407171142.png]]
### Arreglando chunk PHYS
![[Pasted image 20250407171840.png]]
![[Pasted image 20250407172253.png]]
![[Pasted image 20250407172423.png]]
### Bandera
![[Pasted image 20250407172458.png | 500]]
## Notas adicionales
## Referencias
- https://en.wikipedia.org/wiki/PNG
- https://en.wikipedia.org/wiki/PNG#/media/File:PNG-Gradient_hex.png