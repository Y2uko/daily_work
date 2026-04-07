## Co je firewall

Firewall je bezpečnostní systém, který monitoruje a řídí síťový provoz na základě předem definovaných pravidel. Funguje jako „brána" mezi důvěryhodnou sítí (např. firemní LAN) a nedůvěryhodnou sítí (internet). Může být hardwarový, softwarový nebo kombinace obojího.---

## Typy firewallů

**Paketový filtr (Packet Filter)** je nejstarší a nejjednodušší typ. Kontroluje každý paket samostatně podle zdrojové/cílové IP adresy a portu. Nezná kontext spojení – neví, jestli paket patří k existující komunikaci, nebo jde o nový útok. Používá se v routerech.

**Stavový firewall (Stateful Inspection)** si pamatuje stav spojení – ví, která komunikace byla zahájena zevnitř sítě, a povolí odpovědi. Výrazně bezpečnější než paketový filtr. Toto je dnes standardní typ.

**Aplikační brána / Proxy firewall** pracuje na aplikační vrstvě (Layer 7). Rozumí konkrétním protokolům jako HTTP, FTP nebo DNS a dokáže blokovat nebezpečný obsah i při jinak povoleném portu. Je pomalejší, ale nejdůkladnější.

**Next-Generation Firewall (NGFW)** kombinuje stavovou kontrolu s inspekcí aplikačního provozu, detekcí průniků (IDS/IPS), filtrováním URL a antivirem. Moderní firemní standard.

---

## Jak fungují pravidla (ACL)

Firewall prochází pravidla shora dolů a první shoda rozhoduje. Každé pravidlo říká: _pokud paket odpovídá podmínkám → povol / zamítni_. Na konci bývá implicitní pravidlo **deny all** – co není výslovně povoleno, je zakázáno.

Příklad pravidel:

|Pravidlo|Zdroj|Cíl|Port|Akce|
|---|---|---|---|---|
|1|Jakýkoli|192.168.1.10|80, 443|Povoleno|
|2|10.0.0.5|Jakýkoli|Jakýkoli|Blokováno|
|3|Jakýkoli|Jakýkoli|Jakýkoli|Blokováno|

---

## DMZ – demilitarizovaná zóna

DMZ je oddělená síťová oblast mezi internetem a interní sítí. Umísťují se do ní servery, které musí být dostupné z internetu (webový server, mailový server, DNS). Pokud útočník kompromituje server v DMZ, nedostane se přímo do interní sítě – firewall ho zastaví.

---

## Klíčové pojmy pro maturitu

**Whitelist vs. blacklist** – whitelist povoluje pouze vyjmenovaný provoz (bezpečnější), blacklist blokuje konkrétní věci a vše ostatní pouští.

**IDS/IPS** – Intrusion Detection System pouze detekuje útoky a hlásí je, Intrusion Prevention System je aktivně blokuje. NGFW je většinou obsahuje.

**NAT (Network Address Translation)** – firewall/router překládá privátní IP adresy na veřejnou. Vedlejší efekt je skrytí vnitřní topologie sítě před útočníkem.

**Port** – číslo 0–65535 identifikující službu. Důležité porty: 80 (HTTP), 443 (HTTPS), 22 (SSH), 25 (SMTP), 53 (DNS). Firewall může blokovat konkrétní porty.

**Osobní firewall** – softwarový firewall přímo v OS (Windows Defender Firewall, iptables na Linuxu). Chrání jednotlivý počítač, ne celou síť.

---

