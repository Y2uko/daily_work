# 17 – C# a události tříd

> **Maturitní otázka:** C# a události tříd, přidání reference na obslužnou metodu, tvorba obslužných metod.

Viz také: [[16_WinForms]] | [[15_Metody]]

---

## Co je událost?

**Událost (event)** = mechanismus, který umožňuje objektu **oznámit ostatním**, že něco nastalo.

Příklady: klik na tlačítko, změna textu, načtení formuláře, pohyb myši.

---

## Klíčové pojmy

| Pojem | Popis |
|-------|-------|
| **Event (událost)** | Oznámení, že nastala akce |
| **Delegate** | Typ reprezentující referenci na metodu |
| **Obslužná metoda (handler)** | Metoda, která se zavolá při události |
| **Subscription (přihlášení)** | Registrace handleru k události pomocí `+=` |

---

## Delegate – základ událostí

**Delegate** = typ, který drží odkaz na metodu (nebo více metod).

```csharp
// Definice delegátu – metoda bez parametrů, nic nevrací
delegate void MojeAkce();

// Metoda odpovídající signatuře
void Pozdrav() { Console.WriteLine("Ahoj!"); }

// Přiřazení
MojeAkce akce = Pozdrav;
akce();   // zavolá Pozdrav()
```

---

## EventHandler – standardní delegát pro události

WinForms (a většina C# kódu) používá předdefinovaný delegát `EventHandler`:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
// sender = zdroj události (které tlačítko, …)
// e      = data o události
```

---

## Tvorba obslužné metody (event handler)

Obslužná metoda musí mít **signaturu odpovídající delegátu**.

```csharp
// Pro EventHandler:
private void button1_Click(object sender, EventArgs e) {
    MessageBox.Show("Kliknuto!");
}
```

**Konvence pojmenování:** `NázevPrvku_NázevUdálosti` → `button1_Click`

---

## Přidání reference – přihlášení k události

### Způsob 1: Designer (vizuálně ve Visual Studiu)

1. Klikni na prvek v návrháři
2. V okně Properties → záložka ⚡ Events
3. Dvakrát klikni na událost (např. `Click`) → VS vytvoří metodu automaticky

### Způsob 2: Kód – operátor `+=`

```csharp
// V konstruktoru nebo InitializeComponent
button1.Click += button1_Click;   // přidání reference

// Nebo anonymní metodou (lambda)
button1.Click += (sender, e) => {
    MessageBox.Show("Lambda handler!");
};
```

### Odhlášení od události – `–=`

```csharp
button1.Click -= button1_Click;   // odebrání reference
```

---

## Příklady běžných událostí WinForms

| Prvek | Událost | Kdy nastane |
|-------|---------|-------------|
| `Button` | `Click` | Klik myší nebo Enter |
| `TextBox` | `TextChanged` | Při každé změně textu |
| `TextBox` | `KeyPress` | Stisk klávesy |
| `Form` | `Load` | Načtení formuláře |
| `Form` | `FormClosing` | Před zavřením okna |
| `ListBox` | `SelectedIndexChanged` | Výběr jiné položky |
| `Timer` | `Tick` | Pravidelný interval |

---

## Kompletní příklad

```csharp
public partial class MainForm : Form {

    public MainForm() {
        InitializeComponent();

        // Přihlášení k události v kódu
        button1.Click += ZobrazPozdrav;
        textBox1.TextChanged += AktualizujNahled;
    }

    // Obslužná metoda pro Click
    private void ZobrazPozdrav(object sender, EventArgs e) {
        string jmeno = textBox1.Text;
        label1.Text = $"Ahoj, {jmeno}!";
    }

    // Obslužná metoda pro TextChanged
    private void AktualizujNahled(object sender, EventArgs e) {
        label2.Text = $"Zadáváš: {textBox1.Text}";
    }
}
```

---

## Vlastní události ve vlastní třídě

Lze definovat události i mimo WinForms.

```csharp
class Teploměr {
    public event EventHandler? PrekrocenoPrahU;   // definice události

    private int teplota;
    public int Teplota {
        get => teplota;
        set {
            teplota = value;
            if (teplota > 37) {
                PrekrocenoPrahU?.Invoke(this, EventArgs.Empty);  // vyvolání
            }
        }
    }
}

// Použití
Teploměr t = new Teploměr();
t.PrekrocenoPrahU += (s, e) => Console.WriteLine("Horečka!");
t.Teplota = 38;   // → Horečka!
```

---

## `EventArgs` s daty – `EventArgs<T>` nebo vlastní třída

```csharp
class TeplotaEventArgs : EventArgs {
    public int Hodnota { get; }
    public TeplotaEventArgs(int hodnota) { Hodnota = hodnota; }
}

// Delegát s vlastními daty
public event EventHandler<TeplotaEventArgs>? ZmenaTeplotY;

// Vyvolání
ZmenaTeplotY?.Invoke(this, new TeplotaEventArgs(teplota));

// Handler
t.ZmenaTeplotY += (s, e) => Console.WriteLine($"Teplota: {e.Hodnota}°C");
```

---

## Rychlé opakování – otázky

- [ ] Co je událost a jak funguje v C#?
- [ ] Co je delegate a jak se liší od metody?
- [ ] Jak přidáš obslužnou metodu k události tlačítka?
- [ ] Jaká je signatura standardního EventHandleru?
- [ ] Jak odhlásíš handler od události?
