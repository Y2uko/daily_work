==Co je OOP (Objektově Orientované Programování)==
- Programovací paradigma založené na konceptech „objektů“, které obsahují data ve formě polí (atributů) a kód ve formě procedur (metod).]] 
- OOP je programovací paradigma, které nám umožňuje navrhovat programy jako systémy spolupracujících objektů. Místo psaní dlouhého procedurálního kódu „shora dolů“ si svět aplikace rozdělíme na logické celky, které spolu komunikují, uchovávají si svá data a vykonávají specifické operace. Je to způsob, jakým v kódu odrážíme realitu – ať už jde o reálné objekty jako „auto“ nebo „člověk“, nebo abstraktní koncepty jako „bankovní účet“. Program je v tomto pojetí sestaven z objektů, které spolu mohou komunikovat či uchovávají data.
- Jedná se o filozofii a způsob myšlení, designu a implementace, kde klademe důraz na **znovu použitelnost**.  

==Jak OOP funguje ?==
- **Základní jednotkou je objekt**, který odpovídá nějakému objektu z reálného světa (např. objekt _člověk_ nebo _databáze_).  
	- **Objekt** má své atributy a metody.  
		- *Atributy*  
		- Atributy objektu jsou **vlastnosti** neboli data, která uchovává (např. u člověka jméno a věk, u databáze heslo). Jedná se o prosté proměnné, se kterými jsme již stokrát pracovali. Někdy o nich hovoříme jako o vnitřním stavu objektu.  
		- *Metody*
		- Metody jsou **schopnosti**, které umí objekt vykonávat  
			- U databáze by to mohlo být `PridejZaznam()` nebo `Vyhledej()`
		- Metody mohou mít **parametry** a mohou také vracet nějakou **hodnotu**  

## Třída
- třída je kód odrážející okolní svět, proto můžeme vytvořit třídu pro cokoliv
- Můžeme ji chápat jako definici vnější struktury a rozhraní objektu. Třída v sobě spojuje data (atributy) a funkčnost (metody).
- je to **vzor**, podle kterého se objekty vytvářejí. Definuje jejich vlastnosti a schopnosti.  
- **objekt**, který se vytváří podle třídy je *instance* třídy
    - z jedné třídy může vznikat libovolný počet objektů
    - vzniká pomocí operátoru `new`, který zavolá:
	    - **konstruktor**
		    - Speciální metoda třídy, která se automaticky spustí při vytváření nové instance objektu a slouží k jeho inicializaci.
	        - konstruktory mohou být bezparametrické (každá nová instance je identická) nebo parametrické (posíláme atributy)
    - Objekt je konkrétní realizace třídy v paměti počítače. Zatímco třída je „plán domu“, objekt je „postavený dům“.
    *Ukázka*
    - Mějme například třídu `Clovek` a od ní si vytvořme instance `karel` a `josef`. Obě instance mají jistě ty samé metody a atributy, jako třída například:
	    - atributy `jmeno` a `vek`
	    - metody `JdiDoPrace()` a `Pozdrav()`)
		Ale hodnoty v nich se liší (první instance má v atributu `jmeno` hodnotu `"Karel"` a v atributu `vek` hodnotu `22`, druhá `"Josef"` a `45`).  
- ==Co Třída dělá ?==
	- definuje vlastnosti, které bude mít každý objekt vzniklý z této třídy
	- slouží k organizaci kódu do logických celků
	- z jedné třídy můžeme vytvořit libovolný počet objektů (instancí)
	- v C# je třída základní stavební jednotkou, která může být i **Abstraktní datový typ** *(Model dat, který definuje vnější rozhraní a chování bez specifikace vnitřní implementace.)*
	- třída odráží realitu světa a nese stejné vlastnosti pro všechny své instance

- ### Objekt
	- instance třídy
	- Objekt je konkrétní realizace třídy v paměti počítače. Zatímco třída je „plán domu“, objekt je „postavený dům“.
	-  vzniká pomocí operátoru `new`, který zavolá **konstruktor**
		- Speciální metoda třídy, která se automaticky spustí při vytváření nové instance objektu a slouží k jeho inicializaci.
				`Auto auto1 = new Auto();`
	- obsahuje konkrétní data (hodnoty atributů) a metody, které s těmito daty pracují
	- objekty mezi sebou komunikují pomocí metod, které jsou nastaveny jako public
	-  Třída `Auto` definuje, že každé auto má značku a rok výroby. Objekt `mojeAuto` je pak konkrétní instance, kde `znacka = "Škoda"` a `rokVyroby = 2020`.

