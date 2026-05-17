

**1:1 (jedna k jedné):** 
- Jeden záznam v první tabulce odpovídá maximálně jednomu záznamu v druhé tabulce. Příkladem je uživatel a jeho profil.

> 	Každý uživatel má právě jeden profil. Profil patří právě jednomu uživateli.
```
uzivatele          profily
----------         ----------
id = 1      ────  user_id = 1
id = 2      ────  user_id = 2
id = 3      ────  user_id = 3
```


**1:N (jedna k mnoha):** 
- Jeden záznam v první tabulce může mít více vazeb na druhou tabulku, ale záznam v druhé tabulce patří vždy jen jednomu záznamu v první. Typicky zákazník a jeho objednávky.

> 	Novák má 3 objednávky, Svoboda 2, Dvořák 1. Každá objednávka patří jen jednomu zákazníkovi.
```
zakaznici          objednavky
----------         ----------
id= 1 (Novák)    ──┬─ zakaznik_id = 1 (obj. #101)
                   ├─ zakaznik_id = 1 (obj. #102)
                   └─ zakaznik_id = 1 (obj. #103)
id = 2 (Svoboda) ──┬─ zakaznik_id = 2 (obj. #104)
	               └─ zakaznik_id = 2 (obj. #105)
```

**N:M (mnoho k mnoha):** 
- Každý záznam v první tabulce může souviset s více záznamy v druhé a naopak. Nelze realizovat přímo, musíme vytvořit tzv. spojovací (vazební) tabulku. Příkladem je vztah mezi filmy a herci (jeden film má více herců, jeden herec hraje ve více filmech).

 > 	Spojovací tabulka obsahuje dvojici cizích klíčů. Společně tvoří primární klíč (PK).
```
 filmy              filmy_herci                  herci 
----------           ----------                 ----------
id=1 Matrix    ── film_id=1,herec_id=1   ── id=1 Keanu Reeves
id=1 Matrix    ── film_id=1, herec_id=2  ── id=2 Laurence Fishburne
id=2 John Wick ── film_id=2, herec_id=1  ── id=1 Keanu Reeves
```

