## Descripción
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools! You can download the challenge files here:

- challenge.zip

`ssh -p 51063 ctf-player@atlas.picoctf.net`Using the password `6abf4a82`. Accept the fingerprint with `yes`, and `ls` once connected to begin. Remember, in a shell, passwords are hidden!
## Solución
1. Nos dicen que el número está entre 0 y 1000
2. Adivinamos el 500 y nos dice que el número que buscamos es más grande 
3. Adivino el 700 y nos dicen que el número buscado es más chico
4. Con esa información ya sabemos que el número está entre el rango 500 y el 700
5. Ya solo es cuestión de ir adivinando rangos más pequeños hasta que encontremos el número 
6. En este caso el número era 670
```
Qwerty3341-picoctf@webshell:~$ ssh -p 60470 ctf-player@atlas.picoctf.net
The authenticity of host '[atlas.picoctf.net]:60470 ([18.217.83.136]:60470)' can't be established.
ED25519 key fingerprint is SHA256:M8hXanE8l/Yzfs8iuxNsuFL4vCzCKEIlM/3hpO13tfQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:13: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[atlas.picoctf.net]:60470' (ED25519) to the list of known hosts.
ctf-player@atlas.picoctf.net's password: 
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 700
Lower! Try again.
Enter your guess: 600
Higher! Try again.
Enter your guess: 650
Higher! Try again.
Enter your guess: 660
Higher! Try again.
Enter your guess: 690
Lower! Try again.
Enter your guess: 680
Lower! Try again.
Enter your guess: 670
Congratulations! You guessed the correct number: 670
Here's your flag: picoCTF{g00d_gu355_bee04a2a}
Connection to atlas.picoctf.net closed.
Qwerty3341-picoctf@webshell:~$ 
```
## Notas adicionales

## Referencias