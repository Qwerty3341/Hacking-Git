## Descripción
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?
## Solución
Recibimos una imagen que contiene los siguientes números
```
16 9 3 15 3 20 6 { 20 8 5
14 21 13 2 5 18 19 13 1
19 15 14 }
```
Podemos usar [dCode.fr](https://www.dcode.fr/en) para aplicar el algoritmo A1Z26
```
PICOCTFTHENUMBERSMASON
```
La bandera sería
```
PICOCTF{THENUMBERSMASON}
```
## Notas adicionales
The Letter-to-Number Cipher (or _Number-to-Letter Cipher_ or _numbered alphabet_) consists in replacing each letter by its position in the alphabet, for example A=1, B=2, Z=26, hence its over name A1Z26.
## Referencias
https://www.dcode.fr/letter-number-cipher