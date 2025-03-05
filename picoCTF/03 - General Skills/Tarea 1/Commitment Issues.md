## Descripción
I accidentally wrote the flag down. Good thing I deleted it! You download the challenge files here:
- challenge.zip
## Solución
- Vemos los commits con `git log`
- En uno de los commits dice que se removió información sensible
- Como solo son dos commits podemos ver las diferencias entre los dos con `git diff commit1 commit2`
- vemos que el archivo `message.txt` antes tenía escrita la bandera
```shell
debian3341@DESKTOP-VDLU0ET:~$ wget https://artifacts.picoctf.net/c_titan/138/challenge.zip
...
debian3341@DESKTOP-VDLU0ET:~$ ls
challenge.zip
debian3341@DESKTOP-VDLU0ET:~$ unzip challenge.zip
Archive:  challenge.zip
   ...
 extracting: drop-in/message.txt
 
debian3341@DESKTOP-VDLU0ET:~$ ls
challenge.zip  drop-in
debian3341@DESKTOP-VDLU0ET:~$ cd drop-in/
debian3341@DESKTOP-VDLU0ET:~/drop-in$ ls
message.txt
debian3341@DESKTOP-VDLU0ET:~/drop-in$ cat message.txt
TOP SECRET
debian3341@DESKTOP-VDLU0ET:~/drop-in$ git branch
* master
debian3341@DESKTOP-VDLU0ET:~/drop-in$ git log
commit 42942c9c605b30100f5d859ef6e172027447c0db (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:23 2024 +0000

    remove sensitive info

commit b562f0b425907789d11d2fe2793e67592dc6be93
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:06:23 2024 +0000

    create flag
    
debian3341@DESKTOP-VDLU0ET:~/drop-in$ git diff b562f0b425907789d11d2fe2793e67592dc6be93 42942c9c605b30100f5d859ef6e172027447c0db
diff --git a/message.txt b/message.txt
index 0e0fefc..d552d1e 100644
--- a/message.txt
+++ b/message.txt
@@ -1 +1 @@
-picoCTF{s@n1t1z3_c785c319}
+TOP SECRET
debian3341@DESKTOP-VDLU0ET:~/drop-in$
```
## Notas adicionales
Lo que es eliminado git le pone un `-` y lo que fue añadido le pone un `+`
## Referencias