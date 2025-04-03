## Descripción
We have several pages hidden. Can you find the one with the flag?

Additional details will be available after launching your challenge instance.
## Solución
Si inspeccionamos la página vemos que hay una carpeta `secret/assets` por lo tanto existe la `secret` si nos metemos a esa, vamos a ir encontrando carpetas:
```
http://saturn.picoctf.net:62119/secret/


http://saturn.picoctf.net:62119/secret/hidden/


http://saturn.picoctf.net:62119/secret/hidden/superhidden/
```
En la última carpeta vemos un :
```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="mycss.css" />
  </head>

  <body>
    <h1>Finally. You found me. But can you see me</h1>
    <h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_790d2615}</h3>
  </body>
</html>
```

## Notas adicionales
## Referencias
