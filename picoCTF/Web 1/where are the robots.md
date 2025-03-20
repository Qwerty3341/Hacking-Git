## Descripción
Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/60915/` ([link](https://jupiter.challenges.picoctf.org/problem/60915/)) or http://jupiter.challenges.picoctf.org:60915
## Solución
Podemos buscar los archivos robots directamente en la url de la web
`https://jupiter.challenges.picoctf.org/problem/60915/robots.txt`
Al hacer esto nos manda a una página que nos devuelve esto:
```
User-agent: *
Disallow: /8028f.html
```
Lo que está después del Disallow es la raíz de la web la cual nos da esta página:
```
Guess you found the robots  
picoCTF{ca1cu1at1ng_Mach1n3s_8028f}
```
## Notas adicionales
## Referencias
https://developers.google.com/search/docs/crawling-indexing/robots/intro?hl=es