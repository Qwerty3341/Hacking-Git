## Descripción
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?
## Solución
1. Descargamos el archivo con `wget`
2. Instalamos ruby
```shell
$ sudo apt install ruby
$ ruby -v
ruby 3.3.7 (2025-01-15 revision be31f993d7) [x86_64-linux-gnu]
```
3. Usamos gem (instalador de paquetes de Ruby) para instalar `zsteg`
```shell
sudo gem install zsteg
```
4. Usamos `zsteg` para encontrar la bandera
```shell
$ zsteg -a buildings.png | grep pico
b1,rgb,lsb,xy       .. text: "picoCTF{h1d1ng_1n_th3_b1t5}"
```
## Notas adicionales
- El comando `zsteg` es para buscar datos ocultos en los bits de una imagen PNG o BMP.
- La opción `-a` es para ejecutar todos los métodos de detección disponibles en la imagen.
## Referencias
https://blog.desafiolatam.com/crear-una-gema-ruby/
https://linuxcommandlibrary.com/man/zsteg
https://mynixos.com/nixpkgs/package/zsteg