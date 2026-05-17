
- Třída je základní šablona (kód), podle které vznikají jednotlivé objekty. Můžeme ji chápat jako definici vnější struktury a rozhraní objektu. 
	- - Skupina objektů, která nese stejné vlastnosti
- Třída v sobě spojuje
	- **Atributy (Vlastnosti):** To jsou data, která objekt uchovává. U auta by to byla například _barva_, _značka_ nebo _maximální rychlost_. V kódu se chovají jako proměnné.
    
	- **Metody (Chování):** To jsou funkce definované uvnitř třídy, které určují, co objekt dokáže. U auta by to bylo _nastartovat()_, _zrychlit()_ nebo _zabrzdit()_.
- ==Co dělá ?==
	- definuje vlastnosti, které bude mít každý objekt vzniklý z této třídy
	- slouží k organizaci kódu do logických celků
	- z jedné třídy můžeme vytvořit libovolný počet objektů (instancí)
	- v C# je třída základní stavební jednotkou, která může být i Abstraktní datový typ
- třída odráží realitu světa a nese stejné vlastnosti pro všechny své instance

### Klíčové koncepty třídy

- **Instanciace:** Proces, kdy z obecné třídy vytvoříš konkrétní **objekt** (instanci). Například ze třídy `Auto` vytvoříš objekt `moje_cervena_fabia`.
    
- **Konstruktor:** Speciální metoda, která se spustí automaticky ve chvíli, kdy objekt vytváříš. Jejím úkolem je nastavit počáteční hodnoty atributů (např. přiřadit autu barvu hned při výrobě).
    
- **Zapouzdření (Encapsulation):** Třída umožňuje skrýt vnitřní složitost. Uživatel objektu ví, jakou metodu zavolat ale nemusí vědět, jak přesně je vnitřně naprogramované vstřikování paliva.


 *Praktická ukázka (Python)*
	Takhle vypadá definice jednoduché třídy a následné vytvoření objektu:

``` Python
class Kniha: 
	# Konstruktor - nastaví vlastnosti při vytvoření 
	def __init__(self, nazev, autor): 
		self.nazev = nazev # Atribut 
		self.autor = autor # Atribut
		
	 # Metoda - definuje chování 
	def popis(self): 
		print(f"Kniha: {self.nazev}, Autor: {self.autor}") 
		
	# Vytvoření instance (objektu)
	 moje_kniha = Kniha("Zaklínač", "Andrzej Sapkowski") 
	 
	# Volání metody objektu
	 moje_kniha.popis()
```