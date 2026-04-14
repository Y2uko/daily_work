**Multitasking**
- Zpracování více úloh na jednou
- Operační systém přiděluje procesorový čas běžícím procesům (přepíná mezi nimi)
- Jedno jádro (vlákno) dokáže zpracovávat v danou chvíli pouze jednu operaci.
- Přerušení (anglicky interrupt) je metoda pro asynchronní obsluhu událostí, kdy procesor přeruší vykonávání sledu instrukcí, vykoná obsluhu přerušení, a pak pokračuje v předchozí činnosti
- Dělení:
	- **Kooperativní multitasking** - Operační systém respektuje požadavek aplikace, řízení si navzájem předávají jednotlivé procesy, je velmi zranitelný
	- **Preemptivní multitasking** - Zdroje přiděluje operační systém, pád jednoho procesu neznamená ukončení práce celého systému

