# 18 – BlueJ a jednosměrný uzlový seznam

> **Maturitní otázka:** Vývojové prostředí BlueJ – tvorba tříd, vztahy mezi třídami, tvorba dokumentace, volání statických a nestatických metod, užití příkazového panelu. Jednosměrný uzlový seznam.

Viz také: [[12_Principy_OOP]] | [[15_Metody]]

---

## BlueJ – přehled

**BlueJ** je výukové vývojové prostředí pro Javu. Vizualizuje třídy a jejich vztahy přímo jako diagram.

### Základní prvky rozhraní

| Část | Popis |
|------|-------|
| **Diagram tříd** | Graficky zobrazuje třídy a vztahy |
| **Příkazový panel** | Interaktivní konzole – volání metod bez spuštění |
| **Editor** | Kód třídy |
| **Object Bench** | Plocha s vytvořenými instancemi |

---

## Tvorba tříd v BlueJ

1. `New Class…` → zadej název → zvol typ (Class / Abstract Class / Interface / Enum)
2. Třída se zobrazí jako rámeček v diagramu
3. Dvojklik → otevře editor kódu
4. Po úpravě: **Compile** (zkompiluj) – šedé šrafování = nezkompilovano

---

## Vztahy mezi třídami v diagramu

| Symbol | Vztah | Jak přidat |
|--------|-------|-----------|
| Šipka plná (→) | Používání (asociace) | Nakresli šipku z třídy A do B |
| Šipka prázdná (△) | Dědičnost (`extends`) | BlueJ detekuje automaticky z kódu |
| Tečkovaná šipka | Implementace (`implements`) | Automaticky z kódu |

---

## Volání metod v BlueJ

### Nestatické (instanční) metody

1. Pravý klik na třídu v diagramu → `new NázevTřídy(…)` → vznikne objekt na Object Bench
2. Pravý klik na objekt → vyber metodu → zadej parametry → potvrď

### Statické metody

1. Pravý klik přímo na **třídu** v diagramu (bez vytvoření instance)
2. Vyber statickou metodu ze seznamu

---

## Příkazový panel (Code Pad)

Interaktivní REPL – příkazy se provádějí okamžitě.

```java
// Vytvoření objektu
Auto a = new Auto("Škoda", 2020);

// Volání metody
a.getZnacka()        // vrátí "Škoda"

// Výpis
System.out.println(a.getRok())
```

> 💡 Příkazový panel je výborný na testování bez psaní `main` metody.

---

## Tvorba dokumentace (Javadoc)

BlueJ generuje HTML dokumentaci ze speciálních komentářů.

```java
/**
 * Třída reprezentující osobu.
 * @author Jana Novák
 * @version 1.0
 */
public class Osoba {

    /**
     * Vrátí celé jméno osoby.
     * @param titulem zda přidat titul
     * @return celé jméno jako String
     */
    public String getCeleJmeno(boolean titulem) {
        // ...
    }
}
```

**Klíčové tagy Javadoc:**

| Tag | Popis |
|-----|-------|
| `@author` | Autor třídy |
| `@version` | Verze |
| `@param nazev popis` | Popis parametru |
| `@return popis` | Popis návratové hodnoty |
| `@throws Typ popis` | Výjimka |

**Vygenerování:** Menu `Tools` → `Project Documentation`

---

## Jednosměrný uzlový seznam

### Princip

Lineární datová struktura tvořená **uzly**. Každý uzel obsahuje:
- **data** (hodnotu)
- **odkaz** na následující uzel

Poslední uzel odkazuje na `null`.

```
[Hlava] → [Uzel A] → [Uzel B] → [Uzel C] → null
```

### Implementace uzlu

```java
class Uzel {
    int data;
    Uzel dalsi;   // odkaz na následující

    public Uzel(int data) {
        this.data = data;
        this.dalsi = null;
    }
}
```

### Implementace seznamu

```java
class SeznamUzlu {
    private Uzel hlava;   // první uzel

    // Přidání na začátek – O(1)
    public void pridejNaZacatek(int hodnota) {
        Uzel novy = new Uzel(hodnota);
        novy.dalsi = hlava;
        hlava = novy;
    }

    // Přidání na konec – O(n)
    public void pridejNaKonec(int hodnota) {
        Uzel novy = new Uzel(hodnota);
        if (hlava == null) { hlava = novy; return; }
        Uzel aktualni = hlava;
        while (aktualni.dalsi != null) {
            aktualni = aktualni.dalsi;
        }
        aktualni.dalsi = novy;
    }

    // Výpis všech uzlů
    public void vypis() {
        Uzel aktualni = hlava;
        while (aktualni != null) {
            System.out.print(aktualni.data + " → ");
            aktualni = aktualni.dalsi;
        }
        System.out.println("null");
    }

    // Odebrání ze začátku – O(1)
    public void odeberZeZacatku() {
        if (hlava != null) hlava = hlava.dalsi;
    }

    // Vyhledání – O(n)
    public boolean obsahuje(int hodnota) {
        Uzel aktualni = hlava;
        while (aktualni != null) {
            if (aktualni.data == hodnota) return true;
            aktualni = aktualni.dalsi;
        }
        return false;
    }
}
```

### Použití

```java
SeznamUzlu seznam = new SeznamUzlu();
seznam.pridejNaKonec(10);
seznam.pridejNaKonec(20);
seznam.pridejNaKonec(30);
seznam.vypis();      // 10 → 20 → 30 → null
seznam.obsahuje(20); // true
```

### Složitosti operací

| Operace | Jednosměrný seznam | Pole |
|---------|-------------------|------|
| Přidání na začátek | O(1) | O(n) |
| Přidání na konec | O(n) | O(1) amort. |
| Vyhledání | O(n) | O(n) |
| Přístup na index | O(n) | O(1) |
| Odebrání ze začátku | O(1) | O(n) |

---

## Rychlé opakování – otázky

- [ ] Jak vytvoříš novou třídu v BlueJ?
- [ ] Jak zavoláš statickou metodu v BlueJ bez vytváření instance?
- [ ] K čemu slouží příkazový panel (Code Pad)?
- [ ] Jak se generuje dokumentace v BlueJ (Javadoc)?
- [ ] Z čeho se skládá uzel v jednosměrném seznamu?
- [ ] Proč je přidání na začátek O(1) a na konec O(n)?
