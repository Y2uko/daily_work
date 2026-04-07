**VPN** (Virtual Private Network) je technologie, která vytváří šifrovaný „tunel" přes veřejnou síť (internet). Data uvnitř tohoto tunelu jsou zašifrovaná a nečitelná pro kohokoli, kdo je zachytí na cestě. Uživatel tak komunikuje, jako by byl přímo připojen k cílové síti, přestože fyzicky sedí jinde.
![[Pasted image 20260329114034.png]]

- **Využití**:
	- VPN se používá ve třech hlavních scénářích. V podnikovém prostředí jde o vzdálený přístup zaměstnanců do firemní sítě a propojení poboček. V oblasti ochrany soukromí jde o skrytí aktivit před ISP a použití nezabezpečených veřejných WiFi sítí (kavárny, hotely, letiště). Třetím scénářem je obcházení geografických omezení – přístup k obsahu dostupnému jen v určité zemi.
# Jak VPN funguje – krok za krokem

Uživatel spustí VPN klienta, který se připojí k VPN serveru a provede autentizaci (heslo, certifikát, nebo obojí). Po úspěšném ověření se mezi klientem a serverem sestaví šifrovaný tunel. Veškerá komunikace pak prochází tímto tunelem – ISP (poskytovatel internetu) ani nikdo jiný na cestě nevidí obsah, jen to, že uživatel komunikuje s VPN serverem. VPN server data rozbalí a pošle je dál do cílové sítě, jako by přišla přímo od uživatele.

Důležitým efektem je také změna IP adresy – cílový server vidí IP adresu VPN serveru, ne skutečnou IP uživatele.

---

### Typy VPN

- **Remote Access VPN** (vzdálený přístup) – nejběžnější typ. Jednotlivý uživatel se připojuje k firemní síti z domova nebo z veřejné WiFi. Typické použití: home office, připojení k firemním sdíleným diskům.

- **Site-to-Site VPN** – propojuje dvě celé sítě navzájem, například pobočku firmy v Praze s centrálou v Brně. VPN je transparentní pro uživatele – nepotřebují žádný klient.

- **SSL/TLS VPN** – funguje přes webový prohlížeč (port 443), nevyžaduje instalaci speciálního klienta. Výhodou je průchodnost skrz firewally, protože HTTPS je téměř vždy povoleno.

#### Klíčové pojmy

- **Tunelování** je zabalení jednoho síťového paketu do druhého. Původní paket (i s hlavičkou) se stane datovou náplní nového paketu – proto může „cestovat" přes jinou síť, jako by byl v tunelu.
- **Split tunneling** – situace, kdy přes VPN jde jen firemní provoz a ostatní (Netflix, YouTube) jde přímo bez VPN. Šetří přenosové pásmo, ale snižuje ochranu soukromí.
- **Kill switch** – funkce VPN klienta, která při výpadku VPN připojení okamžitě zablokuje veškerý internetový provoz. Zabraňuje tomu, aby data unikla mimo tunel bez vědomí uživatele.
- **No-log politika** – seriózní VPN poskytovatelé neukládají záznamy o aktivitách uživatelů. Důležité pro oukromí.
- **DNS leak** – bezpečnostní chyba, kdy DNS dotazy (překlady doménových jmen) unikají mimo VPN tunel a jsou viditelné pro ISP nebo útočníka, i když samotný datový provoz je šifrovaný.