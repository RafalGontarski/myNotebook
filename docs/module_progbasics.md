# Programming Basic


#### Does Java have dynamic or static typing? What does it mean?
>Java używa statycznego typowania, co oznacza, że typy zmiennych muszą być zadeklarowane przed użyciem i nie mogą być zmieniane po deklaracji. Na przykład, jeśli zadeklarujesz zmienną jako int, nie możesz później przypisać do niej wartości String.

>Statyczne typowanie pomaga zapewnić większą bezpieczeństwo typów, ponieważ kompilator może wykryć błędy typów przed uruchomieniem programu. W rzeczywistości, Java jest silnie typowana, co oznacza, że nie wykonuje automatycznych konwersji typów, które mogą prowadzić do nieoczekiwanych wyników.

Przykład:

    int number = 10; // deklaracja zmiennej typu int
    number = "Hello"; // to spowoduje błąd kompilacji, ponieważ "Hello" jest Stringiem, a nie int

>Ten kod nie zostanie skompilowany, ponieważ próbujemy przypisać wartość String do zmiennej, która została zadeklarowana jako int. To jest przykład, jak statyczne typowanie w Javie pomaga wykrywać błędy przed uruchomieniem programu.

#### Throws keyword

>W Javie, słowo kluczowe **throws** jest używane w deklaracji metody do wskazania, że metoda może rzucić wyjątek określonego typu. Wyjątki są sytuacjami, które mogą wystąpić podczas wykonywania programu i które zakłócają normalny przepływ sterowania programu.

>Gdy metoda może rzucić wyjątek, musi to zgłosić, używając słowa kluczowego **throws**. Jeśli wywołujesz metodę, która zgłasza wyjątek, musisz albo obsłużyć ten wyjątek, używając bloku **try**/**catch**, albo zgłosić go dalej, dodając **throws** do deklaracji swojej metody.

Przykład:

    public class Main {
        public static void main(String[] args) {
            try {
                riskyMethod();
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    
        static void riskyMethod() throws Exception {
            // kod, który może rzucić wyjątek
            throw new Exception("To jest wyjątek");
        }
    }

>W tym przykładzie metoda **riskyMethod()** deklaruje, że może rzucić wyjątek **Exception**, używając słowa kluczowego **throws**. Metoda **main()** wywołuje **riskyMethod()** i obsługuje możliwy wyjątek, używając bloku **try**/**catch**.

#### Try-catch block (how does it work?)

>Blok **try**/**catch** jest używany w Javie do obsługi wyjątków, które mogą wystąpić podczas wykonywania programu. Wyjątki to nieprzewidziane błędy, które zakłócają normalny przepływ sterowania programu.

>Blok **try** zawiera kod, który może potencjalnie wygenerować wyjątek. Blok **catch** natomiast jest używany do przechwycenia i obsługi wyjątku, jeśli taki wystąpi.

>Jeśli podczas wykonania kodu w bloku **try** wystąpi wyjątek, przepływ sterowania jest natychmiast przekazywany do odpowiedniego bloku **catch**, który może obsłużyć ten typ wyjątku. Po obsłużeniu wyjątku, przepływ sterowania kontynuowany jest po bloku **catch**.

Przykład:

    public class Main {
        public static void main(String[] args) {
            try {
                int[] numbers = new int[5];
                numbers[10] = 50; // To wygeneruje ArrayIndexOutOfBoundsException
            } catch (ArrayIndexOutOfBoundsException e) {
                System.out.println("Wystąpił błąd: " + e);
            }
        }
    }

>W tym przykładzie, próbujemy przypisać wartość do indeksu, który jest poza zakresem tablicy. To generuje wyjątek **ArrayIndexOutOfBoundsException**. Ponieważ ten kod jest w bloku **try**, wyjątek jest przechwytywany i obsługiwany w bloku **catch**, który wyświetla komunikat o błędzie.

#### Try-catch-with-resources block (how does it work?)

>Konstrukcja **try**-with-resources, wprowadzona w Javie 7, jest specjalną wersją bloku **try**/**catch**, która pozwala na automatyczne zamknięcie zasobów używanych w bloku **try**. "Zasoby" tutaj to obiekty, które implementują interfejs **java.lang.AutoCloseable** lub **java.io.Closeable**, co oznacza, że mają metodę **close()**, która może być wywołana, gdy zasób nie jest już potrzebny.

