## Descripción
Can you break into this super secure portal? `https://jupiter.challenges.picoctf.org/problem/56816/` ([link](https://jupiter.challenges.picoctf.org/problem/56816/)) or http://jupiter.challenges.picoctf.org:56816
## Solución
- Inspeccionamos la página
- Vemos que hay un código de JS
- Podemos formatearlo con una opción de la consola en la sección Source
- Vemos que hay una variable la cual parece tener la bandera (`_0x5a46`)
- Podemos agarrar esa variable y formar la bandera 
```JS
[
  '37115}',
  '_again_3',
  'this',
  'Password Verified',
  'Incorrect password',
  'getElementById',
  'value',
  'substring',
  'picoCTF{',
  'not_this'
]
```
- Vemos que hay partes que concuerdan con una bandera de pico
- Empezamos a formar la bandera concatenando los elementos del arreglo en un `console.log()`
```js
console.log(_0x5a46[8] + _0x5a46[9] + _0x5a46[1] + _0x5a46[0])
// salida:
// picoCTF{not_this_again_337115}
```
## Notas adicionales
La ofuscación es hacer que un código sea menos legible y que sea más difícil de vulnerar y de hacer ingeniería inversa.
## Referencias
https://www.preemptive.com/what-is-obfuscation/
https://glot.io/new/javascript