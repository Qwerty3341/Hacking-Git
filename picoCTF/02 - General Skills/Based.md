## Descripción
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29956`.
## Solución
- Nos conectamos a un servidor con el comando: nc jupiter.challenges.picoctf.org 
- Usamos cyberchef para ir traduciendo los números a letras 

```shell
Qwerty3341-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29956 
Let us see how data is stored
street
Please give the 01110011 01110100 01110010 01100101 01100101 01110100 as a word.
...
you have 45 seconds.....

Input:
street^[[F
WRONG!
street                  
Qwerty3341-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29956
Let us see how data is stored
falcon
Please give the 01100110 01100001 01101100 01100011 01101111 01101110 as a word.
...
you have 45 seconds.....

Input:
falcon
Please give me the  143 150 141 151 162 as a word.
Input:
Too slow!
chair
Qwerty3341-picoctf@webshell:~$ nc jupiter.challenges.picoctf.org 29956 
Let us see how data is stored
colorado
Please give the 01100011 01101111 01101100 01101111 01110010 01100001 01100100 01101111 as a word.
...
you have 45 seconds.....

Input:
colorado
Please give me the  160 145 141 162 as a word.
Input:
pear
Please give me the 70656172 as a word.
Input:
pear
You've beaten the challenge
Flag: picoCTF{learning_about_converting_values_b375bb16}

Qwerty3341-picoctf@webshell:~$ 
```

`picoCTF{learning_about_converting_values_b375bb16}`
## Notas adicionales
El ejercicio también se podría realizar con python pero debido al corto tiempo de respuesta es más fácil usar cyber chef
## Referencias
- https://gchq.github.io/CyberChef/#input=NzA2NTYxNzI