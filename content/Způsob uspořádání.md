Představ si databázi jako chytrou kartotéku. Abychom se v ní neztratili a data dávala smysl, používáme právě tyto klíče. Pojďme si to ukázat na naprosto reálném příkladu: **e-shopu, kde nakupují zákazníci a dělají objednávky**.

---
## 1. Primary Key (Primární klíč) – „Jedinečné ID“

Představ si tabulku **Zákazníci**. Každý zákazník musí být jednoznačně rozpoznatelný, i kdyby se v databázi sešli dva lidé se stejným jménem (např. dva Janové Novákové).

- **Příklad z praxe:** E-shop ti při registraci přidělí `ID_zakaznika` (např. `1024`). Toto číslo je tvůj **primární klíč**.
    
- **Proč to funguje:** Nikdo jiný na světě v tomto e-shopu nedostane číslo `1024`. Toto políčko **nesmí být prázdné (NULL)**, protože e-shop musí vědět, komu účet patří. Většinou se toto číslo zvětšuje automaticky (+1 s každým novým člověkem).
    

---

## 2. Foreign Key (Cizí klíč) – „Propojovací most“

Teď máme druhou tabulku: **Objednávky**. Každá objednávka má své vlastní ID (svůj primární klíč), ale my potřebujeme vědět, _který_ zákazník si zboží koupil. Nechceme do objednávky znovu vypisovat celé jméno a adresu zákazníka (to by byl chaos).

- **Příklad z praxe:** Do tabulky **Objednávky** přidáme sloupec `ID_zakaznika`. Když si jako zákazník `1024` koupíš boty, v tabulce objednávek se objeví řádek: `ID_objednavky: 555`, `Zbozi: Boty`, `ID_zakaznika: 1024`.
    
- **Vztah:** Sloupec `ID_zakaznika` v tabulce objednávek je **cizí klíč**. Odkazuje zpět do tabulky zákazníků.
    
- **Jak hlídá integritu:** Databáze ti nedovolí vytvořit objednávku s `ID_zakaznika: 9999`, pokud zákazník s tímto číslem vůbec neexistuje.
    
- **Proč může být duplicitní nebo NULL:**
    
    - _Nemusí být unikátní:_ Ty (zákazník `1024`) můžeš udělat 5 různých objednávek. Číslo `1024` se tedy v tabulce objednávek objeví pětkrát.
        
    - _Může být NULL:_ Představ si, že e-shop umožňuje nákup bez registrace (anonymní rychlý nákup). Objednávka se vytvoří, ale políčko `ID_zakaznika` zůstane prázdné (**NULL**), protože objednávka nepatří žádnému registrovanému účtu.
        

---

## 3. Candidate Key (Kandidátní klíč) – „Zaskakující náhradník“

Vraťme se k tabulce **Zákazníci**. Při registraci zadáváš kromě jména také svůj **E-mail** a **Rodné číslo** (nebo třeba IČO, pokud jsi firma).

- **Příklad z praxe:** E-mail musí mít každý člověk unikátní – dva lidé nemohou mít v e-shopu stejný e-mail. Rodné číslo je také unikátní. Jak E-mail, tak Rodné číslo by klidně _mohly_ sloužit jako jednoznačný identifikátor (primární klíč).
    
- **Volba:** My jsme si ale jako hlavní identifikátor vybrali uměle vytvořené `ID_zakaznika` (protože s čísly se databázi pracuje nejlépe).
    
- **Výsledek:** E-mail a Rodné číslo jsou **kandidátní klíče**. Byly to skvělí _kandidáti_ na primární klíč, ale volbu nevyhráli. Přesto databáze hlídá, aby v nich nikdo neměl duplicity.
    

---
