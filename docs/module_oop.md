# OOP

#### Define a constructor? (Zdefiniuj konstruktor)
>Konstruktor to specjalna metoda w klasie, która jest automatycznie wywoływana podczas tworzenia nowego obiektu tej klasy. Nazwa konstruktora musi być taka sama jak nazwa klasy. Konstruktory są często używane do inicjalizacji pól klasy.

>Konstruktor może przyjmować parametry, które umożliwiają ustawienie wartości początkowych pól podczas tworzenia obiektu. Konstruktor, który nie przyjmuje żadnych parametrów, nazywany jest konstruktorem domyślnym lub bezparametrowym.

Oto przykład konstruktora w Javie:

**Here's an example of a constructor in Java:**


    public class KlasaPrzykladowa {
        private String pole;
    
        // To jest konstruktor
        public KlasaPrzykladowa(String parametr) {
            this.pole = parametr;
        }
    }


>W tym przykładzie **KlasaPrzykladowa** ma jeden konstruktor, który przyjmuje jeden parametr typu **String**. Gdy tworzymy nowy obiekt typu **KlasaPrzykladowa**, musimy dostarczyć ten parametr:

    KlasaPrzykladowa obiekt = new KlasaPrzykladowa("wartosc");

W tym przypadku, "wartosc" jest wartością początkową dla pola pole w nowo utworzonym obiekcie.


#### Difference between overloading and overriding? (Różnica między przeciążaniem a nadpisywaniem?)

>Zarówno przeciążanie (overloading) jak i nadpisywanie (overriding) metod to dwa ważne koncepty w programowaniu obiektowym, ale mają różne zastosowania i semantykę.

**Przeciążanie metod (overloading)**

>Przeciążanie metod występuje, gdy w obrębie jednej klasy definiujemy dwie lub więcej metod o tej samej nazwie, ale z różnymi listami parametrów (różnią się typem i/lub liczbą argumentów). Przeciążanie pozwala na wykonanie różnych operacji w zależności od typu i liczby argumentów.

Przykład w Javie:

    public class PrzykladowaKlasa {
        public void metoda(int liczba) {
            System.out.println("Metoda z jednym argumentem: " + liczba);
        }
    
        public void metoda(int liczba1, int liczba2) {
            System.out.println("Metoda z dwoma argumentami: " + liczba1 + ", " + liczba2);
        }
    }

**Nadpisywanie metod (overriding)*

>Nadpisywanie metod występuje, gdy klasa pochodna dostarcza własną implementację metody, która już istnieje w klasie bazowej. W tym przypadku nazwa metody, jej typ zwracany i lista parametrów muszą być identyczne jak w klasie bazowej. Nadpisywanie pozwala zmienić zachowanie metody dla klasy pochodnej.

Przykład w Javie:

    public class KlasaBazowa {
        public void metoda() {
            System.out.println("Metoda z klasy bazowej");
        }
    }
    
    public class KlasaPochodna extends KlasaBazowa {
        @Override
        public void metoda() {
            System.out.println("Metoda z klasy pochodnej");
        }
    }

>Podsumowując, przeciążanie metod odnosi się do definiowania wielu metod o tej samej nazwie, ale różnej liczbie lub typach parametrów w obrębie jednej klasy, podczas gdy nadpisywanie metod dotyczy dostarczenia nowej implementacji metody w klasie pochodnej, która została już zdefiniowana w klasie bazowej.

#### Do we require parameters for constructors? (Czy wymagamy parametrów dla konstruktorów?)

>Parametry konstruktora nie są wymagane, ale mogą być bardzo przydatne.

>Konstruktor, który nie przyjmuje żadnych parametrów, nazywamy konstruktorem domyślnym lub bezparametrowym. Służy on zwykle do inicjalizacji pól obiektu wartościami domyślnymi.

>Jednak w wielu przypadkach konstruktory z parametrami są użyteczne do dostarczenia początkowych wartości dla pól obiektu podczas jego tworzenia. W ten sposób możemy zapewnić, że obiekt jest od samego początku w prawidłowym stanie.

Oto przykład klasy w Javie, która ma oba typy konstruktorów:

    public class KlasaPrzykladowa {
        private int liczba;
    
        // To jest konstruktor domyślny
        public KlasaPrzykladowa() {
            this.liczba = 0; // domyślna wartość
        }
    
        // To jest konstruktor z parametrem
        public KlasaPrzykladowa(int liczba) {
            this.liczba = liczba; // wartość inicjalna dostarczona jako argument
        }
    }

>Teraz możemy stworzyć obiekty **KlasaPrzykladowa** zarówno za pomocą konstruktora domyślnego, jak i konstruktora z parametrem:

    KlasaPrzykladowa obiekt1 = new KlasaPrzykladowa(); // używa konstruktora domyślnego
    KlasaPrzykladowa obiekt2 = new KlasaPrzykladowa(10); // używa konstruktora z parametrem

>Decyzja o tym, czy konstruktor powinien mieć parametry, zależy od konkretnych wymagań i charakterystyki klasy.

#### Explain the “Single Responsibility” principle! (Wyjaśnij zasadę „pojedynczej odpowiedzialności”!)

>Zasada jednej odpowiedzialności (Single Responsibility Principle, SRP) to jedno z pięciu podstawowych założeń SOLID, które są fundamentalnymi zasadami programowania obiektowego i projektowania oprogramowania.

>Zgodnie z tą zasadą, każda klasa lub moduł w systemie powinien mieć tylko jedną odpowiedzialność. Innymi słowy, klasa powinna mieć tylko jeden powód do zmiany.

>SRP pomaga utrzymać kod w czystości i ułatwia jego zrozumienie, ponieważ mniej jest zależności pomiędzy różnymi częściami kodu. Dzięki temu zmiany w jednej części systemu mają mniejszy wpływ na inne części, co ułatwia testowanie i utrzymanie kodu.

Przykład złamania SRP w Javie:

    public class Pracownik {
        private String imie;
        private String email;
    
        // Konstruktor, gettery, settery...
    
        public void zapiszDoBazyDanych() {
            // Logika zapisu pracownika do bazy danych
        }
    }

>W powyższym kodzie klasa **Pracownik** ma dwie odpowiedzialności - zarządzanie danymi pracownika oraz zapisywanie tych danych do bazy. Jest to naruszenie SRP.

Prawidłowa implementacja SRP mogłaby wyglądać tak:

    public class Pracownik {
        private String imie;
        private String email;
    
        // Konstruktor, gettery, settery...
    }
    
    public class BazaDanychPracownikow {
        public void zapisz(Pracownik pracownik) {
        // Logika zapisu pracownika do bazy danych
        }
    }

>Teraz mamy dwie klasy, z których każda ma tylko jedną odpowiedzialność. Klasa **Pracownik** zarządza danymi pracownika, a klasa **BazaDanychPracownikow** jest odpowiedzialna za interakcje z bazą danych. Każda z nich ma teraz tylko jeden powód do zmiany, co jest zgodne z zasadą jednej odpowiedzialności.

#### How do you prevent developers from changing the value of a variable? (Jak uniemożliwić programistom zmianę wartości zmiennej?)

>W wielu językach programowania, takich jak Java, C++ czy C#, możemy uniemożliwić zmianę wartości zmiennej, deklarując ją jako stałą lub używając słowa kluczowego **final** (w Javie) lub **const** (w C++ czy C#).

Oto przykład użycia final w Javie:

    public class KlasaPrzykladowa {
        public final int LICZBA = 10;
    }

>W tym przypadku, **LICZBA** jest zmienną, której wartości nie można zmienić po jej inicjalizacji. Każda próba zmiany wartości **LICZBA** spowoduje błąd kompilacji.

Podobnie, w C++ lub C#, możemy użyć słowa kluczowego **const**:

    public class PrzykladowaKlasa
    {
        public const int Liczba = 10;
    }

>Pamiętaj, że używanie **final** lub **const** oznacza, że musisz zainicjować zmienną podczas deklaracji lub w konstruktorze (w przypadku pól klas). Po jej zainicjowaniu, nie możesz już zmienić wartości tej zmiennej.


#### How do you prevent developers from inheriting a class? (Jak uniemożliwić programistom dziedziczenie klasy?)

>Aby uniemożliwić dziedziczenie klasy w różnych językach programowania, używamy różnych słów kluczowych.

W **Javie**, używamy słowa kluczowego **final** przed deklaracją klasy:

    public final class KlasaPrzykladowa {
        // kod klasy
    }

>W tym przypadku, żadna inna klasa nie może dziedziczyć po KlasaPrzykladowa.

W **C#**, używamy słowa kluczowego **sealed**:

    public sealed class PrzykladowaKlasa {
        // kod klasy
    }

>Podobnie, żadna inna klasa nie może dziedziczyć po **PrzykladowaKlasa** w tym przypadku.

W **C++**, możemy uniemożliwić dziedziczenie, ustawiając konstruktor klasy jako **private**:

    class PrzykladowaKlasa {
    private:
        PrzykladowaKlasa() {}
        // kod klasy
    };

>W tych przykładach, każda próba dziedziczenia po klasie, która jest oznaczona jako **final**, **sealed** lub ma **private** konstruktor, spowoduje błąd kompilacji.


#### How do you prevent developers from overriding a method in a child class? (Jak uniemożliwić programistom zastąpienie metody w klasie potomnej?)

>Aby uniemożliwić nadpisywanie metody w klasie potomnej, używamy różnych słów kluczowych w zależności od języka programowania.

**Java:**

W Javie, używamy słowa kluczowego **final** przed deklaracją metody:

    public class KlasaPrzykladowa {
        public final void metoda() {
            // implementacja metody
        }
    }

>Teraz, żadna klasa potomna nie może nadpisać metody **metoda()**.

