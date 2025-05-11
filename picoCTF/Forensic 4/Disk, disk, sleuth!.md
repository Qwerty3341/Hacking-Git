## Descripción
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image: [dds1-alpine.flag.img.gz](https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz)
## Solución 1
1- Descargamos el archivo
```sh
$wget https://mercury.picoctf.net/static/f63e4eba644c99e92324b65cbd875db6/dds1-alpine.flag.img.gz
```
2- Usamos gzip para descomprimir el archivo 
```sh
$gzip -d dds1-alpine.flag.img.gz
```
3- Usamos srch_strings 
```sh
$srch_strings dds1-alpine.flag.img | grep pico
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96c0}
```
## Solución 2
Usamos strings
```sh
$strings dds1-alpine.flag.img | grep pico
ffffffff81399ccf t pirq_pico_get
ffffffff81399cee t pirq_pico_set
ffffffff820adb46 t pico_router_probe
  SAY picoCTF{f0r3ns1c4t0r_n30phyt3_ad5c96c0}
```
## Notas adicionales
**srch_strings** - muestra cadenas imprimibles en archivos
## Referencias
- https://manpages.ubuntu.com/manpages/bionic/man1/srch_strings.1.html