## Descripción
Run the Python script and convert the given number from decimal to binary to get the flag.
## Solución
1. Usamos `wget` para descargar el archivo
2. Usamos nano para revisar el código antes de ejecutarlo
3. Corremos el programa con `python3`
4. Nos pide que pasemos el número 33 a binario
5. Usamos la calculadora del sistema operativo para pasarlo a binario
```shell
debian3341@DESKTOP-VDLU0ET:~$ ls
convertme.py
debian3341@DESKTOP-VDLU0ET:~$ nano convertme.py
debian3341@DESKTOP-VDLU0ET:~$ python3 convertme.py
If 33 is in decimal base, what is it in binary base?
Answer: 100001
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_9c3b7d4d}
debian3341@DESKTOP-VDLU0ET:~$
```
![[33aBinario.png]]
## Solución 2
Usamos `cyberchef` para transformar de decimal a binario
Receta:
```
From Decimal
To Binary

Input
	33
Output
	100001
```
## Notas adicionales
Se puede usar python para hacer convertir decimales a binarios
## Referencias
- https://gchq.github.io/CyberChef/