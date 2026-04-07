**Serverové a desktopové operační systémy**

  

Operační systém je **systémový software**, který:

- zprostředkovává **komunikaci mezi hardwarem a softwarem**
- spravuje **procesor, paměť, diskové úložiště a zařízení**
- poskytuje programům a uživatelům **služby pro běh aplikací**  
    Operační systém funguje jako **“mozek” počítače** – bez něj by počítač prakticky nefungoval. 

**Hlavní funkce** 

- Operační systém plní tři základní funkce: ovládání počítače, abstrakce hardware a správa prostředků:

- Řízení zpracovávaných úloh
- Řídí a spravuje přístup k systémovým prostředkům
- Řízení a obsluhu vstupních/výstupních zařízení:

- Připojení k počítačové síti (LAN, WAN)
- Tiskárny

- Správu paměti
- Správu disků a údržbu systému souborů
- Komunikaci s uživatelem a obsluhu jeho požadavků
- Spouštění programů

  

  

  

**Rozdělení operačních systémů**

  

**Desktopové OS**

-  pro běžné uživatele
- Osobní PC nebo notebooky 
- Práce s aplikacemi, internetem, hry a multimédia
- Snadné a ovládání
- Příklady:

  

**A) Desktopové (klientské) operační systémy**

Jsou určeny pro **běžné uživatele** a osobní počítače:

- pracují s aplikacemi (internet, kancelářské programy, multimédia)
- mají **grafické uživatelské rozhraní (GUI)**
- kladou důraz na pohodlí uživatele

**Příklady:**

- Microsoft Windows (10, 11)
- macOS (Apple)
- Linuxové distribuce (Ubuntu, Linux Mint)

**Vlastnosti:**

- víceúlohové (multitasking)
- obvykle podporují širokou škálu aplikací
- vhodné pro každodenní práci i hry 

  

**B) Serverové operační systémy**

Serverový OS je takový operační systém, který je **optimalizován pro běh služeb pro ostatní počítače** (klient/server architektura). 

**Server** je počítač, který poskytuje služby klientům (např. jiným počítačům v síti). 

**Charakteristické vlastnosti:**

- vysoká **stabilita a výkon**
- zaměřené na **správu více uživatelů a služeb**
- často bez grafického rozhraní (jen příkazový řádek) 

  

**Přehled serverových operačních systémů**

Mezi známé serverové OS patří: 

- **Windows Server** (různé verze: 2000, 2003, 2008, 2012, 2016…)
- **Linux Server** (např. Ubuntu Server, Red Hat Enterprise Linux)
- **Solaris**
- **FreeBSD**
- **Mac OS X Server**

Serverové OS podporují služby jako:

- správa uživatelů a práv (např. **Active Directory**)
- sdílení dat nebo tiskáren
- webhosting, mailserver atd. 

  

**Typické serverové služby**

Serverové OS poskytují různé služby, například: 

**_Databázový server_**

Ukládá a zpřístupňuje databáze klientům (MySQL, Oracle, PostgreSQL). 

**_Souborový server_**

Sdílí soubory mezi uživateli a usnadňuje zálohování dat. 

**_Webový server_**

Hostuje webové stránky a odpovídá na HTTP požadavky. 

**_Mail server_**

Zpracovává e-maily pomocí protokolů:

- SMTP server – přenos pošty mezi servery
- POP3/IMAP – přístup klienta k poště 

**_Tiskový server_**

Spravuje frontu tiskových úloh a připojené tiskárny. 

**_Proxy server_**

Zprostředkovává připojení klientů a tím zvyšuje bezpečnost a výkon. 

**_DNS server_**

Překládá doménová jména na IP adresy (např. seznam.cz → 77.77.77.77). 

  

**Tabulka Desktop/Server OS**

|   |   |   |
|---|---|---|
|**Vlastnost**|**Desktop OS**|**Server OS**|
|Určeno pro|jednotlivce|více uživatelů|
|Uživatelské rozhraní|GUI|CLI nebo minimalistické GUI|
|Zaměření|komfort a aplikace|výkon a služby|
|Provoz|interaktivní práce|nepřetržitý běh|
|Příklady|Windows, macOS, Linux|Windows Server, Linux Server|

  

**Uživatelské rozhraní**

