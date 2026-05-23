# 19 – Návrhové vzory: Utility, Singleton, Tovární metoda, Enum

> **Maturitní otázka:** Návrhové vzory – Utility, Singleton + tovární metoda, Enum.

Viz také: [[20_Vzory_Interface_Servant_Generika]] | [[12_Principy_OOP]]

---

## Co je návrhový vzor?

**Návrhový vzor (Design Pattern)** = osvědčené, opakovaně použitelné řešení běžného problému v návrhu softwaru. Není to kód – je to **recept/šablona**.

---

## 1. Utility (Helper třída)

### Problém

Potřebuji skupinu pomocných metod, které nesouvisí s žádným konkrétním objektem (matematické funkce, formátování, konverze).

### Řešení – Utility třída

- Třída obsahuje **pouze statické metody**
- **Nelze vytvořit instanci** (konstruktor je `private`)
- Přístup přes název třídy

```csharp
public static class MathHelper {
    // Pouze statické metody
    public static double Zaokrouhli(double cislo, int desetinna) {
        return Math.Round(cislo, desetinna);
    }

    public static bool JePrvocislo(int n) {
        if (n < 2) return false;
        for (int i = 2; i <= Math.Sqrt(n); i++)
            if (n % i == 0) return false;
        return true;
    }

    public static int[] Seradit(int[] pole) {
        Array.Sort(pole);
        return pole;
    }
}

// Použití – bez new, přímo přes název třídy
double vysledek = MathHelper.Zaokrouhli(3.14159, 2);  // 3.14
bool je = MathHelper.JePrvocislo(17);                 // true
```

### Klíčové znaky

| Vlastnost | Popis |
|-----------|-------|
| `static class` | V C# klíčové slovo zabraňuje instanciaci |
| Všechny metody `static` | Voláme přes třídu, ne objekt |
| Bez stavu | Nedrží žádná data (atributy) |
| Příklady | `Math`, `Console`, `File`, `Convert` v .NET |

---

## 2. Singleton

### Problém

Potřebuji mít v celé aplikaci **právě jednu instanci** určité třídy (logger, konfigurace, připojení k DB).

### Řešení – Singleton

```csharp
public class Logger {
    // Jediná instance – statická, private
    private static Logger? instance;

    // Privátní konstruktor – zabrání new Logger()
    private Logger() { }

    // Přístupová metoda – vrátí vždy tu samou instanci
    public static Logger ZjistiInstanci() {
        if (instance == null) {
            instance = new Logger();
        }
        return instance;
    }

    public void Log(string zprava) {
        Console.WriteLine($"[LOG] {zprava}");
    }
}

// Použití
Logger log1 = Logger.ZjistiInstanci();
Logger log2 = Logger.ZjistiInstanci();
Console.WriteLine(log1 == log2);  // true – je to stejný objekt!
log1.Log("Spuštění aplikace");
```

### Thread-safe Singleton (bezpečný pro vlákna)

```csharp
public class Konfigurace {
    private static readonly Konfigurace instance = new Konfigurace();
    private Konfigurace() { }
    public static Konfigurace Instance => instance;
    // vlastnosti...
}
```

### Klíčové znaky

| Vlastnost | Popis |
|-----------|-------|
| `private static` instance | Jedna pro celou aplikaci |
| `private` konstruktor | Nelze vytvořit zvenčí pomocí `new` |
| `public static` přístupová metoda | Vrátí nebo vytvoří instanci |
| Příklady | Logger, ConfigManager, ConnectionPool |

---

## 3. Singleton + Tovární metoda (Factory Method)

### Problém

Chci skrýt, jakého konkrétního potomka vracím – rozhodnutí o typu přenechám metodě.

### Řešení

Tovární metoda = statická metoda, která **vytváří a vrací objekty** (místo konstruktoru). Singleton ji může využít pro vytváření různých potomků.

```csharp
abstract class Platba {
    public abstract void Zpracuj(decimal castka);

    // Tovární metoda – rozhodne, který typ vrátí
    public static Platba Vytvor(string typ) {
        return typ switch {
            "karta"  => new KartovaPlatba(),
            "paypal" => new PayPalPlatba(),
            "hotovost" => new HotovostniPlatba(),
            _ => throw new ArgumentException("Neznámý typ platby")
        };
    }
}

class KartovaPlatba : Platba {
    public override void Zpracuj(decimal castka) {
        Console.WriteLine($"Platím kartou: {castka} Kč");
    }
}

class PayPalPlatba : Platba {
    public override void Zpracuj(decimal castka) {
        Console.WriteLine($"Platím přes PayPal: {castka} Kč");
    }
}

// Použití – neznáme konkrétní typ, továrna rozhodne
Platba p = Platba.Vytvor("karta");
p.Zpracuj(500);   // Platím kartou: 500 Kč
```

### Klíčové znaky

| Vlastnost | Popis |
|-----------|-------|
| Statická metoda | Nahrazuje konstruktor |
| Vrací abstraktní typ | Skrývá konkrétní implementaci |
| Polymorfismus | Různé potomky stejného rodiče |
| Příklady | `DateTime.Parse()`, `DbConnection.Create()` |

---

## 4. Enum (výčtový typ)

### Problém

Potřebuji proměnnou, která může nabývat jen pevně daných hodnot (dny, barvy, stavy).

### Řešení – Enum

```csharp
// Definice
enum DenTydne {
    Pondeli,
    Utery,
    Streda,
    Ctvrtek,
    Patek,
    Sobota,
    Nedele
}

// Použití
DenTydne dnes = DenTydne.Streda;

if (dnes == DenTydne.Sobota || dnes == DenTydne.Nedele) {
    Console.WriteLine("Víkend!");
}

// Switch
switch (dnes) {
    case DenTydne.Pondeli: Console.WriteLine("Začátek týdne"); break;
    case DenTydne.Patek:   Console.WriteLine("Páteček!"); break;
}
```

### Enum s hodnotami

```csharp
enum StavObjednavky {
    Prijata    = 1,
    Zpracovana = 2,
    Odeslana   = 3,
    Dorucena   = 4,
    Zrusena    = 99
}

StavObjednavky stav = StavObjednavky.Odeslana;
int cislo = (int)stav;          // 3 – přetypování na číslo
string nazev = stav.ToString(); // "Odeslana"

// Ze stringu / čísla
StavObjednavky s = (StavObjednavky)Enum.Parse(typeof(StavObjednavky), "Prijata");
```

### Enum jako návrhový vzor

Enum jako vzor = nahrazení nebezpečných „magic numbers" nebo stringů pojmenovanými konstantami.

```csharp
// Špatně – magic numbers
if (stav == 3) { /* co je 3? */ }

// Správně – enum
if (stav == StavObjednavky.Odeslana) { /* jasné! */ }
```

---

## Přehled vzorů

| Vzor | Problém | Řešení |
|------|---------|--------|
| **Utility** | Pomocné statické metody | `static class` bez instance |
| **Singleton** | Jedna instance v celé appce | `private` konstruktor + static instance |
| **Factory Method** | Skrytí konkrétního typu při vytváření | Statická metoda místo `new` |
| **Enum** | Pevná množina hodnot | Výčtový typ místo čísel/stringů |

---

## Rychlé opakování – otázky

- [ ] Co je Utility třída a jak zavoláš její metodu?
- [ ] Jak je implementován Singleton? Proč je konstruktor `private`?
- [ ] Co dělá tovární metoda a jakou výhodu má oproti `new`?
- [ ] K čemu slouží Enum? Napiš příklad definice a použití.
- [ ] Jak přetypuješ hodnotu Enum na číslo a zpět?
