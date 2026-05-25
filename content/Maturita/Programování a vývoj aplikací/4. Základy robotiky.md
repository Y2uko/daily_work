- Vše začalo průmyslovou revolucí 
- [[Vývoj průmyslové revoluce]]:
	1. mechanicky a ručně (**období páry**)
	2. přichází manufaktury a masová výroba (**elektrika**)
	3. začátek automatizace, rozmachy PC, **digitální technologie , automatizace** (první automatické linky)
	4. spolupráce robotů (koboti), a plná automatizace (**IOT, AI**)
	5. návrat člověka, a zapojení AI do robotické sféry
- ==Co je to robot?==
	Termín „robot“ poprvé použil Karel Čapek ve své divadelní hře R.U.R. (Rossumovi Univerzální Roboti), přičemž samotné slovo vymyslel jeho bratr Josef (odvozeno od slova „robota“).

	Robot je stroj, který vykonává práci samostatně bez nutnosti přímého vstupu člověka. Své okolí vnímá pomocí senzorů a na základě dat z nich reaguje. Moderní systémy už dokáží vyhodnocovat i svůj vliv na prostředí, což nazýváme **zpětnou vazbou** – výstup systému (např. pohyb ramene) zpětně ovlivňuje jeho vstup (např. korekce dráhy). Pro implementaci těchto algoritmů se často využívá C# nebo Java.
	
	Roboti mohou být:
	- **Řízení/ovládaní**: vyžadují interakci člověka (např. dálkově ovládaný dron).
	- **Autonomní/inteligentní**: rozhodují se sami na základě naprogramované logiky nebo AI.
#### Generace robotů

- Vývoj robotů dělíme do tří generací podle jejich schopností:

	1. generace 
		stroje ==pracující podle pevně daného programu== (cyklus se neustále opakuje bez ohledu na okolí).
	
	2. generace 
		program už umožňuje ==reakce na podněty z okolí díky signálům ze senzorů== (např. zastaví, když narazí na překážku).
	
	3. generace
		obsahují prvky umělé inteligence, mají ==schopnost učení a přizpůsobení se novým situacím==.

#### Druhy robotů:

- **Samostatní roboti**
	- třeba robotická ruka

- **Koboti** (Cooperation bot)
	- roboti co pracují buď spolu nebo s člověkem
	- Jde o specifickou podskupinu robotů navržených pro přímou spolupráci s člověkem v jednom pracovním prostoru. Kobot není náhradou člověka, ale jeho pomocníkem – zvyšuje efektivitu práce. Člověk by danou činnost mohl vykonat sám, ale kobot mu ji usnadní.
		- *Příklad* Kobot drží těžké dveře auta ve správné poloze, zatímco člověk je následně přišroubuje ke karoserii.

- **specializovaní roboti** (kam nemůže člověk tam nastrčej clankera)
	- zdravotnictví
	- armáda
		- likvidace bomb
		- průzkum
	- pyrotechnika

# Hardwarový vývoj robota

### pohony:
- **pneumatický** 
	- Vzduch, například vzduchový rozvody (relativně bezpečné), lehký průmysl, robotické ruce, dopravníky atd...
	- Má menší výkon než elektrika a hydraulika
- **hydraulický** 
	- Používá se v těžkém průmyslu (lisovna), využívá tlak oleje. Ne moc ekologický, velmi náročná údržba
- **elektrický** 
	- Menší náročnost na údržbu, proto se dnes často používá, například u robotů

### Pojmy
- **čidlo** - slouží k regulaci (něco snímá)
	- například (čidlo teploty)
- **Detektor** - snímá fyzikální jevy
	- el. proud či napětí
	- například detektor kouře
- **sensor** - přeměňuje fyzikální veličinu na el. signál
	- patří sem například čidl
- **detektor** - zjišťuje přítomnost fyzikálního jevu
	- termistor
- **snímač** - převádí (světlo, zvuk..) na elektriku
- **spínač** - mechanické zařízení k vytvoření nebo přerušení el. obvodu
- **hlídač** - automatické pojištění zařízení, signalizující nebezpečí poruchy
	- světelné brány
- **hlásič** - zařízení odhalující nebezpečí

### příklad Robotická ruka

##### Hardware
- konstrukční rám
- klouby
- motor
- chňapka, svářečka držák (to co ruka ovládá)
	- pen
	- 3d Printer
	- Laser 
- řídící deska (programuje se)
- kamery a bezpečnostní brány
##### Software
- základní firmware (třeba BIOS)
- ovládací software 

# 3 zákony robotiky

- **POZNÁMKA** - pravidla nemají stejnou prioritu, největší má 1 nejmenší má 3

1. Robot nesmí ublížit člověku nebo svou nečinností dopustit, aby bylo člověku ublíženo.
2. Robot musí uposlechnout příkazů člověka, kromě případů, kdy jsou tyto příkazy v rozporu s prvním zákonem.
3. Robot musí chránit sám sebe před poškozením, kromě případů, kdy je tato ochrana v rozporu s prvním, nebo druhým zákonem.

- obhájit pravidla robotů užitých ve válkách

# Programování robotů 

Při programování robotů se často setkáváme s potřebou definovat tzv. „trajektorii“. Robot musí vědět, kudy se má pohybovat, aby nenarazil do překážky. K tomu slouží matematické modely (kinematika). V praxi se často používají programovací jazyky jako C++ nebo Python, případně specifické průmyslové jazyky (např. RAPID pro ABB nebo KRL pro KUKA). Pro vizualizaci rozhraní robotů se často využívá HTML a CSS

```
// Příklad: Velmi zjednodušený pseudokód pro pohyb robota
if (senzor_vzdalenosti < 10) {
    robot.stop();
    robot.otocit(90);
} else {
    robot.jet_vpred(50);
}
```

Tento kód ukazuje základní princip 2. generace robotů – čtení hodnoty ze senzoru a následné rozhodnutí (if-else). V 3. generaci by robot místo jednoduchého zastavení mohl pomocí neuronové sítě vyhodnotit, zda je lepší překážku objet, nebo ji odsunout.

### Význam senzoriky

Senzory jsou „smysly“ robota. Bez nich by robot byl jen slepý stroj. Dělíme je na:

- **Vnitřní**: hlídají stav robota (teplota motorů, poloha kloubů, napětí baterie).
- **Vnější**: hlídají okolí (kamery, ultrazvukové senzory vzdálenosti, LiDARy pro mapování prostoru, dotykové senzory).

Vývoj senzorů jde ruku v ruce s miniaturizací. Dnes máme senzory, které se vejdou na čip a přitom dokáží měřit zrychlení v osách (akcelerometry) nebo náklon (gyroskopy), což je klíčové pro stabilitu například u balancujících robotů nebo dronů.