**C#:**

W C#, używamy słowa kluczowego **sealed** w klasie pochodnej po deklaracji metody **override**:

    public class KlasaBazowa {
        public virtual void Metoda() {
            // implementacja metody
        }
    }
    
    public class KlasaPochodna : KlasaBazowa {
        public sealed override void Metoda() {
            // implementacja metody
        }
    }

>Teraz, żadna klasa dziedzicząca po **KlasaPochodna** nie może nadpisać metody **Metoda()**.

**C++:**

W C++, język nie oferuje bezpośredniego mechanizmu do zapobiegania nadpisywaniu metod. Możemy jednak osiągnąć podobny efekt, nie deklarując metody jako **virtual**:

    class KlasaPrzykladowa {
    public:
        void metoda() {
        // implementacja metody
        }
    };

>W tym przypadku, metoda **metoda()** nie może być nadpisana w klasie pochodnej, ponieważ nie jest **virtual**.

>Te techniki są użyteczne, gdy chcemy zapewnić, że konkretna implementacja metody pozostanie niezmieniona w klasach pochodnych.

#### How do you prevent developers from overriding a method in a subclass? (Jak uniemożliwić programistom zastąpienie metody w podklasie?)

>Aby zapobiec nadpisywaniu metody w klasie potomnej, można użyć różnych mechanizmów w zależności od języka programowania.

**Java:**

W Javie używa się słowa kluczowego **final** przed deklaracją metody, aby uniemożliwić jej nadpisanie:

    public class KlasaBazowa {
        public final void metoda() {
            // implementacja metody
        }
    }

>W tym przypadku, żadna klasa potomna nie może nadpisać metody **metoda()**.

**C#:**

W C# używa się słowa kluczowego **sealed** w klasie pochodnej, aby uniemożliwić dalsze nadpisywanie metody:

    public class KlasaBazowa {
        public virtual void metoda() {
            // implementacja metody
        }
    }
    
    public class KlasaPochodna : KlasaBazowa {
        public sealed override void metoda() {
        // implementacja metody
        }
    }

>Teraz, żadna klasa, która dziedziczy po **KlasaPochodna**, nie może nadpisać metody **metoda()**.

**C++:**

W C++ nie ma bezpośredniego mechanizmu do zapobiegania nadpisywaniu metod. Jednak, nie deklarując metody jako **virtual**, możemy osiągnąć podobny efekt:

    class KlasaBazowa {
    public:
        void metoda() {
        // implementacja metody
        }
    };

>W tym przypadku, metoda **metoda()** nie może być nadpisana w klasie potomnej, ponieważ nie jest **virtual**.

>Używanie tych technik pozwala utrzymać pewne metody konsekwentne w hierarchii klas i zapobiega niezamierzonym zmianom w klasach potomnych.


#### How do you prevent developers from subclassing a class? (Jak uniemożliwić programistom podklasowanie klasy?)

>Aby zapobiec tworzeniu podklas (subclassing) klasy w różnych językach programowania, stosuje się różne słowa kluczowe.

**Java:**

W Javie, używamy słowa kluczowego **final** przed deklaracją klasy:

    public final class KlasaPrzykladowa {
        // kod klasy
    }

>W tym przypadku, żadna inna klasa nie może dziedziczyć po **KlasaPrzykladowa**.

**C#:**

W C#, używamy słowa kluczowego **sealed**:

    public sealed class PrzykladowaKlasa {
        // kod klasy
    }

>Podobnie, żadna inna klasa nie może dziedziczyć po **KlasaPrzykladowa** w tym przypadku.

**C++:**

W C++, możemy uniemożliwić dziedziczenie, czyniąc konstruktor klasy prywatnym:

    class PrzykladowaKlasa {
    private:
        PrzykladowaKlasa() {}
        // kod klasy
    };

>W tych przykładach, każda próba dziedziczenia po klasie, która jest oznaczona jako **final**, **sealed** lub ma **private** konstruktor, spowoduje błąd kompilacji. Zastosowanie tych technik pozwala na kontrolę hierarchii dziedziczenia w programie.


#### What are access modifiers? (Czym są modyfikatory dostępu?)

>Modyfikatory dostępu, zwane także poziomami dostępu, są kluczowym elementem języków programowania obiektowego. Określają one, jakie elementy kodu (tj. klasy, metody, zmienne) są dostępne z innych części kodu.

>Poniżej przedstawiam modyfikatory dostępu w kontekście Javy, lecz podobne koncepcje dotyczą większości języków programowania obiektowego:

1. **private**: Elementy oznaczone jako **private** są dostępne tylko w obrębie klasy, w której zostały zdefiniowane.

        public class KlasaPrzykladowa {
            private int zmiennaPrywatna; // dostępna tylko w KlasaPrzykladowa
        }

2. **default (package-private)**: Jeśli element nie ma modyfikatora dostępu, jest domyślnie dostępny dla wszystkich klas w tym samym pakiecie.

        class KlasaPrzykladowa {
            int zmiennaDomyslna; // dostępna dla klas w tym samym pakiecie
       }
3. **protected**: Elementy oznaczone jako **protected** są dostępne dla wszystkich klas w tym samym pakiecie oraz dla wszystkich klas dziedziczących po klasie, w której zostały zdefiniowane.

        public class KlasaPrzykladowa {
            protected int zmiennaChroniona; // dostępna dla klas w tym samym pakiecie i klas dziedziczących po KlasaPrzykladowa
        }

4. **public**: Elementy oznaczone jako **public** są dostępne dla wszystkich klas, niezależnie od pakietu.

        public class KlasaPrzykladowa {
            public int zmiennaPubliczna; // dostępna dla wszystkich klas
        }

>Wybór odpowiedniego modyfikatora dostępu jest kluczowy dla zapewnienia bezpieczeństwa i poprawnego działania programu, zapobiegając niepożądanym modyfikacjom danych lub korzystaniu z metod w niewłaściwy sposób.

#### What are base class, subclass and superclass? (Co to jest klasa podstawowa, podklasa i nadklasa?)

>Terminy "base class", "subclass" i "superclass" są kluczowymi pojęciami w obiektowo zorientowanym programowaniu i są związane z koncepcją dziedziczenia.

>**Base class / Superclass**: To klasa, od której inne klasy są dziedziczone. Zawiera atrybuty i metody, które są wspólne dla wszystkich klas dziedziczących po niej. W niektórych językach, jak C++ czy C#, termin "base class" jest częściej używany, podczas gdy w innych, jak Java, preferowany jest "superclass".

    public class Zwierze { // To jest superclass
        public void jedzenie() {
            System.out.println("Zwierze je");
        }
    }

>**Subclass**: To klasa, która dziedziczy atrybuty i metody od innej klasy (nazywanej superclass lub base class). Subklasa może również dodawać nowe metody i atrybuty lub nadpisywać metody superclass.

    public class Pies extends Zwierze { // Pies jest subclass
        // dziedziczy metodę jedzenie() od superclass
    
        // dodajemy nową metodę specyficzną dla Pies
        public void szczekanie() {
            System.out.println("Pies szczeka");
        }
    }

>W powyższym przykładzie, **Zwierze** jest superclass (lub base class), a **Pies** jest subclass, które dziedziczy metody i atrybuty od **Zwierze**. Subklasa może również dodawać swoje własne specyficzne metody, jak w tym przypadku **szczekanie()**.

>Dziedziczenie jest jednym z głównych mechanizmów obiektowo zorientowanego programowania, umożliwiających tworzenie bardziej skomplikowanych hierarchii klas i zwiększającą efektywność kodu poprzez eliminację redundancji.

#### What are different types of arguments? (context: pass by value / pass by reference) (Jakie są różne rodzaje argumentów? (kontekst: przekazać przez wartość / przekazać przez referencję))

>W kontekście przekazywania argumentów do funkcji czy metod, mamy do czynienia głównie z dwoma typami argumentów: "przez wartość" (pass by value) i "przez referencję" (pass by reference).

**Pass by value (Przekazanie przez wartość)**:

>W przypadku przekazywania przez wartość, kopia wartości argumentu jest przekazywana do funkcji. Wszelkie zmiany dokonane na tej kopii w ciele funkcji nie wpływają na pierwotną zmienną.

Przykład w Java (jako język przekazujący przez wartość):

    public class Main {
        public static void zmienWartosc(int wartosc) {
            wartosc = 30;
        }
    
        public static void main(String[] args) {
            int wartosc = 20;
            zmienWartosc(wartosc);
            System.out.println(wartosc); // Wypisze: 20
        }
    }

**Pass by reference (Przekazanie przez referencję)**:

>Przy przekazywaniu przez referencję, funkcja otrzymuje nie wartość, ale odwołanie do (referencję na) pierwotnej zmiennej. Wszelkie zmiany dokonane na tej zmiennej w ciele funkcji wpływają na pierwotną zmienną.

Przykład w Python (jako język przekazujący obiekty przez referencję):

    def zmien_wartosc(lista):
    lista.append(1)

    lista = []
    zmien_wartosc(lista)
    print(lista)  # Wypisze: [1]

>Zauważ, że różne języki programowania mają różne domyślne metody przekazywania argumentów. W niektórych językach, jak C++ i C#, programista ma możliwość wyboru pomiędzy przekazaniem przez wartość a przekazaniem przez referencję.

#### What are generic types and why are they used? (Co to są typy generyczne (ogólne) i dlaczego są używane?)

>Typy generyczne to koncepcja w programowaniu, która pozwala na tworzenie klas i metod, które mogą działać na różnych typach danych. Są one używane do tworzenia kodu, który jest wielokrotnie używany, jest bezpieczny typowo i łatwo utrzymywalny.

