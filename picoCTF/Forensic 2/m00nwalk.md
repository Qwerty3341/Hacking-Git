## Descripción
Decode this [message](https://jupiter.challenges.picoctf.org/static/14393e18d98fedbaedbc28896d7ef31a/message.wav) from the moon.
## Solución n
Si abrimos el archivo nos va a dar un audio sin sentido.

1. Podemos usar una herramienta de python llamada `sstv`
2. Nos vamos al directorio /opt/ y ahí clonamos el repositorio
3. después con python3 instalamos la herramienta
4. Vamos al directorio donde está el audio y ejecutamos el comando:
```bash
$sstv -d message.wav -o bandera.png
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [##############################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!
```
5. Vemos la imagen y ahí esta la bandera
![[bandera_m00nwalk.png]]
`picoCTF{beep_boop_im_in_space}`
## Notas adicionales
## Referencias
- https://www.marketingdirecto.com/diccionario-marketing-publicidad-comunicacion-nuevas-tecnologias/wav
- https://github.com/colaclanth/sstv