## Descripción
Can you get the flag?
Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:57360/) and see what you can discover.
## Solución
Al revisar el código fuente vemos que hay un `script.js`
```js
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_6edef411}
```
En el `style.css` vemos esto:
```css
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */
```
Bandera completa:
```
picoCTF{1nclu51v17y_1of2_f7w_2of2_6edef411}
```
## Notas adicionales
## Referencias