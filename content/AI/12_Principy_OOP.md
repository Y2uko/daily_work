# 12 – Principy OOP

> **Maturitní otázka:** Principy OOP – třída, objekt, skládání, dědění, zapouzdření, delegování a polymorfismus.

Viz také: [[13_Atributy_a_modifikatory]] | [[14_Konstruktory]] | [[15_Metody]]

---

## Co je OOP?

**Objektově orientované programování (OOP)** je programovací paradigma – způsob myšlení a organizace kódu. Program je tvořen objekty, které spolu komunikují.

Místo psaní dlouhého **procedurálního** kódu „shora dolů“ si ==svět aplikace rozdělíme na logické celky==, které spolu komunikují, uchovávají si svá data a vykonávají specifické operace.

Je to způsob, jakým v kódu odrážíme realitu

---

## Třída a Objekt

| Pojem          | Definice                                                          |
| -------------- | ----------------------------------------------------------------- |
| **[[Třída]]**  | Šablona (blueprint) – popis, jak budou objekty vypadat a co umějí |
| **[[Objekt]]** | Konkrétní instance třídy v paměti, vzniklá pomocí `new`           |

```csharp
// Třída = šablona
class Auto {
    public string Barva;
    public void Jeď() { Console.WriteLine("Jedu!"); }
}

// Objekt = konkrétní výskyt
Auto mojeAuto = new Auto();
mojeAuto.Barva = "červená";
mojeAuto.Jeď();
```

> 💡 Z jedné třídy lze vytvořit libovolný počet objektů – každý má vlastní data.

---

## 4 pilíře OOP

### 1. Zapouzdření (Encapsulation)

- Skrytí vnitřní implementace před okolím
	-  objekt by měl skrývat svou vnitřní strukturu a vystavovat navenek jen to, co je nezbytné.
- Data jsou přístupná jen přes definované rozhraní (metody, vlastnosti)
- zamezuje nechtěným změnám dat zvenčí – s atributy objektu nepracujeme přímo, ale přes metody (`gettery` a `settery`)
- Realizováno pomocí **modifikátorů přístupu** 
	- `private` viditelné pouze uvnitř dané třídy
	- `public` viditelné kdekoli mimo třídu
	- `Protected` viditelné v rámci třídy a jejích potomků
	- `Internal` viditelné pouze v rámci aktuálního **Assembly** (souboru)

```csharp
class BankovniUcet {
    private decimal zustatek;  // skryté

    public void Vloz(decimal castka) {
        if (castka > 0) zustatek += castka;  // kontrolovaný přístup
    }
    public decimal ZjistiZustatek() => zustatek;
}
```

> 🔑 Zapouzdření = `private` atributy + `public` metody pro přístup.

---

### 2. Dědičnost (Inheritance)

- Umožňuje vytvářet nové třídy na základě již existujících. Nová třída (potomek) přebírá **[[atributy]]**, **[[vlastnosti]]** a **[[metody]]** rodičovské třídy.
- usnadňuje znovu použitelnost kódu a zpřehledňuje strukturu
- Vztah **„je"** (is-a): `Pes` je `Zvíře`
- Klíčové slovo: `: NázevRodiče` v C#

```csharp
class Zvire {
    public string Jmeno;
    public void Dychej() { Console.WriteLine("Dýchám."); }
}

class Pes : Zvire {          // Pes dědí od Zvíře
    public void Stekej() { Console.WriteLine("Haf!"); }
}

Pes rex = new Pes();
rex.Dychej();   // zděděná metoda
rex.Stekej();   // vlastní metoda
```

> ⚠️ C# podporuje jen **jednonásobnou dědičnost** (jeden přímý rodič).

---

### 3. Polymorfismus

- „Mnoho forem" – stejné volání, různé chování
-  zajišťuje, že objekty různých tříd mohou reagovat na stejný podnět (volání metody) různým způsobem.
- Rodičovský typ odkazuje na různé potomky

```csharp
class Tvar {
    public virtual void Nakresli() { Console.WriteLine("Tvar"); }
}
class Kruh : Tvar {
    public override void Nakresli() { Console.WriteLine("Kruh ○"); }
}
class Ctverec : Tvar {
    public override void Nakresli() { Console.WriteLine("Čtverec □"); }
}

Tvar[] tvary = { new Kruh(), new Ctverec() };
foreach (var t in tvary) t.Nakresli();
// Kruh ○
// Čtverec □
```

**Druhy polymorfismu:**

| Druh                    | Kdy          | Klíčové slovo                                                                                                                        |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Přetížení (overloading) | Překlad      | Třída obsahuje více metod se stejným názvem, ale různými parametry. Umožňuje jednomu objektu volat jednu metodu s různými parametry. |
| Přepsání (overriding)   | Běh programu | Potomek může změnit implementaci metody, kterou zdědil od rodiče, pomocí klíčového slova override.                                   |

---

### 4. Abstrakce

- Zobrazení jen podstatného, skrytí detailů
- Realizováno přes **abstraktní třídy** nebo **rozhraní (interface)**

```csharp
abstract class Platba {
    public abstract void Zpracuj();  // bez implementace
}
class KartovaPlatba : Platba {
    public override void Zpracuj() { Console.WriteLine("Platím kartou."); }
}
```

---

## Vztahy mezi třídami

### Skládání (Composition) – „má" (has-a)

Objekt **vlastní** jiný objekt – bez vlastníka zanikne i část.

```csharp
class Motor {
    public int Vykon;
}
class Auto {
    private Motor motor = new Motor();  // Auto vlastní Motor
}
```

> 💡 Motto: *„Preferuj skládání před dědičností."* – flexibilnější kód.

---

### Agregace – slabší forma skládání

Objekt **odkazuje** na jiný, ale nevlastní ho – část může existovat samostatně.

```csharp
class Student { public string Jmeno; }
class Trida {
    public List<Student> Studenti;  // studenti existují i bez třídy
}
```

---

### Delegování (Delegation)

Objekt **přeposílá** volání metody jinému objektu (delegátu). Alternativa dědičnosti.

```csharp
class Tiskarna {
    public void Tiskni(string text) { Console.WriteLine(text); }
}
class Kancelar {
    private Tiskarna tiskarna = new Tiskarna();
    public void TiskniDokument(string text) => tiskarna.Tiskni(text); // deleguje
}
```

---

## Přehled vztahů

| Vztah | Typ | Příklad | Vazba |
|-------|-----|---------|-------|
| Dědičnost | is-a | Pes je Zvíře | silná |
| Kompozice | has-a (vlastní) | Auto má Motor | střední |
| Agregace | has-a (odkazuje) | Třída má Studenty | slabší |
| Delegování | uses | Kancelář → Tiskárna | volná |
| Asociace | knows | Zaměstnanec zná Firmu | nejvolnější |

> Čím slabší vazba, tím flexibilnější a udržitelnější kód.

---

## Rychlé opakování – otázky

- [x] Co je rozdíl mezi třídou a objektem?
- [ ] Vysvětli zapouzdření a uveď příklad.
- [ ] Co je polymorfismus? Jaké jsou jeho dva druhy?
- [ ] Jaký je rozdíl mezi skládáním a dědičností?
- [ ] Co je delegování a proč ho používáme?
