# 20 – Návrhové vzory: Interface, Servant, Generické třídy, Messenger

> **Maturitní otázka:** Návrhové vzory – Interface, Servant, Generické třídy, Messenger.

Viz také: [[19_Vzory_Singleton_Utility_Enum]] | [[12_Principy_OOP]]

---

## 1. Interface (rozhraní) jako vzor

### Co je interface?

**Interface** = čistý kontrakt – definuje, **co** třída musí umět, ale ne **jak** to udělá.

```csharp
interface IUlozitelny {
    void Uloz();
    void Nacti();
}

interface ITiskovatelny {
    void Tiskni();
}
```

### Implementace

```csharp
class Dokument : IUlozitelny, ITiskovatelny {   // třída může implementovat více interface!
    public string Obsah;

    public void Uloz()   { File.WriteAllText("soubor.txt", Obsah); }
    public void Nacti()  { Obsah = File.ReadAllText("soubor.txt"); }
    public void Tiskni() { Console.WriteLine(Obsah); }
}
```

### Interface vs Abstraktní třída

| | Interface | Abstraktní třída |
|--|-----------|-----------------|
| Implementace | Žádná (jen C# 8+ default) | Může mít |
| Dědičnost | Lze implementovat **více** | Jen jedna |
| Konstruktor | Ne | Ano |
| Kdy použít | Kontrakt chování | Sdílení kódu + kontrakt |

### Interface jako vzor v praxi

```csharp
interface IPorovnatelny {
    int PorovnejS(object jiny);
}

// Jakákoli třída ho může implementovat
class Produkt : IPorovnatelny {
    public decimal Cena;
    public int PorovnejS(object jiny) {
        var p = (Produkt)jiny;
        return this.Cena.CompareTo(p.Cena);
    }
}
```

---

## 2. Servant (sluha)

### Problém

Více různých tříd potřebuje **stejnou funkcionalitu**, ale nemůžeme (nebo nechceme) ji přidat přes dědičnost (třídy mají různé rodiče).

### Řešení – Servant

Servant = třída, která poskytuje funkcionalitu **ostatním třídám** (slouží jim). Pracuje s objekty přes společné rozhraní.

```csharp
// Rozhraní, které musí třídy implementovat
interface IPresuvatelny {
    int X { get; set; }
    int Y { get; set; }
}

// Servant – třída poskytující přesun
class Presunovy {
    public void Presun(IPresuvatelny objekt, int dx, int dy) {
        objekt.X += dx;
        objekt.Y += dy;
    }

    public void NastavPozici(IPresuvatelny objekt, int x, int y) {
        objekt.X = x;
        objekt.Y = y;
    }
}

// Různé třídy, které Servant obsluhuje
class Obdelnik : IPresuvatelny {
    public int X { get; set; }
    public int Y { get; set; }
    public int Sirka, Vyska;
}

class Ikona : IPresuvatelny {
    public int X { get; set; }
    public int Y { get; set; }
    public string Obrazek;
}

// Použití
Presunovy servant = new Presunovy();
Obdelnik rect = new Obdelnik { X = 0, Y = 0 };
Ikona ikona = new Ikona { X = 10, Y = 10 };

servant.Presun(rect, 5, 5);      // Obdelnik přesunut
servant.Presun(ikona, -5, 0);    // Ikona přesunuta
```

### Klíčové znaky

| Vlastnost | Popis |
|-----------|-------|
| Servant třída | Poskytuje operace ostatním |
| Interface | Definuje kontrakt objektů, které Servant obsluhuje |
| Výhoda | Žádná duplicita kódu, nezávislost na hierarchii |
| Příklady | Renderer (kreslí různé tvary), Validator, Sorter |

---

## 3. Generické třídy (Generics)

### Problém

Chci napsat třídu nebo metodu, která funguje s **libovolným typem** – bez opakování kódu pro každý typ.

### Řešení – Generika

```csharp
// Generická třída – T je typový parametr
class Zasobnik<T> {
    private List<T> polozky = new List<T>();

    public void Vloz(T polozka) { polozky.Add(polozka); }
    public T Vyndej() {
        if (polozky.Count == 0) throw new InvalidOperationException("Zásobník je prázdný.");
        T posledni = polozky[polozky.Count - 1];
        polozky.RemoveAt(polozky.Count - 1);
        return posledni;
    }
    public int Pocet => polozky.Count;
}

// Použití se stringy
Zasobnik<string> textovy = new Zasobnik<string>();
textovy.Vloz("prvni");
textovy.Vloz("druhy");
string s = textovy.Vyndej();  // "druhy"

// Stejná třída s čísly – žádný nový kód!
Zasobnik<int> ciselny = new Zasobnik<int>();
ciselny.Vloz(42);
int i = ciselny.Vyndej();  // 42
```

### Generická metoda

```csharp
class Nastroje {
    public static T[] Otoc<T>(T[] pole) {
        Array.Reverse(pole);
        return pole;
    }

    public static T VezmiPrvni<T>(List<T> seznam) {
        return seznam[0];
    }
}

int[]    cisla   = Nastroje.Otoc(new int[]    { 1, 2, 3 });
string[] retezce = Nastroje.Otoc(new string[] { "a", "b" });
```

### Omezení typového parametru (`where`)

```csharp
// T musí implementovat IComparable (musí být porovnatelný)
class MinMax<T> where T : IComparable<T> {
    public T Minimum(T a, T b) => a.CompareTo(b) <= 0 ? a : b;
}

MinMax<int>    mm1 = new MinMax<int>();
MinMax<double> mm2 = new MinMax<double>();
```

| Omezení | Popis |
|---------|-------|
| `where T : class` | T musí být referenční typ |
| `where T : struct` | T musí být hodnotový typ |
| `where T : new()` | T musí mít bezparametrický konstruktor |
| `where T : IInterface` | T musí implementovat rozhraní |
| `where T : BaseClass` | T musí dědit od třídy |

---

## 4. Messenger (Mediátor / Message Bus)

### Problém

Objekty spolu potřebují komunikovat, ale **nechceme přímé závislosti** mezi nimi – volné propojení.

### Řešení – Messenger

Messenger = centrální zprostředkovatel zpráv. Objekty posílají zprávy do Messengeru, ostatní se přihlásí k odběru.

```csharp
// Zpráva
class ZpravaNakladu {
    public decimal Castka { get; }
    public ZpravaNakladu(decimal castka) { Castka = castka; }
}

// Messenger – jednoduchá implementace
class Messenger {
    private static Messenger? instance;
    public static Messenger Instance => instance ??= new Messenger();

    private Dictionary<Type, List<Action<object>>> odberate
        = new Dictionary<Type, List<Action<object>>>();

    public void Prihlas<T>(Action<T> handler) {
        var typ = typeof(T);
        if (!odberate.ContainsKey(typ)) odberate[typ] = new List<Action<object>>();
        odberate[typ].Add(msg => handler((T)msg));
    }

    public void Posli<T>(T zprava) {
        if (odberate.TryGetValue(typeof(T), out var handlery))
            foreach (var h in handlery) h(zprava!);
    }
}

// Použití
// Modul A – přihlásí se k odběru
Messenger.Instance.Prihlas<ZpravaNakladu>(zprava => {
    Console.WriteLine($"Přijata zpráva o nákladu: {zprava.Castka} Kč");
});

// Modul B – odešle zprávu (nezná modul A!)
Messenger.Instance.Posli(new ZpravaNakladu(1500));
// → Přijata zpráva o nákladu: 1500 Kč
```

### Klíčové znaky

| Vlastnost | Popis |
|-----------|-------|
| Volné propojení | Odesílatel nezná příjemce |
| Centrální bod | Vše prochází Messengerem |
| Rozšiřitelnost | Nový odběratel bez změny odesílatele |
| Příklady | Event Bus, MediatR v .NET, Redux v JS |

---

## Přehled vzorů – srovnání

| Vzor | Problém | Klíčový prvek |
|------|---------|--------------|
| **Interface** | Kontrakt bez implementace | `interface` + `implements` |
| **Servant** | Sdílená funkce pro různé třídy bez dědičnosti | Servant třída + společné rozhraní |
| **Generika** | Jeden kód pro různé typy | `<T>` typový parametr |
| **Messenger** | Komunikace bez přímých závislostí | Centrální zprostředkovatel zpráv |

---

## Rychlé opakování – otázky

- [ ] Jaký je rozdíl mezi interface a abstraktní třídou?
- [ ] Jak funguje vzor Servant? Napiš příklad.
- [ ] Co jsou generické třídy a proč jsou užitečné?
- [ ] Co dělá `where T : IComparable<T>`?
- [ ] Jak funguje Messenger? Jakou výhodu má oproti přímému volání?
