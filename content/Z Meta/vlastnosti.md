- je v podstatě **„chytrý“ nebo „převlečený“ atribut**.
- Navenek se chová jako obyčejná proměnná (atribut), do které můžete ukládat data nebo z ní číst. Uvnitř ní jsou ale schované **metody (funkce)**, které kontrolují, co se s těmi daty děje.
- Vlastnost vznikla proto, aby chránila data objektu před neplatnými hodnotami. Skládá se ze dvou částí:
	1. **Getter** (čtení): Spustí se automaticky, když chcete hodnotu zjistit. Možná ji cestou upraví nebo zformátuje.
	2. **Setter** (zápis): Spustí se automaticky, když chcete hodnotu změnit. Zkontroluje, zda je hodnota validní.