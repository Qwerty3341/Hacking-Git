## Descripción
Play this short game to get familiar with terminal applications and some of the most important rules in scope for picoCTF. Connect to the program with netcat: `$ nc verbal-sleep.picoctf.net 63285`
## Solución
Al conectarnos al host solo nos dan instrucciones del concurso, al presionar muchas veces enter, en un momento nos piden seleccionar opciones de un cuestionario:
```
A) *Register multiple accounts*
B) *Share an account with a friend*
C) *Register a single, private account*
[a/b/c] > c
```
Al elegir una nos dan más instrucciones hasta que después de elegir varias opciones podemos obtener la bandera: `picoCTF{m1113n1um_3d1710n_e41acbee}`
## Notas adicionales
## Referencias