>Główną zaletą **try**-with-resources jest to, że nie musimy ręcznie zamykać zasobów (co jest zwykle konieczne, by uniknąć wycieków pamięci lub innego rodzaju problemów zasobów). Java automatycznie zamknie te zasoby dla nas, niezależnie od tego, czy w bloku **try** wystąpi wyjątek, czy nie.

Przykład:

    import java.io.BufferedReader;
    import java.io.FileReader;
    import java.io.IOException;
    
    public class Main {
        public static void main(String[] args) {
            try (BufferedReader br = new BufferedReader(new FileReader("plik.txt"))) {
                String line;
                while ((line = br.readLine()) != null) {
                    System.out.println(line);
                }
            } catch (IOException e) {
                System.out.println("Wystąpił błąd podczas czytania pliku: " + e);
            }
        }
    }

>W tym przykładzie, **BufferedReader** jest zasobem, który jest otwarty w bloku **try** i automatycznie zamykany po zakończeniu bloku, niezależnie od tego, czy wystąpi wyjątek, czy nie. Jeśli podczas czytania pliku wystąpi **IOException**, jest on przechwytywany i obsługiwany w bloku **catch**.

#### What are the differences between `break` and `continue` keywords?

>Słowa kluczowe **break** i **continue** w Javie są używane do kontrolowania przepływu w pętlach (**for**, **while**, **do-while**).

>**break**: Słowo kluczowe **break** jest używane do natychmiastowego zakończenia całej pętli. Po wywołaniu **break**, sterowanie jest przekazywane do pierwszej instrukcji po pętli.

>**continue**: Słowo kluczowe **continue** jest używane do natychmiastowego zakończenia bieżącej iteracji pętli i rozpoczęcia następnej iteracji. Instrukcje po **continue** w bieżącej iteracji nie są wykonywane.

Oto przykład ilustrujący różnicę:

    public class Main {
        public static void main(String[] args) {
            for (int i = 0; i < 10; i++) {
                if (i == 5) {
                    break; // Przerywa całą pętlę, jeśli i jest równa 5
                }
                System.out.println(i);
            }
    
            for (int i = 0; i < 10; i++) {
                if (i == 5) {
                    continue; // Przechodzi do następnej iteracji pętli, pomijając wartość 5
                }
                System.out.println(i);
            }
        }
    }

>W pierwszej pętli, po osiągnięciu **i == 5**, **break** przerywa całą pętlę i nie drukuje żadnych wartości dla **i >= 5**.

>W drugiej pętli, kiedy **i == 5**, **continue** pomija resztę tej iteracji i przechodzi do następnej, więc **5** nie jest drukowane, ale pętla kontynuuje działanie dla **i > 5**.

#### What are the differences between `import` and `static import` keywords?

>Słowa kluczowe **import** i **static import** są używane w Javie do importowania klas, metod i zmiennych ze zdefiniowanych pakietów.

>**import**: Słowo kluczowe **import** jest używane do importowania całych klas lub całych pakietów. Dzięki temu możemy korzystać z klas bez potrzeby podawania pełnej nazwy klasy (wraz z nazwą pakietu) za każdym razem, gdy z niej korzystamy.

>**static import**: **static import** jest specjalnym rodzajem importu, który pozwala na bezpośrednie importowanie statycznych członków (metod i zmiennych) klasy, bez potrzeby podawania nazwy klasy za każdym razem, gdy z nich korzystamy.

Przykład:

    import java.util.Arrays; // normalny import
    import static java.lang.Math.PI; // static import
    
    public class Main {
        public static void main(String[] args) {
            int[] numbers = {5, 3, 2, 1, 4};
            Arrays.sort(numbers); // możemy użyć sort() bez podawania pełnej nazwy klasy Arrays
        
            System.out.println(PI); // możemy użyć PI bez podawania pełnej nazwy klasy Math
        }
    }

>W tym przykładzie, zaimportowaliśmy klasę **Arrays** i statyczny członek **PI** klasy **Math**. Dzięki temu możemy używać **sort()** i **PI** bez podawania pełnej nazwy klasy.

#### What are the differences between `private` and `package-private` access modifiers?