**Dlaczego używamy typów generycznych?**

1. **Zwiększenie ponownego użycia kodu**: Generyki pozwalają na tworzenie ogólnych szablonów, które mogą być zastosowane do różnych typów danych, eliminując potrzebę pisania oddzielnych kodów dla różnych typów danych.

2. **Bezpieczeństwo typowe**: Generyki zapewniają bezpieczeństwo typowe. Kompilator sprawdza poprawność typu dla generyków i zgłasza błędy na etapie kompilacji, a nie w czasie wykonania.

3. **Ulepszona wydajność**: Generyki eliminują potrzebę rzutowania typów, co może poprawić wydajność kodu.

**Przykład w Javie:**

Poniższy przykład ilustruje generyczną klasę **Kontener**, która może przechowywać obiekty różnych typów.

    public class Kontener<T> {
        private T element;
    
        public void dodajElement(T element) {
            this.element = element;
        }
    
        public T pobierzElement() {
            return element;
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Kontener<String> kontenerString = new Kontener<>();
            kontenerString.dodajElement("Witaj Świecie");
            System.out.println(kontenerString.pobierzElement());
    
            Kontener<Integer> kontenerInteger = new Kontener<>();
            kontenerInteger.dodajElement(123);
            System.out.println(kontenerInteger.pobierzElement());
        }
    }

>W tym przykładzie, **Kontener<T>** to generyczna klasa, która może przechowywać różne typy danych. W klasie **Main** tworzymy instancje **Kontener<String>** i **Kontener<Integer>**, które przechowują odpowiednio Stringi i Integery.

#### What are mutable and immutable types? (Co to są typy zmienne i niezmienne?)

>W kontekście Javy, kiedy mówimy o mutowalności, zazwyczaj mówimy o obiektach, a nie prostych typach danych, ponieważ w Javie, typy proste (int, float, boolean etc.) są zawsze niemutowalne.

>**Mutable (Mutowalne)**: Mutowalne typy to takie, których stan (wartość) można zmienić po utworzeniu. Przykładem może być klasa StringBuilder w Javie:

      StringBuilder sb = new StringBuilder("Witaj");
      sb.append(" Świecie");  // Zmieniamy stan obiektu sb
      System.out.println(sb); // Wypisze: "Witaj Świecie"

>**Immutable (Niemutowalne)**: Typy niemutowalne to takie, których stan nie może być zmieniony po ich utworzeniu. Wszelkie zmiany stanu prowadzą do utworzenia nowego obiektu. Przykładem jest klasa **String** w Javie:

      String s = "Witaj";
      s += " Świecie";  // Tworzymy nowy obiekt String
      System.out.println(s); // Wypisze: "Witaj Świecie"

>W powyższym przykładzie, mimo że wygląda to na zmianę stanu zmiennej **s**, tak naprawdę tworzony jest nowy obiekt **String** z zawartością "Witaj Świecie", a zmienna **s** jest aktualizowana, aby wskazywać na ten nowy obiekt.

>Niemutowalność jest ważnym konceptem, szczególnie w kontekście wielowątkowości, gdzie niemutowalne obiekty są bezpieczne do używania przez wiele wątków bez potrzeby synchronizacji.


#### What are the differences between abstract classes and interfaces? (Jakie są różnice między klasami abstrakcyjnymi a interfejsami?)

>Abstrakcyjne klasy i interfejsy są dwoma mechanizmami w Javie, które umożliwiają abstrakcję i wielokrotne dziedziczenie. Mają one jednak istotne różnice:

**Klasa abstrakcyjna**:

* Klasa abstrakcyjna może zawierać stan (pola).
* Klasa abstrakcyjna może zawierać metody z implementacją.
* Klasa abstrakcyjna może zawierać metody abstrakcyjne (bez implementacji), które muszą być zaimplementowane w klasach dziedziczących.
* Klasa może dziedziczyć tylko jedną klasę abstrakcyjną.

      abstract class Zwierze {
         private String nazwa;

         public Zwierze(String nazwa) {
            this.nazwa = nazwa;
         }

         public abstract void wydajDzwiek();

         public void opis() {
            System.out.println("Jestem zwierzęciem o nazwie " + nazwa);
         }
      }

**Interfejs**:

* Interfejs nie może zawierać stanu (do wersji Java 8).
* Interfejs może zawierać tylko metody bez implementacji (do wersji Java 8). Od Javy 8, interfejsy mogą zawierać metody domyślne i statyczne z implementacją.
* Klasa może implementować wiele interfejsów.

      interface PoruszajacySie {
         void poruszajSie();
      }

>Od Javy 8, interfejsy mogą zawierać metody domyślne i statyczne, co sprawia, że różnice między interfejsami i klasami abstrakcyjnymi są mniej wyraźne. Mimo to, kluczowa różnica polega na tym, że interfejsy są przeznaczone do definiowania kontraktów dla zachowań (co klasa potrafi robić), podczas gdy klasy abstrakcyjne są używane do reprezentowania hierarchii typów i mogą zawierać stan wspólny dla tych typów.

#### What are the differences between classes and objects? (Jakie są różnice między klasami i obiektami?)

>Klasa i obiekt to dwie podstawowe koncepcje w programowaniu obiektowym, takim jak Java.

**Klasa**:

>Klasa jest szablonem lub definicją, która określa właściwości (pola) i metody, które będą wspólne dla wszystkich obiektów tej klasy. Klasy są abstrakcyjnymi konceptami - są to schematy, które definiują, jakie informacje i działania powinien mieć obiekt.

Przykładowa klasa w Javie:

      public class Samochod {
          // pola klasy
          private String marka;
          private String model;
      
          // konstruktor klasy
          public Samochod(String marka, String model) {
              this.marka = marka;
              this.model = model;
          }
      
          // metody klasy
          public void pokazInformacje() {
              System.out.println("Samochód: " + marka + " " + model);
          }
      }

**Obiekt**:

>Obiekt to konkretna instancja klasy. Każdy obiekt ma swój własny stan (wartości pól), ale dzieli metody zdefiniowane w klasie. Tworzenie obiektu nazywane jest instancjonowaniem klasy.
      
Przykładowy obiekt klasy Samochod:
         
      Samochod mojSamochod = new Samochod("Toyota", "Corolla");
      mojSamochod.pokazInformacje();  // wywołanie metody na obiekcie

>Podsumowując, klasa to szablon, który definiuje, jakie pola i metody powinny mieć obiekty tej klasy. Obiekt to konkretna instancja klasy, która ma swój własny stan (wartości pól), ale dzieli metody z klasą.


#### What are the differences between overriding and overloading? (Jakie są różnice między nadpisywaniem a przeciążaniem?)

>**Overriding (nadpisywanie)**:

>Nadpisywanie metody polega na zdefiniowaniu metody w klasie podrzędnej, która ma tę samą sygnaturę (nazwę i listę argumentów) co metoda w klasie nadrzędnej. Nadpisana metoda w klasie podrzędnej zastępuje metodę z klasą nadrzędną.

Przykład nadpisywania:

    class Zwierze {
    void wydajDzwiek() {
        System.out.println("Zwierzę robi dźwięk");
    }
    }
    
    class Pies extends Zwierze {
        @Override
        void wydajDzwiek() {
            System.out.println("Pies robi hau hau");
        }
    }

>W tym przypadku metoda **wydajDzwiek** w klasie **Pies** nadpisuje metodę wydajDzwiek w klasie Zwierze.

**Overloading (przeładowanie)**:

>Przeładowanie metody polega na zdefiniowaniu w tej samej klasie więcej niż jednej metody o tej samej nazwie, ale z różnymi listami argumentów (różniących się typem lub liczbą argumentów).

Przykład przeładowania:

    class Kalkulator {
        int dodaj(int a, int b) {
            return a + b;
        }
    
        double dodaj(double a, double b) {
            return a + b;
        }
    }

>W tym przypadku metoda **dodaj** jest przeładowana: mamy dwie metody **dodaj**, jedna dodaje dwie liczby całkowite, a druga dodaje dwie liczby zmiennoprzecinkowe.

>Podsumowując, nadpisywanie i przeładowywanie są różnymi konceptami: nadpisywanie związane jest z dziedziczeniem i polega na zmianie zachowania metody w klasie podrzędnej, podczas gdy przeładowanie polega na udostępnieniu wielu metod o tej samej nazwie, ale z różnymi listami argumentów w tej samej klasie.

#### What are the differences between static and instance members? (Jakie są różnice między członkami statycznymi i wystąpieniami?)

>**Członkowie statyczni**:

>Członkowie statyczni należą do klasy, a nie do instancji klasy. Zmienne statyczne dzielą jedną kopię swojej wartości między wszystkimi instancjami klasy. Metody statyczne mogą bezpośrednio działać tylko na zmiennych statycznych - nie mogą bezpośrednio odwoływać się do zmiennych instancji ani wywoływać metod instancji.

Przykład zmiennych i metod statycznych:

    public class KlasaStatyczna {
        public static int zmiennaStatyczna = 0;
    
        public static void metodaStatyczna() {
            System.out.println("Jestem metodą statyczną");
        }
    }

**Członkowie instancji**:

>Członkowie instancji należą do instancji klasy. Każda instancja klasy ma swoją własną kopię każdej zmiennej instancji, więc zmiany dokonane na zmiennej instancji w jednym obiekcie nie wpłyną na inne obiekty.

Przykład zmiennych i metod instancji:

    public class KlasaInstancji {
        public int zmiennaInstancji = 0;
    
        public void metodaInstancji() {
            System.out.println("Jestem metodą instancji");
        }
    }

Musisz utworzyć instancję klasy, aby odwołać się do członków instancji:


    KlasaInstancji obiekt = new KlasaInstancji();
    obiekt.metodaInstancji();
    System.out.println(obiekt.zmiennaInstancji);

