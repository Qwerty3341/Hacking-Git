## Descripción
How about trying to match a regular expression

Additional details will be available after launching your challenge instance.
## Solución
En el código fuente vemos este código
```js
function send_request() {
	let val = document.getElementById("name").value;
	// ^p.....F!?
	fetch(`/flag?input=${val}`)
		.then(res => res.text())
		.then(res => {
			const res_json = JSON.parse(res);
			alert(res_json.flag)
			return false;
		})
	return false;
}
```
- En el comentario vemos una expresión regular.
	- `^p` indica que inicia con la letra p
	- `.....` Indica que podemos poner 5 caracteres dentro de ese rango
	- `F` va a ser una F
	- `!?` Opcionalmente puede acabar con un !
Si colocamos `p12345F!` en la página nos dan la bandera:
```
picoCTF{succ3ssfully_matchtheregex_c64c9546}
```
## Notas adicionales
## Referencias