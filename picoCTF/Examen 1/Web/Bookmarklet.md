## Descripción
Why search for the flag when I can make a bookmarklet to print it for me? Browse [here](http://titan.picoctf.net:51361/), and find the flag!
## Solución 1
Cuando nos metemos a la página podemos agarrar el código que nos dan:
```js
javascript:(function() {
	var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÓÇ¡¥Ìí";
	var key = "picoctf";
	var decryptedFlag = "";
	for (var i = 0; i < encryptedFlag.length; i++) {
		decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
	}
	alert(decryptedFlag);
})();
```
Podemos ejecutar el código en un archivo `.js` o ejecutarlo en [Glot.io](https://glot.io/new/javascript) para esto podemos cambiar la alerta con la bandera descifrada por un `console.log`
```js
javascript:(function() {
    var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÓÇ¡¥Ìí";
    var key = "picoctf";
    var decryptedFlag = "";
    for (var i = 0; i < encryptedFlag.length; i++) {
        decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256);
    }
    console.log(decryptedFlag);
})();
```
Bandera: `picoCTF{p@g3_turn3r_0c0d211f}`
## Solución 2
Usando la consola del navegador nos va a saltar la alerta.
```
titan.picoctf.net:51361 says
picoCTF{p@g3_turn3r_0c0d211f}

							OK
```
## Solución 3
Usando el bookmark del navegador.
Podemos colocar el código en un bookmark y al visitar el bookmark el código se va a ejecutar.
```
+-------------------------------------+
|         Edit Bookmark               |
+-------------------------------------+
| Name: [       hola             ]    |
| URL:  [ javascript:(function()...) ]|
+-------------------------------------+
|         All Bookmarks               |
| + Bookmarks                         |
+-------------------------------------+
| [New Folder]          [Cancel][Save]|
+-------------------------------------+
```
## Notas adicionales
[Bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet) are browser bookmarks that execute JavaScript instead of opening a webpage. They're also known as bookmark applets, favlets, or JavaScript bookmarks.

Bookmarklets are natively available in all major browsers, including Mozilla Firefox and Chromium-based browsers like Chrome or Brave `[1]`.
## Referencias
- `[1]` https://www.freecodecamp.org/news/what-are-bookmarklets/