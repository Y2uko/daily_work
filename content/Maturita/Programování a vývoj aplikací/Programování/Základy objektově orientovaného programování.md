## Co je OOP?

OOP (Object-Oriented Programming) je **způsob psaní programů**, kde vše modelujeme jako **objekty** — stejně jako v reálném světě. Objekty mají vlastnosti (data) a chování (funkce).
jazyky (csharp a java)

### Proč OOP?

- Kód je přehledný a organizovaný
- Snadná opakovaná použitelnost (znovupoužití kódu)
- Snadnější údržba a rozšiřování
- Modeluje reálný svět přirozeným způsobem

#### 3 základní vlastnosti OOP
**Zapouzdření** (obalení)
	- Vyjadřuje schopnost objektu spojit v jeden celek data a metody
	- ukrytí uvnitř struktury objektu
	- Nemůžeme manipulovat přímo s atributy objektu, ale pouze pomocí operací z veřejného rozhraní objektu
	- Zamezuje nechtěným změnám či chybám stavu objektu
	- *Modularita* – každý objekt lze udržovat a spravovat nezávisle na jiném objektu, aniž by to nějak ovlivnilo celkovou funkčnost programu

**[[Dědičnost]]**
	- Umožňuje vytvářet ==nové objekty (potomky)== již ==existujících objektů (předků)==, přebírat od nich datové položky a metody a může je modifikovat či upřesňovat.
	- usnadňuje ==znovu použitelnost kódu== a zpřehledňuje strukturu
	- **potomek** může využít konstruktor rodiče pomocí klíčového slova `base()`
	- *příklad*:
		- Máme třídu `Osoba`, ze které dědí `Žák`.
		- `Žák` má vše, co `Osoba`, ale přidává si vlastní specifické atributy (např. `trida` nebo `prumerZnamek`)

**Polymorfismus** (mnohotvárnost)
	- vlastnost OOP, která umožňuje pojmenovat metodu jedním jménem a tato metoda může být společná pro různé objekty ve stromové hierarchii
	- Příklad: 
		- když ve třídě vytvořím metodu `počítej`, se 2 parametry
		- můžeme se stejným názvem vytvořit metodu znovu akorát se 3 parametry (a pak 4 parametry a tak dále a tak dále)


## OOP vs procedurální programování

|Procedurální|OOP|
|---|---|
|Kód = seznam příkazů|Kód = objekty spolupracující|
|Data a funkce odděleny|Data a funkce spolu v objektu|
|C, Pascal, starší PHP|Java, C#, Python, C++|
|Pro malé programy|Pro velké systémy|

## Klíčové pojmy — přehled

**[[Třída]]** (Class)        - Šablona / plán — předpis pro objekty

**[[Objekt]]**                   - Konkrétní instance třídy (živý objekt)

**Atribut**                  - Vlastnost *objektu* (proměnná uvnitř třídy)

**Metoda**                 - Funkce uvnitř třídy — co *objekt* umí dělat

**[[Konstruktor]]**        - Speciální metoda pro vytvoření objektu


### skládání a delegování 
- **Skládání** je technika, kdy vytváříme složitější objekty z objektů jednodušších.
	- ==Použití několika objektů k vytvoření dalšího objektu==
```
1  //například - popsat slovněBod 
2  bod1 = new Bod(0,5);
3  Bod bod2 = new Bod(3,3);
4
5  Usecka usecka1 = new Usecka(bod1, bod2);
```

-  **Delegování**,  
	- třída může delegovat některé činnosti
	- objekt nekoná činnost sám, předá činnost jiné třídě na vykonán
	    - třída `auto` deleguje funkci oprav třídě `mechanik`
	- delegát
	    - zastupuje procedůru
	    - pomocí `event` lze vytvořit událost
	    - pomocí `.NazevEventu += new NazevDelegata(nazevFunkce, ktera se pri eventu spusti)`
	- podle IOC by si třída neměla generovat vlastní závislosti


### Typické otázky u maturity

1. **Jaký je rozdíl mezi třídou a objektem?** Třída je šablona (kód) definující vlastnosti, objekt je konkrétní instance této třídy vytvořená v paměti pomocí new.
2. **K čemu slouží konstruktor a kolik jich může být?** Konstruktor inicializuje objekt a přiřazuje hodnoty atributům. Můžeme jich mít tolik, kolik je atributů + 1 (bezparametrický).
3. **Co je to zapouzdření a proč se používá?** Je to skrývání vnitřní struktury objektu. Zamezuje přímé manipulaci s daty, čímž chrání objekt před nechtěnými změnami a chybami.
4. **Jaký je rozdíl mezi procedurou a funkcí?** Procedura (void) pouze vykoná kód, funkce vrací hodnotu, kterou lze dále zpracovat nebo přiřadit do proměnné.
5. **Co znamená skládání (kompozice) v OOP?** Je to způsob tvorby objektů, kdy jeden objekt obsahuje jako své součásti objekty jiné (např. auto obsahuje motor, kola, volant).