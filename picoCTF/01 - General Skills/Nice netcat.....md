## Descripción
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 43239`, but it doesn't speak English...
## Solución 
Ejecutar el comando `nc mercury.picoctf.net 43239` y los valores que te arroja el servidor dejarlos en una sola línea para después convertir la cadena de números a ASCII con el traductor ascii de [RAKKOTOLLS](https://es.rakko.tools/)

```
Qwerty3341-picoctf@webshell:~$ nc mercury.picoctf.net 43239
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
55 
99 
48 
56 
50 
49 
102 
53 
125 
10 
```

Lo dejamos en una linea para convertir cada numero a ascii
```
112 105 99 111 67 84 70 123 103 48 48 100 95 107 49 116 116 121 33 95 110 49 99 51 95 107 49 116 116 121 33 95 55 99 48 56 50 49 102 53 125 10 

picoCTF{g00d_k1tty!_n1c3_k1tty!_7c0821f5}
```

![[Pasted image 20250212193634.png]]
## Notas adicionales
Se puede usar la función `chr()` de python para convertir un número a ascii con la posibilidad de hacer un programa que traduzca archivos con números a ascii
## Referencias
- https://es.rakko.tools/tools/76/