## Descripción
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext).
## Solución
#### Usando dCode
Nos vamos a la herramienta de `caesar cipher` https://www.dcode.fr/caesar-cipher

```
crossingtherubiconvfhsjkou
```
#### Usando python
```python
mensaje_cifrado = "ynkooejcpdanqxeykjrbdofgkq"
alfabeto = 'abcdefghijklmnopqrstuvwxyz'

for clave in range(1, 26):
    descifrado = ""
    for letra in mensaje_cifrado.lower():
        if letra in alfabeto:
            posicion = alfabeto.find(letra)
            nueva_posicion = (posicion - clave) % 26
            descifrado += alfabeto[nueva_posicion]
        else:
            descifrado += letra
    print(f"Clave {clave}: {descifrado}")
```
Nos da la sig. salida.
```
Clave 1: xmjnndiboczmpwdxjiqacnefjp
Clave 2: wlimmchanbylovcwihpzbmdeio
Clave 3: vkhllbgzmaxknubvhgoyalcdhn
Clave 4: ujgkkafylzwjmtaugfnxzkbcgm
Clave 5: tifjjzexkyvilsztfemwyjabfl
Clave 6: sheiiydwjxuhkrysedlvxizaek
Clave 7: rgdhhxcviwtgjqxrdckuwhyzdj
Clave 8: qfcggwbuhvsfipwqcbjtvgxyci
Clave 9: pebffvatgurehovpbaisufwxbh
Clave 10: odaeeuzsftqdgnuoazhrtevwag
Clave 11: nczddtyrespcfmtnzygqsduvzf
Clave 12: mbyccsxqdrobelsmyxfprctuye
Clave 13: laxbbrwpcqnadkrlxweoqbstxd
Clave 14: kzwaaqvobpmzcjqkwvdnparswc
Clave 15: jyvzzpunaolybipjvucmozqrvb
Clave 16: ixuyyotmznkxahoiutblnypqua
Clave 17: hwtxxnslymjwzgnhtsakmxoptz
Clave 18: gvswwmrkxlivyfmgsrzjlwnosy
Clave 19: furvvlqjwkhuxelfrqyikvmnrx
Clave 20: etquukpivjgtwdkeqpxhjulmqw
Clave 21: dspttjohuifsvcjdpowgitklpv
Clave 22: crossingtherubiconvfhsjkou
Clave 23: bqnrrhmfsgdqtahbnmuegrijnt
Clave 24: apmqqglerfcpszgamltdfqhims
Clave 25: zolppfkdqeboryfzlkscepghlr
```
#### Llave
```
picoCTF{crossingtherubiconvfhsjkou}
```
## Notas adicionales
The Caesar cipher (or Caesar code) is a [monoalphabetic substitution](https://www.dcode.fr/monoalphabetic-substitution) cipher, where each letter is replaced by another letter located a little further in the alphabet (therefore shifted but always the same for given cipher message).
## Referencias
https://www.dcode.fr/caesar-cipher