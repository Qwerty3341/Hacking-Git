## Descripción
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.

Additional details will be available after launching your challenge instance.
## Solución n
1. Indagamos por la página y nos damos cuenta que hay una pequeña documentación de una api.
2. Ahí vemos rutas para la página como about, services, etc. 
3. Si nos vamos al diagnostic vemos una ruta que es la de `/heapdump`, si la visitamos la página nos dará un archivo `.heapsnapshot` que es un archivo que guarda el rendimiento de memoria.
4. Si lo descargamos y lo abrimos en un editor de texto, podemos usar la función `ctl f` del editor para ver si está la bandera ahí
5. Vemos que la bandera se encuentra en la línea número 273,061
```
,6,7838,256338
,6,21628,256344
,6

picoCTF{Pat!3nt_15_Th3_K3y_388d10f7}

,7880,256350
,6,8003,256356
,6,7882,256362
,6,21629,256368
```
## Notas adicionales
La extensión de archivo HEAPSNAPSHOT está relacionada principalmente con las llamadas Heap Snapshots, archivos que se utilizan para perfilar el rendimiento de la memoria y corregir pérdidas de memoria `[1]`.

Las instantáneas se almacenan inicialmente en la memoria del proceso del renderizador. Se transfieren a DevTools a pedido, cuando los usuarios hacen clic en el icono de instantánea para verlo `[1]`.
## Referencias
- `[1]` https://archivos.xyz/extension/heapsnapshot