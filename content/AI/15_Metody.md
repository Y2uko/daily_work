# 15 – Metody tříd

> **Maturitní otázka:** Metody tříd – návratový typ, parametry, modifikátory přístupu.

Viz také: [[13_Atributy_a_modifikatory]] | [[14_Konstruktory]] | [[12_Principy_OOP]]

---

## Co je metoda?

**Metoda** = pojmenovaný blok kódu definovaný uvnitř třídy. Popisuje **chování** objektu.

```csharp
class Auto {
    public void Zatroub() {          // metoda
        Console.WriteLine("Tůůůt!");
    }
}
```

### Základní syntaxe

```
[modifikátor] [návratový_typ] NázevMetody([parametry]) {
    // tělo metody
    return hodnota;  // pokud není void
}
```

---

## Návratový typ

Říká, **co metoda vrátí** po svém dokončení.

| Typ | Popis | Příklad |
|-----|-------|---------|
| `void` | Nic nevrací | `void Pozdrav()` |
| `int`, `double`, … | Vrátí číslo | `int Secti(int a, int b)` |
| `string` | Vrátí text | `string ZjistiJmeno()` |
| `bool` | Vrátí true/false | `bool JePlnoletý()` |
| Třída/objekt | Vrátí vlastní typ | `Auto VytvorAuto()` |

```csharp
class Kalkulacka {
    public int Secti(int a, int b) {
        return a + b;       // vrací int
    }

    public void Vypis(string text) {
        Console.WriteLine(text);  // nic nevrací
    }

    public bool JeKladne(int cislo) {
        return cislo > 0;   // vrací bool
    }
}
```

---

## Parametry metody

Parametry = vstupní data, se kterými metoda pracuje.

```csharp
// Žádné parametry
public void Pozdrav() { Console.WriteLine("Ahoj!"); }

// Jeden parametr
public void PozdravOsobu(string jmeno) { Console.WriteLine($"Ahoj, {jmeno}!"); }

// Více parametrů
public double Obsah(double sirka, double vyska) { return sirka * vyska; }
```

### Výchozí hodnoty parametrů

```csharp
public void Pozdrav(string jmeno = "světe") {
    Console.WriteLine($"Ahoj, {jmeno}!");
}

Pozdrav();           // Ahoj, světe!
Pozdrav("Tomáši");   // Ahoj, Tomáši!
```

### Předávání hodnotou vs. odkazem

| Způsob | Klíčové slovo | Efekt |
|--------|--------------|-------|
| Hodnotou (výchozí) | *(nic)* | Metoda dostane kopii – originál se nemění |
| Odkazem | `ref` | Metoda pracuje s originálem |
| Výstupní parametr | `out` | Metoda *vrátí* hodnotu přes parametr |

```csharp
void Zdvoj(ref int cislo) { cislo *= 2; }

int x = 5;
Zdvoj(ref x);
Console.WriteLine(x);  // 10
```

---

## Modifikátory přístupu u metod

Stejné jako u atributů – určují, kdo smí metodu volat.

| Modifikátor | Kdo může volat |
|-------------|---------------|
| `public` | Kdokoli |
| `private` | Jen třída sama |
| `protected` | Třída + potomci |
| `internal` | Stejné sestavení |

```csharp
class Ucet {
    private decimal zustatek;

    public void Vloz(decimal castka) { zustatek += castka; }     // veřejná
    private void Zaloguj(string zprava) { /* ... */ }            // interní pomocná
}
```

---

## Statické metody

- Patří třídě, ne instanci
- Volání přes název třídy
- Nemohou přistupovat k instančním atributům

```csharp
class Matematika {
    public static double Mocnina(double zaklad, double exponent) {
        return Math.Pow(zaklad, exponent);
    }
}

double vysledek = Matematika.Mocnina(2, 8);  // 256
```

---

## Přetížení metod (Overloading)

Více metod se **stejným názvem**, ale **různými parametry**.

```csharp
class Tiskarna {
    public void Tiskni(string text) { Console.WriteLine(text); }
    public void Tiskni(int cislo)   { Console.WriteLine(cislo); }
    public void Tiskni(string text, int pocet) {
        for (int i = 0; i < pocet; i++) Console.WriteLine(text);
    }
}
```

> Kompilátor rozliší, která metoda se zavolá, podle **počtu a typů argumentů**.

---

## Přepsání metod (Overriding) – polymorfismus

Potomek přepíše metodu rodiče – klíčová slova `virtual` + `override`.

```csharp
class Tvar {
    public virtual double Obsah() { return 0; }
}

class Kruh : Tvar {
    public double Polomer;
    public override double Obsah() { return Math.PI * Polomer * Polomer; }
}

class Obdelnik : Tvar {
    public double Sirka, Vyska;
    public override double Obsah() { return Sirka * Vyska; }
}
```

---

## Výrazové metody (Expression-bodied)

Zkrácený zápis pro jednoduché metody.

```csharp
// Klasický zápis
public int Secti(int a, int b) { return a + b; }

// Výrazový zápis (C# 6+)
public int Secti(int a, int b) => a + b;
```

---

## Přehled – druhy metod

| Druh | Klíčové slovo | Popis |
|------|--------------|-------|
| Instanční | *(nic)* | Pracuje s daty objektu |
| Statická | `static` | Patří třídě, bez objektu |
| Abstraktní | `abstract` | Bez těla, potomek musí implementovat |
| Virtuální | `virtual` | Může být přepsána potomkem |
| Přepsaná | `override` | Potomek přepsal virtuální metodu |
| Zapečetěná | `sealed override` | Potomek ji přepsal, ale další potomci už ne |

---

## Rychlé opakování – otázky

- [ ] Co je návratový typ metody? Co je `void`?
- [ ] Jak předáme parametr odkazem (`ref`)?
- [ ] Jaký je rozdíl mezi přetížením a přepsáním metody?
- [ ] Co je statická metoda a jak ji voláme?
- [ ] K čemu slouží `virtual` a `override`?
