
==STŘEDNĚ== 

**Kybernetická bezpečnost** ==se zabývá ochranou systémů, sítí a dat před digitálními útoky.== Cílem je zajistit důvěrnost, integritu a dostupnost informací. Pro komplexní pochopení je nutné pracovat s modelem **CIA Triad**
#### CIA Triáda
- **Confidentiality** (důvěrnost) – data jsou dostupná pouze oprávněným osobám 
- **Integrity** (integrita) – data nejsou neoprávněně měněna 
- **Availability** (dostupnost)  – data a služby jsou dostupné, když je potřebujeme

V oboru informatiky, se kybernetika zabývá ochranou počítačových systémů a sítí před neoprávněným přístupem k informacím či systémům
- chrání před narušením nebo zneužitím poskytovaných služeb - ==před kybernetickým útokem==


### Definice a principy
Bezpečnost je definována **prevencí**, tedy ==systematickým předcházením rizikům==, která mohou ohrozit `hardware` (fyzické vybavení), `software` (programové vybavení) i samotná `aktiva`. Klíčovým prvkem je zde Defense in depth

- ==Počítačová ochrana ve třech krocích:==
	- **prevence** – ochrana před hrozbami (*riziky*)  
	- **detekce** – odhalení neoprávněných činností a slabých míst v systému
	- **náprava** – odstranění slabých míst v systému

- **Kybernetika**
	- ==Vědní obor (zakladatel Norbert Wiener), který se zabývá procesy řízení a komunikace v živých organismech i strojích==. V IT se zaměřuje na algoritmy a principy řízení systémů.
	
- **Zpětná vazba**
	- Mechanismus, kdy ==výstup systému ovlivňuje jeho budoucí vstup==. 
	- Slouží ke kontrole chyb a následné nápravě (např. automatická aktualizace systému na základě hlášení o chybách).

- **Kybernetická Hrozba** 
	- příčina bezpečnostní události nebo incidentu
	- výsledkem může být poškození aktiva

- **Riziko**: ==Pravděpodobnost, že hrozba využije zranitelnosti== a způsobí škodu na aktivu.

Bezpečnostní událost/incident
- *událost*
	- může způsobit narušení bezpečnosti aktiva
- *incident*
	- narušení bezpečnosti aktiva
	- Reakce na bezpečnostní incident 
		- **Postup: (zjednodušeně)**
			1. identifikace incidentu 
			2. Izolace problému 
			3. odstranění hrozby 
			4. obnova systému 
			5. vyhodnocení incidentu (dokumentace)
			6. Opravit a znemožnit opakování stejné situace
	
- **Bezpečnostní politika**
	- dokument či stok papírů, ve kterých jsou ==zásady a pravidla pro nasazení bezpečnosti v organizacích==
	- cílem je ochrana aktiva



# Ochrana zařízení a soukromí

##### Co se využívá pro ochranu dat 
- Firewall: ==Síťový prvek kontrolující provoz na bázi Packet Filtering==
- Zálohování: ==Jediná metoda obnovy dat po útoku==. Doporučuje se pravidlo 3-2-1 zálohování
- Veřejné Wi-Fi: ==Rizikové sítě náchylné k útoku== Man-in-the-Middle
- HTTPS a VPN: ==Protokoly zajišťující šifrování komunikace==. HTTPS využívá TLS
- Více faktorové ověření
- Šifrování komunikace

### Ochrana aktiv
**Aktivum** je vše, co ==má pro organizaci/uživatele hodnotu== a vyžaduje ochranu.
- Dělení
	- **Hmotná aktiva**: Fyzické prostředky (počítače, servery, budovy).
	- **Nehmotná aktiva**: Informace, know-how, software, dobré jméno (reputace).

	- **Primární aktiva**: Klíčové hodnoty (např. receptura Kofoly, osobní údaje zákazníků).
	- **Podpůrná aktiva**: Vše, co zajišťuje provoz primárních (např. zaměstnanci, suroviny, infrastruktura).
	- **Technická aktiva**: Konkrétní stroje, výrobní linky či datové servery zajišťující chod firmy.


### Hesla a přihlašování
**Heslo** je ==jedno z prvních zabezpečení, mělo by být komplexní a unikátní.==

