## Descripción
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/15796/` ([link](https://jupiter.challenges.picoctf.org/problem/15796/)) or http://jupiter.challenges.picoctf.org:15796
## Solución
Si tratamos de acceder como Joe nos va a dar un mensaje que no podemos hacerlo, sin embargo si accedemos como cualquier otro usuario nos dice que hemos accedido con éxito pero que no hay bandera para nosotros.

Si nos vamos a la consola en la pestaña de 'Application' en las cookies, vemos que se genera una cookie la muestra una columna como esta:

| Name         | Value                                                                  |
| ------------ | ---------------------------------------------------------------------- |
| admin        | False                                                                  |
| cf_clearance | z4EAQimOkuzlav$kotTVPxmXDrj_OMAt&c1nebktw-1741899567-1.2.11--wROvcl... |
| password     | (Oculto o no mostrado en la imagen)                                    |
| username     | Joedede                                                                |
Si el valor del admin lo cambiamos a True y recargamos la página, ahora nos van a mostrar la bandera la cual es: `picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}`
## Notas adicionales
## Referencias
https://developer.chrome.com/docs/devtools/application/cookies?hl=es-419