>W Javie mamy cztery modyfikatory dostępu: **private**, **package-private** (domyślny, kiedy nie używamy żadnego modyfikatora), **protected** i **public**. Definiują one, gdzie klasa, metoda lub zmienna mogą być dostępne.

>**private**: Elementy oznaczone jako **private** są dostępne tylko wewnątrz klasy, w której są zdefiniowane. Nie mogą być dostępne z innych klas, nawet jeśli te klasy są w tym samym pakiecie.

>**package-private** (domyślny): Jeśli element nie ma żadnego modyfikatora dostępu (jest **package-private**), jest dostępny dla wszystkich klas w tym samym pakiecie. Nie jest dostępny dla klas w innych pakietach.

Oto przykład:

    package com.example;

    public class MyClass {
        private int privateVariable = 1; // dostępne tylko w MyClass
        int packagePrivateVariable = 2; // dostępne dla wszystkich klas w pakiecie com.example
    }

>W tym przykładzie **privateVariable** jest dostępne tylko wewnątrz **MyClass**. **packagePrivateVariable** jest dostępne dla wszystkich klas w pakiecie **com.example**, ale nie jest dostępne dla klas w innych pakietach.

#### What are the differences between `protected` and `package-private` access modifiers?

>W Javie, modyfikatory **protected** i **package-private** (domyślny, kiedy nie używamy żadnego modyfikatora) są używane do określenia dostępności klas, metod i zmiennych.

>**package-private** (domyślny): Jeśli element nie ma żadnego modyfikatora dostępu, jest dostępny dla wszystkich klas w tym samym pakiecie. Nie jest dostępny dla klas w innych pakietach.

>**protected**: Elementy oznaczone jako **protected** są dostępne dla wszystkich klas w tym samym pakiecie, podobnie jak dla **package-private**. Ale dodatkowo, są one dostępne również dla klas w innych pakietach, które dziedziczą po klasie, w której element jest zdefiniowany.

Oto przykład:

    package com.example;

    public class MyClass {
        protected int protectedVariable = 1; // dostępne dla wszystkich klas w pakiecie com.example oraz klas dziedziczących po MyClass
        int packagePrivateVariable = 2; // dostępne dla wszystkich klas w pakiecie com.example
    }

>W tym przykładzie **protectedVariable** jest dostępne dla wszystkich klas w pakiecie **com.example**, oraz dla wszystkich klas w innych pakietach, które dziedziczą po **MyClass**. **packagePrivateVariable** jest dostępne tylko dla klas w pakiecie **com.example**.

#### What are the differences between `public` and `protected` access modifiers?

>Modyfikatory dostępu **public** i **protected** w Javie służą do określenia, gdzie klasa, metoda lub zmienna mogą być dostępne.

>**public**: Kiedy element (klasa, metoda, zmienna) jest oznaczony jako **public**, jest on dostępny wszędzie. Można do niego uzyskać dostęp z dowolnej klasy, niezależnie od tego, czy znajduje się ona w tym samym pakiecie, czy nie.

>**protected**: Elementy oznaczone jako **protected** są dostępne dla wszystkich klas w tym samym pakiecie, a także dla klas w innych pakietach, które dziedziczą po klasie, w której element jest zdefiniowany.

Przykład:

    package com.example;

    public class MyClass {
        public int publicVariable = 1; // dostępne wszędzie
        protected int protectedVariable = 2; // dostępne dla wszystkich klas w pakiecie com.example oraz klas dziedziczących po MyClass
    }

>W tym przykładzie **publicVariable** jest dostępna wszędzie, więc można do niej uzyskać dostęp z dowolnej klasy, niezależnie od tego, czy jest ona w tym samym pakiecie, czy nie. Z kolei **protectedVariable** jest dostępna dla wszystkich klas w pakiecie **com.example**, a także dla klas dziedziczących po **MyClass** w innych pakietach.

#### What are the differences between == and equals?
>W Javie, **==** i **equals()** są obie używane do porównywania obiektów, ale istnieje między nimi istotna różnica.

* Operator **==** jest używany do porównywania referencji do obiektów, a nie faktycznych wartości tych obiektów. Oznacza to, że **==** zwróci **true** tylko wtedy, gdy obie referencje wskazują na ten sam obiekt.

