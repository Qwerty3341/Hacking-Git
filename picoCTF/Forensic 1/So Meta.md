## Descripción
Find the flag in this [picture](https://jupiter.challenges.picoctf.org/static/00efdf2961da1e21470ffc0d496c3cc2/pico_img.png).
## Solución 1
1. Descargamos con `wget`
2. Usamos `strings -n 10 strings -n 10 pico_img.png`
```
tEXtSoftware
Adobe ImageReadyq
"iTXtXML:com.adobe.xmp
<?xpacket begin="
" id="W5M0MpCehiHzreSzNTczkc9d"?> <x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27        "> <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"> <rdf:Description rdf:about="" xmlns:xmp="http://ns.adobe.com/xap/1.0/" xmlns:xmpMM="http://ns.adobe.com/xap/1.0/mm/" xmlns:stRef="http://ns.adobe.com/xap/1.0/sType/ResourceRef#" xmp:CreatorTool="Adobe Photoshop CS6 (Windows)" xmpMM:InstanceID="xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B" xmpMM:DocumentID="xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B"> <xmpMM:DerivedFrom stRef:instanceID="xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B" stRef:documentID="xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B"/> </rdf:Description> </rdf:RDF> </x:xmpmeta> <?xpacket end="r"?>
hcccfffhhhdd
xDEEEDDDFF
HIIIaaaYYYZZ
heeedddaa1r
0OSSSNNNCC
$666!!!,,,::
 |zzz666={
&dllliiinn^
Q`EPxYYYCCC
 ggg`^@@@^^
XFDiMq\\\II
>}jjj*x.C
,/cRc^CBB&O
Mx1\>,,,!!!&&
;22RTdohh<v
 tEXtArtist
picoCTF{s0_m3ta_fec06741}
```
## Solución 2
1. Usamos `exiftool` para ver los metadatos de la imagen
2. En el metadato "Artist" tiene la bandera
```shell
$ exiftool pico_img.png

ExifTool Version Number         : 13.10
File Name                       : pico_img.png
Directory                       : .
File Size                       : 109 kB
File Modification Date/Time     : 2020:10:26 12:38:23-06:00
File Access Date/Time           : 2025:04:01 17:26:09-06:00
File Inode Change Date/Time     : 2025:04:01 17:26:04-06:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 600
Image Height                    : 600
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Software                        : Adobe ImageReady
XMP Toolkit                     : Adobe XMP Core 5.3-c011 66.145661, 2012/02/06-14:56:27
Creator Tool                    : Adobe Photoshop CS6 (Windows)
Instance ID                     : xmp.iid:A5566E73B2B811E8BC7F9A4303DF1F9B
Document ID                     : xmp.did:A5566E74B2B811E8BC7F9A4303DF1F9B
Derived From Instance ID        : xmp.iid:A5566E71B2B811E8BC7F9A4303DF1F9B
Derived From Document ID        : xmp.did:A5566E72B2B811E8BC7F9A4303DF1F9B
Warning                         : [minor] Text/EXIF chunk(s) found after PNG IDAT (may be ignored by some readers)
Artist                          : picoCTF{s0_m3ta_fec06741}
Image Size                      : 600x600
Megapixels                      : 0.360
```
## Notas adicionales
## Referencias
https://abdc.es/blog/metadatos-de-un-documento/