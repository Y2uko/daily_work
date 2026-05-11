- Proces převodu čitelné informace (otevřený text) do nečitelné podoby (šifrový text).
- Druhy:
### Symetrická kryptografie

- používá se 1 společný klíč 
		  --> stejný klíč pro šifrování a dešifrování
	- bezpečnostní riziko může tedy být odhalení klíče
	- **použití**:
		- šifrování disku
		- VPN
		-  WI-FI (WPA2, WPA3)
	- ochrana při cestě klíče za příjemcem
		- **[[AES]]** (**Advanced Encryption Standard**): V současnosti celosvětový standard pro symetrické šifrování. Je odolný vůči útokům hrubou silou a využívá se v zabezpečení Wi-Fi (`WPA2/3`) nebo šifrování disků (`BitLocker`).
		- [[DES]] / [[3DES]]: Starší šifrovací standardy. DES (Data Encryption Standard) je kvůli krátkému 56bitovému klíči dnes považován za prolomený, 3DES (Triple DES) aplikuje DES třikrát za sebou, což zvyšuje bezpečnost, ale je pomalý a postupně se od něj ustupuje
		- [[Salsa20]]
	- Příklad symetrické šifry:
		- Caesarova šifra (jednoduchý příklad)

### Asymetrická kryptografie	

- používají se 2 různé klíče
		- Veřejný klíč	  (**public key**)
		- soukromý klíč   (**private key**)
	- nevýhodou je výpočetní náročnost (pomalejší než symetrické šifrování)
	- zašifrováno (public key) a pro rozšifrování je potřeba (private key)
	- **použití**:
		- HTTPS (zabezpečení webové stránky, používají to protokoly SSL/TLS)
		- digitální podpisy
		- bezpečné doručování symetrických klíčů	
		- šifrovaní emailů
	- příklady algoritmů:
		- **RSA** - Rivest–Shamir–Adleman — nejrozšířenější asymetrický šifrovací algoritmus. Bezpečnost je založena na faktorizaci velkých čísel.
		- **ECC** - (**Elliptic Curve Cryptography**): Moderní kryptosystém využívající vlastnosti eliptických křivek. Poskytuje stejnou úroveň bezpečnosti jako RSA, ale s podstatně menšími klíči, což šetří výpočetní výkon a přenosovou kapacitu (vhodné pro mobily nebo čipové karty).
		- **Diffie-Hellman** - Protokol pro bezpečnou výměnu klíčů přes nezabezpečený kanál. Umožňuje dvěma stranám vytvořit společný tajný klíč, aniž by jej kdykoliv přenášely po síti.