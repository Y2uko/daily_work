# Základy algoritmizace


### Typová konverze
Převod hodnoty z jednoho datového typu na jiný:

```java
int x = 5;
double y = (double) x;  // explicitní konverze: 5 → 5.0
```

---

## 5. Základní řídicí struktury

Každý algoritmus se skládá z kombinace tří základních řídicích struktur:

### a) Sekvence
Příkazy se provádějí **jeden za druhým v pořadí**, jak jsou zapsány. Nejjednodušší struktura.

```java
int a = 5;
int b = 3;
int soucet = a + b;
System.out.println(soucet); // výstup: 8
```

### b) Větvení (podmínky)
Program se **rozhoduje**, jakou cestu provést, na základě podmínky.

**`if / else if / else`:**
```java
int znamka = 2;

if (znamka == 1) {
    System.out.println("Výborně");
} else if (znamka == 2) {
    System.out.println("Chvalitebně");
} else {
    System.out.println("Jiná známka");
}
```

**`switch`** – vhodný pro více možností jedné proměnné:
```java
switch (znamka) {
    case 1: System.out.println("Výborně"); break;
    case 2: System.out.println("Chvalitebně"); break;
    default: System.out.println("Jiná známka");
}
```


## 7. Pole (Array)

**Pole** je datová struktura, která uchovává **více hodnot stejného datového typu** pod jedním názvem. Prvky pole jsou uloženy za sebou v paměti a přistupujeme k nim pomocí **indexu** (čísluje se od 0).

```java
int[] cisla = {10, 20, 30, 40, 50};

System.out.println(cisla[0]); // 10 (první prvek)
System.out.println(cisla[4]); // 50 (pátý prvek)
```

**Procházení pole cyklem `for`:**
```java
for (int i = 0; i < cisla.length; i++) {
    System.out.println(cisla[i]);
}
```

Pole jsou základním stavebním kamenem většiny algoritmů (řazení, vyhledávání atd.).

---


- **Funkce** je pojmenovaný blok kódu, který vykonává konkrétní úlohu. Lze ji volat opakovaně z různých míst programu.
- Proč používat funkce?
	- **Znovupoužitelnost** — kód napíšeme jednou, použijeme mnohokrát
	- **Přehlednost** — hlavní program je kratší a srozumitelnější
	- **Snadná oprava** — chybu opravíme na jednom místě
```java
// Definice funkce
static int secti(int a, int b) {
    return a + b;
}

// Volání funkce
int vysledek = secti(3, 5); // vysledek = 8
```

> **Procedura** vs. **Funkce:** Procedura nic nevrací (návratový typ `void`), funkce vrací hodnotu.

---

#### Rekurze
- **Rekurze** je situace, kdy **funkce volá sama sebe**. Je to alternativa k iteraci (cyklům) pro řešení problémů, které lze rozložit na menší podproblémy stejného typu.

-  Podmínky správné rekurze:
	1. **Základní případ (base case)** — podmínka, při které se rekurze zastaví
	2. **Rekurzivní volání** — volání funkce s menším/jednodušším vstupem, které se blíží základnímu případu
 - Příklad: Faktoriál
	- Faktoriál čísla n (zápis n!) je součin všech přirozených čísel od 1 do n.
		- 5! = 5 × 4 × 3 × 2 × 1 = 120
```java
static int faktorial(int n) {
    if (n == 0) return 1;        // základní případ
    return n * faktorial(n - 1); // rekurzivní volání
}

// faktorial(3) → 3 * faktorial(2)
//                    → 2 * faktorial(1)
//                           → 1 * faktorial(0)
//                                  → 1
// výsledek: 3 * 2 * 1 * 1 = 6
```


---

##### Základní algoritmy

-  a) Vyhledávací algoritmy
	-  **Lineární vyhledávání**
		- Prochází pole postupně prvek po prvku, dokud nenajde hledanou hodnotu.
	```java
static int linearniHledani(int[] pole, int hledany) {
    for (int i = 0; i < pole.length; i++) {
        if (pole[i] == hledany) return i; // vrátí index
    }
    return -1; // nenalezeno
}
	```
	- **Výhoda:** funguje na neseřazené pole
	- **Nevýhoda:** pomalé pro velká data — v nejhorším případě projde vše

	- Binární vyhledávání
		- Funguje pouze na **seřazeném poli**. Opakovaně dělí prohledávaný úsek na poloviny.
	```java
static int binarniHledani(int[] pole, int hledany) {
    int leva = 0, prava = pole.length - 1;
    while (leva <= prava) {
        int stred = (leva + prava) / 2;
        if (pole[stred] == hledany) return stred;
        else if (pole[stred] < hledany) leva = stred + 1;
        else prava = stred - 1;
    }
    return -1;
}
	```
	- **Výhoda:** velmi rychlé — každý krok eliminuje polovinu zbývajících prvků
	- **Nevýhoda:** pole musí být seřazeno

-  b) Řadící algoritmy

#### Bubble Sort (bublinkové řazení)
Opakovaně prochází pole a **vyměňuje sousední prvky**, pokud jsou ve špatném pořadí. Větší prvky „probublávají" na konec.

```java
static void bubbleSort(int[] pole) {
    int n = pole.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (pole[j] > pole[j + 1]) {
                // prohození sousedů
                int temp = pole[j];
                pole[j] = pole[j + 1];
                pole[j + 1] = temp;
            }
        }
    }
}
```

Průběh na příkladu `{5, 3, 1, 4, 2}`:
```
Průchod 1: {3, 1, 4, 2, 5}  ← 5 se dostalo na konec
Průchod 2: {1, 3, 2, 4, 5}
Průchod 3: {1, 2, 3, 4, 5}  ← seřazeno
```

- **Složitost:** O(n²) — pro velká data velmi pomalý
- **Výhoda:** jednoduchá implementace, vhodný pro výuku

#### Selection Sort (výběrové řazení)
V každém průchodu najde **nejmenší prvek** zbývající části a přesune ho na správnou pozici.

```java
static void selectionSort(int[] pole) {
    int n = pole.length;
    for (int i = 0; i < n - 1; i++) {
        int minIndex = i;
        for (int j = i + 1; j < n; j++) {
            if (pole[j] < pole[minIndex]) minIndex = j;
        }
        // prohození
        int temp = pole[minIndex];
        pole[minIndex] = pole[i];
        pole[i] = temp;
    }
}
```


