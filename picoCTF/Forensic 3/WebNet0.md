## Descripción
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.
## Solución
Al descargar los dos archivos nos vamos a wireshark

```sh
$l
capture.pcap  picopico.key
```

```sh
$wireshark capture.pcap &
```

Para decodificar un TSL necesitamos la llave así que la cargamos desde el archivo `picopico.key`
1. Nos vamos a Edit
2. Protocols
3. TLS
4. Edit en RSA keys list
5. Presionamos el botón `+`
6. En el bloque de File le damos en Browse
7. Cargamos el archivo `picopico.key'
8. Le damos a OK

Después vamos a los paquetes y buscamos la bandera
1. Le damos en Edit
2. Find Next 
3. En la nueva pestaña que se abre en la primera lista de opciones la ponemos en Packet details
4. En la tercera lista le ponemos String
5. Finalmente en el buscador colocamos "`picoCTF`"
![[Pasted image 20250429163858.png]]

```
00e0   67 3a 20 67 7a 69 70 0d 0a 50 69 63 6f 2d 46 6c   g: gzip..Pico-Fl
00f0   61 67 3a 20 70 69 63 6f 43 54 46 7b 6e 6f 6e 67   ag: picoCTF{nong
0100   73 68 69 6d 2e 73 68 72 69 6d 70 2e 63 72 61 63   shim.shrimp.crac
0110   6b 65 72 73 7d 0d 0a 43 6f 6e 74 65 6e 74 2d 4c   kers}..Content-L
0120   65 6e 67 74 68 3a 20 38 32 31 0d 0a 4b 65 65 70   ength: 821..Keep
```
### Bandera 
`picoCTF{nongshim.shrimp.crackers}`
## Notas adicionales
## Referencias
- https://www.cloudflare.com/learning/ssl/transport-layer-security-tls/
- https://wiki.wireshark.org/TLS
- https://blog.didierstevens.com/2020/12/14/decrypting-tls-streams-with-wireshark-part-1/