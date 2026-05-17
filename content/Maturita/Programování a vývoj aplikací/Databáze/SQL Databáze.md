==Co znamená SQL databáze ?==
- organizovaný systém pro ukládání, správu a manipulaci se strukturovanými daty uspořádanými do tabulek s řádky a sloupci
- SQL databáze jsou nezbytné pro správu velkého množství dat, kde je nutná vysoká přesnost a rychlý přístup k informacím
- Využívá jazyk SQL *(Structured Query Language)* k efektivnímu vyhledávání, aktualizaci, vkládání a mazání informací. Často se synonymicky označuje jako relační databáze
- Původně vznikl jako jazyk SEQUEL, který byl později upraven a přejmenován.
- Dnes je standardem verze SQL3. I když se tento standard snaží sjednotit způsob, jakým databáze ovládáme, v praxi každá databáze (např. **MySQL** , **PostgreSQL** ) přidává vlastní rozšíření. Kvůli tomu není kód napsaný pro jednu databázi vždy přímo přenositelný do jiné.
- Data jsou uložená v tabulkách
	- používá **relace** - vyžaduje id u každého záznamu - 
	- tabulky jsou navzájem propojeny 


==Základní příklad zápisu dotazu==
- Pro představu, jak vypadá práce s daty v SQL, zde je ukázka jednoduchého výběru:
**Vytvoření tabulky**
```
CREATE TABLE Uzivatele (ID int, Jmeno varchar(255));
```
**Vložení dat:**
```
INSERT INTO Uzivatele VALUES (1, 'Jan');
```
**Výběr Dat:**
```
SELECT jmeno, prijmeni FROM uzivatele WHERE vek > 18;
```

- Tento příkaz vybere jména a příjmení všech uživatelů z tabulky `uzivatele`, kteří jsou starší 18 let. Pro složitější dotazy se využívá [[JOIN]] , která umožňuje propojit data z více tabulek najednou.


# Jazyk SQL

### Rozdělení příkazů
- funkce - CRUD
    - Create, Read, Update, Delete
    - `INSERT, SELECT, UPDATE, DELETE`
    
    - **DDL** *(Data Definition Language)*
	    - Slouží k definici struktury databáze. 
	    - Hlavní příkazy jsou: 
		    - `CREATE` (vytvoření tabulky/databáze)
		    - `ALTER` (úprava struktury) 
		    - `DROP` (smazání tabulky/databáze)
		    
	- **DML** *(Data Manipulation Language)*
		- Používá se pro práci s obsahem tabulek. 
		- Patří sem:
			- `SELECT` (čtení dat)
			- `INSERT` (vkládání nových řádků)
			- `UPDATE` (úprava existujících záznamů) 
			- `DELETE` (mazání záznamů)
			
	- **DCL** *(Data Control Language)*
		- Řeší řízení přístupových práv, tedy kdo může s daty pracovat a co s nimi smí dělat. 
		- Zahrnuje příkazy jako:
			- `GRANT` (přidělení oprávnění) 
			- `REVOKE` (odebrání oprávnění)
			
	- **TCL** *(Transaction Control Language)*
		- Slouží k řízení transakcí v databázi. Zajišťuje ACID pomocí příkazů `COMMIT` a `ROLLBACK`.

### Datové typy
- Při návrhu tabulky musíme každému sloupci (atributu) přiřadit datový typ, aby databáze věděla, jak s hodnotami nakládat
- Výběr správného typu je klíčový pro optimalizaci úložiště a výkon dotazů.

	- **Číselné typy (Numeric):**
	    - Celá čísla: `INT` (nebo `INTEGER`), `SMALLINT`, `TINYINT`, `BIGINT`.
	    - Přesná čísla: `DECIMAL` (nebo `NUMERIC`) – ideální pro peněžní částky, kde je nutná přesnost.
	    - Plovoucí čárka (přibližná): `FLOAT`, `REAL`.
	- **Textové typy (Character/String):**
	    - `CHAR(n)`: Pevná délka, doplňuje se mezerami.
	    - `VARCHAR(n)`: Proměnná délka, efektivnější pro šetření místa.
	    - `TEXT` / `CLOB`: Pro velmi dlouhé textové řetězce.
	- **Datum a čas (Date & Time):**
	    - `DATE`: Pouze datum (rok, měsíc, den).
	    - `TIME`: Pouze čas.
	    - `DATETIME` / `TIMESTAMP`: Datum a čas dohromady.
	- **Binární typy (Binary/LOB):**
	    - `BINARY`, `VARBINARY`: Pro ukládání binárních dat (např. souborů).
	    - `BLOB` (Binary Large Object): Pro objemná data (obrázky, video).
	- **Ostatní typy:**
	    - `BOOLEAN` / `BIT`: Pravdivostní hodnoty (TRUE/FALSE).
	    - `JSON`: Pro ukládání strukturovaných dat v JSON formátu (podporováno v moderních SQL db).

