## Descripción
Class, take your seats! It's PRIME-time for a quiz... `nc jupiter.challenges.picoctf.org 18821`
## Solución
Primero vamos a instalar esta librería de python 
```sh
sudo apt install python3-pwntools
```
Para que no se agote el tiempo de las preguntas podemos usar un script de python:
```python
import binascii
from pwn import *

def MMI(A, n, s=1, t=0, N=0):
    if n < 2:
        return t % N if N else t
    else:
        if n < 1:
            return -1
        return MMI(n, A % n, t, s - (A // n) * t, N or n)

r = remote("jupiter.challenges.picoctf.org",18821)
# Q1
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
q = int([l for l in lines.split('\n') if 'q :' in l][0].split(':')[1].strip())
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'n:').decode())
ans = q * p
print('Sending: {}'.format(ans))
r.sendline('{}'.format(ans).encode())

# Q2
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip())
n = int([l for l in lines.split('\n') if 'n :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'q:').decode())
ans = n // p
print('Sending: {}'.format(ans))

r.sendline('{}'.format(ans).encode())

# Q3
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
r.sendline(b'N')

# Q4
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
q = int([l for l in lines.split('\n') if 'q :' in l][0].split(':')[1].strip())
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'totient(n):').decode())
ans = (q - 1) * (p - 1)
print('Sending: {}'.format(ans))
r.sendline('{}'.format(ans).encode())

# Q5
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
plain = int([l for l in lines.split('\n') if 'plaintext :' in l][0].split(':')[1].strip())
e = int([l for l in lines.split('\n') if 'e :' in l][0].split(':')[1].strip())
n = int([l for l in lines.split('\n') if 'n :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'ciphertext:').decode())
ans = pow(plain, e, n)
print('Sending: {}'.format(ans))
r.sendline('{}'.format(ans).encode())

# Q6
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
r.sendline(b'N')

# Q7
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
q = int([l for l in lines.split('\n') if 'q :' in l][0].split(':')[1].strip())
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip())
e = int([l for l in lines.split('\n') if 'e :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'd:').decode())
ans = MMI(e, (q - 1) * (p - 1))
print('Sending: {}'.format(ans))
r.sendline('{}'.format(ans).encode())

# Q8
lines = r.recvuntil(b'IS THIS POSSIBLE and FEASIBLE? (Y/N):').decode()
print(lines)
p = int([l for l in lines.split('\n') if 'p :' in l][0].split(':')[1].strip())
cipher = int([l for l in lines.split('\n') if 'ciphertext :' in l][0].split(':')[1].strip())
e = int([l for l in lines.split('\n') if 'e :' in l][0].split(':')[1].strip())
n = int([l for l in lines.split('\n') if 'n :' in l][0].split(':')[1].strip())
r.sendline(b'Y')
print(r.recvuntil(b'plaintext:').decode())
q = n // p
d = MMI(e, (q - 1) * (p - 1))
ans = pow(cipher, d, n)
print('Sending: {}'.format(ans))
r.sendline('{}'.format(ans).encode())
lines = r.recvall().decode()
print(lines)
print('In hex: {}'.format(hex(ans)))
print(binascii.unhexlify(hex(ans)[2:]))
```

```
If you convert the last plaintext to a hex number, then ascii, you'll find what you need! ;)

In hex: 0x7069636f4354467b7741385f74683474245f696c6c336147616c2e2e6f61326432323339627d
b'picoCTF{wA8_th4t$_ill3aGal..oa2d2239b}'
```
## Notas adicionales
## Referencias
https://simple.wikipedia.org/wiki/RSA_algorithm