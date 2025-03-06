## Descripción
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell. Download runme.py Python script
## Solución 1 (Usar cat)
Usamos cat para ver el contenido del archivo antes de ejecutarlo
```python
debian3341@DESKTOP-VDLU0ET:~$ cat runme.py
#!/usr/bin/python3
################################################################################
# Python script which just prints the flag
################################################################################

flag ='picoCTF{run_s4n1ty_run}'
print(flag)
```
## Solución 2 (Ejecutar el `.py`)
Con python3 ejecutamos el archivo `.py` que nos dan
```shell
debian3341@DESKTOP-VDLU0ET:~$ python3 runme.py
picoCTF{run_s4n1ty_run}
```
## Notas adicionales
Es mejor ver el contenido del archivo con un `cat` en ves de ejecutarlo, ya que si el código es malicioso al ejecutarlo podemos tener un problema
## Referencias
