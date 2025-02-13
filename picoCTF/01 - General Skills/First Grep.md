## Descripción
Can you find the flag in file? This would be really tedious to look through manually, something tells me there is a better way.
## Solución 1
Usando el comando egrep para ver considencias de texto en el archivo
- Se usa egrep para encontrar el patrón de caracteres 'picoCTF{' ya que en la descripción del problema se menciona que la bandera está en una parte del texto
```bash
Qwerty3341-picoctf@webshell:~$ egrep 'picoCTF{' file 
picoCTF{grep_is_good_to_find_things_5af9d829}
Qwerty3341-picoctf@webshell:~$ 
```

## Solución 2
Buscarlo a mano en un editor de texto
- Si se usa nano en la segunda línea del  archivo se ve claramente la bandera
- `Qwerty3341-picoctf@webshell:~$ nano file`
![[Pasted image 20250212180916.png]]
```
picoCTF{grep_is_good_to_find_things_5af9d829}
```
## Notas adicionales
Aunque se puede ver la bandera a simple vista es mejor usar `egrep` ya que lo hace más rápido y en casos de qué el archivo sea más grande se tardaría mucho tiempo en encontrar la bandera a mano
## Referencias
- [Learn Grep and Regular Expressions with examples - Linux Tutorial](https://ryanstutorials.net/linuxtutorial/grep.php)