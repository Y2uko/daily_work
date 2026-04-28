==Co je OOP (Objektově Orientované Programování)==
- Programovací paradigma založené na konceptech „objektů“, které obsahují data ve formě polí (atributů) a kód ve formě procedur (metod).]] 
- OOP je programovací paradigma, které nám umožňuje navrhovat programy jako systémy spolupracujících objektů. Místo psaní dlouhého procedurálního kódu „shora dolů“ si svět aplikace rozdělíme na logické celky, které spolu komunikují, uchovávají si svá data a vykonávají specifické operace. Je to způsob, jakým v kódu odrážíme realitu – ať už jde o reálné objekty jako „auto“ nebo „člověk“, nebo abstraktní koncepty jako „bankovní účet“. Program je v tomto pojetí sestaven z objektů, které spolu mohou komunikovat či uchovávají data.

## Třída
- třída je kód odrážející okolní svět, proto můžeme vytvořit třídu pro cokoliv
- Můžeme ji chápat jako definici vnější struktury a rozhraní objektu. Třída v sobě spojuje data (atributy) a funkčnost (metody).
- **objekt** je instance třídy
    - z jedné třídy může vznikat libovolný počet objektů
    - objekt vzniká pomocí konstruktoru
        - konstruktory mohou být bezparametrické (každá nová instance je identická) nebo parametrické (posíláme atributy)
- ==Co Třída dělá ?==
	- definuje vlastnosti, které bude mít každý objekt vzniklý z této třídy
	- slouží k organizaci kódu do logických celků
	- z jedné třídy můžeme vytvořit libovolný počet objektů (instancí)
	- v C# je třída základní stavební jednotkou, která může být i **Abstraktní datový typ** *(Model dat, který definuje vnější rozhraní a chování bez specifikace vnitřní implementace.)*
	- třída odráží realitu světa a nese stejné vlastnosti pro všechny své instance

### Objekt
- instance třídy
- Objekt je konkrétní realizace třídy v paměti počítače. Zatímco třída je „plán domu“, objekt je „postavený dům“.
- - vzniká pomocí operátoru new, který zavolá konstruktor

`Auto auto1 = new Auto();`