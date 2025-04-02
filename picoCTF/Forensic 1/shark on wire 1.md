## Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.
## Solución
1. Wireshark
2. Usamos `wireshark`
```shell
$wireshark capture.pcap &
[1] 2167
```
3. Agarramos un paquete UDP 
4. Lo seguimos y le aumentamos el stream hasta 6
![[Pasted image 20250401175447.png | 300]]
## Notas adicionales
El `&` en el comando utilizado es que el proceso se va a ejecutar en segundo plano (permite que la terminal siga estando disponible para otros comandos)
## Referencias
https://www.wireshark.org/about.html
https://openwebinars.net/blog/wireshark-que-es-y-ejemplos-de-uso/