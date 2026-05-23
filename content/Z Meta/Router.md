**ROUTER** (směrovač) 
- je síťové zařízení, které ==přeposílá datové pakety mezi různými sítěmi.== Spojuje například domácí síť s internetem.
- slouží k **routování podsítí** *(vyhledávání správné cesty pro daný packet)*
	- směřuje paket skrz podsítí, popřípadě vyhodí packet s podsítě pomocí takzvané defaultní routy
- **princip routeru:**
	1.  Přijme datový paket
	2. Přečte cílovou IP adresu
	3.  Nahlédne do **směrovací tabulky** (routovací tabulky)
	4.  Odešle paket správným rozhraním (portem) směrem k cíli
- ==Proč se používá ?==
	- Na rozdíl od **Switche**, který propojuje počítače jen v místní síti, **Router** propojuje jakékoliv dvě sítě. Často se používá v sítích WAN, ale také pro připojení lokální sítě k Internetu. Rozdíl mezi přepínači a směrovači si můžeme pro ilustraci představit tak, že přepínače jsou cesty propojující všechny města ve státě a směrovače jsou hraniční přechody mezi jednotlivými státy.
- Typy směřování:
	- **Statické** 
		- administrátor plní routovací tabulky a sám ručně nastaví cesty
		- Jednoduché, stabilní, ale nepružné
		- Vhodné pro malé sítě
	- **Dynamické**  
		- routování na základě routovacích protokolů
		- Router se **sám učí** cesty pomocí protokolů (automaticky se přizpůsobuje změnám sítě)
		- routovací protokoly:
			- **Interní** (IGP) -
				- pro sítě v rámci jedné autonomní oblasti *(lokální sítě)*
					- např. OSPF, RIP, EIGRP
				- používají 2 metody pro typ routování
					- **distance-vector** - Next-hop 
					-  **link-state** - cena linky 
			- **Externí** (EGP) 
				- pro propojení sítí
					- např. BGP
				- - jediná metoda
				    - **path vector** - cesta

| Protokol  | Typ             | Popis                                      | Účel                                     |
| --------- | --------------- | ------------------------------------------ | ---------------------------------------- |
| **RIP**   | Distance-vector | Jednoduchý, max. 15 hopů                   | Malé sítě                                |
| **OSPF**  | Link-state      | Rychlý, používá Dijkstrův algoritmus       | Velké podnikové sítě                     |
| **EIGRP** | Hybrid          | Cisco proprietární                         | Cisco prostředí                          |
| **BGP**   | Path-vector     | Páteř internetu, spojuje autonomní systémy | systémySměrování mezi ISP / na internetu |
|           |                 |                                            |                                          |
![[Pasted image 20260522091420.png|570]]