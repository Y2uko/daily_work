# DATABÁZE
- uspořádaný celek dat, který slouží k jejich efektivnímu ukládání, vyhledávání a správě.
- Oproti běžným souborům jsou databáze optimalizované pro rychlou práci s velkým množstvím dat, umožňují přístup více uživatelům současně a zajišťují vyšší bezpečnost a integritu informací
- FUNKCE 
	- definice dat – jaká data budou ukládána, jaké jsou vztahy mezi dat
	- manipulace s daty - výběr, přidání, mazání,…
	- řízení dat - oprávnění pro manipulaci s daty
- Pro správu těchto dat se využívá **DBRMS** nebo **DBMS** (Database Management System)
	- Softwarový systém umožňující definici, tvorbu, údržbu a řízení přístupu k databázi (např. MySQL, PostgreSQL, Oracle)
	- 2 základní typy:
		1. Non-Relation Databases (**NoSQL**)
			- používá se většinou pro key/value pair
			- minimální struktura (obrázky)
			- MongoDB, Couchbase
			- jedna tabulka
		2. Relational Database (**SQL**)
			- strukturovaný dotazovací jazyk 
			- pomáhá zpracovávat požadovaná data napříč více tabulek
			- k jednotlivým datům má vytvořené logické tabulky, které jsou propojeny právě přes (relations)
			- příklad: tabulka na (informace zákazníka, platební informace, přidané obrázky)
			- PostgreSQL, MySQL
			- [[Typy relací]]:
				- 1 - 1 (jedna k jedné)
				- 1 - N (jedna k mnoha)
				- N - M (mnoha k mnoha)
### Jak funguje **SQL** ?
- (Structured Query Language)
- jazyk pro psaní databázových dotazů (query)
- `Příklad SELECT id, name, price FROM products`
-  SQL v kostce
	- SQL obsahuje příkazy pro definici dat (`CREATE`, `ALTER`, `DROP`), manipulaci s daty (SELECT, `INSERT`, `UPDATE`, `DELETE`) a řízení přístupových práv.
		- `WHERE` – podmínka, která omezuje výběr (např. `WHERE id = 5`).
		- `JOIN` – `JOIN`
*SQL - logika*
![[Pasted image 20260517084536.png]]

*SQL - Relations* (logické spojování více tabulek)
![[Pasted image 20260517084824.png]]



###  **NoSQL** database ?
- příklad MongoDB
- není zde žádné schéma, kterého se ukládána data musí držet
	- ![[Pasted image 20260517085400.png|416]]
- **žádné** (relations) mezi tabulkami
- všechny informace na jednom místě 
	- ![[Pasted image 20260517085559.png|425]]
- samostatně stojící tabulky (nečerpají data z jiných tabulek ale mají všechny co potřebují u sebe)
- jsou zde často duplikované informace


SQL vs NoSQL
![[Pasted image 20260517090152.png]]


**Normalizace dat**
- Databáze se navrhují tak, aby se data zbytečně neopakovala. Tomu se říká normalizace. Cílem je, aby každá informace byla uložena ideálně jen na jednom místě. Tím se předchází chybám při aktualizaci dat (anomáliím). Existuje několik **normální forma**
	- normální forma = *Pravidla pro uspořádání dat v relační databázi, která minimalizují redundanci a závislosti. Nejčastěji se používá 1NF, 2NF a 3NF.*

**Transakce a ACID**
- V profesionálních databázích se řeší tzv. transakce. To je série operací, které se musí provést buď všechny, nebo žádná. Vlastnosti transakcí se označují zkratkou **ACID**
	- ACID = 
		- **A**tomicity (vše nebo nic)
		- **C**onsistency (konzistence dat)
		- **I**solation (izolace transakcí)
		- **D**urability (trvalost po potvrzení)
### Historie a vývoj
Předchůdcem moderních databází byly klasické papírové kartotéky. ==První strojové zpracování dat probíhalo pomocí děrných štítků koncem 19. století==, kde se data zaznamenávala jako přítomnost nebo absence díry.

- V polovině 20. století se standardem stal programovací jazyk **COBOL**, který byl pro práci s daty klíčový.
	- COBOL = *Programovací jazyk navržený pro obchodní administrativu, který byl klíčový pro rané systémy zpracování dat.*
- V roce 1974 se objevila první verze ==**SQL**, což je dodnes nejpoužívanější jazyk pro dotazování v relačních databázích.== SQL je nástupcem jazyka SEQUEL a dnešním standardem je SQL:3, ačkoliv jednotlivé databázové systémy často implementují vlastní rozšíření, což omezuje přenositelnost dotazů.
	- SQL = *Deklarativní jazyk používaný pro správu a dotazování v relačních databázích.*