* Metoda **equals()** jest używana do porównywania wartości dwóch obiektów. Dla klas, które nie nadpisują metody **equals()**, domyślna implementacja z klasy **Object** działa tak samo jak operator **==**, porównując referencje. Jednak wiele klas, takich jak **String**, **Integer**, **Date**, itp., nadpisuje metodę **equals()**, aby umożliwić porównywanie faktycznych wartości obiektów.

Przykład:

    String s1 = new String("Hello");
    String s2 = new String("Hello");
    
    System.out.println(s1 == s2); // wyświetla "false", ponieważ s1 i s2 to dwie różne referencje do dwóch różnych obiektów
    
    System.out.println(s1.equals(s2)); // wyświetla "true", ponieważ s1 i s2 mają taką samą wartość ("Hello")

>W tym przykładzie, **s1** i **s2** to dwie różne referencje do dwóch różnych obiektów, więc **s1 == s2** zwraca **false**. Jednak **s1** i **s2** mają tę samą wartość ("Hello"), więc **s1.equals(s2)** zwraca **true**.

#### What are the differences between Arrays and Lists?

>Tablice (**Arrays**) i listy (**Lists**) są dwoma fundamentalnymi strukturami danych w Javie, ale istnieje między nimi kilka kluczowych różnic:

>**Rozmiar**: Rozmiar tablicy jest stały i nie może być zmieniany po jej utworzeniu. Z drugiej strony, listy są dynamiczne, co oznacza, że ich rozmiar może się zmieniać (mogą rosnąć i maleć) w trakcie wykonywania programu.

>**Typy**: Tablice mogą przechowywać zarówno typy pierwotne (takie jak **int**, **char**, **boolean** itp.), jak i typy obiektowe (takie jak **Integer**, **String**, **Object** itp.). Listy natomiast mogą przechowywać tylko typy obiektowe.

>**Metody**: Listy, jako część kolekcji w Javie, oferują szereg użytecznych metod, takich jak **add()**, **remove()**, **contains()**, **size()** itp., których tablice nie oferują.

Oto przykład, który ilustruje te różnice:

    import java.util.ArrayList;
    import java.util.List;
    
    public class Main {
        public static void main(String[] args) {
            int[] array = new int[3]; // tablica o stałym rozmiarze 3
            array[0] = 1;
            array[1] = 2;
            array[2] = 3;
            // array[3] = 4; // to spowoduje błąd, ponieważ rozmiar tablicy jest stały
        
            List<Integer> list = new ArrayList<>(); // lista o dynamicznym rozmiarze
            list.add(1);
            list.add(2);
            list.add(3);
            list.add(4); // to jest w porządku, ponieważ rozmiar listy jest dynamiczny
        }
    }

>W tym przykładzie, tablica **array** ma stały rozmiar i nie można do niej dodać więcej elementów po jej utworzeniu. Z drugiej strony, lista **list** ma dynamiczny rozmiar, więc możemy dodawać do niej elementy na bieżąco.

#### What are the differences between Lists and Maps?

>**List** i **Map** to dwa podstawowe interfejsy kolekcji w Javie, które mają różne cechy:

* **Struktura danych**: **List** jest liniową strukturą danych, która przechowuje elementy w porządku dodawania, podobnie do tablic. Każdy element w liście ma indeks, który jest używany do dostępu do tego elementu. Z drugiej strony, **Map** jest strukturą danych opartą na kluczach, która przechowuje pary klucz-wartość. Każda wartość jest powiązana z unikalnym kluczem, który jest używany do dostępu do tej wartości.

* **Unikalność elementów**: W **List**, elementy mogą się powtarzać. Tzn. możemy mieć wiele elementów o tej samej wartości. W przypadku **Map**, klucze są unikalne. Nie możemy mieć dwóch par klucz-wartość z tym samym kluczem. Jeśli spróbujemy dodać parę klucz-wartość z kluczem, który już istnieje, stara wartość powiązana z tym kluczem zostanie zastąpiona nową wartością.