>Podsumowując, różnica między członkami statycznymi a członkami instancji polega na tym, do czego należą: członkowie statyczni należą do klasy jako całości, podczas gdy członkowie instancji należą do poszczególnych instancji klasy.

#### What do S & D stand for in SOLID? (Co oznacza S&D w SOLID?)

>SOLID to akronim, który reprezentuje pięć zasad projektowania oprogramowania zorientowanego obiektowo, które pomagają tworzyć systemy łatwiejsze do utrzymania, zrozumienia i rozbudowy.

>"S" w SOLID reprezentuje zasadę Single Responsibility (Jednej Odpowiedzialności). Ta zasada mówi, że klasa powinna mieć tylko jeden powód do zmiany - czyli powinna mieć tylko jedną odpowiedzialność.

>"D" w SOLID reprezentuje zasadę Dependency Inversion (Odwrócenia Zależności). Ta zasada mówi, że powinniśmy zależeć od abstrakcji, a nie od konkretnych klas. Moduły wysokiego poziomu nie powinny zależeć od modułów niskiego poziomu. Wszystkie powinny zależeć od abstrakcji.

Przykładowy kod w Javie:

**Single Responsibility Principle**:

    public class Employee {
        private String employeeName;
    
        public Employee(String employeeName) {
            this.employeeName = employeeName;
        }
    
        public void getEmployeeDetails() {
            // Wyswietl szczegóły pracownika
        }
    }
    
    public class EmployeeDB {
        public void saveEmployee(Employee e) {
        // Zapisz pracownika do bazy danych
        }
    }

>W tym przypadku, zgodnie z zasadą jednej odpowiedzialności, klasa **Employee** jest odpowiedzialna za przechowywanie danych pracownika, a klasa **EmployeeDB** jest odpowiedzialna za zapisywanie pracownika do bazy danych.

**Dependency Inversion Principle**:

    public interface DataSource {
        void saveData(String data);
    }
    
    public class MySQLDatabase implements DataSource {
        public void saveData(String data) {
        // Zapisz dane do bazy danych MySQL
        }
    }
    
    public class EmployeeDB {
    private DataSource dataSource;
    
        public EmployeeDB(DataSource dataSource) {
            this.dataSource = dataSource;
        }
    
        public void saveEmployee(Employee e) {
            dataSource.saveData(e.toString());
        }
    }

>W tym przypadku klasa **EmployeeDB** nie zależy bezpośrednio od konkretnej klasy **MySQLDatabase**. Zamiast tego zależy od interfejsu **DataSource**, co jest zgodne z zasadą odwrócenia zależności.

#### What do S & I stand for in SOLID? (Co oznaczają S & I w SOLID?)

>SOLID to akronim, który reprezentuje pięć zasad projektowania oprogramowania zorientowanego obiektowo, które pomagają tworzyć systemy łatwiejsze do utrzymania, zrozumienia i rozbudowy.

>"S" w SOLID reprezentuje zasadę Single Responsibility (Jednej Odpowiedzialności). Ta zasada mówi, że klasa powinna mieć tylko jeden powód do zmiany - czyli powinna mieć tylko jedną odpowiedzialność.

>"I" w SOLID reprezentuje zasadę Interface Segregation (Segregacji Interfejsów). Ta zasada mówi, że klienci (inne klasy, moduły) nie powinny być zmuszone do zależności od interfejsów, których nie używają. Innymi słowy, interfejsy powinny być małe i skoncentrowane na konkretnej funkcjonalności, zamiast być jednym "wielkim" interfejsem do wszystkiego.

Przykładowy kod w Javie:

**Single Responsibility Principle**:

    public class Employee {
        private String employeeName;
    
        public Employee(String employeeName) {
            this.employeeName = employeeName;
        }
    
        public void getEmployeeDetails() {
            // Wyswietl szczegóły pracownika
        }
    }
    
    public class EmployeeDB {
        public void saveEmployee(Employee e) {
        // Zapisz pracownika do bazy danych
        }
    }

>W tym przypadku, zgodnie z zasadą jednej odpowiedzialności, klasa **Employee** jest odpowiedzialna za przechowywanie danych pracownika, a klasa **EmployeeDB** jest odpowiedzialna za zapisywanie pracownika do bazy danych.

**Interface Segregation Principle**:

    public interface EmployeeDetails {
        void getEmployeeDetails();
    }
    
    public interface EmployeeStorage {
    void saveEmployee(Employee e);
    }
    
    public class Employee implements EmployeeDetails {
    private String employeeName;
    
        public Employee(String employeeName) {
            this.employeeName = employeeName;
        }
    
        public void getEmployeeDetails() {
            // Wyswietl szczegóły pracownika
        }
    }
    
    public class EmployeeDB implements EmployeeStorage {
        public void saveEmployee(Employee e) {
        // Zapisz pracownika do bazy danych
        }
    }

>W tym przypadku zasada segregacji interfejsów jest przestrzegana poprzez podzielenie funkcji na dwa interfejsy: **EmployeeDetails** i **EmployeeStorage**. W ten sposób klasy mogą zależeć tylko od interfejsów, które faktycznie używają.

#### What do S & O stand for in SOLID? (Co oznacza S & O w SOLID?)

>Akronim SOLID reprezentuje pięć kluczowych zasad projektowania i struktury oprogramowania zorientowanego obiektowo. Te zasady pomagają tworzyć kod, który jest bardziej zrozumiały, elastyczny i łatwy do utrzymania.

>"S" w SOLID oznacza zasadę Single Responsibility (Jednej Odpowiedzialności). Ta zasada mówi, że klasa lub moduł powinien mieć tylko jeden powód do zmiany, co w praktyce oznacza, że powinien mieć tylko jedną odpowiedzialność.

>"O" w SOLID oznacza zasadę Open-Closed (Otwarty-Zamknięty). Ta zasada mówi, że "obiekty lub encje (takie jak klasy, moduły, funkcje itp.) powinny być otwarte na rozszerzenia, ale zamknięte na modyfikacje". Oznacza to, że klasa powinna być zaprojektowana tak, aby można było dodać nową funkcjonalność bez zmiany istniejącego kodu.

Przykładowy kod w Javie:

**Single Responsibility Principle**:

    public class Employee {
        private String employeeName;
    
        public Employee(String employeeName) {
            this.employeeName = employeeName;
        }
    
        public void getEmployeeDetails() {
            // Wyswietl szczegóły pracownika
        }
    }
    
    public class EmployeeDB {
        public void saveEmployee(Employee e) {
        // Zapisz pracownika do bazy danych
        }
    }

>W tym przypadku, zgodnie z zasadą jednej odpowiedzialności, klasa **Employee** jest odpowiedzialna za przechowywanie danych pracownika, a klasa **EmployeeDB** jest odpowiedzialna za zapisywanie pracownika do bazy danych.

**Open-Closed Principle**:

    public abstract class Shape {
        abstract void draw();
    }
    
    public class Circle extends Shape {
        void draw() {
        // Rysuj koło
        }
    }
    
    public class Square extends Shape {
        void draw() {
        // Rysuj kwadrat
        }
    }
    
    public class Drawing {
    private List<Shape> shapes;
    
        public Drawing(List<Shape> shapes) {
            this.shapes = shapes;
        }
    
        public void drawShapes() {
            for (Shape shape : shapes) {
                shape.draw();
            }
        }
    }

>Tutaj klasa **Drawing** jest otwarta na rozszerzenia (możemy łatwo dodawać nowe typy kształtów), ale zamknięta na modyfikacje (nie musimy modyfikować klasy **Drawing**, aby dodać nowy typ kształtu). Wszystko, co musimy zrobić, to utworzyć nową klasę, która rozszerza klasę **Shape** i zaimplementować metodę **draw()**.

#### What does "this" keyword do? (Co robi słowo kluczowe „to”?)

>Słowo kluczowe "this" w Javie odnosi się do bieżącego obiektu w metodzie lub konstruktorze. Główne zastosowania "this" to:

1. Wskazanie na bieżący obiekt w kontekście metody lub konstruktora.
2. Wywołanie jednego konstruktora z innego w tej samej klasie.
3. Przesłanianie nazw pól klasy przez parametry metody lub konstruktora.

Poniżej znajduje się przykład użycia "this" w Javie:

    public class Pracownik {
        private String imie;
    
        public Pracownik(String imie) {
            this.imie = imie; // 'this' wskazuje na pole 'imie' klasy, a nie na argument konstruktora
        }
    
        public void wyswietlImie() {
            System.out.println("Imię pracownika to: " + this.imie); // 'this' wskazuje na pole 'imie' bieżącego obiektu
        }
    
        public Pracownik() {
            this("Nieznane"); // 'this' służy do wywołania innego konstruktora w tej samej klasie
        }
    }

>W powyższym przykładzie, w konstruktorze **Pracownik(String imie)**, "this.imie" odnosi się do pola **imie** w bieżącym obiekcie, podczas gdy **imie** bez "this" odnosi się do argumentu konstruktora. W metodzie **wyswietlImie()**, "this.imie" odnosi się do pola imie w bieżącym obiekcie. W konstruktorze **Pracownik()**, "this("Nieznane")" wywołuje konstruktor **Pracownik(String imie)**.

#### What does it mean that an object is Immutable? (Co to znaczy, że obiekt jest niezmienny?)

>Obiekt nazywany jest niezmiennym (ang. immutable), gdy jego stan nie może być zmieniony po utworzeniu. Innymi słowy, po stworzeniu instancji klasy, wartości pól tej instancji nie mogą być zmienione.

