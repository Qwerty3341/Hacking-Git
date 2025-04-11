## Descripción
If you want to hash with the best, beat this test!
`nc saturn.picoctf.net 53226`
Additional details will be available after launching your challenge instance.
## Solución
- Cuando nos conectamos al servidor nos piden que hagamos un hash md5 de una frase que nos dan.
- Podemos usar el comando `echo -n 'texto para hacer el hash' | md5sum`
```shell
$ nc saturn.picoctf.net 53226
Please md5 hash the text between quotes, excluding the quotes: 'Clint Eastwood'
Answer:
b84954cb41831fa842dd69f6e1836b6e
b84954cb41831fa842dd69f6e1836b6e
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'clowns'
Answer:
f9b12092c70ec2d9ae6d9ff68b061b27
f9b12092c70ec2d9ae6d9ff68b061b27
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'Hollywood'
Answer:
1ac441036f927b9815ba1137464ee064
1ac441036f927b9815ba1137464ee064
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_3eb82b73}
```
Comandos para cada frase:
```bash
$ echo -n 'Clint Eastwood' | md5sum
b84954cb41831fa842dd69f6e1836b6e  -
$ echo -n 'clowns' | md5sum
f9b12092c70ec2d9ae6d9ff68b061b27  -
$ echo -n 'Hollywood' | md5sum
1ac441036f927b9815ba1137464ee064  -
```
## Notas adicionales
El "-" en la salida del comando md5sum no se toma en cuenta para la respuesta, indica que el hash generado corresponde a datos proporcionados a través de la entrada estándar (stdin), en lugar de un archivo específico.
## Referencias