Oto przykład, który ilustruje te różnice:

    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
    
    public class Main {
        public static void main(String[] args) {
            List<String> list = new ArrayList<>();
            list.add("apple");
            list.add("banana");
            list.add("apple"); // to jest dozwolone, elementy mogą się powtarzać
    
            Map<String, Integer> map = new HashMap<>();
            map.put("apple", 1);
            map.put("banana", 2);
            map.put("apple", 3); // klucz "apple" był już użyty, stara wartość zostanie zastąpiona nową
        }
    }

>W tym przykładzie, lista **list** przechowuje elementy w porządku dodawania, a elementy mogą się powtarzać. Mapa **map** przechowuje pary klucz-wartość, a klucze są unikalne.



#### What are the differences between Lists and Sets?

>**List** i **Set** to dwa podstawowe interfejsy kolekcji w Javie, które mają różne cechy:

* **Unikalność elementów**: W **List**, elementy mogą się powtarzać. To znaczy, że możemy mieć wiele elementów o tej samej wartości. Z drugiej strony, **Set** przechowuje tylko unikalne elementy. Jeśli spróbujemy dodać element, który już istnieje w zbiorze, nie zostanie on dodany ponownie.

* **Porządek elementów**: **List** przechowuje elementy w porządku ich dodania. Każdy element ma określony indeks, podobnie jak w tablicy. **Set** nie gwarantuje żadnego konkretnego porządku elementów. Istnieją jednak pewne implementacje **Set**, takie jak **LinkedHashSet**, które zachowują porządek dodawania, lub **TreeSet**, które przechowują elementy w porządku naturalnym.

Oto przykład, który ilustruje te różnice:

    import java.util.ArrayList;
    import java.util.HashSet;
    import java.util.List;
    import java.util.Set;
    
    public class Main {
        public static void main(String[] args) {
            List<String> list = new ArrayList<>();
            list.add("apple");
            list.add("banana");
            list.add("apple"); // to jest dozwolone, elementy mogą się powtarzać
    
            Set<String> set = new HashSet<>();
            set.add("apple");
            set.add("banana");
            set.add("apple"); // nie zostanie dodane, ponieważ "apple" już istnieje w zbiorze
        }
    }

>W tym przykładzie, lista **list** przechowuje elementy w porządku ich dodawania i pozwala na powtarzające się elementy. Zbiór **set** przechowuje tylko unikalne elementy i nie gwarantuje żadnego konkretnego porządku.

#### What is a bytecode?

>Bytecode, zwany też kodem bajtowym, to forma pośrednia kodu, która jest bardziej abstrakcyjna niż kod maszynowy. Głównym celem bytecode'u jest zapewnienie platformowej niezależności kodu, co oznacza, że ten sam bytecode może być uruchamiany na różnych systemach operacyjnych bez konieczności modyfikacji.

>W kontekście Javy, po napisaniu i skompilowaniu kodu źródłowego, kompilator Javy (javac) generuje bytecode, który jest zapisywany w plikach .class. Bytecode ten jest później interpretowany lub skompilowany do natywnego kodu maszynowego przez Java Virtual Machine (JVM) podczas wykonania.

Na przykład, jeżeli mamy plik **HelloWorld.java**:

    public class HelloWorld {
        public static void main(String[] args) {
            System.out.println("Hello, World!");
        }
    }

Gdy skompilujemy go za pomocą kompilatora Javy (javac):
    
    javac HelloWorld.java

>Kompilator wygeneruje plik **HelloWorld.class**, który zawiera bytecode Javy. Bytecode ten można potem uruchomić na dowolnej maszynie, która ma zainstalowaną Java Virtual Machine (JVM), niezależnie od systemu operacyjnego. Bytecode jest zatem jednym z kluczowych elementów umożliwiających przenośność kodu w Javie.

#### What is a constructor? What does it return?

>Konstruktor to specjalna metoda w klasie, która jest wywoływana automatycznie podczas tworzenia obiektu tej klasy. Konstruktor ma tę samą nazwę, co nazwa klasy i nie ma typu zwracanego (nawet void).

>Konstruktor jest używany do inicjalizacji obiektów. Możemy zdefiniować konstruktor, aby przypisać początkowe wartości do pól obiektu lub aby wykonać jakiekolwiek inne operacje setupowe, które są potrzebne przed użyciem obiektu.

>Jeśli nie zdefiniujemy żadnego konstruktora w klasie, Java automatycznie dostarczy konstruktor domyślny (bez argumentów), który nie robi nic poza tworzeniem obiektu.

