## Descripción
Connect to this PostgreSQL server and find the flag!`psql -h saturn.picoctf.net -p 56279 -U postgres pico`Password is `postgres`
## Solución
Nos conectamos con el comando que nos dan y vemos que estamos en una línea de comandos de Postgre SQL.
```sql
pico=#
```
Si usamos el comando `\dt` podemos ver todas las tablas de la base y vemos esto:
```sql
pico=# \dt
         List of relations
 Schema | Name  | Type  |  Owner
--------+-------+-------+----------
 public | flags | table | postgres
(1 row)
```
Ahora que vemos que hay una tabla llamada flags vamos a hacer una consulta a esa tabla
```sql
pico=# select * from flags;
 id | firstname | lastname  |                address
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_21c94904}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
(3 rows)
```
## Notas adicionales
Antes de conectarnos al servidor tenemos que tener instalado un cliente postgre sql 
```sh
sudo apt install postgresql-client
```
## Referencias
- https://www.postgresql.org/docs/17/app-psql.html