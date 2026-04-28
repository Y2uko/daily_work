# IOT (internet of Things)
- například **chytrá domácnost**
	- Smart home je vybavení domácnosti, které pomocí IoT zajišťuje co největší autonomitu a minimalizuje nutnost zásahu obyvatel. Uživatel ovládá systém nejčastěji přes mobilní aplikaci nebo pomocí virtuálního asistenta (Alexa, Google Home, Siri).
- Mezi běžné funkce patří:
	- **Osvětlení**: Automatické přizpůsobení denní době nebo intenzitě světla venku.
	- **Vytápění**: Inteligentní regulace teploty pro zajištění komfortu a úsporu energií.
	- **Komunikace**: Propojení jednotlivých místností a zařízení do jednoho celku.
	- **Zabezpečení**: Kamerové systémy, chytré zámky a automatické otevírání brán.
- Hlavním přínosem IoT je zvýšení efektivity a v komerční sféře také výrazné snížení personálních nákladů. Celý systém funguje na základě propojení hardwaru, softwarových platforem pro analýzu dat (**[[Big Data]]**) a prvků umělé inteligence (**[[AI]]**) , která dokáže vyhodnotit uživatelovy návyky a automatizovat procesy. Architektura IoT se obvykle dělí na tři vrstvy: vnímání (senzory), síťovou vrstvu (přenos dat) a aplikační vrstvu (zpracování a uživatelské rozhraní).
- ==co se musí splňovat aby to bylo IOT ?==
	- přístup k internetu
	- nějaký kontrolér
	- vzdálený přístup skrze aplikaci
- ==realizace pomocí==
	- Arduino
	- raspberry PI
	- obsahují vstupy, výstupy atd..
	- klasický jednodeskový PC
		- zmenšenina PC
- ==bezpečnost:==
	- **běží na OS** 
		- antivir
		- VPN
		- hesla
		- atd..
	- **segmentace v rámci IOT**
		- odděleno od domácí sítě, kde mohou být uložena vaše data
	- **připojení k wi-fi**
		- opět řešeno VLAN 
	- **práva aplikace** 
		- aby asijská firma nevěděla kontakt na vašeho barbara
- ==Hrozby:==
	- **Sběr dat**: 
		- Systémy třetích stran sbírají data o uživateli a jeho návycích. Souhlas s tímto sběrem je součástí podmínek používání, které nikdo nečte.
	- **Bezpečnostní díry**: 
		- Mnoho IoT zařízení je „zbastlených“ z technologií různého původu, často bez řádné aktualizace. Pro útočníky jsou tak snadným cílem pro vstup do domácí sítě.
	- **Zneužití dat**:
		- Systémy zaznamenávají vzorce chování, audio, a pokud uživatel není dostatečně obezřetný, i vizuální data. Tato data se odesílají na externí servery, kde s nimi třetí strany mohou nakládat dle odsouhlasených podmínek.
	- **Botnety**: Botnet

### Typy senzorů
- Senzory jsou „smysly“ IoT zařízení, které sbírají data z okolí:

	- **Teplotní senzory**: Sledují klima v místnosti nebo v průmyslových procesech.
	- **Gyroskopické senzory**: Gyroskop Měří polohu, náklon a rychlost pohybu objektu.
	- **IR (infračervené) senzory**: Detekují přítomnost objektů nebo osob (pohybová čidla).
	- **Plynové senzory**: Monitorují kvalitu ovzduší a upozorňují na únik nebezpečných plynů, jako je CO nebo CO2.
	- **Akcelerometry**: Akcelerometr

### Rozdělení IoT dle využití
- **Spotřební**: Chytré žárovky, termostaty, chytré hodinky nebo hlasoví asistenti.
- **Podnikatelské**: Sledování logistiky, automatizace skladů a optimalizace výrobních linek.
- **Infrastrukturní**: Inteligentní řízení dopravy, správa veřejného osvětlení nebo monitorování inženýrských sítí.
- **Průmyslové (IIoT)**: IIoT

### Srovnávací tabulka protokolů

|Protokol|Typické využití|Hlavní výhoda|
|---|---|---|
|**MQTT**|Senzory, zprávy|Nízká režie, spolehlivost|
|**HTTP/S**|Webová rozhraní|Univerzálnost, snadná integrace|
|**CoAP**|Zařízení s nízkým výkonem|Úspora energie a paměti|
|**LoRaWAN**|Dálkové senzory|Velký dosah signálu|

# Jak to funguje ?
- je vývojové prostředí (IDE), které se používá pro tvorbu aplikací pro Android. Umožňuje psát kód, navrhovat vzhled aplikace a testovat ji přímo na emulátoru nebo mobilu.

## Příklad projektu: Chytrý květináč 🌱

 ==Co to je ?==
- Chytrý květináč je zařízení, které se stará o rostlinu automaticky – sleduje podmínky a podle nich reaguje.

---
==Co k tomu potřebujeme ?==
- **Senzory:**
	- senzor vlhkosti půdy
	- teplotní senzor
	- světelný senzor

- **Obvody a komponenty:**
	- mikrokontrolér (např. Arduino / ESP32)
	- relé nebo tranzistor (pro zapnutí čerpadla)
	- vodní pumpa
	- napájení

- **Další:**
	- mobilní aplikace (v Android Studio)
	- propojení (např. Wi-Fi nebo Bluetooth)
---
 ==Co to dělá ?==
- měří vlhkost půdy
- sleduje světlo a teplotu
- automaticky zalévá rostlinu
- může posílat data do mobilní aplikace
---
### Jak to funguje
1. **Senzor změří vlhkost půdy**
2. Data se pošlou do mikrokontroléru
3. Program vyhodnotí:
    - pokud je sucho → zapne pumpu
    - pokud je dost vody → nic nedělá
4. Aplikace může zobrazovat:
    - aktuální hodnoty
    - historii
    - upozornění

## GPIO – co to je a k čemu slouží
![[asdasdasd 1.jpg]]
- GPIO = **General Purpose Input/Output**
- Je to sada pinů (vývodů) na mikrokontroléru, které můžeme použít podle potřeby.
-  ==Jak fungují==
	- Pin může být:
		- **INPUT (vstup)** → čte data (např. ze senzoru)
		- **OUTPUT (výstup)** → posílá signál (např. zapne LED nebo pumpu)

- ==Příklad použití==
	- vstup:
	    - čtení vlhkosti z půdy
	- výstup:
	    - zapnutí čerpadla
	    - rozsvícení LED

- ==Jednoduchý princip==
	- HIGH = zapnuto (1)
	- LOW = vypnuto (0)