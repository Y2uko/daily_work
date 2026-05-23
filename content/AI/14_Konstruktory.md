# 14 – Konstruktor třídy

> **Maturitní otázka:** Konstruktor třídy, přetížené konstruktory, konstruktor s parametrem a bezparametrický.

Viz také: [[12_Principy_OOP]] | [[13_Atributy_a_modifikatory]] | [[15_Metody]]

---

## Co je konstruktor?

**Konstruktor** je speciální metoda, která se automaticky zavolá při vytváření objektu (`new`).

**Úkol konstruktoru:** inicializovat atributy objektu do výchozího stavu.

```csharp
class Auto {
    public string Znacka;
    public int Rok;

    // Konstruktor
    public Auto() {
        Znacka = "Neznámá";
        Rok = 2000;
    }
}

Auto a = new Auto();  // zavolá se konstruktor
```

### Pravidla konstruktoru

| Pravidlo | Popis |
|----------|-------|
| Název = název třídy | `Auto()` pro třídu `Auto` |
| Žádný návratový typ | Ani `void` se nepíše |
| Modifikátor | Obvykle `public` |
| Volání | Automaticky při `new` |

---

## Bezparametrický konstruktor

Konstruktor **bez parametrů** – nastaví výchozí hodnoty.

```csharp
class Osoba {
    public string Jmeno;
    public int Vek;

    public Osoba() {               // bezparametrický
        Jmeno = "Neznámý";
        Vek = 0;
    }
}

Osoba o = new Osoba();
Console.WriteLine(o.Jmeno);  // Neznámý
```

> 💡 Pokud žádný konstruktor nenapíšeš, C# automaticky vytvoří prázdný bezparametrický konstruktor.
> Jakmile napíšeš jakýkoli vlastní konstruktor, automatický **zmizí**.

---

## Konstruktor s parametrem

Parametry umožňují nastavit atributy hned při vytváření objektu.

```csharp
class Osoba {
    public string Jmeno;
    public int Vek;

    public Osoba(string jmeno, int vek) {   // s parametry
        Jmeno = jmeno;
        Vek = vek;
    }
}

Osoba o = new Osoba("Jana", 22);
Console.WriteLine(o.Jmeno);  // Jana
```

---

## Přetížené konstruktory (Overloading)

Třída může mít **více konstruktorů** – liší se počtem nebo typy parametrů.

```csharp
class Obdelnik {
    public double Sirka;
    public double Vyska;

    // Bezparametrický – čtverec 1×1
    public Obdelnik() {
        Sirka = 1;
        Vyska = 1;
    }

    // Čtverec – jedna strana
    public Obdelnik(double strana) {
        Sirka = strana;
        Vyska = strana;
    }

    // Plný – šířka i výška
    public Obdelnik(double sirka, double vyska) {
        Sirka = sirka;
        Vyska = vyska;
    }
}

Obdelnik a = new Obdelnik();         // 1 × 1
Obdelnik b = new Obdelnik(5);        // 5 × 5
Obdelnik c = new Obdelnik(3, 7);     // 3 × 7
```

---

## Volání jiného konstruktoru – `this(...)`

Aby se nekopírovalo, lze z jednoho konstruktoru volat druhý.

```csharp
class Osoba {
    public string Jmeno;
    public int Vek;
    public string Email;

    public Osoba(string jmeno, int vek) {
        Jmeno = jmeno;
        Vek = vek;
        Email = "neuveden@example.com";
    }

    public Osoba(string jmeno, int vek, string email)
        : this(jmeno, vek) {         // volá konstruktor výše
        Email = email;
    }
}
```

---

## Konstruktor v dědičnosti – `base(...)`

Potomek musí zavolat konstruktor rodiče pomocí `base`.

```csharp
class Zvire {
    public string Jmeno;
    public Zvire(string jmeno) { Jmeno = jmeno; }
}

class Pes : Zvire {
    public string Plemeno;

    public Pes(string jmeno, string plemeno)
        : base(jmeno) {              // volá konstruktor Zvíře
        Plemeno = plemeno;
    }
}

Pes p = new Pes("Rex", "Labrador");
```

---

## Destruktor (Finalizer)

Volaný při zániku objektu – uvolňuje prostředky.

```csharp
class Soubor {
    ~Soubor() {   // destruktor – tilda
        Console.WriteLine("Objekt zanikl.");
    }
}
```

> V C# s garbage collectorem se destruktory používají zřídka. Pro uvolňování zdrojů se preferuje rozhraní `IDisposable` s metodou `Dispose()`.

---

## Přehled – kdy který konstruktor?

| Situace | Typ konstruktoru |
|---------|-----------------|
| Výchozí stav, parametry neznáme | Bezparametrický |
| Chceme nastavit data hned při vytvoření | S parametry |
| Různé způsoby vytvoření objektu | Přetížené konstruktory |
| Nechceme opakovat kód | `this(...)` |
| Potomek potřebuje inicializovat rodiče | `base(...)` |

---

## Rychlé opakování – otázky

- [ ] Co je konstruktor a kdy se volá?
- [ ] Jaký je rozdíl mezi bezparametrickým a parametrickým konstruktorem?
- [ ] Co jsou přetížené konstruktory? Napiš příklad.
- [ ] K čemu slouží `this(...)` a `base(...)` v konstruktoru?
- [ ] Co se stane, pokud konstruktor vůbec nenapíšeš?
