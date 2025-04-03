## Descripción
Do you know how to use the web inspector?

Additional details will be available after launching your challenge instance.
## Solución
1. Vemos que en about hay un texto con caracteres random
```html
</header>
<section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMWY4MzI2MTV9">
<h1>
	Try inspecting the page!! You might find it there
</h1>
<!-- .about-container -->
</section>
```
2. Si lo desciframos con base64 nos da la bandera
```bash
$ echo cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMWY4MzI2MTV9 | base64 -d
picoCTF{web_succ3ssfully_d3c0ded_1f832615}
```
## Notas adicionales
En la página about hay un texto que dice "Try inspecting the page!! You might find it there"
## Referencias