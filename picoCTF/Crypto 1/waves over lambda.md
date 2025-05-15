## Descripción
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 39894`.
## Solución
Nos dan este texto al conectarnos:
```
-------------------------------------------------------------------------------
xqjyroav smrm gv nqbr eioy - ermhbmjxn_gv_x_qtmr_iofcko_oyeixyanbm
-------------------------------------------------------------------------------
oimpmn enqkqrqtgaxs worofodqt uov asm asgrk vqj qe enqkqr lotiqtgaxs worofodqt, o iojk qujmr umii wjquj gj qbr kgvargxa gj sgv quj kon, ojk vagii rmfmfcmrmk ofqjy bv qugjy aq sgv yiqqfn ojk aroygx kmoas, usgxs sollmjmk asgrammj nmorv oyq, ojk usgxs g vsoii kmvxrgcm gj gav lrqlmr lioxm. eqr asm lrmvmja g ugii qjin von asoa asgv iojkqujmreqr vq um bvmk aq xoii sgf, oiasqbys sm sorkin vlmja o kon qe sgv igem qj sgv quj mvaoamuov o varojym anlm, nma qjm lrmaan ermhbmjain aq cm fma ugas, o anlm oczmxa ojk tgxgqbv ojk oa asm vofm agfm vmjvmimvv. cba sm uov qjm qe asqvm vmjvmimvv lmrvqjv usq orm tmrn umii xolocim qe iqqwgjy oeamr asmgr uqrikin oeeogrv, ojk, ollormjain, oeamr jqasgjy mivm. enqkqr lotiqtgaxs, eqr gjvaojxm, cmyoj ugas jmpa aq jqasgjy; sgv mvaoam uov qe asm vfoiimva; sm roj aq kgjm oa qasmr fmj'v aocimv, ojk eovamjmk qj asmf ov o aqokn, nma oa sgv kmoas ga ollmormk asoa sm sok o sbjkrmk asqbvojk rqbcimv gj sork xovs. oa asm vofm agfm, sm uov oii sgv igem qjm qe asm fqva vmjvmimvv, eojaovagxoi emiiquv gj asm usqim kgvargxa. g rmlmoa, ga uov jqa vablgkganasm fozqrgan qe asmvm eojaovagxoi emiiquv orm vsrmuk ojk gjamiigymja mjqbyscba zbva vmjvmimvvjmvv, ojk o lmxbigor joagqjoi eqrf qe ga.
```
Usar Substitution solver
Da de resultado de llave:
```
abcdefghijklmnopqrstuvwxyz     This clear text ...  
**tubzfmiqlndpeyaxorhvwskcgj**     ... maps to this cipher text
```
Y esto de texto descifrado 
```
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_agflcgtyue
-------------------------------------------------------------------------------
alexey fyodorovitch karamazov was the third son of fyodor pavlovitch karamazov, a land owner well known in our district in his own day, and still remembered among us owing to his gloomy and tragic death, which happened thirteen years ago, and which i shall describe in its proper place. for the present i will only say that this landownerfor so we used to call him, although he hardly spent a day of his life on his own estatewas a strange type, yet one pretty frequently to be met with, a type abject and vicious and at the same time senseless. but he was one of those senseless persons who are very well capable of looking after their worldly affairs, and, apparently, after nothing else. fyodor pavlovitch, for instance, began with next to nothing; his estate was of the smallest; he ran to dine at other men's tables, and fastened on them as a toady, yet at his death it appeared that he had a hundred thousand roubles in hard cash. at the same time, he was all his life one of the most senseless, fantastical fellows in the whole district. i repeat, it was not stupiditythe majority of these fantastical fellows are shrewd and intelligent enoughbut just senselessness, and a peculiar national form of it.
```

Bandera: `frequency_is_c_over_lambda_agflcgtyue`
## Notas adicionales

## Referencias
https://www.guballa.de/substitution-solver