>Niezmienniczość jest przydatna w wielu sytuacjach, szczególnie kiedy obiekt jest używany w kontekście wielowątkowym. Niezmienniczość gwarantuje, że obiekt zachowa swój stan nawet w obliczu jednoczesnej modyfikacji przez wiele wątków, co może prowadzić do większej stabilności i bezpieczeństwa aplikacji.

>Jednym z popularnych przykładów niezmiennej klasy w Javie jest klasa **String**.

>Możemy także stworzyć własną klasę niezmienną. Podstawowe zasady tworzenia klasy niezmiennej to:

1. Oznaczenie wszystkich pól jako **final**, aby ich wartości nie mogły być zmieniane po inicjalizacji.
2. Brak setterów, które mogłyby zmieniać stan obiektu.
3. Zapewnienie, że klasa nie może być rozszerzona (w Javie można to zrobić deklarując klasę jako **final**).
4. Jeśli klasa zawiera pola odnoszące się do obiektów zmiennych, musi zapewnić głęboką kopię tych pól podczas tworzenia i zwracania wartości.

Przykład klasy niezmiennej w Javie:

    public final class Osoba {
        private final String imie;
        private final String nazwisko;
    
        public Osoba(String imie, String nazwisko) {
            this.imie = imie;
            this.nazwisko = nazwisko;
        }
    
        public String getImie() {
            return imie;
        }
    
        public String getNazwisko() {
            return nazwisko;
        }
    }

>W powyższym przykładzie, po utworzeniu obiektu klasy **Osoba**, jego stan (wartości **imie** i **nazwisko**) nie mogą być zmienione.

#### What is a class? (Co to jest klasa?)

>Klasa w Javie, podobnie jak w wielu innych językach programowania obiektowego, jest szablonem lub niebieskim planem do tworzenia obiektów. Definiuje strukturę danych (pola, czasem nazywane atrybutami lub właściwościami) oraz zachowania (metody) obiektów.

>Struktura klasy w Javie zwykle obejmuje:

1. Pola (zmienne) - reprezentują stan obiektu.
2. Metody - reprezentują zachowanie obiektu.
3. Konstruktory - są specjalnymi metodami używanymi do inicjalizacji obiektów.

Oto przykład klasy **Samochod** w Javie:

    public class Samochod {
        // Pola klasy
        private String marka;
        private String model;
        private int rokProdukcji;
    
        // Konstruktor klasy
        public Samochod(String marka, String model, int rokProdukcji) {
            this.marka = marka;
            this.model = model;
            this.rokProdukcji = rokProdukcji;
        }
    
        // Metody klasy
        public String getMarka() {
            return marka;
        }
    
        public String getModel() {
            return model;
        }
    
        public int getRokProdukcji() {
            return rokProdukcji;
        }
    }

>W tym przykładzie, **Samochod** jest klasą z trzema polami (**marka**, **model**, **rokProdukcji**), konstruktorem do inicjalizacji tych pól i trzema metodami dostępu (getterami), które zwracają wartości pól.


#### What is a constructor? (Co to jest konstruktor?)

>Konstruktor to specjalna metoda w klasie, która jest wywoływana, gdy tworzy się nową instancję (obiekt) tej klasy. Nazwa konstruktora musi być taka sama jak nazwa klasy. Konstruktor nie ma typu zwracanego, nawet void.

>Konstruktory są używane do inicjalizacji pól obiektu podczas tworzenia obiektu. W Javie, jeśli nie zdefiniujesz żadnego konstruktora w klasie, kompilator Java automatycznie utworzy konstruktor domyślny (bezparametrowy). Jeśli jednak zdefiniujesz własny konstruktor, Java już nie dostarczy konstruktora domyślnego.

Przykład klasy z konstruktorem w Javie:

    public class Pies {
        private String imie;
        private String rasa;
    
        // Konstruktor klasy
        public Pies(String imie, String rasa) {
            this.imie = imie;
            this.rasa = rasa;
        }
    
        // Metody klasy
        public String getImie() {
            return imie;
        }
    
        public String getRasa() {
            return rasa;
        }
    }

>W powyższym przykładzie, konstruktor klasy **Pies** przyjmuje dwa parametry (**imie** i **rasa**) i inicjalizuje pola **imie** i **rasa** obiektu. Gdy tworzymy nowy obiekt klasy **Pies**, musimy dostarczyć te dwa argumenty:

    Pies mojPies = new Pies("Burek", "Labrador");

#### What is abstraction and why is it used? (Czym jest abstrakcja i dlaczego jest używana?)

>Abstrakcja to jeden z kluczowych konceptów programowania obiektowego, który pozwala na ukrycie szczegółów implementacji i pokazywanie tylko funkcjonalności użytkownikowi.

>W Javie abstrakcję można osiągnąć na dwa główne sposoby: za pomocą klas abstrakcyjnych i interfejsów.

>Klasa abstrakcyjna to klasa, która nie może być zainstancjonowana (nie możemy utworzyć obiektu tej klasy) i zwykle zawiera jedną lub więcej metod abstrakcyjnych (metod bez ciała). Klasa, która dziedziczy klasę abstrakcyjną, musi zaimplementować wszystkie jej metody abstrakcyjne (chyba że ta klasa również jest abstrakcyjna).

>Interfejs to kolekcja metod bez implementacji oraz stałych. Wszystkie metody w interfejsie są domyślnie publiczne i abstrakcyjne. Klasa implementująca interfejs musi zaimplementować wszystkie jego metody.

?Abstrakcja pomaga w zarządzaniu złożonością systemu poprzez podział na mniejsze, zarządzalne części. Ponadto, umożliwia to lepszą organizację kodu, zapewniając jednocześnie bezpieczeństwo (ukrywanie detali) i elastyczność (polimorfizm).

Oto przykład abstrakcji w Javie za pomocą klasy abstrakcyjnej:

        // Klasa abstrakcyjna
    abstract class Zwierze {
        // Metoda abstrakcyjna
        abstract void wydajDzwiek();
    }
    
    // Klasa Pies dziedziczy klasę Zwierze
    class Pies extends Zwierze {
        // Implementacja metody abstrakcyjnej
        void wydajDzwiek() {
            System.out.println("Hau! Hau!");
        }
    }
    
    // Klasa Kot dziedziczy klasę Zwierze
    class Kot extends Zwierze {
        // Implementacja metody abstrakcyjnej
        void wydajDzwiek() {
            System.out.println("Miau! Miau!");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Pies pies = new Pies();
            pies.wydajDzwiek();
            Kot kot = new Kot();
            kot.wydajDzwiek();
        }
    }

>W tym kodzie, **Zwierze** to klasa abstrakcyjna, a **Pies** i **Kot** są klasami, które dziedziczą po klasie **Zwierze** i implementują jej metodę abstrakcyjną **wydajDzwiek()**.

#### What is an abstraction? (Czym jest abstrakcja?)

>Abstrakcja to kluczowy koncept w programowaniu obiektowym, który pozwala na ukrycie szczegółów implementacji, skupiając się na tym, co dana klasa lub metoda robi, a nie jak to robi. To jest podobne do samochodu: nie musisz wiedzieć, jak działa silnik, aby go prowadzić.

>Abstrakcję w Javie realizujemy za pomocą klas abstrakcyjnych i interfejsów.

1. **Klasa abstrakcyjna** to taka, która nie może być bezpośrednio zainstancjonowana, tzn. nie możemy utworzyć jej obiektu. Może ona zawierać metody abstrakcyjne (metody bez ciała), które muszą być zaimplementowane przez każdą klasę, która dziedziczy po klasie abstrakcyjnej.

2. **Interfejs** to deklaracja typu w Javie, która składa się z metod. Klasy implementują interfejsy, co oznacza, że zapewniają ciała dla metod zadeklarowanych w interfejsie.

Oto przykład abstrakcji za pomocą klasy abstrakcyjnej:

    abstract class Samochod {    
        // metoda abstrakcyjna
        abstract void wypiszMaxPredkosc();
    }
    
    class Ferrari extends Samochod {
        void wypiszMaxPredkosc() {
            System.out.println("Max predkosc Ferrariego to 340 km/h.");
        }
    }
    
    class Fiat extends Samochod {
        void wypiszMaxPredkosc() {
            System.out.println("Max predkosc Fiata to 180 km/h.");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Ferrari ferrari = new Ferrari();
            ferrari.wypiszMaxPredkosc();
            Fiat fiat = new Fiat();
            fiat.wypiszMaxPredkosc();
        }
    }

>W tym kodzie, **Samochod** to klasa abstrakcyjna, a **Ferrari** i **Fiat** są klasami, które dziedziczą po klasie **Samochod** i implementują jej metodę abstrakcyjną w**ypiszMaxPredkosc()**.

#### What is an interface? (Co to jest interfejs?)

>Interfejs w Javie to deklaracja typu, która składa się z metod abstrakcyjnych i stałych. Klasy implementują interfejsy, co oznacza, że zapewniają ciała dla metod zadeklarowanych w interfejsie. Interfejsy są używane do uzyskania pełnej abstrakcji, ponieważ pozwalają one na utworzenie metod, które nie mają ciała.

Poniżej znajduje się przykład interfejsu w Javie:

    interface Zwierze {
        void dajGlos(); // metoda abstrakcyjna
    }
    
    class Pies implements Zwierze {
        public void dajGlos() {
            System.out.println("Hau! Hau!");
        }
    }
    
    class Kot implements Zwierze {
        public void dajGlos() {
            System.out.println("Miau! Miau!");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Pies pies = new Pies();
            pies.dajGlos();
            Kot kot = new Kot();
            kot.dajGlos();
        }
    }

