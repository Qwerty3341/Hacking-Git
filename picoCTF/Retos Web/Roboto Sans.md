## Descripción
The flag is somewhere on this web application not necessarily on the website. Find it.

Additional details will be available after launching your challenge instance.
## Solución
1. Vamos al robots.txt
```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```
2. Los caracteres random los podemos descifrar con base64 (podemos usar CyberChef)
```base64
ZmxhZzEudHh0;anMvbXlmaW ->  flag1.txtjs/myfi

anMvbXlmaWxlLnR4dA==    ->  js/myfile.txt
```
3. Si vemos la ruta `http://saturn.picoctf.net:51689/js/myfile.txt` nos dan la bandera
```
picoCTF{Who_D03sN7_L1k5_90B0T5_718c9043}
```
## Notas adicionales
## Referencias
https://gchq.github.io/CyberChef/