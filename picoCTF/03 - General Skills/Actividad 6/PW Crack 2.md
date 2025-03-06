## Descripción
Can you crack the password to get the flag? Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.
## Solución
La contraseña la ocultan con números hexadecimales que luego los pasan a texto
```python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################

flag_enc = open('level2.flag.txt.enc', 'rb').read()

def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
level_2_pw_check()
```

Lo que hice fue imprimir esa concatenación de funciones `chr()` antes de que se llame la función `level_2_pw_check()`:
```python
print(chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36))
level_2_pw_check()
```

Al ejecutar el archivo de python obtenemos esto:
```shell
debian3341@DESKTOP-VDLU0ET:~$ nano level2.py
debian3341@DESKTOP-VDLU0ET:~$ python3 level2.py
de76
Please enter correct password for flag: de76
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_489dea9a}
```
## Notas adicionales
## Referencias
