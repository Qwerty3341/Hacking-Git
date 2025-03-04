## Descripción
How to automate tasks to run at intervals on Linux servers?
Additional details will be available after launching your challenge instance.
## Solución
- Nos conectamos por ssh al host que nos dan 
- Buscamos la bandera con grep
```
debian3341@DESKTOP-VDLU0ET:~$ ssh picoplayer@saturn.picoctf.net -p 54433
The authenticity of host '[saturn.picoctf.net]:54433 ([13.59.203.175]:54433)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:2: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:54433' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password:
Welcome to Ubuntu 20.04.5 LTS (GNU/Linux 6.5.0-1023-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

...

picoplayer@challenge:/$ pwd
/
picoplayer@challenge:/$ grep -r "picoCTF{" /
grep: /etc/.pwd.lock: Permission denied
grep: /etc/gshadow: Permission denied 

...

grep: /proc/26/task/26/io: Permission denied
grep: /proc/26/task/26/patch_state: Permission denied
grep: /proc/26/task/26/ksm_merging_pages: Permission denied
grep: /proc/26/task/26/ksm_stat: Permission denied



^X^C
picoplayer@challenge:/$ grep -r "picoCTF{" etc/
grep: etc/.pwd.lock: Permission denied
grep: etc/gshadow: Permission denied
grep: etc/security/opasswd: Permission denied
grep: etc/shadow: Permission denied
grep: etc/ssh/ssh_host_ecdsa_key: Permission denied
grep: etc/ssh/ssh_host_ed25519_key: Permission denied
grep: etc/ssh/ssh_host_rsa_key: Permission denied
grep: etc/ssh/ssh_host_dsa_key: Permission denied
etc/crontab:# picoCTF{Sch3DUL7NG_T45K3_L1NUX_0bb95b71}
grep: etc/gshadow-: Permission denied
grep: etc/shadow-: Permission denied
grep: etc/ssl/private: Permission denied
grep: etc/sudoers: Permission denied
grep: etc/sudoers.d/README: Permission denied
picoplayer@challenge:/$ Connection to saturn.picoctf.net closed by remote host.
Connection to saturn.picoctf.net closed.
debian3341@DESKTOP-VDLU0ET:~$
```
## Notas adicionales
- No es recomendable usar grep en el directorio raíz
- Al conectarnos por ssh debemos colocar `username@` antes de la dirección del host
## Referencias
- https://www.digitalocean.com/community/tutorials/how-to-use-ssh-to-connect-to-a-remote-server-es