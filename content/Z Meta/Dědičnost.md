#### 1. Rodičovská třída (Superclass): Vozidlo

Každé vozidlo má nějakou značku a umí troubit. To je náš základ.

Python

```
class Vozidlo:
    def __init__(self, znacka):
        self.znacka = znacka

    def zatroubit(self):
        print("Tút tút!")
```

#### 2. Odvozená třída (Subclass): Auto

Třída `Auto` „dědí“ od `Vozidla`. Získá automaticky značku i schopnost troubit, ale přidáme jí něco navíc – počet dveří.

Python

```
class Auto(Vozidlo): # V závorce říkáme, z čeho dědíme
    def __init__(self, znacka, pocet_dveri):
        # Zavoláme konstruktor rodiče, aby nastavil značku
        super().__init__(znacka) 
        self.pocet_dveri = pocet_dveri

    def info(self):
        print(f"Tohle je {self.znacka} a má {self.pocet_dveri} dveře.")
```

#### 3. Jak to vypadá v akci?

Když vytvoříme objekt typu `Auto`, můžeme volat metody z obou tříd.

Python

```
moje_auto = Auto("Škoda", 5)

moje_auto.zatroubit() # Metoda zděděná od Vozidla
moje_auto.info()      # Vlastní metoda třídy Auto
```

**Polymorfismus** (mnohotvárnost)

