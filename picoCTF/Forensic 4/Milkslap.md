## Descripción
[🥛](http://mercury.picoctf.net:48380/)
## Solución
1. Visitamos la página
2. Vemos el css y vemos el nombre de la imagen 
```css
#image {
  height: 720px;
  margin-top: 5%;
  margin-bottom: 20px;
  background-image: url(concat_v.png);
  background-position: 0 0; }
```
3. Ponemos el nombre de la imagen en la url del navegador
```
http://mercury.picoctf.net:48380/concat_v.png
```
4. Descargamos la imagen 
```sh
$wget http://mercury.picoctf.net:48380/concat_v.png
```
5. Instalamos zsteg
```ruby
sudo gem install zsteg
```
6. Ponemos la variable `RUBY_THREAD_VM_STACK_SIZE` en 500 millones para que la pila de máquina virtual de Ruby no se desborde.
```ruby
export RUBY_THREAD_VM_STACK_SIZE=500000000
```
7. Buscamos en los fragmentos de la imagen
```ruby
zsteg -a concat_v.png
imagedata           .. text: "\n\n\n\n\n\n\t\t"
b1,b,lsb,xy         .. text: "picoCTF{imag3_m4n1pul4t10n_sl4p5}\n"
b1,bgr,lsb,xy       .. Killed
```
## Notas adicionales
zsteg se usa para analizar una imagen PNG en busca de **datos ocultos** mediante técnicas de **esteganografía**. La opción `-a` indica que se deben aplicar **todas** las técnicas de análisis disponibles en `zsteg`
## Referencias