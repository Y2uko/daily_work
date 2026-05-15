- Algoritmus je přesný návod či postup, kterým lze vyřešit daný typ úlohy.
- Jako takový soubor algoritmů můžeme uvést třeba kuchařku
	- krok za krokem návod jak dosáhnout výsledného pokrmu
- snaha o to ho udělat co nejjednodušší
- Algoritmus se může objevit snad ve všech odvětvích, v programování ale znamená algoritmus - teoretický princip řešení problému
- #### Jaké vlastnosti by měl algoritmus obsahovat
	1. Jednoduchost (elementárnost)
		- skládá se z **konečného** počtu kroků
	2. Konečnost
		- každý algoritmus má určitý počet kroku, který ==musí být konečný==
		- Postupy, které tuto podmínku nesplňují se mohou nazývat výpočetní metody (např. reaktivní proces, který průběžně reaguje s okolním prostředím)
	3. Obecnost
		- Algoritmus ==má širokou množinu možných vstupů==
		- algoritmus by měl řešit všechny úlohy daného typu
	4. Určitost
		- Každý krok algoritmu musí být ==jednoznačně a přesně definován==
		- kroky musí být srozumitelné jako by jsme určovali přesně každý krok dané operace
	5. Korektnost
		- algoritmus skončí pro libovolná (korektní) data ==správným výsledkem== v konečném množství kroků.
	6. Výstup
		- Algoritmus má ==alespoň jeden výstup==, veličinu, která je v požadovaném vztahu k zadaným vstupům, a tím tvoří odpověď na problém, který algoritmus řeší
		- výstup je to samotné řešení na problém, který algoritmus řeší
		- 

	- ##### Praktická ukázka
	- Chtějme po počítači, aby prohodil dvě čísla. Tedy hodnoty dvou proměnných, pojmenovaných například `a`, `b`). Jistě víme, že následující kód nebude fungovat:
		a = b;
		b = a;
	- Do proměnné `a` se uloží obsah proměnné `b`. Do proměnné `b` se potom uloží obsah proměnné `a`, ale ten je už `b`, takže je v obojím `b`. Musíme si tedy pomoci další proměnnou `c`:

		c = a;
		a = b;
		b = c;

	- Nyní se obsahy proměnných `a` & `b` prohodily. Máme tu tedy první algoritmus na prohození dvou čísel. Všimněme si, že nelze říci "prohoď čísla". Musíme dokonale popsat, co má program dělat pomocí soustavy příkazů.

- ###### vysvětlení důležitých pojmů
	- **Proměnná**
		-  pojmenované místo v paměti, do kterého lze uložit hodnotu. 
		- Tato hodnota se může v průběhu programu měnit.
	```java
int vek = 18;       // proměnná "vek" uchovává číslo 18
String jmeno = "Jan"; // proměnná "jmeno" uchovává text
	```
	- **Konstanta**
		-  pojmenované místo v paměti, jehož hodnota se **nemění** po celou dobu běhu programu.
	```java
final double PI = 3.14159;
	```
	- **[[Datové typy]]**


- #### Cykly (loop)
	- v kontextu algoritmu znamenají řídicí strukturu, která umožňuje **opakovaně provádět určitou část kódu**, dokud není splněna nebo splněna určitá podmínka
	- základní stavební kámen algoritmizace
	- eliminují nutnost psát stejný kód několikrát
	- 2 typy na které se cykly dělí:
		- **bez podmínky**
			- `for`
				- 3 parametry - `int i = 0; i < 5; i++`
					- 1. parametr = deklarace řídící proměnné cyklu
					- 2. parametr = podmínka, po jakou dobu bude cyklus běžet
					- 3. parametr = jakým způsobem se bude řídící proměnná měnit po každém cyklu
		- **s podmínkou**
			- `while` - s podmínkou na začátku
				- Podmínka se kontroluje před každým průběhem
				- Pokud není splněna, tělo cyklu se nespustí ani jednou
				- Opakuje se, dokud je podmínka pravdivá (`true`)
			- `do-while` - s podmínkou na konci
				- Tělo cyklu se provede vždy alespoň jednou, podmínka se kontroluje až po prvním průchodu.
				- **Kdy použít `do-while`?** Typicky při čtení vstupu od uživatele — chceme načíst vstup alespoň jednou a pak se zeptat, zda chce pokračovat.
				
		- ![[Pasted image 20260512141649.png|588]]
	- #### `break` a `continue`
		- **`break`** — okamžitě ukončí cyklus a přejde za něj
		- **`continue`** — přeskočí zbytek aktuálního průchodu a přejde na další iteraci
```java
for (int i = 0; i < 10; i++) {
    if (i == 3) continue; // přeskočí číslo 3
    if (i == 7) break;    // zastaví cyklus na čísle 7
    System.out.println(i);
}
// Výstup: 0, 1, 2, 4, 5, 6
```


- #### Způsoby jak zapsat algoritmus
	- **slovní** popis kroků (kuchařka)
	- **programovací** jazyk - konkrétní implementace
		- pseudokód - zápis podobný programovacímu jazyku, ale bez přísné syntaxe
	- vývojový **diagram** - grafické znázornění pomocí symbolu jako třeba obrázek , který můžeme vidět u cyklů


### Dělení algoritmu
- rekurzivní 
	- Rekurzivní opakuje kód prostřednictvím volání sebe sama
	- Každý rekurzivní algoritmus lze převést do iterativní podoby.
	-  **+** Výhoda rekurzivních algoritmů je v jejich snadno čitelném a kompaktním zápisu.
	-  **-** Nevýhodou je spotřeba dodatečných systémových prostředků pro udržení jednotlivých rekurzivních volání.
- Iterativní
	- algoritmus je takový, který spočívá v opakování určité své části (bloku).