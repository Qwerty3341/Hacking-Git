## Descripción
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/17682/` ([link](https://jupiter.challenges.picoctf.org/problem/17682/)) or http://jupiter.challenges.picoctf.org:17682
## Solución
En los elementos de la página vemos que tienen un script de JS en el cual está la contraseña fragmentada en muchos if's
```js
function verify() {
  checkpass = document.getElementById("pass").value;
  split = 4;
  if (checkpass.substring(0, split) == 'pico') {
    if (checkpass.substring(split*6, split*7) == '706c') {
      if (checkpass.substring(split, split*2) == 'CTF{') {
       if (checkpass.substring(split*4, split*5) == 'ts_p') {
        if (checkpass.substring(split*3, split*4) == 'lien') {
          if (checkpass.substring(split*5, split*6) == 'lz_b') {
            if (checkpass.substring(split*2, split*3) == 'no_c') {
              if (checkpass.substring(split*7, split*8) == '5}') {
                alert("Password Verified")
                }
              }
            }
    
          }
        }
      }
    }
  }
  else {
    alert("Incorrect password");
  }
  
}
```
Podemos ver que el script comprueba por rangos la contraseña así que traduciendo y ordenando los rangos obtenemos esto:
```
split = 4;
if (checkpass.substring(0, split) == 'pico')
  0-4 pico

if (checkpass.substring(split, split*2) == 'CTF{')
  4-8

if (checkpass.substring(split*2, split*3) == 'no_c')
  8-12

if (checkpass.substring(split*3, split*4) == 'lien')
  12-16

if (checkpass.substring(split*4, split*5) == 'ts_p')
  16-20

if (checkpass.substring(split*5, split*6) == 'lz_b')
  20-24

if (checkpass.substring(split*6, split*7) == '706c')
  24-28

if (checkpass.substring(split*7, split*8) == '5}')
  28-32
```
## Notas adicionales
## Referencias
https://jupiter.challenges.picoctf.org/problem/17682/