## Descripción
Can you get the flag?

Additional details will be available after launching your challenge instance.

Go to this [website](http://saturn.picoctf.net:54716/) and see what you can discover.
## Solución
- Si tratamos de ingresar con cualquier contraseña nos dice que fallamos en el ingreso.
- Si vemos el código fuente de la página vemos que hay un archivo `secure.js`.
- Si vamos a ese archivo vemos este código:
```js
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}
```
- Si ingresamos como admin y con la contraseña que nos da el script nos dan la bandera 
```
picoCTF{j5_15_7r4n5p4r3n7_a8788e61}
```
## Notas adicionales

## Referencias
