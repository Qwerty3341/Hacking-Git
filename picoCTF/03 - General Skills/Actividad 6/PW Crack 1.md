## Descripción
Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/11/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/11/level1.flag.txt.enc) in the same directory too.
## Solución
Al ejecutar el archivo de python nos indica que debemos poner la contraseña para que nos de la bandera la cual está en el archivo `.enc`
Lo que debemos hacer es usar `nano` para ver la contraseña dentro de un if del código
Aquí vemos el código:
```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)>######################################################

flag_enc = open('level1.flag.txt.enc', 'rb').read()

def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "1e1a"):
        print("Welcome back... your flag, user:")
        decryption = st
```

```shell
debian3341@DESKTOP-VDLU0ET:~$ python3 level1.py
Please enter correct password for flag: 1a1e
That password is incorrect
debian3341@DESKTOP-VDLU0ET:~$ python3 level1.py
Please enter correct password for flag: 1e1a
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_fa343060}
debian3341@DESKTOP-VDLU0ET:~$
```
## Notas adicionales
Podríamos modificar también el código para que no nos pida la contraseña y muestre la bandera directamente pero es más rápido ver el código y ver la contraseña directamente
## Referencias
