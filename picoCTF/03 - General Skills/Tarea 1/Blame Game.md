## Descripción
Someone's commits seems to be preventing the program from working. Who is it? You can download the challenge files here:
- challenge.zip
## Solución
1. Con `wget` descargamos el archivo
2. Nos vamos al directorio `/drop-in`
3. Una vez ahí vamos que hay un archivo `.py` el cual al ejecutarlo solo manda un error
4. Cuando vemos el contenido con cat no hay ninguna pista de la bandera 
5. En la descripción nos dicen que el programa no sirve por los commits de alguien
6. Con `git log message.py` vemos que el autor de un commit de es la bandera
```shell
debian3341@DESKTOP-VDLU0ET:~/drop-in$ cat message.py
print("Hello, World!"

debian3341@DESKTOP-VDLU0ET:~/drop-in$ git log message.py
commit 0fe87f16cbd8129ed5f7cf2f6a06af6688665728
Author: picoCTF{@sk_th3_1nt3rn_ea346835} <ops@picoctf.com>
Date:   Sat Mar 9 21:09:25 2024 +0000

    optimize file size of prod code

commit 7e8a2415b6cca7d0d0002ff0293dd384b5cc900d
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:25 2024 +0000

    create top secret project
debian3341@DESKTOP-VDLU0ET:~/drop-in$
```
## Notas adicionales

## Referencias
- https://primer.picoctf.org/#_git_version_control