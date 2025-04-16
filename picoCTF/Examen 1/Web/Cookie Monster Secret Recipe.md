## Descripción
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe? You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:60118/) and good luck
## Solución
Accedemos al login con cualquier nombre. Ejemplo name admin y password admin.
Nos devuelven esta página:
```
# Access Denied

Cookie Monster says: 'Me no need password. Me just need cookies!'

Hint: Have you checked your cookies lately?

[Go back](http://verbal-sleep.picoctf.net:60118/)
```
Si revisamos las cookies de la página vemos que hay una que se llama `"secret_recipe"` con un valor de: `cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzX0E5NjRBMTM0fQ%3D%3D`.
### Descifrar con base64
En este caso probe a descifrarlo en base64 y sí dio la bandera
```sh
$ echo "cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzX0E5NjRBMTM0fQ%3D%3D" | base64 -d
picoCTF{c00k1e_m0nster_l0ves_c00kies_A964A134}base64: invalid input
```
## Notas adicionales
## Referencias