>W tym przykładzie **Zwierze** to interfejs, który zawiera jedną metodę abstrakcyjną **dajGlos()**. Klasa **Pies** i **Kot** implementują ten interfejs, co oznacza, że dostarczają implementację dla metody **dajGlos()**. W ten sposób, za pomocą interfejsów, zapewniamy abstrakcję i umożliwiamy wielorakie dziedziczenie w Javie.

#### What is an object oriented program? (Co to jest program obiektowy?)

>Programowanie obiektowe (OOP) to paradygmat programowania, który wykorzystuje "obiekty" - instancje klas do projektowania aplikacji i programów. OOP pozwala na tworzenie modularnych programów oraz na ponowne użycie kodu. Jest to metoda strukturalna, która opiera się na koncepcji "obiektów", które mogą zawierać dane w postaci pól, znanych jako atrybuty; oraz kody, w postaci funkcji, znanych jako metody.

OOP jest oparte na czterech fundamentalnych koncepcjach:

1. **Enkapsulacja** - ukrywanie szczegółów implementacji, udostępnianie tylko bezpiecznych do użycia interfejsów.
2. **Dziedziczenie** - tworzenie nowych klas na podstawie istniejących klas.
3. **Polimorfizm** - wykorzystywanie jednego interfejsu do kontroli różnych implementacji kodu.
4. **Abstrakcja** - tworzenie prostych interfejsów do reprezentowania bardziej złożonych układów.

Oto prosty przykład obiektowego programowania w Javie:

    public class Samochod {
        // atrybuty
        private String marka;
        private String model;
        private int rok;
    
        // konstruktor
        public Samochod(String marka, String model, int rok) {
            this.marka = marka;
            this.model = model;
            this.rok = rok;
        }
    
        // metody
        public String getMarka() {
            return marka;
        }
    
        public String getModel() {
            return model;
        }
    
        public int getRok() {
            return rok;
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Samochod mojSamochod = new Samochod("Toyota", "Corolla", 2022);
            System.out.println("Moj samochod to: " + mojSamochod.getMarka() + " " + mojSamochod.getModel() + ", rok produkcji: " + mojSamochod.getRok());
        }
    }

>W powyższym kodzie **Samochod** jest klasą, która posiada trzy atrybuty (**marka**, **model** i **rok**), jeden konstruktor i trzy metody. W klasie **Main**, tworzymy obiekt **mojSamochod** typu **Samochod**, a następnie wykorzystujemy metody dostępu do wydrukowania szczegółów na temat tego samochodu.


#### What is an object? (Co to jest obiekt?)

>Obiekt w programowaniu obiektowym to instancja klasy. Klasa to zasadniczo szablon, który opisuje atrybuty i zachowania (metody) wspólne dla danego rodzaju obiektów. Obiekt jest konkretym wystąpieniem klasy, które zawiera rzeczywiste wartości dla tych atrybutów i zachowań zdefiniowanych w klasie.

>W kontekście języka Java, obiekt jest instancją klasy tworzonej za pomocą operatora new. Kiedy tworzymy obiekt, Java rezerwuje pamięć na przechowywanie jego stanu (wartości atrybutów) i powiązanych z nim metod.

Poniżej znajduje się prosty przykład tworzenia obiektu w Javie:

    public class Samochod {
        private String marka;
        private String model;
        private int rok;
    
        public Samochod(String marka, String model, int rok) {
            this.marka = marka;
            this.model = model;
            this.rok = rok;
        }
    
        public String getMarka() {
            return marka;
        }
    
        public String getModel() {
            return model;
        }
    
        public int getRok() {
            return rok;
        }
    }
    
    public class Main {
        public static void main(String[] args) {
        // Tworzymy obiekt klasy Samochod
        Samochod mojSamochod = new Samochod("Toyota", "Corolla", 2022);
        
            // Korzystamy z metód obiektu
            System.out.println("Moj samochod to: " + mojSamochod.getMarka() + " " + mojSamochod.getModel() + ", rok produkcji: " + mojSamochod.getRok());
        }
    }

>W tym przykładzie **Samochod** to klasa, a **mojSamochod** to obiekt klasy **Samochod**.

#### What is casting? What is the difference between up vs downcasting? (Co to jest casting? Jaka jest różnica między rzutowaniem w górę i w dół?)

>Rzutowanie (casting) w języku programowania to konwersja jednego typu na inny. W kontekście programowania obiektowego i języka Java, rzutowanie często odnosi się do zmiany typu referencji na obiekt.

>Rozróżniamy dwa rodzaje rzutowania - "upcasting" i "downcasting".

1. **Upcasting**: Jest to proces przekształcania referencji na klasę potomną do klasy nadrzędnej. Jest to zawsze bezpieczne, ponieważ klasa potomna jest typem klasy nadrzędnej. W Javie, upcasting wykonuje się automatycznie.

        class Zwierze {}
    
        class Pies extends Zwierze {}
        
        public class Main {
            public static void main(String[] args) {
                Pies pies = new Pies();
        
                // Upcasting
                Zwierze zwierze = pies;  // pies jest automatycznie rzutowany (upcasted) do typu Zwierze
            }
        }

2. **Downcasting**: Jest to proces przekształcania referencji na klasę nadrzędną do klasy podrzędnej. Downcasting jest niebezpieczne i wymaga jawnej deklaracji, ponieważ klasa nadrzędna nie jest typem klasy podrzędnej. Może to prowadzić do błędów w czasie wykonania, jeśli obiekt nie jest rzeczywiście instancją klasy, do której jest rzutowany.

       class Zwierze {}

       class Pies extends Zwierze {}
    
       public class Main {
           public static void main(String[] args) {
               Zwierze zwierze = new Zwierze();
    
               // Downcasting
               Pies pies = (Pies) zwierze;  // Rzutujemy Zwierze do Psa - to spowoduje błąd w czasie wykonania, ponieważ zwierze nie jest Psem
           }
       }

>W tym przykładzie próbujemy rzutować **zwierze** na **Pies**, co spowoduje **ClassCastException** w czasie wykonania, ponieważ **zwierze** nie jest instancją **Pies**.

#### What is encapsulation and why is it used? (Co to jest enkapsulacja i dlaczego jest stosowana?)

>Hermetyzacja, czyli Encapsulation, to jedna z fundamentalnych koncepcji programowania obiektowego. Polega na ukrywaniu szczegółów implementacyjnych klasy i udostępnianiu jedynie bezpiecznych metod do manipulowania danymi.

>W praktyce hermetyzacja osiągana jest przez ustawianie pól klasy jako prywatne (**private**) i udostępnianie publicznych metod dostępowych - getterów i setterów - do tych pól. Getter pozwala na odczytanie wartości pola, a setter pozwala na jej zmianę pod kontrolą klasy - możemy np. sprawdzić, czy nowa wartość jest poprawna zanim ją ustawimy.

Dzięki hermetyzacji:

1. Moduły programu są od siebie niezależne - zmiana implementacji jednego nie wpływa na inne
2. Dane są bezpieczne - nie mogą być zmienione bezpośrednio, tylko przez odpowiednie metody
3. Możemy kontrolować dostęp do danych - np. niektóre pola mogą być tylko do odczytu

Przykład zastosowania hermetyzacji w Javie:

    public class Osoba {
        // Pola są prywatne - dostęp do nich jest ograniczony do tej klasy
        private String imie;
        private String nazwisko;
    
        // Getter do pola "imie"
        public String getImie() {
            return imie;
        }
    
        // Setter do pola "imie"
        public void setImie(String imie) {
            // Możemy sprawdzić, czy imię jest poprawne zanim je ustawimy
            if (imie != null && !imie.isEmpty()) {
                this.imie = imie;
            }
        }
    
        // Analogicznie dla "nazwisko"
        public String getNazwisko() {
            return nazwisko;
        }
    
        public void setNazwisko(String nazwisko) {
            if (nazwisko != null && !nazwisko.isEmpty()) {
                this.nazwisko = nazwisko;
            }
        }
    }

>W tym przykładzie **Osoba** ma dwa prywatne pola: **imie** i **nazwisko**. Do manipulacji tymi polami służą publiczne metody - gettery i settery. Dzięki temu, nawet jeśli zmienimy sposób przechowywania imienia i nazwiska w klasie **Osoba**, inne części programu będą nadal działać, ponieważ używają one getterów i setterów, a nie bezpośrednio pól klasy.

#### What is Encapsulation? Explain the concept with a realistic example! (Co to jest enkapsulacja? Wyjaśnij pojęcie na realistycznym przykładzie!)

>Hermetyzacja (encapsulation) to jedna z podstawowych zasad programowania obiektowego. Hermetyzacja polega na ukrywaniu wewnętrznych detali działania obiektu i udostępnianiu jedynie niezbędnych do interakcji z nim elementów (metod i właściwości).

>Jest to połączenie danych obiektu z metodami tego obiektu. Użytkownicy obiektu widzą tylko jego interfejs, nie muszą znać szczegółów implementacji. Jeśli zmienimy sposób, w jaki obiekt przechowuje i manipuluje danymi, użytkownicy obiektu nie muszą tego wiedzieć, ponieważ interfejs pozostaje taki sam.

>Załóżmy, że mamy klasę BankAccount. Klasa ta ma dwie zmienne prywatne: balance (saldo) i accountNumber (numer konta). Chcemy, aby saldo i numer konta były bezpieczne, a dostęp do nich był ograniczony tylko przez metody w klasie BankAccount.

