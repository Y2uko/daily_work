**L3switch**
- FUNKCE
	- Směruje data mezi různými sítěmi tkzv. subnety 
	- Přeposílá data na základě IP adres 
- Switch pracující na síťové vrstvě (vrstva 3/ model OSI). Umí směrovat pakety jako router a spravovat VLAN.
- kombinuje funkce klasického switche (přepínání na úrovni datové vrstvy) s funkcemi routeru (směrování na úrovni síťové vrstvy).
- Rozumí IP adresám a dokáže směrovat provoz mezi různými sítěmi nebo VLANy. Přepínání přitom provádí hardwarově pomocí speciálních čipů (ASIC), což je mnohem rychlejší než softwarové směrování klasického routeru.
- Více vhodný než L2 pro větší a složitější sítě - vysoký objem interního provozu v LAN síti *(datová centra, firemní sítě)*

### Rozdíl mezi L2 a L3 switchem

|Vlastnost|L2 Switch|L3 Switch|
|---|---|---|
|**OSI vrstva**|Vrstva 2 (linková)|Vrstva 3 (síťová)|
|**Adresování**|MAC adresy|MAC adresy + IP adresy|
|**Směrování**|Ne|Ano (inter-VLAN routing)|
|**Tabulka**|MAC tabulka|MAC tabulka + směrovací tabulka|
|**VLANy**|Odděluje, ale nepropojuje|Odděluje i propojuje|
|**Protokoly**|Ethernet, STP|OSPF, RIP, EIGRP, BGP...|
|**Cena**|Nižší|Vyšší|
|**Výkon**|Velmi vysoký (HW)|Vysoký (HW, ASIC)|
|**Použití**|Přístupová vrstva sítě|Distribuční/páteřní vrstva|