### Relační databáze (SQL)
Relační databáze organizují data do tabulek, které se skládají ze sloupců (atributů) a řádků (záznamů). Jsou velmi pevně strukturované, což je jejich hlavní výhoda i nevýhoda. Jsou ideální tam, kde potřebujeme vysokou integritu dat a jasné vazby, například v bankovních systémech nebo při řízení skladových zásob. Klíčovým prvkem je **Primární klíč** a **Cizí klíč** Na druhou stranu nejsou příliš flexibilní – pokud chceme změnit strukturu tabulky u běžícího systému, může to být komplikované.

#### Typy relací

- **1:1 (Jedna k jedné):** Jeden záznam v jedné tabulce odpovídá nejvýše jednomu záznamu v druhé tabulce a naopak (např. uživatel a jeho profil).
- **1:N (Jedna k mnoha):** Jeden záznam v první tabulce může odpovídat více záznamům v druhé, ale každý záznam v druhé patří právě jednomu v první (např. zákazník a jeho objednávky).
- **N:M (Mnoho k mnoha):** Každý záznam v první tabulce může souviset s více záznamy v druhé a naopak; vyžaduje vytvoření tzv. spojovací tabulky (např. filmy a herci).

# Přehled SQL databázových systémů

##### SQLite: 
- ==Databáze, která se ukládá do jediného souboru na disku==. 
- Nevyžaduje instalaci serveru, takže je ideální pro mobilní aplikace, výuku nebo malé programy, kde nechceme řešit složitou konfiguraci.
##### MySQL: 
- Velmi rozšířený open-source systém vlastněný společností Oracle.
- Je oblíbený pro svou ==jednoduchost a výkon u menších až středních projektů, ale pro extrémně složité systémy s obrovským množstvím vazeb už nemusí stačit.==
##### MariaDB:
- Vznikla jako komunitní odvozenina (fork) MySQL poté, co ji koupil Oracle.
- ==Je s MySQL plně kompatibilní a těží z obrovské podpory komunity, která ji neustále vylepšuje.==
##### PostgreSQL: 
- Robustní a velmi spolehlivý open-source systém.
- ==Je považován za nejvyspělejší volně dostupnou databázi, která zvládne i velmi složité operace a velké objemy dat.==
- Náročnější na naučení a konfiguraci.
##### MS SQL Server: 
- Komerční řešení od Microsoftu.
- Je to volba číslo jedna, pokud firma využívá technologie .NET a prostředí Windows. 
- ==Nabízí skvělé nástroje pro správu a integraci do podnikového prostředí.==

# NoSQL databáze

- NoSQL databáze představují alternativu k relačním systémům.
- Data neukládají do tabulek, ale většinou do dokumentů (často ve formátu JSON ). 
- Nemají pevnou strukturu, což znamená, že každý záznam může obsahovat odlišná pole.

	- **Hlavní výhody:** Jsou extrémně flexibilní, velmi rychle zpracovávají data a jsou snadno škálovatelné (horizontální škálování na více serverů).
	- **Použití:** Jsou skvělé pro velké objemy dat, IoT , ukládání grafů nebo různorodá data z webových aplikací.
	- **Nevýhody:** Nejsou vhodné pro systémy s hodně provázanými daty, kde je potřeba striktní kontrola vazeb (tzv. transakční integrita).

### Srovnání databázových přístupů

|Vlastnost|Relační (SQL)|NoSQL|
|---|---|---|
|Struktura|Pevná (tabulky)|Flexibilní (dokumenty)|
|Schéma|Předem definované|Dynamické|
|Škálovatelnost|Vertikální (výkonnější HW)|Horizontální (více serverů)|
|Vhodné pro|Bankovnictví, ERP|Big Data, IoT, Real-time|
