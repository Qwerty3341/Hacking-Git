## Descripción
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/fa4a277cfa846e07a5981d8a19288a2e/whitepages.txt) is all blank!
## Solución
- Si vemos el archivo con `xxd` obtenemos esto:
```bash
$ cat whitepages.txt | xxd | head
00000000: e280 83e2 8083 e280 83e2 8083 20e2 8083  ............ ...
00000010: 20e2 8083 e280 83e2 8083 e280 83e2 8083   ...............
00000020: 20e2 8083 e280 8320 e280 83e2 8083 e280   ...... ........
00000030: 83e2 8083 20e2 8083 e280 8320 e280 8320  .... ...... ...
00000040: 2020 e280 83e2 8083 e280 83e2 8083 e280    ..............
00000050: 8320 20e2 8083 20e2 8083 e280 8320 e280  .  ... ...... ..
00000060: 8320 20e2 8083 e280 83e2 8083 2020 e280  .  .........  ..
00000070: 8320 20e2 8083 2020 2020 e280 8320 e280  .  ...    ... ..
00000080: 83e2 8083 e280 83e2 8083 2020 e280 8320  ..........  ...
00000090: e280 8320 e280 8320 e280 83e2 8083 e280  ... ... ........
```
- Usaremos el editor `Ghex` para modificar los bytes del archivo
- Lo primero que haremos es modificar los bytes `E2 80 83` por 30, esto sustituye los bytes por un 0
![[img-p1-wp.png]]
- Después vamos a reemplazar los espacios en blanco por 1s. Encontramos los 20s para reemplazarlos por 31.
![[img-2-wp.png]]
- Copiamos el binario resultante y lo mandamos a un conversor de binario a ASCCI para eso nos vamos al sitio [RapidTables](https://www.rapidtables.com/)  y obtenemos este resultado
```
		picoCTF

		SEE PUBLIC RECORDS & BACKGROUND REPORT
		5000 Forbes Ave, Pittsburgh, PA 15213
		picoCTF{not_all_spaces_are_created_equal_3e2423081df9adab2a9d96afda4cfad6}
		
```
## Notas adicionales
Esto se puede hacer con otros editores o con python
## Referencias
- https://www.geeksforgeeks.org/linux-network-information-service/
- https://wiki.gnome.org/Apps/Ghex
- https://www.rapidtables.com/convert/number/binary-to-ascii.html