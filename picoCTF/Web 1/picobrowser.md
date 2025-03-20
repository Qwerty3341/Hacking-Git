## Descripción
This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/50522/` ([link](https://jupiter.challenges.picoctf.org/problem/50522/)) or http://jupiter.challenges.picoctf.org:50522
## Solución
Tenemos que cambiar el User-Agent, para hacerlo en navegadores basados en chromium:
- Inspeccionamos la página
- Nos vamos a Network
- Le damos en los tres puntos de la parte superior derecha
- Le damos en More tools
- Seleccionamos Network Conditions
- En la sección de User agent quitamos el check box de 'Use browser default'
- Colocamos `picobrowser` y hacemos una nueva solicitud (refrescamos la página)
```
picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}
```
## Notas adicionales
- En navegadores basados en Firefox el proceso es similar ya que la consola es diferente
- En algunos navegadores el DevTools bloquea las solicitudes con un diferente User Agent
## Referencias
https://www.searchenginejournal.com/change-user-agent/368448/