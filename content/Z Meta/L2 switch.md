**L2 switch**  
- Inteligentní prvek, který pracuje s **rámci** (`frames`). Na jejichž třízení využívá **metody**
	- **Metody přepínání (switching):**
		- `Store and forward` Switch přijme celý rámec do vyrovnávací paměti (**cache**), zkontroluje chyby (FCS/CRC) a teprve poté odešle. Je spolehlivý, ale pomalejší.
		- `Cut and through` Switch začne odesílat rámec ihned po přečtení cílové **MAC adresy**, nečeká na zbytek rámce. Je velmi rychlý, ale může šířit i poškozené rámce.
		- `Fragment free` Kompromis – čeká na přijetí prvních 64 bajtů, čímž vyloučí většinu kolizních rámců, a poté začne odesílat.
		- `Adaptive switching` 
			- Automaticky volí mezi `Store and forward` a `Cut and through` podle vytížení a kvality linky.
- FUNKCE
	- přepíná podle MAC adres
	- Udržuje si tabulku (`MAC table`) a propojuje porty přímo mezi odesilatelem a příjemcem (slouží tedy jako takový prostředník, který vezme co jste poslali a dá to na port kde je příjemce)
- PRINCIP
	- K učení používají tzv. Zpětný učící algoritmus (Backward Learning Algorithm), díky němuž vychází ze své vnitřní tabulky, kde jsou uloženy MAC adresy připojených zařízení a pokud přijdou data pro nějaké zařízení, které tam ještě nemá, chová se jako rozbočovač (pošle je do všech segmentů) a předpokládá, že přijímací zařízení se ozve. Poté si jeho adresu uloží a příště už ví, kam má data poslat.
- max 52 portů
- spojuje zařízení v síti do síťové topologie **STAR**
- **Výhoda:** Eliminuje kolize, data tečou jen k adresátovi (zvýšení propustnosti a bezpečnosti).
- **Port mirroring** Funkce switche, která kopíruje provoz z jednoho nebo více portů na jiný port (kde může být připojen např. analyzátor sítě pro monitoring).
- **“hello packet”**: žádá nově připojené zařízení o MAC adresu, ty si ukládá do MAC tabulky *(MAC adresy připojených zařízení)*
- **VLAN (Virtual LAN):** Logické rozdělení jednoho fyzického switche na několik nezávislých virtuálních sítí, což zvyšuje bezpečnost a efektivitu provozu.
- **Dělení:** 
	- **A**
		- SOHO (Small Office/Home Office) pro domácnosti
		- PRO (profesionální) s podporou správy (např. Cisco, Aruba).
	- **B**
		- s OS
		- bez OS


