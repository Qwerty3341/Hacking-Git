## Descripción
Help us test the form by submitting the username as `test` and password as `test!`The website running [here](http://saturn.picoctf.net:63156/).
## Solución
Vamos a usar burp suite
Si usamos el usuario test y la contraseña test! burp va a interceptar varias peticiones, pero después de unos forwards nos sale esto
```
GET /next-page/id=bF90aGVfd2F5XzAxZTc0OGRifQ== HTTP/1.1
Host: saturn.picoctf.net:64466
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://saturn.picoctf.net:64466/next-page/id=cGljb0NURntwcm94aWVzX2Fs
DNT: 1
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Priority: u=0, i
```
En el refer vemos un id=cGljb0NURntwcm94aWVzX2Fs que si lo decodificamos a base 64 nos va a aparecer un fragmento de la bandera
```
picoCTF{proxies_al
```
Si seguimos con los forwards nos encontramos con esto:
```
GET /home HTTP/1.1
Host: saturn.picoctf.net:64466
User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://saturn.picoctf.net:64466/next-page/id=bF90aGVfd2F5XzAxZTc0OGRifQ==
DNT: 1
Connection: keep-alive
Upgrade-Insecure-Requests: 1
Priority: u=0, i
```
Ahora si decodificamos el id nos da el resto de la bandera:
```
l_the_way_01e748db}
```
Bandera:
```
picoCTF{proxies_all_the_way_01e748db}
```
## Notas adicionales
## Referencias