Poniżej znajduje się przykład klasy z konstruktorem:

    public class Student {
        private String name;
        private int age;
    
        // To jest konstruktor
        public Student(String name, int age) {
            this.name = name;
            this.age = age;
        }
    }

Aby utworzyć obiekt klasy **Student**, używamy konstruktora w taki sposób:

    Student student = new Student("Jan Kowalski", 20);

>Jak widać, konstruktor **Student** przyjmuje dwa argumenty (name i age) i używa ich do inicjalizacji pól obiektu.

>Konstruktor nie zwraca żadnej wartości. Słowo **new** jest używane do tworzenia nowego obiektu, a konstruktor jest wywoływany, aby zainicjować ten obiekt. Wartością zwracaną przez wyrażenie **new Student("Jan Kowalski", 20)** jest nowy obiekt klasy **Student**.

#### What is Boxing and Unboxing?

>Boxing i Unboxing to mechanizmy w Javie, które umożliwiają automatyczne konwertowanie między typami pierwotnymi (np. int, char, boolean etc.) a ich odpowiadającymi klasami opakowującymi (Integer, Character, Boolean etc.).

>**Boxing** to proces automatycznego konwertowania wartości typu pierwotnego na obiekt klasy opakowującej. Na przykład:

    int i = 10;
    Integer boxed = i;  // Autoboxing

>W tym przypadku, wartość **i** typu pierwotnego **int** jest automatycznie konwertowana (boxed) do obiektu klasy **Integer**.

>**Unboxing** to proces automatycznego konwertowania obiektu klasy opakowującej z powrotem na wartość typu pierwotnego. Na przykład:

    Integer boxed = new Integer(10);
    int unboxed = boxed;  // Unboxing

>W tym przypadku, obiekt **boxed** klasy **Integer** jest automatycznie konwertowany (unboxed) z powrotem na wartość typu pierwotnego **int**.

>Mechanizmy te są bardzo użyteczne, ponieważ umożliwiają łatwe używanie typów pierwotnych i klas opakowujących zamiennie, szczególnie podczas pracy z kolekcjami, które mogą przechowywać tylko obiekty, a nie typy pierwotne.

#### What is Function Overriding and Overloading in Java?

>**Przeładowanie funkcji (Function Overloading)** w Javie występuje, gdy w klasie definiowane są dwie lub więcej metod o tej samej nazwie, ale z różną liczbą lub typami argumentów. Kompilator wybiera odpowiednią metodę do wywołania na podstawie typów argumentów podanych podczas wywołania metody.

Przykład przeładowania metody:

    public class OverloadExample {
        void display(String s) {
            System.out.println("Witaj, " + s);
        }
    
        void display(int i) {
            System.out.println("Liczba to: " + i);
        }
    }

>W powyższym przykładzie metoda **display** jest przeładowana - raz przyjmuje argument typu **String**, a drugi raz typu **int**.

>**Przesłanianie funkcji (Function Overriding)** w Javie występuje, gdy podklasa definiuje metodę, która już istnieje w jej klasie nadrzędnej. Metoda w klasie pochodnej musi mieć tę samą nazwę, ten sam typ zwracany i tę samą listę argumentów, co metoda w klasie nadrzędnej. Przesłonięcie metody pozwala nam zdefiniować specyficzne dla klasy zachowanie dla metody, która już jest dostarczana przez jej klasę nadrzędną.

Przykład przesłonięcia metody:

    public class Animal {
        void makeSound() {
            System.out.println("Dźwięk zwierzęcia...");
        }
    }
    
    public class Dog extends Animal {
        // przesłonięcie metody makeSound
        @Override
        void makeSound() {
            System.out.println("Hau, Hau!");
        }
    }

>W powyższym przykładzie metoda **makeSound** w klasie **Dog** przesłania metodę **makeSound** z klasy nadrzędnej **Animal**. Dzięki temu, gdy wywołamy metodę **makeSound** na obiekcie klasy **Dog**, zostanie wywołana metoda zdefiniowana w klasie **Dog**, a nie ta z klasy **Animal**.


#### What is static initializer?