[](https://github.com/vofy/Maturita/blob/main/Informa%C4%8Dn%C3%AD%20a%20komunika%C4%8Dn%C3%AD%20technologie/11.%20Z%C3%A1klady%20opera%C4%8Dn%C3%ADch%20syst%C3%A9m%C5%AF.md#u%C5%BEivatelsk%C3%A9-rozhran%C3%AD)  

**CLI**

[](https://github.com/vofy/Maturita/blob/main/Informa%C4%8Dn%C3%AD%20a%20komunika%C4%8Dn%C3%AD%20technologie/11.%20Z%C3%A1klady%20opera%C4%8Dn%C3%ADch%20syst%C3%A9m%C5%AF.md#cli)  

- **C**ommand **L**ine **I**nterface
- Příkazový řádek
- Nenáročný na systémové prostředky ale náročnejší na použití

**GUI**

[](https://github.com/vofy/Maturita/blob/main/Informa%C4%8Dn%C3%AD%20a%20komunika%C4%8Dn%C3%AD%20technologie/11.%20Z%C3%A1klady%20opera%C4%8Dn%C3%ADch%20syst%C3%A9m%C5%AF.md#gui)  

- **G**raphical **U**ser **I**nterface
- Náročný na systémové prostředky ale méně náročný na použití
- Ovládání pomocí myši a klávesnice
- Je uživatelsky přívětivější

  

**komponenty**

- Jádro
- Prostředí (GUI, CLI)

  

**Jádro**

- Část operačního systému, která je při startu počítače zavedena do operační paměti.
- Po zavedení do paměti je jádru předáno řízení, jádro dokončí inicializaci hardwaru a následně zajišťuje správu prostředků, umožňuje spouštění programů a poskytuje jim své služby.
- U pokročilých operačních systémů nikdy neztrácí kontrolu nad počítačem a po celou dobu jeho běhu koordinuje činnost všech spuštěných procesů.

  

**Licencování**

Open-source

- BSD - FreeBSD
- GPL - Linux

Closed-source (proprietární)

- EULA - Microsoft Windows
- Apple SLA - MacOS

  

**Architektura**

- 32bit (adresuje maximálně 4GB paměti RAM)
- 64bit (dokáže adresovat 16 exabajtů paměti RAM)

  

**Ovladač**

- Zpřístupňuje služby zařízení
- Umožňuje komunikaci se zařízením

  

**Multitasking**

- Zpracování více úloh na jednou
- Operační systém přiděluje procesorový čas běžícím procesům (přepíná mezi nimi)

- Jedno jádro (vlákno) dokáže zpracovávat v danou chvíli pouze jednu operaci.

- Přerušení (anglicky interrupt) je metoda pro asynchronní obsluhu událostí, kdy procesor přeruší vykonávání sledu instrukcí, vykoná obsluhu přerušení, a pak pokračuje v předchozí činnosti
- Dělení

- **Kooperativní multitasking** - Operační systém respektuje požadavek aplikace, řízení si navzájem předávají jednotlivé procesy, je velmi zranitelný
- **Preemptivní multitasking** - Zdroje přiděluje operační systém, pád jednoho procesu neznamená ukončení práce celého systému

**BOOT**

[](https://github.com/vofy/Maturita/blob/main/Informa%C4%8Dn%C3%AD%20a%20komunika%C4%8Dn%C3%AD%20technologie/11.%20Z%C3%A1klady%20opera%C4%8Dn%C3%ADch%20syst%C3%A9m%C5%AF.md#boot)  

- Zavádění operačního systému
- Spuštění služeb

**Proces**

[](https://github.com/vofy/Maturita/blob/main/Informa%C4%8Dn%C3%AD%20a%20komunika%C4%8Dn%C3%AD%20technologie/11.%20Z%C3%A1klady%20opera%C4%8Dn%C3%ADch%20syst%C3%A9m%C5%AF.md#proces)  

- Úloha, kterou procesor zpracovává
- Využívá instrukce

  

**Instrukce**

- Příkaz pro provedení elementární operace procesoru, kterou je procesor schopen přímo vykonat

  

**Souborový systém**

- Organizace dat

  

**Souborové systémy**

- Multiplatformní - FAT32, exFAT
- Windows - NTFS, exFAT, ReFS
- Linux - Ext4, Ext3, ZFS, Btrfs

  

**Služba / démon**

- Proces na pozadí
- Spouští se při spouštění systému

  

**Organizace paměti**

- Stránkovací soubor (swap file) - virtuální paměť na disku
- Alokace paměti

  

**Zabezpečení**

- Firewall (slouží k řízení a zabezpečování síťového provozu mezi sítěmi)
- Aktualizace
- Antimalware (PC software sloužící k identifikaci a eliminaci PC virů)