- **Zásady bezpečného hesla**: Minimálně 12–16 znaků, kombinace velkých a malých písmen, číslic a speciálních znaků. Nesmí obsahovat osobní údaje. Doporučuje se používat [[Passphrase]]
- **Správce hesel (`Password Manager`)**: Aplikace pro bezpečné ukládání a generování hesel. Doporučení: Nikdy v nich neukládejte heslo k primárnímu e-mailu nebo internetovému bankovnictví.
- **Dvoufaktorové ověřování ([[2FA]])**: Metoda vyžadující pro přihlášení kromě hesla i druhý důkaz. Často využívá **TOTP**
	- TOTP - Time-based One-Time Password. Algoritmus generující časově omezená hesla na základě sdíleného tajemství a aktuálního času.


### Základní pojmy 

- **Model**: 
	- ==Zmenšený nebo virtuální systém napodobující chování reálného stroje==. 
	- Používá se pro testování aktualizací, softwaru či hardwaru před nasazením do ostrého provozu.
- **Zranitelnost**: 
	- ==Slabina v systému== *(např. neaktualizovaný software)*, ==kterou může hrozba zneužít==. 
	- Často se identifikuje pomocí Vulnerability Scanning

- **Pen-test (Penetrační test)**: 
	- ==Kontrola zabezpečení firmy z kybernetického hlediska==. 
	- Musí být prováděn autorizovanou osobou, neboť neoprávněný pokus o průnik je nelegální.
- **Zero day** 
    - ==Označení pro zranitelnosti softwaru, které jsou odhaleny ještě před vydáním aktualizace==.
    - zero day referuje na časovou osu dnů chyby
        - den 1 - zjištění zranitelnosti,
        - den 2 - enumerace problému atd..
    - zero day zranitelnosti jsou velmi vyhledávané na dark netu, nejlepší jsou no-click zranitelnosti (nakažení zařízení bez jakékoliv akce na cíleném zařízení), za jejichž znalost útočníci platí často přes 2 miliony korun (cena bývá 100 000 dolarů a více)




# Hrozby

### Rozdělení kybernetických hrozeb

| Typ rozdělení  | Kategorie     | Příklady                                                  |
| -------------- | ------------- | --------------------------------------------------------- |
| Podle úmyslu   | **Úmyslné**   | Kybernetické útoky, krádeže, ransomware                   |
|                | **Neúmyslné** | Chyba při práci, prozrazení informací, poškození techniky |
|                | **Náhodné**   | Živelné pohromy, blackout, přepětí v síti                 |
|                |               |                                                           |
| Podle umístění | **Vnitřní**   | Technické závady, personální selhání, špionáž             |
|                | **Vnější**    | Útoky z kyberprostoru, živelné katastrofy                 |

## Sociální inženýrství a podvodné praktiky
Manipulace s lidmi za účelem získání citlivých dat či přístupů.

- **Phishing**: ==Podvodné e-maily imitující známé instituce či osoby==. Specifickou formou je [[Spear Phishing]]
- **Vishing**: ==Hlasová podoba phishingu (telefonát)==, kdy se útočník vydává za autoritu.
- **Baiting**: Útočník láká oběť na "výhru" nebo "dárek" (např. infikovaný USB disk).
- **SPAM**: Nevyžádaná hromadná elektronická komunikace.
- **Krádež identity**: ==Zneužití osobních údajů oběti k páchání trestné činnosti== nebo finančním podvodům.

## Malware a útoky na infrastrukturu

- **Malware**: Souhrnný název pro škodlivý software.
- **Viry**: Programy schopné replikace připojením k jiným souborům. Odstraňují se pomocí Antimalware *(Software určený k detekci, izolaci a odstranění škodlivého kódu ze systému.)*
- **Trojský kůň**: Škodlivý program maskovaný za užitečnou aplikaci. 
	- Typy: 
		- otevírání zadních vrátek (`backdoor`),
		- špionážní moduly, nebo `Trojan Dalmond` stahující další hrozby.
- **Ransomware**: Malware šifrující data s požadavkem na výkupné. Dnes existuje již 6. generace těchto útoků.
- **DDoS útok**: Útok zahlcením služby velkým množstvím požadavků. Obrana zahrnuje využití služeb jako [[Cloudflare]], přesměrování provozu, omezení přístupů a konfiguraci `Firewallu`.
- **Spoofing** - padělání 
    - komunikace odeslána z neznámého zdroje, který se tváří jako zdroj známý přijímači 
    - imitace známých wi-fi sítí aby se zařízení automaticky připojili

