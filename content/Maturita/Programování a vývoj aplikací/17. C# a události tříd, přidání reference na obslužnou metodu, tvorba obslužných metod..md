
- **Události** (events) Tříd
	- v C# slouží k tomu, aby třída mohla upozornit ostatní objekty na to, že nastala nějaká specifická akce
	- Využívají tzv. _delegáty_ (nejčastěji `EventHandler`), které fungují jako ukazatele na metody.
	- [[Delegát]]
		- Princip fungování delegátu:
			- Delegát je v podstatě typově bezpečný ukazatel na metodu. Definujeme jím signaturu (vstupní parametry a návratový typ), kterou musí každá metoda, která chce událost obsloužit, splňovat.
	1. Jak fungují základní prvky
		- **Vydavatel** (Publisher)
			Třída, která událost definuje a spouští.
		- **Odběratel** (Subscriber)
			Třída, která se k události přihlásí a reaguje na ni.
		- operátory `+=` a `-=` 
			Používají se k přihlášení (přidání) nebo odhlášení odběru metody od události.
		- **Delegát** 
			Definuje signaturu metody (vstupní parametry a návratový typ), která bude událost zpracovávat
	- **Přihlášení a odhlášení k události** (event)
		k události se přihlásíme pomocí operátoru:
		- `+=`
			- operátor = *speciální symbol nebo klíčové slovo, které se používá k provedení operace s jednou nebo více proměnnými (variables) a hodnotami*
		 - říkáme tím "Až se událost stane zavolej tuto moji metodu"
			``` Csharp
		// Příklad přihlášení k události tlačítka ve WinForms 
		button1.Click += MojeObsluznaMetoda;
			```
		- Pokud už na  tuto událost reagovat nechceme použijeme operátor:
			- - `-=`
		``` Csharp
	// Odhlášení button1.Click 
	button1.Click -= MojeObsluznaMetoda;
		```
		- U práce s událostmi musíme dbát na **memory leak**
			-  Únik paměti, ke kterému v C# dochází, pokud se zapomeneme odhlásit od události objektu s delší životností, čímž zabráníme Garbage Collectoru v uvolnění paměti.

- ## Obslužná metoda 
	- Obslužná metoda - `EventHandler`
	- je běžná metoda, která musí odpovídat signatuře definované delegátem události
		- signatura musí přesně odpovídat definici delegáta
	- Ve WinForms, kde se s událostmi setkáváme nejčastěji, mají obslužné metody standardně dva parametry:
		- `object sender` (říká nám kdo událost vyvolal) 
		- `EventArgs e` (data o události)
	-  V prostředí **Visual Studia** se ==obslužná metoda často vygeneruje automaticky== po dvojitém kliknutí na prvek v návrháři formulářů.
	- #Příklad: Kliknutí na tlačítko ve  (Windows Forms)
		Tohle je nejklasičtější příklad. Máte tlačítko a chcete, aby se po kliknutí na něj ukázalo okno s textem.
	``` C#
	//OBSLUŽNÁ METODA pro talčítko button
	private void Button_Click(object sender, RoutedEventArgs e)
	{
	    // Tento kód se spustí, jakmile uživatel klikne na tlačítko
	    MessageBox.Show("Ahoj! Kliknul jsi na mě.");
	}
	```

	- `Object senders`
		- Pokud by ale pět různých tlačítek používalo tuhle stejnou metodu, v `sender` bude uloženo to konkrétní tlačítko, na které se zrovna kliklo.
	- `RoutedEventArgs e` nebo `EventArgs e`
		- U kliknutí to nemusí být nic velkého, ale např. u události „stisk klávesy“ (KeyDown) v tomto parametru najdete informaci o tom, _která_ klávesa byla stisknuta.

	- #### Přidání reference na obslužnou metodu
		- ve zkratce znamená ==propojíte událost s konkrétní metodou, která na ni má reagovat==
			- Říkáte tím programu: „Až se stane **TATO** věc (např. kliknutí), jdi a spusť **TUTO** metodu.“
		- V C# je lze vytvořit 2 hlavními způsoby:
			- **vizuálně** (klikáním ve Visual Studiu) 
			- **ručně v kódu**
			
		- 1. vizuálně (krok po kroku)
			- otevřeme okno designér v souboru `forms`
			- přetáhneme do pole kde tlačítka uvidíme
			- označíme dané tlačítko, ke kterému chceme přidatreferenci
			- v panelu klikněme na properties a v ikonce blesku (událost) najdeme událost, kterou chceme (například `Click`)
			- Dvakrát klikněte do prázdného pole vedle názvu této události.
			- ==Visual Studio samo vygeneruje prázdnou obslužnou metodu v kódu a automaticky ji k tlačítku připojí (přidá referenci).==
	
		- 2. ručně v kódu (krok po kroku)
			- pomocí operátoru `+=`
			- Představte si, že máte v kódu t
				- **tlačítko** pojmenované `mojeTlacitko` 
				- **metodu** `ZpracujKliknuti`. 
			- Propojíte je takto:
```
	// Přidání reference (přihlášení k odběru události)
	mojeTlacitko.Click += ZpracujKliknuti;
	
```

- Událost `Click` funguje jako takový **seznam úkolů** (odborně se tomu říká *delegát*).
	- - Pomocí `+=` říkáte: _„Přidej na konec tohoto seznamu úkolů moji metodu `ZpracujKliknuti`.“_
	- Všimněte si, že za názvem metody `ZpracujKliknuti` **nejsou kulaté závorky `()`**. To je klíčové! Pokud byste napsali závorky, metodu byste hned spustili. Bez závorek předáváte pouze _odkaz (referenci)_ na tu metodu, aby ji tlačítko mohlo spustit až někdy v budoucnu.