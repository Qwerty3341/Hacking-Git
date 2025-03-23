## Descripción
There is some interesting information hidden around this site [http://mercury.picoctf.net:27393/](http://mercury.picoctf.net:27393/). Can you find it?
## Solución
`Inspeccionando`
- Primero vemos el html del `What` y hay un comentario que dice 
	- `Here's the first part of the flag: picoCTF{t`
- Después nos vamos al CSS y vemos otro comentario 
	- `/* CSS makes the page look nice, and yes, it also has part of the flag. Here's part 2: h4ts_4_l0 */`
- Si vamos al `.js` encontramos un comentario que dice 
	- `/* How can I keep Google from indexing my website? */`
- Vamos al `robots.txt` y nos encontramos con esto
	```
	User-agent: *
	Disallow: /index.html
	# Part 3: t_0f_pl4c
	# I think this is an apache server... can you Access the next flag?
	```
- Como nos menciona el apache server podríamos acceder al archivo `.htaccess` que es un archivo de configuración de Apache server para administrar configuraciones del servidor por directorio. Al entrar al archivo vemos este mensaje:
	```
	# Part 4: 3s_2_lO0k
	# I love making websites on my Mac, I can Store a lot of information there.
	```
- Lo de hacer webs con la Mac da la pista de que debemos buscar el archivo `.DS_Store` que es un archivo que se crea en macOS para colocar algunas configuraciones del sistema. Obtenemos este mensaje:
	`Congrats! You completed the scavenger hunt. Part 5: _d375c750}`
- Armamos la bandera y queda así:
	- `picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_d375c750}`
## Notas adicionales
El problema se resuelve solo con el navegador
## Referencias
- https://stackoverflow.com/questions/390368/stop-google-from-indexing
- https://developers.google.com/search/docs/crawling-indexing/robots/intro?hl=en&visit_id=638783583221658810-2891618495&rd=2
- https://httpd.apache.org/docs/current/howto/htaccess.html
- https://helpx.adobe.com/es/dreamweaver/kb/remove-ds-store-files-mac.html