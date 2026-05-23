# 13 – Atributy třídy, modifikátory přístupu, vlastnosti

> **Maturitní otázka:** Atributy třídy, modifikátory přístupu k atributům, přístup k atributům pomocí vlastností tříd.

Viz také: [[12_Principy_OOP]] | [[14_Konstruktory]] | [[15_Metody]]

---

## Atribut třídy

**Atribut** (také pole / field) = proměnná definovaná přímo v těle třídy. Uchovává stav objektu.

```csharp
class Osoba {
    public string Jmeno;       // atribut
    private int vek;           // atribut (skrytý)
    protected string adresa;   // atribut (pro potomky)
}
```

### Druhy atributů

| Druh | Klíčové slovo | Popis |
|------|--------------|-------|
| Instanční | *(žádné)* | Každý objekt má vlastní kopii |
| Třídní (statický) | `static` | Sdílený všemi objekty, patří třídě |
| Konstantní | `const` | Neměnná hodnota, určena při překladu |
| Pouze pro čtení | `readonly` | Nastavitelný jen v konstruktoru |

```csharp
class Priklad {
    public int instancni;           // každý objekt má své
    public static int sdileny;      // všechny objekty sdílí
    public const double PI = 3.14;  // konstanta
    public readonly int id;         // nastavitelný jen v konstruktoru
}
```

---

## Modifikátory přístupu

Určují, odkud je možné atribut (nebo metodu) číst nebo měnit.

| Modifikátor | Dostupný v | Příklad použití |
|-------------|-----------|-----------------|
| `public` | Kdekoli | Veřejné API třídy |
| `private` | Jen ve třídě samotné | Interní data – základ zapouzdření |
| `protected` | Ve třídě + potomcích | Sdílení s dědici |
| `internal` | V rámci sestavení (assembly) | Moduly projektu |
| `protected internal` | Potomci + stejné sestavení | Kombinace |

```csharp
class Auto {
    public string Znacka;      // vidí všichni
    private int rokVyroby;     // vidí jen Auto
    protected int vykon;       // vidí Auto a jeho potomci
}
```

> 🔑 Pravidlo: atributy téměř vždy `private`, přístup přes **vlastnosti** nebo metody.

---

## Vlastnosti (Properties)

**Vlastnost** = řízený přístup k `private` atributu pomocí `get` a `set`.

```csharp
class Osoba {
    private int vek;  // skrytý atribut

    public int Vek {          // vlastnost
        get { return vek; }
        set {
            if (value >= 0) vek = value;  // validace!
        }
    }
}

Osoba o = new Osoba();
o.Vek = 25;       // volá set
int v = o.Vek;    // volá get
```

### Zkrácené zápisy

```csharp
// Auto-implementovaná vlastnost (get + set bez logiky)
public string Jmeno { get; set; }

// Pouze pro čtení (jen get)
public string Jmeno { get; private set; }

// Výrazová vlastnost (C# 6+)
public string CeleJmeno => $"{Jmeno} {Prijmeni}";
```

### Proč vlastnosti místo přímého přístupu?

| Přímý atribut (`public`) | Vlastnost (`get`/`set`) |
|--------------------------|------------------------|
| Žádná kontrola hodnoty | Validace při zápisu |
| Nelze sledovat změny | Lze přidat logiku (event, log) |
| Porušuje zapouzdření | Dodržuje zapouzdření |

---

## `static` atributy a vlastnosti

```csharp
class Pocitadlo {
    private static int pocet = 0;

    public Pocitadlo() { pocet++; }

    public static int ZjistiPocet() => pocet;
}

new Pocitadlo();
new Pocitadlo();
Console.WriteLine(Pocitadlo.ZjistiPocet()); // 2
```

> `static` = přistupuješ přes **název třídy**, ne přes objekt.

---

## `readonly` vs `const`

| | `const` | `readonly` |
|-|---------|-----------|
| Kdy se nastaví | Překlad | Konstruktor nebo deklarace |
| Může být `static` | Vždy static | Může být instanční |
| Typ hodnot | Primitivní typy | Libovolný typ |

```csharp
public const double PI = 3.14159;     // vždy stejné, překlad
public readonly DateTime Vznik;       // nastavím v konstruktoru, pak neměnné
```

---

## Rychlé opakování – otázky

- [ ] Co je atribut a čím se liší od lokální proměnné?
- [ ] Jaký je rozdíl mezi `public` a `private`?
- [ ] Co je vlastnost (property) a proč ji používáme místo přímého přístupu?
- [ ] Co dělá `static` u atributu?
- [ ] Jaký je rozdíl mezi `const` a `readonly`?
