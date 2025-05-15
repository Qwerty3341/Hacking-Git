## Descripción
Theres tapping coming in from the wires. What's it saying `nc jupiter.challenges.picoctf.org 21610`.
## Solución
Vemos que al conectarnos al servidor nos mandan esto:
```
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. ...-- ----. ----- ..--- ----- .---- ----. ..... .---- ----. }
```
Usamos CyberChef y ponemos la receta:
```
From Morse Code
Letter delimitter = Space
Word delimiter = Line feed
```
Nos suelta esto:
```
PICOCTFM0RS3C0D31SFUN3902019519

La bandera sería

PICOCTF{M0RS3C0D31SFUN3902019519}
```
## Notas adicionales
Se podría hacer la conversión de puntos y rallas con la tabla:

| Letra | Código | Letra | Código |
| ----- | ------ | ----- | ------ |
| A     | •–     | N     | –•     |
| B     | –•••   | O     | –––    |
| C     | –•–•   | P     | •––•   |
| D     | –••    | Q     | ––•–   |
| E     | •      | R     | •–•    |
| F     | ••–•   | S     | •••    |
| G     | ––•    | T     | –      |
| H     | ••••   | U     | ••–    |
| I     | ••     | V     | •••–   |
| J     | •–––   | W     | •––    |
| K     | –•–    | X     | –••–   |
| L     | •–••   | Y     | –•––   |
| M     | ––     | Z     | ––••   |
## Referencias
