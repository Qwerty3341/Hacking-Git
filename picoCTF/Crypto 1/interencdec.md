## Descripción
Can you get the real meaning from this file. Download the file [here](https://artifacts.picoctf.net/c_titan/111/enc_flag).
## Solución
Usar base64 para descifrar el texto 
```sh
$ l
enc_flag

$ cat enc_flag
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==

$ cat enc_flag | base64 -d
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='

$ echo d3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ== | base64 -d
wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
```

Usamos CyberChef para rotar el texto que nos dan
```
Input: wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}
Recipe: ROT13 Amount = 19
Output: picoCTF{caesar_d3cr9pt3d_890d2379}
```
## Notas adicionales
## Referencias