>Statyczny blok inicjalizacyjny (Static Initialization Block) to specjalny blok kodu w Javie, który jest używany do inicjalizacji statycznych zmiennych w klasie. Ten blok jest wykonywany tylko raz, kiedy klasa jest załadowana do pamięci.

>Statyczny blok inicjalizacyjny jest zdefiniowany w klasie za pomocą słowa kluczowego **static**, a potem nawiasów klamrowych **{}**. Wszystko, co znajduje się wewnątrz tych nawiasów, jest wykonane, kiedy klasa jest załadowana. Jeśli w klasie istnieje więcej niż jeden statyczny blok inicjalizacyjny, są one wykonywane w kolejności, w jakiej zostały zdefiniowane w klasie.

Oto przykład statycznego bloku inicjalizacyjnego:

    public class Example {
        // Statyczna zmienna
        static int i;
      
        // Statyczny blok inicjalizacyjny
        static {
            i = 10;
            System.out.println("Statyczny blok inicjalizacyjny wywołany.");
        }
    }

>W tym przypadku, statyczny blok inicjalizacyjny inicjalizuje zmienną i wartością 10 i wyświetla komunikat, kiedy klasa **Example** jest załadowana do pamięci.

>Statyczne bloki inicjalizacyjne są użyteczne, kiedy inicjalizacja statycznej zmiennej wymaga więcej logiki, niż tylko przypisanie wartości. Może to obejmować wywoływanie metod, operacje na kolekcjach, obsługa wyjątków i tak dalej.

#### What is the difference between static and abstract methods?

>Metody statyczne i abstrakcyjne w Javie są bardzo różne.

>**Statyczne metody** są metodami, które należą do samej klasy, a nie do instancji (obiektu) klasy. Można je wywołać bez tworzenia obiektu klasy. Statyczne metody są zazwyczaj używane do wykonywania operacji, które nie są związane z konkretnym obiektem klasy. Metody statyczne mogą bezpośrednio dostępować tylko do statycznych zmiennych i metod.

Przykład metody statycznej:

    public class Example {
    static void staticMethod() {
        System.out.println("To jest metoda statyczna.");
    }
    }
    
    // Wywołanie metody statycznej
    Example.staticMethod();

>**Abstrakcyjne metody** są deklarowane, ale nie są implementowane w klasie abstrakcyjnej. Klasa, która dziedziczy klasę abstrakcyjną, musi dostarczyć implementację dla tych metod, chyba że sama jest klasą abstrakcyjną. Abstrakcyjne metody są używane, gdy wszystkie klasy pochodne powinny mieć daną metodę, ale implementacja tej metody będzie się różnić w zależności od klasy.

Przykład metody abstrakcyjnej:

    public abstract class Animal {
        abstract void makeSound();
    }
    
    public class Dog extends Animal {
        // Implementacja metody abstrakcyjnej
        void makeSound() {
            System.out.println("Hau, Hau!");
        }
    }
    
    // Użycie
    Animal myDog = new Dog();
    myDog.makeSound();  // Wypisze "Hau, Hau!"

>Ważnym punktem do zrozumienia jest to, że **metody abstrakcyjne nie mogą być statyczne**. Metoda abstrakcyjna jest związana z obiektem (jest wywoływana na obiekcie), a metoda statyczna nie jest związana z obiektem. Metoda abstrakcyjna musi być przesłonięta w klasie pochodnej, a metoda statyczna nie może być przesłonięta w klasie pochodnej (może być ukryta, ale to nie to samo co przesłonięcie).

#### What is the main difference between StringBuffer and StringBuilder?

>**StringBuffer** i **StringBuilder** to dwie klasy w Javie, które są używane do tworzenia i modyfikowania łańcuchów znaków.

>**Główna różnica** między nimi polega na tym, że **StringBuffer** jest synchronizowany, co oznacza, że jest bezpieczny do użycia w środowisku wielowątkowym, podczas gdy **StringBuilder** nie jest synchronizowany, co oznacza, że nie jest bezpieczny do użycia w środowisku wielowątkowym.

>W związku z tym, **StringBuilder** jest generalnie szybszy, ponieważ nie musi zapewniać bezpieczeństwa wątku, które może być kosztowne pod względem wydajności. Z drugiej strony, **StringBuffer** powinien być używany, gdy istnieje ryzyko dostępu do obiektu przez wiele wątków jednocześnie.

