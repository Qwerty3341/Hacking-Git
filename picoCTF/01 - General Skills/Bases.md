## Descripción
What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.
## Solución
Descifrar el mensaje con comandos de Linux
- Usar el comando `echo "bDNhcm5fdGgzX3IwcDM1" | base64 -d`
```bash
Qwerty3341-picoctf@webshell:~$ echo "bDNhcm5fdGgzX3IwcDM1" | base64 -d
l3arn_th3_r0p35
Qwerty3341-picoctf@webshell:~$ 

picoCTF{l3arn_th3_r0p35}
```
## Notas adicionales
El texto dice `learn the ropes` que significa: `to learn/know how to do a job or activity`
## Referencias
- https://es.linux-console.net/?p=30495
- https://www.youtube.com/shorts/4Ate0kVYbUY
- [LEARN/KNOW THE ROPES - Cambridge English Dictionary](https://dictionary.cambridge.org/dictionary/english/learn-know-the-ropes)
