## Descripción
What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:
- challenge.zip
## Solución
Usamos el comando `git log` para ver el historial de los commits. 

```shell
debian3341@DESKTOP-VDLU0ET:~$ wget https://artifacts.picoctf.net/c_titan/161/challenge.zip
--2025-03-04 15:31:05--  https://artifacts.picoctf.net/c_titan/161/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.161.55.64, 3.161.55.26, 3.161.55.61, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.161.55.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17739 (17K) [application/octet-stream]
Saving to: ‘challenge.zip’

challenge.zip                     100%[==========================================================>]  17.32K  --.-KB/s    in 0s

2025-03-04 15:31:06 (85.9 MB/s) - ‘challenge.zip’ saved [17739/17739]

debian3341@DESKTOP-VDLU0ET:~$ ls
challenge.zip
debian3341@DESKTOP-VDLU0ET:~$ unzip challenge.zip
Archive:  challenge.zip
  creating: drop-in/
  ...
  inflating: drop-in/.git/logs/refs/heads/master
  
debian3341@DESKTOP-VDLU0ET:~$ ls
challenge.zip  drop-in
debian3341@DESKTOP-VDLU0ET:~$ cd drop-in/
debian3341@DESKTOP-VDLU0ET:~/drop-in$ ls
message.txt
debian3341@DESKTOP-VDLU0ET:~/drop-in$ cat message.txt
This is what I was working on, but I'd need to look at my commit history to know why...debian3341@DESKTOP-VDLU0ET:~/drop-in$
debian3341@DESKTOP-VDLU0ET:~/drop-in$ ls -a
.  ..  .git  message.txt
debian3341@DESKTOP-VDLU0ET:~/drop-in$ git log
commit 10228f3d6437701ef5aaac04213757031f30ebec (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:24 2024 +0000

    picoCTF{t1m3m@ch1n3_8defe16a}
debian3341@DESKTOP-VDLU0ET:~/drop-in$

```
## Notas adicionales

## Referencias
- https://git-scm.com/docs
- https://git-scm.com/docs/git-log