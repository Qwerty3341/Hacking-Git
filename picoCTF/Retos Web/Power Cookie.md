## Descripción
Can you get the flag?
Additional details will be available after launching your challenge instance.
Go to this [website](http://saturn.picoctf.net:49230/) and see what you can discover.
## Solución
1. Vemos una página que nos pide `"continuar como una visita"` si le damos al botón nos dice que no están aceptando visitas
2. Si revisamos el código de la página vemos que hay un documento `guest.js`
	```js
	function continueAsGuest()
	{
	  window.location.href = '/check.php';
	  document.cookie = "isAdmin=0";
	}
	```
3. Si vamos al inicio y accedemos como visita se genera esa cookie y si cambiamos el `"isAdmin"` por el valor de 1 nos dan la bandera
	```
	picoCTF{gr4d3_A_c00k13_0d351e23}
	```
## Notas adicionales
## Referencias