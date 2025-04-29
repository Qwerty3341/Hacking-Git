## Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag
## Solución
1. Cargamos el `.key` en el apartado de RSA keys list
2. Luego vamos a la lista de paquetes y nos vamos al primer TLS que sale que es el que en la columna de Info dice "Client Hello"
3. Le damos click derecho, en Follow y luego en TSL Stream 
4. Con el buscador (el que dice Find) buscamos la bandera (le ponemos "pico")
5. Le damos en next y al principio nos sale esto:
```
Vary: Accept-Encoding

Content-Encoding: gzip

Pico-Flag: picoCTF{this.is.not.your.flag.anymore}

Content-Length: 100

Keep-Alive: timeout=5, max=100
```
6. Si probamos esa bandera la página de pico nos dice que esa no es
7. Si le damos en Find Next ahora nos encontramos con otra bandera igual (sigue siendo incorrecta):
8. Si le damos de nuevo Find Next ahora vemos la bandera real:
```
......JFIF..............Exif..MM.*.................J...........R.(...........;.........Z................................picoCTF{honey.roasted.peanuts}......ICC_PROFILE.......lcms....mntrRGB XYZ .........).9acspAPPL...................................-lcms...............................................
```
## Notas adicionales
## Referencias