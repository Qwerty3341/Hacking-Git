## Descripción
A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag. To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder! Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/a917f567b9cc0f1a730a7801b309955df4d2234a8114326857b9759e9e5d0453/myNetworkTraffic.pcap) and try to get the flag.
## Solución
- Descargamos el archivo con `wget`
- Hay algunos paquetes que tienen una carga cifrada en base 64 
- Aplicamos el filtro para ver los paquetes que tengan una carga de longitud 12 o 4
- Ordenamos los paquetes por tiempo
![[f1-t3Forensic.png]]
- Sacamos la bandera con "Show packet bytes" y ponemos "Decode as `Base64`"
```
picoCTF{1t_w4snt_th4t_34sy_tbh_4r_959f50d3}
```
## Notas adicionales
PCAP files contain critical, packet-level evidence and vital clues into the root cause of a wide range of issues occurring on the network.
## Referencias
- https://www.endace.com/learn/what-is-a-pcap-file