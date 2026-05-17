Proměnná je skrytá. Přístup k ní mají pouze metody uvnitř stejné třídy. Pokus o přímý přístup zvenčí způsobí chybu při kompilaci.

java
```
// Třída definující bankovní účet
public class BankovniUcet {
    private double zustatek = 5000.0; // Skrytá proměnná

    // Veřejná metoda pro bezpečné zobrazení zůstatku
    public double getZustatek() {
        return zustatek;
    }
}

// Použití v jiné třídě
public class Main {
    public static void main(String[] args) {
        BankovniUcet ucet = new BankovniUcet();
        
        // System.out.println(ucet.zustatek); // CHYBA! K proměnné 'zustatek' nelze přímo přistoupit.
        
        System.out.println(ucet.getZustatek()); // Funguje: Voláme veřejnou metodu, vypíše 5000.0
    }
}
```

