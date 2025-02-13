# Descripción
If I told you a word started with 0x70 in hexadecimal, what would it start with un ASCII
## Solución 1
Convertir el numero en hexadecimal a su representación en codigo ASCII
- Usar una página web hex to ascii
- Usar una herramienta web como cyberhef

Con python
```
>>> chr(0x70)
'p'


picoCTF{p}
```
## Solución 2
Usando cyberchef
```
Input : 0x70
Recipe: From Hex
Output: p
```
## Notas adicionales
- Puede usarse incluso el interprete de Python para convertir de hex a ascil
## Referencias
- https://www.rapidtables.com/convert/numbenhex-to-ascii.html
- https://gchq.github.inlCyherCheff
- https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')&input=MHg3MA