Poniżej przedstawiono przykład hermetyzacji w Javie:

    public class BankAccount {
        // zmienne prywatne
        private double balance;
        private String accountNumber;
        
        public BankAccount(String accountNumber, double initialBalance) {
            this.accountNumber = accountNumber;
            this.balance = initialBalance;
        }
        
        // publiczna metoda do wpłacania pieniędzy
        public void deposit(double amount) {
            if(amount > 0){
                balance += amount;
            }
        }
        
        // publiczna metoda do wypłacania pieniędzy
        public boolean withdraw(double amount) {
            if(amount > 0 && balance >= amount){
                balance -= amount;
                return true; // successful withdrawal
            }
            return false; // insufficient balance or invalid amount
        }
        
        // getter dla zmiennej balance
        public double getBalance() {
            return balance;
        }
        
        // getter dla zmiennej accountNumber
        public String getAccountNumber() {
            return accountNumber;
        }
        
        // metoda umożliwiająca ustawienie numeru konta powinna być ograniczona
        // w praktyce, numer konta jest zazwyczaj przypisywany raz i nie można go zmienić
    }

>W powyższym kodzie, mimo że zmienne balance i accountNumber są prywatne, możemy nadal wpłacać i wypłacać pieniądze oraz sprawdzać saldo i numer konta za pomocą publicznych metod. Jednak nie możemy bezpośrednio zmienić salda ani numeru konta z zewnątrz klasy. To jest właśnie hermetyzacja.

#### What is exception handling? (Co to jest obsługa wyjątków?)

>Obsługa wyjątków to mechanizm w językach programowania służący do radzenia sobie z błędami podczas wykonywania programu. Wyjątki są to błędy, które występują podczas wykonywania programu i przerywają normalny przepływ sterowania programu.

>W Javie, obsługa wyjątków jest zrealizowana za pomocą pięciu słów kluczowych: **try**, **catch**, **throw**, **throws** i **finally**.

* Blok **try** zawiera kod, który może potencjalnie generować wyjątek.
* Blok **catch** jest używany do przechwytywania i obsługi wyjątku, jeśli taki wystąpi w bloku try.
* Słowo kluczowe **throw** jest używane do ręcznego generowania wyjątków.
* Słowo kluczowe **throws** jest używane do deklarowania wyjątków, które mogą być generowane przez metodę, ale nie są przez nią obsługiwane.
* Blok **finally** jest blokiem kodu, który jest zawsze wykonywany, niezależnie od tego, czy wystąpi wyjątek, czy nie.

Poniżej znajduje się przykładowy kod, który ilustruje obsługę wyjątków w Javie:

    public class ExceptionHandlingExample {
        public static void main(String[] args) {
            try {
                int divideByZero = 5 / 0;
                System.out.println("Rest of code in try block");
            } catch (ArithmeticException e) {
                System.out.println("ArithmeticException => " + e.getMessage());
            } finally {
                System.out.println("This is the finally block and is always executed.");
            }
            
            System.out.println("Program continues...");
        }
    }

>W powyższym kodzie, próbujemy podzielić liczbę przez zero, co powoduje **ArithmeticException**. Wyjątek ten jest następnie przechwytywany i obsługiwany w bloku **catch**, a następnie blok **finally** jest wykonany. Po zakończeniu obsługi wyjątku, program kontynuuje normalne działanie.


#### What is garbage collection and when does it happen? (Co to jest garbage collection (zbieranie śmieci) i kiedy to się dzieje?)

>Zbieranie śmieci (ang. Garbage Collection, w skrócie GC) to proces zarządzania pamięcią w wielu językach programowania, w tym w Javie. Głównym celem GC jest automatyczne zwalnianie pamięci, która jest już nieużywana przez program.

>W Javie, kiedy tworzony jest nowy obiekt za pomocą słowa kluczowego new, pamięć jest automatycznie przydzielana na stercie (ang. heap). Jeżeli referencje do tego obiektu zostaną usunięte lub wyjdą z zasięgu, obiekt staje się nieosiągalny. Taka pamięć jest uważana za "śmieci", ponieważ nie może być użyta przez resztę programu.

>Garbage Collector działa w tle, aby zwolnić tę pamięć. Działa automatycznie, zazwyczaj kiedy program jest w stanie bezczynności lub kiedy sterta jest bliska wyczerpania dostępnej pamięci. W praktyce, dokładny czas działania GC zależy od konkretnej implementacji JVM i nie jest bezpośrednio kontrolowany przez programistę.

Poniżej znajduje się przykładowy kod, który ilustruje tworzenie i usuwanie referencji do obiektu:

    public class GarbageCollectionExample {
        public static void main(String[] args) {
            // tworzenie obiektu
            ObjectExample objectExample = new ObjectExample();
            
            // usuwanie referencji do obiektu
            objectExample = null;
            
            // wywołanie garbage collector
            System.gc();
        }
    }

>W powyższym kodzie, tworzymy obiekt **objectExample**, a następnie usuwamy referencję do tego obiektu, przypisując **null**. W efekcie, obiekt staje się nieosiągalny. Następnie wywołujemy metodę **System.gc()**, która sugeruje JVM, aby uruchomić Garbage Collector. Jednak należy pamiętać, że nie gwarantuje to natychmiastowego uruchomienia Garbage Collectora. Jest to tylko sugestia dla JVM.

#### What is inheritance? (Co to jest dziedziczenie?)

>Dziedziczenie to jedna z podstawowych zasad programowania obiektowego. W Javie, pozwala na tworzenie nowych klas na podstawie istniejących klas. Nowa klasa, zwana klasą pochodną lub podklasą, dziedziczy pola i metody klasy bazowej (superklasy). Dodatkowo, klasa pochodna może definiować własne pola i metody.

>Dziedziczenie jest wykorzystywane do osiągnięcia wielu celów, takich jak reużywalność kodu, organizacja kodu czy ułatwienie zrozumienia struktury programu.

Poniżej znajduje się przykład dziedziczenia w Javie:

    // klasa bazowa (superklasa)
    public class Zwierze {
        public void jedzenie() {
            System.out.println("Zwierze je");
        }
    }
    
    // klasa pochodna (podklasa)
    public class Pies extends Zwierze {
        public void szczekanie() {
            System.out.println("Pies szczeka");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Pies pies = new Pies();
            pies.jedzenie();  // metoda dziedziczona z klasy Zwierze
            pies.szczekanie();  // metoda definiowana w klasie Pies
        }
    }

>W powyższym przykładzie, klasa **Pies** dziedziczy z klasy **Zwierze**, co pozwala obiektowi klasy **Pies** na wywołanie metody **jedzenie()**. Klasa **Pies** definiuje również własną metodę **szczekanie()**.

#### What is method overloading?

>Przeładowanie metody, znane też jako overloading, to technika w programowaniu obiektowym, która pozwala na definiowanie więcej niż jednej metody o tej samej nazwie w klasie. Te metody różnią się jednak liczbą lub typami argumentów. Java korzysta z tej techniki do obsługi różnych sytuacji z różnymi parametrami w ramach tej samej klasy.

Poniżej znajduje się przykład przeładowania metody w Javie:

    public class PrzykladowaKlasa {

        // pierwsza metoda "wyswietl"
        void wyswietl(int a) {
            System.out.println("Wartość liczby: " + a);
        }
    
        // druga metoda "wyswietl", z dwoma parametrami
        void wyswietl(int a, int b) {
            System.out.println("Wartość pierwszej liczby: " + a + ", wartość drugiej liczby: " + b);
        }
    
        // trzecia metoda "wyswietl", z parametrem typu String
        void wyswietl(String msg) {
            System.out.println("Wiadomość: " + msg);
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            PrzykladowaKlasa obiekt = new PrzykladowaKlasa();
            obiekt.wyswietl(5);
            obiekt.wyswietl(7, 9);
            obiekt.wyswietl("Przykładowa wiadomość");
        }
    }

>W powyższym przykładzie, metoda **wyswietl** jest przeładowana - występuje trzy razy, ale za każdym razem z inną liczbą parametrów lub różnymi typami parametrów. W zależności od tego, jakie argumenty przekażemy podczas wywołania metody, zostanie wybrana odpowiednia wersja metody.


#### What is OOP? Inheritance? Polymorphism? Abstraction? Encapsulation?

>**OOP** - Obiektowe Programowanie (OOP) to paradygmat programowania, który polega na modelowaniu rzeczywistości za pomocą obiektów, które są instancjami klas. Klasa definiuje atrybuty (pola) i działania (metody), które obiekt może wykonać.

    public class Samochod {
        // atrybuty klasy Samochod
        String marka;
        String model;
    
        // metoda klasy Samochod
        void jedz() {
            System.out.println("Jadę!");
        }
    }

>**Dziedziczenie** - Dziedziczenie to mechanizm, który pozwala na utworzenie nowej klasy na podstawie istniejącej (klasy bazowej), dziedzicząc jej atrybuty i metody.

    public class SportowySamochod extends Samochod {
        // nowa metoda tylko dla SportowegoSamochod
        void przyspiesz() {
            System.out.println("Przyspieszam bardzo szybko!");
        }
    }

>**Polimorfizm** - Polimorfizm to zdolność obiektu do przyjmowania wielu form. Najczęstszym użyciem polimorfizmu w OOP występuje, gdy rodzic ma referencję do obiektu dziecka, a dziecko wykonuje daną metodę poprzez tę referencję.

    Samochod myCar = new SportowySamochod();
    myCar.jedz();  // Wywołanie metody z klasy SportowySamochod

>**Abstrakcja** - Abstrakcja to proces ukrywania szczegółów implementacji i pokazywania tylko funkcjonalności użytkownikowi. W Javie możemy osiągnąć abstrakcję za pomocą interfejsów i klas abstrakcyjnych.

    abstract class Pojazd {
        abstract void jedz();
    }
    
    class Samochod extends Pojazd {
        void jedz() {
            System.out.println("Samochód jedzie");
        }
    }

