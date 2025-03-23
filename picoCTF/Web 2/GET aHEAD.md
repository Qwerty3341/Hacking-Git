## Descripción
Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:34561/](http://mercury.picoctf.net:34561/)
## Solución
`Usamos Burpsuite`
1. Desde burp suite vemos la configuración del proxy  y vemos que esta corriendo en el puerto 8080 
	![[paso1.png|600]]
2. Ahora nos vamos a un navegador como Firefox y en las configuraciones de red podemos decirle que el proxy va a ser manual, así que ponemos el proxy 127.0.1 en el puerto 8080 
	![[paso2.png|600]]
3. Activamos el interceptado del proxy
	![[paso3.png|]]
4. Ahora si movemos algo en la página azul y roja podemos ver que Burpsuite intercepta la petición y vemos que el método de petición es el POST
	 ![[paso4.png|600]]
5. Vemos que si cambiamos el método POST por el HEAD obtenemos una respuesta de la página y ahí vemos la bandera
	![[paso5.png|600]]
## Notas adicionales
## Referencias
https://www.youtube.com/watch?v=KT6McmK0FgA