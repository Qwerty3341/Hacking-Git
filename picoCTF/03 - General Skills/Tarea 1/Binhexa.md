## Descripción
How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.
## Solución
Usar la calculadora del sistema operativo en modo programador.
```
debian3341@DESKTOP-VDLU0ET:~$ nc titan.picoctf.net 50749

Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 11110110
Binary Number 2: 01110111


Question 1/6:
Operation 1: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 0001 0110 1101

Incorrect input. Provide the right input
Enter the binary result: 0001 0110 1101

Incorrect input. Provide the right input
Enter the binary result: 0111 0110

Incorrect input. Provide the right input
Enter the binary result: 101101101
'Correct!

Question 2/6:
Operation 2: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 01110110

Incorrect input. Provide the right input
Enter the binary result: 1110110
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11110111
Correct!

Question 4/6:
Operation 4: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 111001001011010
Correct!

Question 5/6:
Operation 5: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 1111011
Incorrect. Try again
Enter the binary result: 10
Incorrect. Try again
Enter the binary result: 0010
Incorrect. Try again
Enter the binary result: 11110110
Incorrect. Try again
Enter the binary result: 000111101100
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00111011
Correct!

Enter the results of the last operation in hexadecimal: 3B

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_d6f8047e}
debian3341@DESKTOP-VDLU0ET:~$
```
## Notas adicionales
- Para las operaciones que no son las de `<<` o `>>` los primeros ceros del numero no se toman en cuenta
- Se puede hacer un programa en python que haga más fácil calcular operaciones binarias
## Referencias
