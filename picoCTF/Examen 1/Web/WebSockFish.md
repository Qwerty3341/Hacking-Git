## Descripción
Can you win in a convincing manner against this chess bot? He won't go easy on you! You can find the challenge [here](http://verbal-sleep.picoctf.net:54668/).
## Solución
Si ponemos a escuchar a Burp Suite, podemos ver que los WebSockets que envía el usuario contienen un comando llamado `eval`, el cual tiene un valor entero. En este caso, mientras el valor sea grande pero negativo, el pez irá soltando diferentes mensajes; y si el valor es muy grande, nos dirá lo siguiente:
```
Huh???? How can I be losing this badly... I resign... here's your flag: picoCTF{c1i3nt_s1d3_w3b_s0ck3t5_50441bef}
```
## Notas adicionales
WebSocket es un **protocolo de comunicación que facilita la interacción bidireccional entre un servidor y un cliente** a través de una única conexión TCP `[1]`.
## Referencias
`[1]` https://www.godaddy.com/resources/es/crearweb/websocket-que-es