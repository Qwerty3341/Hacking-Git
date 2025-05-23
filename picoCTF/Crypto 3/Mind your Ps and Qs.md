## Descripción
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/38f30029ab93478310e906d3d084a4c1/values)
## Solución
Vemos el contenido del archivo y vemos esto:
```sh
$ cat values
Decrypt my super sick RSA:
c:240986837130071017759137533082982207147971245672412893755780400885108149004760496
n:831416828080417866340504968188990032810316193533653516022175784399720141076262857
e:65537
```
Podemos usar la página https://www.dcode.fr/rsa-cipher
```
picoCTF{sma11_N_n0_g0od_23540368}
```
## Notas adicionales
## Referencias