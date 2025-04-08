## Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.
## Solución
Si nos metemos a un paquete UDP vemos que en el stream 32 dice "start" y en el 60 dice "end" y ambos van desde el puerto 5000 al 22.
Podemos usar `Scapy` para hacer un código que agarre el paquete y para cada paquete que tiene como destino el puerto 22 y puerto origen el 5000.
```python
from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
    if UDP in p and p[UDP].dport == 22:
        if p[UDP].sport > 5000:
            flag += chr(p[UDP].sport - 5000)
            
print(flag)
```

Bandera:
```shell
$python3 package.py 
picoCTF{p1LLf3r3d_data_v1a_st3g0}
```
## Notas adicionales
El término "stream" en Wireshark se refiere a la transmisión continua de datos a través de una red.
## Referencias
https://github.com/secdev/scapy