## Descripción
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/c0da20f29337e87ffb58ea987d8c596e/Forensics%20is%20fun.pptm)
## Solución
Podemos ver si olevba puede detectar algo en el archivo de power point
```sh
$olevba Forensics\ is\ fun.pptm 
olevba 0.60.2 on Python 3.11.2 - http://decalage.info/python/oletools
===============================================================================
FILE: Forensics is fun.pptm
Type: OpenXML
WARNING  For now, VBA stomping cannot be detected for files in memory
-------------------------------------------------------------------------------
VBA MACRO Module1.bas 
in file: ppt/vbaProject.bin - OLE stream: 'VBA/Module1'
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
Sub not_flag()
    Dim not_flag As String
    not_flag = "sorry_but_this_isn't_it"
End Sub
No suspicious keyword or IOC found.
```
Vemos que no hay nada

Podemos desempaquetar el archivo `pptm` para ver su contenido
```sh
unzip Forensics\ is\ fun.pptm -d archivos
```
Exploramos las carpetas
```sh
$l
'[Content_Types].xml'   _rels/   docProps/   ppt/
```
En la ruta `.../archivos/ppt/slideMasters` vemos un archivo llamado hidden
```sh
$cat hidden 
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q
```
Si usamos base 64 en un principio no nos muestra nada pero si juntamos las letras nos dan la bandera
```sh
$cat hidden | tr -d ' ' | base64 -d
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}base64: invalid input
```
## Notas adicionales
## Referencias