>**Enkapsulacja** - Enkapsulacja to mechanizm ukrywania danych (zmienne) i metod w jednym obiekcie i kontrolowania dostępu do tego obiektu. Enkapsulacja jest zazwyczaj osiągana za pomocą modyfikatorów dostępu, takich jak public, private i protected.


    public class Samochod {
        // atrybuty są ukryte (private)
        private String marka;
        private String model;
    
        // metody publiczne do dostępu i modyfikacji atrybutów
        public String getMarka() {
            return marka;
        }
    
        public void setMarka(String marka) {
            this.marka = marka;
        }
    
        // analogicznie dla modelu
    }

#### What is polymorphism and why is it used? (Co to jest polimorfizm i dlaczego jest używany?)

>**Polimorfizm** to jedno z fundamentalnych założeń paradygmatu programowania obiektowego, które pozwala obiektom różnych klas być traktowanymi jako instancje jednej wspólnej klasy. Dzięki temu, można tworzyć bardziej elastyczne i łatwiejsze do utrzymania struktury kodu.

>Polimorfizm w Javie pojawia się głównie w dwóch formach:

1. Polimorfizm dynamiczny (w czasie wykonania) - jest to przede wszystkim przesłanianie metod (overriding). Metoda jest wybierana do wykonania na podstawie faktycznego typu obiektu, a nie typu referencji, która do niego prowadzi.

2. Polimorfizm statyczny (w czasie kompilacji) - jest to przeciążanie metod (overloading). Metoda do wykonania jest wybierana na podstawie typów argumentów w momencie kompilacji.

Przykład polimorfizmu w Javie:

    abstract class Zwierze {
        abstract void dzwiek();
    }
    
    class Pies extends Zwierze {
        void dzwiek() {
            System.out.println("Hau hau");
        }
    }
    
    class Kot extends Zwierze {
        void dzwiek() {
            System.out.println("Miau miau");
        }
    }
    
    public class Main {
        public static void main(String[] args) {
            Zwierze mojPies = new Pies();
            Zwierze mojKot = new Kot();
    
            mojPies.dzwiek();  // wydrukuje "Hau hau"
            mojKot.dzwiek();   // wydrukuje "Miau miau"
        }
    }

>W tym przykładzie, obiekty klasy **Pies** i **Kot** są traktowane jako obiekty typu **Zwierze**, ale wywołanie metody **dzwiek()** powoduje wykonanie odpowiedniej wersji tej metody - zgodnej z faktycznym typem obiektu. To jest właśnie polimorfizm - różne formy działania w zależności od typu obiektu.

>Dzięki polimorfizmowi, możemy tworzyć bardziej ogólne i elastyczne struktury kodu - na przykład metody, które mogą pracować z różnymi typami obiektów, o ile tylko są one pewnego wspólnego typu (klasy bazowej lub interfejsu).

#### What is the difference between == and equals method? (Jaka jest różnica między metodą == a metodą równania?)

>Operator **==** oraz metoda **equals()** służą do porównywania dwóch wartości, ale działają na nieco inny sposób:

1. Operator **==** w Javie jest używany do porównywania prymitywnych typów danych, takich jak **int**, **char**, **double**, **boolean** itp. oraz do porównywania referencji w przypadku obiektów. Kiedy używamy operatora == do porównywania obiektów, to sprawdza on, czy oba odwołują się do tego samego obiektu w pamięci, nie sprawdza jednak, czy zawartość obiektów jest taka sama.

       String str1 = new String("Hello");
       String str2 = new String("Hello");
    
       System.out.println(str1 == str2); // Zwróci false, ponieważ str1 i str2 to dwie różne instancje obiektu

2. **Metoda equals()** jest metodą klasy Object w Javie, którą możemy przeciążać w naszych klasach, aby porównać obiekty pod kątem równości ich zawartości. Dla większości klas standardowych bibliotek Javy, takich jak String, Integer, Date i innych, metoda equals() jest już odpowiednio przeciążona, aby porównywać zawartość obiektów, a nie ich referencje.

       String str1 = new String("Hello");
       String str2 = new String("Hello");

       System.out.println(str1.equals(str2)); // Zwróci true, ponieważ zawartość str1 i str2 jest taka sama

>Wniosek: Jeśli chcemy porównać, czy dwie referencje wskazują na ten sam obiekt, używamy operatora **==**. Jeśli chcemy porównać, czy dwie referencje wskazują na obiekty o takiej samej zawartości, używamy metody **equals()**.

#### What is variable scoping? (Co to jest zakres zmiennej?)

>Zasięg zmiennej (ang. "variable scoping") to obszar programu, w którym dana zmienna jest dostępna i widoczna. W Javie możemy wyróżnić trzy podstawowe poziomy zasięgu dla zmiennych:

1. **Zasięg klasowy** - jeśli zmienna jest zdefiniowana na poziomie klasy (często nazywana zmienną instancji lub zmienną statyczną), jest dostępna we wszystkich metodach klasy.

       public class MyClass {
           // zmienna na poziomie klasy
           private int myVariable;

           public void myMethod() {
               // myVariable jest dostępna tutaj
               myVariable = 10;
           }
       }

2. **Zasięg lokalny/metody** - jeśli zmienna jest zdefiniowana wewnątrz metody, jest dostępna tylko wewnątrz tej metody.

        public class MyClass {
            public void myMethod() {
                // zmienna lokalna
                int myLocalVariable = 10;
                // myLocalVariable jest dostępna tylko tutaj, wewnątrz metody myMethod
            }
        }


3. **Zasięg bloku** - jeśli zmienna jest zdefiniowana wewnątrz bloku kodu (na przykład w bloku for, if lub while), jest dostępna tylko wewnątrz tego bloku.

        public class MyClass {
            public void myMethod() {
               for (int i = 0; i < 10; i++) {
                   // zmienna i jest dostępna tylko wewnątrz tego bloku for
               }
               // tutaj zmienna i już nie jest dostępna
            }
        }

>Pamiętaj, że dobrą praktyką jest ograniczanie zasięgu zmiennych do minimum - tzn. deklarowanie ich tak blisko miejsca użycia, jak to tylko możliwe. Pomaga to utrzymać kod czytelnym i zrozumiałym.

#### Whether static method can use non static members? (Czy metoda statyczna może używać elementów niestatycznych?)

>Metody statyczne nie mają dostępu do nie-statycznych członków (pól i metod) klasy. Powodem tego jest to, że metoda statyczna nie jest powiązana z żadnym konkretnym obiektem instancji klasy i jest współdzielona przez wszystkie instancje klasy. W związku z tym, nie ma dostępu do członków klasy, które są specyficzne dla danego obiektu.

Na przykład, jeśli mamy klasę **Przyklad** z metoda statyczną i polem niestatycznym:

    public class Przyklad {
        private int liczba = 5;
    
        public static void metodaStatyczna() {
            System.out.println(liczba);  // To spowoduje błąd kompilacji
        }
    }

>Przy próbie dostępu do pola **liczba** w **metodaStatyczna()**, kompilator wygeneruje błąd, ponieważ metoda statyczna nie ma dostępu do członków niestatycznych.

>Jeżeli chcesz użyć członka niestatycznego w metodzie statycznej, musisz stworzyć obiekt klasy, a następnie wywołać członek niestatyczny na tym obiekcie. Tutaj jest przykład jak to zrobić:

    public class Przyklad {
        private int liczba = 5;
    
        public static void metodaStatyczna() {
            Przyklad przyklad = new Przyklad();
            System.out.println(przyklad.liczba);  // Teraz to jest poprawne
        }
    }


#### What is a UML class diagram? What are the typical elements? (Co to jest diagram klas UML? Jakie są typowe elementy?)

>Diagram klas UML (Unified Modeling Language) to rodzaj diagramu statycznego strukturalnego, który jest używany w analizie obiektowej i projektowaniu obiektowym do opisania struktury systemu. Diagram klas UML pokazuje klasy systemu, ich atrybuty, metody i relacje między nimi.

Podstawowe elementy diagramu klas UML to:

1. **Klasa**: Klasa jest reprezentowana jako prostokąt podzielony na trzy sekcje: nazwa klasy, atrybuty klasy i metody klasy.

        -----------------
        |   KlasaX      |
        -----------------
        | - atrybut1    |
        | - atrybut2    |
        -----------------
        | + metoda1()   |
        | + metoda2()   |
        -----------------

2. **Dziedziczenie**: Dziedziczenie jest reprezentowane jako linia z pustym trójkątem skierowanym do klasy nadrzędnej.

        KlasaX
        ▲
        |
        KlasaY
        
3. **Asocjacja**: Asocjacja reprezentuje relację między dwoma klasami, które są połączone. To jest reprezentowane jako linia łącząca dwie klasy.
        
        KlasaX ◀──▶ KlasaY
        
4. **Agregacja**: Agregacja to specjalny typ asocjacji, który reprezentuje relację "całość-część". Jest reprezentowany jako pusta diamentowa strzałka skierowana do klasy "całości".
        
        KlasaX ◇──▶ KlasaY
        
5. **Kompozycja**: Kompozycja to bardziej rygorystyczny typ agregacji, który reprezentuje silną zależność "całość-część". Jest reprezentowany jako wypełniona diamentowa strzałka skierowana do klasy "całości".
        
        KlasaX ◆──▶ KlasaY

6. **Interfejsy** są reprezentowane podobnie do klas, ale zazwyczaj mają słowo "<<interfejs>>" napisane nad nazwą.


>W praktyce, aby stworzyć diagram UML w Javie, musiałbyś skorzystać z odpowiedniego narzędzia, takiego jak UMLet, Visual Paradigm, czy też zintegrowanych narzędzi w IDE, takich jak IntelliJ IDEA. W tych narzędziach możesz tworzyć diagramy UML zgodnie z konkretną strukturą i zależnościami w twoim kodzie.
