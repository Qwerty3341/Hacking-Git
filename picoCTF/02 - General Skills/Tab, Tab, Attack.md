## Descripción
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: Addadshashanammu.zip
## Solución
- Veo el tipo de archivo con file
- Como tiene caracteres que no se pueden imprimir no se puede buscar directamente con egrep
- Usamos strings para ver los caracteres imprimibles y se lo pasamos al egrep -a para ver si está la bandera

```shell
┌[debian3341 | 25 comands | dir:~/FILES/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku]
└-> $ file fang-of-haynekhtnamet
fang-of-haynekhtnamet: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=47e898db922f38cb54ab4a08fb4e3def5a1cb6a1, not stripped

┌[debian3341 | 26 comands | dir:~/FILES/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku]
└-> $ egrep -a "picoCTF{" fang-of-haynekhtnamet

                                                                                           ����+zRx
 u/H�=�  UH��t                                                                                    $X��� FJ
R���H�����    H� ]����fDUH��]�f���UH��H�=�������]�f.�DAWAVI��AUATL�%F UH�-F SA��I��L)�H�H���W���H��t 1��L��?␦;*3$"DP��\R���A�C[]A\A]A
D|X���eB�B�E �B(�H0�H8�M@r8A0A(B BB�����0�3_4_r35t!_a00cae70}<�����������X"����H��������0zRx
���o�`�                                   �

┌[debian3341 | 29 comands | dir:~/FILES/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku]
└-> $ strings fang-of-haynekhtnamet | egrep -a "picoCTF{"
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_a00cae70}

```
## Notas adicionales

## Referencias
- https://linux--audit-com.translate.goog/elf-binaries-on-linux-understanding-and-analysis/?_x_tr_sl=en&_x_tr_tl=es&_x_tr_hl=es&_x_tr_pto=tc#what-is-an-elf-file