### Práce s databází
==Data z databáze získáváme pomocí dotazů==
Dotazy mohou být například –  **čtení** (výběr dat), **aktualizační** (změna hodnot) a **mazací** dotazy.

- **Sestavy:** ==Slouží k přehlednému uspořádání a prezentaci dat (např. tisk faktur nebo seznam žáků). Data v sestavách se neupravují, pouze zobrazují.== Zdrojem může být tabulka, dotaz nebo jiná sestava (agregace dat).
- **Indexování:** 
	- Index = Datová struktura (často B-strom), která výrazně zrychluje vyhledávání řádků v tabulce na základě hodnoty ve sloupci.


### Základní struktura  databází
Struktura databáze jednoduše označuje způsob, jakým jsou data v databázi uspořádána. Zde jsou její klíčové součásti:

Kde jsou uspořádána
- **Tables** (Tabulky) 
	- Základními stavebními kameny struktury databáze jsou tabulky, které se skládají z řádků a sloupců.
	- **Rows and columns** (Řádky a sloupce) 
		- Řádky představují jednotlivé záznamy (1, Pepa, pepa@gm.com)
		- sloupce obsahují atributy těchto záznamů (id, name, email)

[[Způsob uspořádání]] 
- **Primary key** (Primární klíč) 
	- Jedinečný identifikátor každého záznamu v tabulce. 
	- Nesmí obsahovat hodnotu `NULL` a každá tabulka by měla mít právě jeden. 
	- Pokud ho neurčíme, často se generuje automaticky jako `ID`.
- **Foreign Key** (Cizí klíč)
	- Definuje vztah mezi dvěma tabulkami. 
	- Odkazuje na primární klíč v jiné tabulce.
	- Zajišťuje **integritu** – nedovolí nám vložit do cizího klíče hodnotu, která v cílové tabulce neexistuje. 
	- Může být `NULL` a nemusí být unikátní.
- **Candidate Key** (Kandidátní klíč) 
	- Sloupec nebo skupina sloupců, které jednoznačně identifikují záznam v tabulce, ale nebyly vybrány jako primární klíč.

### Typy Databázových systémů

- Mezi hlavní typy databází patří hierarchické, síťové, objektově orientované, relační a NoSQL databáze. Každý typ je určen pro konkrétní účely, od správy strukturovaných dat až po zpracování rozsáhlých nestrukturovaných dat.

| Typy                      | Popis                                                                                                                                                                                                                                                                        |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Hierarchické**          | ==Data jsou uspořádána ve stromové struktuře s jedním kořenovým záznamem.== Podporují pouze vztahy 1:N. Jejich hlavní nevýhodou je velmi obtížná změna struktury.                                                                                                            |
| **Síťové**                | ==Rozšiřují hierarchické modely a umožňují složitější vztahy typu N:M==. Jsou sice velmi výkonné, ale extrémně náročné na návrh a údržbu.                                                                                                                                    |
| **Objektově orientované** | ==Ukládá data jako objekty==, podobně jako v objektově orientovaném programování, ==a je ideální pro aplikace se složitými datovými modely, jako jsou multimediální nebo finanční systémy.==                                                                                 |
| **Relační**               | Vznikly v 70. letech a způsobily revoluci. ==Data jsou uložena v tabulkách (relacích), které jsou dvourozměrné.== Sloupce představují atributy (vlastnosti) a řádky konkrétní záznamy. Jsou ideální pro bankovní systémy a řízení zásob, kde je vyžadována vysoká integrita. |
| **NoSQL**                 | [[NoSQL]]. ==Ukládají data do dokumentů== (např. JSON), jsou flexibilní a vhodné pro velké objemy dat, IoT nebo grafy, avšak nejsou vhodné pro silně provázaná data.                                                                                                         |

## Srovnání relačních databázových systémů

|Systém|Charakteristika|
|---|---|
|**SQLite**|Ukládá se do jednoho souboru, nevyžaduje server, ideální pro výuku a mobilní aplikace.|
|**MySQL**|Open-source, velmi rozšířená, jednoduchá a výkonná pro menší projekty.|
|**MariaDB**|Open-source odvozenina MySQL, plně kompatibilní s SQL, silná komunita.|
|**PostgreSQL**|Robustní, spolehlivá, vhodná pro komplexní operace, náročnější na naučení.|
|**MS SQL**|Komerční řešení od Microsoftu, optimalizováno pro Windows a .NET, podnikové systémy.|



