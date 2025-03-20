## Descripción
Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670
## Solución
- En el navegador le damos a inspeccionar
- En la pestaña de 'Elements' de la página vemos un comentario que tiene el inicio de la bandera
- Si nos vamos a la pestaña 'Sources' vemos que hay un archivo JS, lo inspeccionamos y hay otro comentario con la segunda parte de la bandera
- Al final nos vamos al archivo CSS que también tiene un comentario con otra parte de la bandera
Aquí se muestran los comentarios que había en cada archivo:
```
<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->
/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */


picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}
```
## Notas adicionales
Para este reto no se necesitó utilizar más que la consola de DevTools.
## Referencias
https://jupiter.challenges.picoctf.org/problem/9670/