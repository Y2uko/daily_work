# 16 – WinForms – standardní ovládací prvky

> **Maturitní otázka:** WinForms – standardní ovládací prvky.

Viz také: [[17_Udalosti_CSharp]]

---

## Co je WinForms?

**Windows Forms (WinForms)** = framework pro tvorbu desktopových aplikací s grafickým rozhraním (GUI) v C#. Každé okno je třída dědící od `Form`.

```csharp
public partial class MainForm : Form {   // formulář = třída
    public MainForm() {
        InitializeComponent();           // inicializace ovládacích prvků
    }
}
```

---

## Ovládací prvky (Controls)

Každý prvek je objekt s atributy (**vlastnostmi**) a **událostmi**.

---

### 📝 Textové prvky

#### `Label` – popisek

```csharp
label1.Text = "Zadej jméno:";
label1.ForeColor = Color.Red;
label1.Font = new Font("Arial", 12, FontStyle.Bold);
```

#### `TextBox` – textové pole

```csharp
string vstup = textBox1.Text;           // čtení
textBox1.Text = "výchozí text";         // zápis
textBox1.Clear();                       // vymazání
textBox1.PasswordChar = '*';            // heslo
textBox1.Multiline = true;             // více řádků
```

#### `RichTextBox` – formátovaný text

```csharp
richTextBox1.Text = "Formátovaný text";
richTextBox1.SelectionColor = Color.Blue;
```

---

### 🔘 Tlačítka a přepínače

#### `Button` – tlačítko

```csharp
button1.Text = "Klikni";
button1.Enabled = false;               // zakázání
button1.BackColor = Color.LightBlue;
// Klik – viz [[17_Udalosti_CSharp]]
```

#### `CheckBox` – zaškrtávací pole

```csharp
bool zaSkrtnuto = checkBox1.Checked;
checkBox1.Text = "Souhlasím s podmínkami";
```

#### `RadioButton` – přepínač (výběr 1 z N)

```csharp
if (radioButton1.Checked) { /* možnost 1 */ }
if (radioButton2.Checked) { /* možnost 2 */ }
// RadioButtony ve stejném GroupBoxu se vylučují
```

---

### 📋 Seznamy a výběry

#### `ListBox` – seznam položek

```csharp
listBox1.Items.Add("Položka 1");
listBox1.Items.Remove("Položka 1");
listBox1.Items.Clear();
string vybrana = listBox1.SelectedItem?.ToString();
int index = listBox1.SelectedIndex;
```

#### `ComboBox` – rozbalovací seznam

```csharp
comboBox1.Items.Add("Možnost A");
comboBox1.SelectedIndex = 0;           // předvolba
string vybrana = comboBox1.Text;
```

#### `CheckedListBox` – seznam se zaškrtáváním

```csharp
checkedListBox1.Items.Add("Volba 1");
foreach (var item in checkedListBox1.CheckedItems) { /* ... */ }
```

---

### 🔢 Číselné a časové prvky

#### `NumericUpDown` – číslo s šipkami

```csharp
numericUpDown1.Minimum = 0;
numericUpDown1.Maximum = 100;
numericUpDown1.Value = 50;
decimal hodnota = numericUpDown1.Value;
```

#### `TrackBar` – posuvník

```csharp
trackBar1.Minimum = 0;
trackBar1.Maximum = 100;
int hodnota = trackBar1.Value;
```

#### `DateTimePicker` – výběr data

```csharp
DateTime datum = dateTimePicker1.Value;
```

---

### 🖼️ Zobrazení a média

#### `PictureBox` – obrázek

```csharp
pictureBox1.Image = Image.FromFile("foto.jpg");
pictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;
```

#### `ProgressBar` – průběh operace

```csharp
progressBar1.Minimum = 0;
progressBar1.Maximum = 100;
progressBar1.Value = 75;
```

---

### 🗂️ Kontejnery (organizace layoutu)

| Prvek | Popis |
|-------|-------|
| `GroupBox` | Rámeček se záhlavím, sdružuje RadioButtony |
| `Panel` | Neviditelný kontejner, lze přidat scrollbar |
| `TabControl` | Záložky (taby) |
| `SplitContainer` | Dvě části oddělené přetahovatelnou hranicí |

---

### 📊 Tabulka

#### `DataGridView` – tabulka dat

```csharp
dataGridView1.Rows.Add("Jana", 25);
dataGridView1.Columns[0].HeaderText = "Jméno";
dataGridView1.AutoSizeColumnsMode = DataGridViewAutoSizeColumnsMode.Fill;
```

---

### 🔔 Dialogová okna

```csharp
// Informace
MessageBox.Show("Hotovo!", "Výsledek", MessageBoxButtons.OK, MessageBoxIcon.Information);

// Otázka
DialogResult r = MessageBox.Show("Opravdu?", "Potvrdit", MessageBoxButtons.YesNo);
if (r == DialogResult.Yes) { /* ... */ }

// Otevřít soubor
OpenFileDialog ofd = new OpenFileDialog();
ofd.Filter = "Textové soubory|*.txt";
if (ofd.ShowDialog() == DialogResult.OK) {
    string cesta = ofd.FileName;
}

// Uložit soubor
SaveFileDialog sfd = new SaveFileDialog();
```

---

## Důležité vlastnosti ovládacích prvků

| Vlastnost | Popis | Příklad |
|-----------|-------|---------|
| `Name` | Název prvku v kódu | `textBox1` |
| `Text` | Zobrazený text | `"Ahoj"` |
| `Enabled` | Povolení/zakázání | `false` |
| `Visible` | Zobrazení/skrytí | `false` |
| `Size` | Rozměry | `new Size(100, 30)` |
| `Location` | Pozice na formuláři | `new Point(10, 20)` |
| `BackColor` | Barva pozadí | `Color.White` |
| `ForeColor` | Barva textu | `Color.Black` |
| `Font` | Písmo | `new Font("Arial", 10)` |
| `TabIndex` | Pořadí Tab-klávesy | `0, 1, 2, …` |

---

## Rychlé opakování – otázky

- [ ] K čemu slouží `TextBox` a jak načteš zadaný text?
- [ ] Jaký je rozdíl mezi `ListBox` a `ComboBox`?
- [ ] K čemu slouží `RadioButton` a proč musí být ve `GroupBoxu`?
- [ ] Jak zobrazíš dialogové okno s otázkou Ano/Ne?
- [ ] Co dělá vlastnost `Enabled` a `Visible`?
