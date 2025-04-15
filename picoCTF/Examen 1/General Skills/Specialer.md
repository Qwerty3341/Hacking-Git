## Descripción
Reception of Special has been cool to say the least. That's why we made an exclusive version of Special, called Secure Comprehensive Interface for Affecting Linux Empirically Rad, or just 'Specialer'. With Specialer, we really tried to remove the distractions from using a shell. Yes, we took out spell checker because of everybody's complaining. But we think you will be excited about our new, reduced feature set for keeping you focused on what needs it the most. Please start an instance to test your very own copy of Specialer.

Additional details will be available after launching your challenge instance.
## Solución
Muchos comandos en el servidor no sirven. Algunos de los que sirven son echo, cd y pwd. Podemos usar el comando `echo '$(< un_archivo)'` para ver el contenido de un archivo, algo así como un cat.

Vemos que en el directorio de nuestro usuario hay varias carpetas (las podemos ver con el comando cd y haciendo un doble tab)
```sh
Specialer$ cd
.hushlogin  .profile    abra/       ala/        sim/
```
Si usamos el echo para ver el contenido de los archivos dentro del directorio `abra/`, aquí no encontramos la bandera pero si vamos al directorio `ala/` podemos ve que hay dos archivos:
```sh
Specialer$ cd
kazam.txt  mode.txt

Specialer$ echo "$(< kazam.txt)"
return 0 picoCTF{y0u_d0n7_4ppr3c1473_wh47_w3r3_d01ng_h3r3_d5ef8b71}
```
## Notas adicionales
## Referencias