Poniżej znajduje się przykład użycia obu klas:

    // Użycie StringBuffer
    StringBuffer stringBuffer = new StringBuffer("Hello");
    stringBuffer.append(" World");
    System.out.println(stringBuffer); // Wypisze "Hello World"
    
    // Użycie StringBuilder
    StringBuilder stringBuilder = new StringBuilder("Hello");
    stringBuilder.append(" World");
    System.out.println(stringBuilder); // Wypisze "Hello World"

>W obu przypadkach, metoda **append** jest używana do dodania łańcucha " World" do istniejącego łańcucha "Hello". Obie klasy mają bardzo podobne API, więc różnica w użyciu wynika głównie z kontekstu, w którym są używane (tj. czy istnieje ryzyko dostępu do obiektu przez wiele wątków jednocześnie czy nie).

#### When we use hashCode() method?

>Metoda **hashCode()** w Javie jest częścią kontraktu pomiędzy metodami **equals(Object other)** i **hashCode()**, który jest zdefiniowany w klasie **Object**, z której wszystkie inne klasy w Javie są dziedziczone.

>Metoda **hashCode()** jest używana, gdy używamy obiektu jako klucza w mapie lub elementu w secie, takim jak **HashMap** lub **HashSet**. Głównym celem metody **hashCode()** jest zwrócenie wartości liczbowej dla danego obiektu, aby struktury danych mogły skutecznie przechowywać i pobierać obiekt.

Przykład użycia metody **hashCode()**:

    String name = "John";
    int hash = name.hashCode();
    System.out.println("Hashcode dla stringa 'John' to: " + hash);

>Zgodnie z kontraktem pomiędzy **equals()** i hashCode(), jeśli dwa obiekty są równe według metody **equals()**, to muszą mieć tę samą wartość **hashCode()**. To znaczy, jeśli mamy własną klasę i nadpisujemy metodę **equals()**, powinniśmy również nadpisać metodę **hashCode()**, aby zachować ten kontrakt.

Przykład nadpisania metody **hashCode()**:

    public class Student {
        private String name;
    
        // konstruktor, gettery, settery itd.
    
        @Override
        public int hashCode() {
            return name.hashCode();
        }
        
        @Override
        public boolean equals(Object obj) {
            if (this == obj) return true;
            if (obj == null || getClass() != obj.getClass()) return false;
            Student student = (Student) obj;
            return Objects.equals(name, student.name);
        }
    }

>W tym przypadku, metoda **hashCode()** jest nadpisana tak, aby zwracała wartość **hashCode()** dla pola **name**. Zauważ, że jeśli dwóch studentów ma to samo imię, będą mieli ten sam kod **hashCode()**. Metoda ****equals()**** jest również nadpisana, aby porównywać studentów na podstawie ich imion.

#### Which class is a superclass for other classes?

>W Javie, wszystkie klasy mają superklasę, a domyślną superklasą dla każdej klasy, która nie dziedziczy bezpośrednio z innej klasy, jest klasa **Object**. To oznacza, że **Object** jest w efekcie superklasą dla wszystkich klas w Javie.

>Klasa **Object** dostarcza metody, które są uniwersalne dla wszystkich obiektów, takie jak **equals(Object)**, **hashCode()**, **toString()**, **getClass()**, **notify()**, **wait()**, itd. Te metody można nadpisać w klasach pochodnych, aby dostosować ich działanie do specyficznych potrzeb tych klas.

>Poniżej znajduje się przykład klasy, która dziedziczy bezpośrednio z klasy **Object** (choć nie musimy jawnie tego pisać, ponieważ każda klasa dziedziczy z **Object** domyślnie):

    public class MyCustomClass {
        // pola, metody, konstruktory etc.
        
        @Override
        public String toString() {
            // dostosowujemy metodę toString() do naszych potrzeb
            return "To jest moja własna klasa!";
        }
    }

    MyCustomClass myObject = new MyCustomClass();
    System.out.println(myObject.toString()); // wypisze: "To jest moja własna klasa!"

>W tym przykładzie, klasa **MyCustomClass** dziedziczy z klasy **Object**, a my nadpisujemy metodę **toString()**, która pochodzi z klasy **Object**, aby dostosować jej działanie do naszych potrzeb.