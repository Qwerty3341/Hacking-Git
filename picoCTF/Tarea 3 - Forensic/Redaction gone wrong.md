## Descripción
Now you DON’T see me. This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?
## Solución 1
Después de descargar el archivo podemos abrirlo y vemos que es un pdf que tiene letras con un subrayado negro para tapar los caracteres.

Si mantenemos el click izquierdo para seleccionar varias letras nos damos cuenta de que se pueden ver algunos caracteres que estaban tapados.

En uno de los rectángulos negros encontramos la bandera.
![[Pasted image 20250511182155.png | 300]] ![[Pasted image 20250511182125.png | 300]]
## Solución 2
==Usando `pdftotext`==
Vamos a la terminal y colocamos el comando `pdftotext`
```bash
$pdftotext Financial_Report_for_ABC_Labs.pdf
```
Nos genera un archivo `txt`
```sh
$l
Financial_Report_for_ABC_Labs.pdf  Financial_Report_for_ABC_Labs.txt
```
Vemos el contenido y ahí está todo el texto del pdf
```bash
$cat Financial_Report_for_ABC_Labs.txt
Financial Report for ABC Labs, Kigali, Rwanda for the year 2021.
Breakdown - Just painted over in MS word.

Cost Benefit Analysis
Credit Debit
This is not the flag, keep looking
Expenses from the
picoCTF{C4n_Y0u_S33_m3_fully}
Redacted document.
```
## Notas adicionales
## Referencias