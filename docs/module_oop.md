# OOP

#### Define a constructor?
>A constructor in Java is a special method that is called when an object of a class is created. It is used to initialize the object's fields and can also perform any other initialization required by the object.

**Here's an example of a constructor in Java:**


    public class Person {
        private String name;
        private int age;
    
        public Person(String name, int age) {
            this.name = name;
            this.age = age;
        }
        
        public void setName(String name) {
            this.name = name;
        }
        
        public String getName() {
            return name;
        }
        
        public void setAge(int age) {
            this.age = age;
        }
        
        public int getAge() {
            return age;
        }
    }

>In this example, we have defined a class **Person** with two private fields **name** and **age**. The constructor of the **Person** class takes two arguments, **name** and **age**, and initializes the corresponding fields of the object using the **this** keyword. The **this** keyword refers to the current instance of the object being created.

>We have also defined getter and setter methods for the **name** and **age** fields. These methods can be used to get and set the values of the fields for an object of the **Person** class. 

**Here's an example of how to create an object of the Person class using the constructor:**

    Person person = new Person("John", 25);

>In this example, we create a new **Person** object called **person** and pass the arguments "John" and 25 to the constructor. The constructor initializes the **name** and **age** fields of the object to "John" and 25 respectively.


#### Difference between overloading and overriding?

>Overloading and overriding are two concepts in object-oriented programming that are used to create methods with different behavior.

>Overloading refers to defining multiple methods in a class with the same name but different parameters. These methods can have different signatures, such as different types or numbers of arguments. When a method is called, the appropriate method is selected based on the number and types of arguments passed to it.

Here's an example of method overloading in Java:


    public class Calculator {
        public int add(int x, int y) {
        return x + y;
        }
    
        public double add(double x, double y) {
            return x + y;
        }
    
        public int add(int x, int y, int z) {
            return x + y + z;
        }
    }

>In this example, we have defined three methods with the same name add, but different parameter lists. The appropriate method is selected based on the number and types of arguments passed to it.

>Overriding, on the other hand, refers to defining a method in a subclass that has the same name and signature as a method in the superclass. The subclass method overrides the superclass method, providing a new implementation for it. When a method is called on an object of the subclass, the overridden method in the subclass is called instead of the method in the superclass.

Here's an example of method overriding in Java:


    public class Animal {
        public void makeSound() {
        System.out.println("The animal makes a sound");
        }
    }

    public class Cat extends Animal {
        @Override
        public void makeSound() {
        System.out.println("The cat meows");
        }
    }

>In this example, we have defined a class Animal with a method makeSound, and a subclass Cat that overrides the makeSound method. When the makeSound method is called on a Cat object, the overridden method in the Cat class is called, which prints "The cat meows" to the console.

>In summary, overloading is used to define multiple methods with the same name but different parameters, while overriding is used to provide a new implementation for a method in a subclass that has the same name and signature as a method in the superclass.

#### Do we require parameters for constructors?

>Parametry w konstruktorach nie są wymagane, ale są bardzo użyteczne, gdy chcemy przekazać jakieś dane do obiektu podczas jego tworzenia.

>Konstruktory to specjalne metody, które są automatycznie wywoływane podczas tworzenia obiektu. Służą do inicjalizacji obiektu, często poprzez ustawianie wartości początkowych dla jego pól.

>W języku Java, na przykład, klasa może mieć konstruktor bezparametrowy, ale może też mieć konstruktory, które przyjmują parametry.

Oto przykład klasy **Osoba** z konstruktorem, który przyjmuje dwa parametry:

    public class Osoba {
        private String imie;
        private String nazwisko;
    
        public Osoba() {
            // to jest konstruktor bezparametrowy
        }
    
        public Osoba(String imie, String nazwisko) {
            // to jest konstruktor z parametrami
            this.imie = imie;
            this.nazwisko = nazwisko;
        }
    }

Jeśli chcemy stworzyć nowy obiekt klasy **Osoba**, używamy operatora **new** wraz z konstruktorem:

    Osoba osobaBezParametrow = new Osoba(); // używamy konstruktora bezparametrowego

    Osoba osobaZParametrami = new Osoba("Jan", "Kowalski"); // używamy konstruktora z parametrami

>Dzięki konstruktorom z parametrami możemy łatwo i wygodnie zainicjować nowo tworzony obiekt. Jednak to nie jest wymagane i można zawsze używać konstruktorów bezparametrowych i następnie ustawiać pola obiektu poprzez metody dostępowe.

#### Explain the “Single Responsibility” principle!

>Zasada "Single Responsibility" (SRP) to jedna z pięciu zasad SOLID, które są podstawą dobrego projektowania oprogramowania obiektowego. SRP mówi, że "klasa powinna mieć tylko jeden powód do zmiany". Inaczej mówiąc, każda klasa powinna mieć tylko jedno zadanie, odpowiedzialność lub obowiązek.

>Zastosowanie zasady SRP pomaga utrzymać kod czystym, łatwym do zrozumienia, testowania i utrzymania, ponieważ zmiany w jednym miejscu mają małe szanse na wpływ na inne części systemu.

>Zobaczmy to na przykładzie w języku Java:

Złe użycie zasady Single Responsibility:

    public class Uzytkownik {
        private String imie;
        private String email;
    
        public Uzytkownik(String imie, String email) {
            this.imie = imie;
            this.email = email;
        }
    
        public void zapiszDoBazyDanych() {
            // logika związana z zapisywaniem użytkownika do bazy danych
        }
    
        public void wyslijEmail() {
            // logika związana z wysyłaniem emaila
        }
    }

>W powyższym kodzie, klasa Uzytkownik jest odpowiedzialna za przechowywanie danych użytkownika, zapisywanie użytkownika do bazy danych oraz wysyłanie e-maili. To jest złamanie zasady Single Responsibility, ponieważ klasa Uzytkownik ma więcej niż jeden powód do zmiany.

Dobre użycie zasady Single Responsibility:

    public class Uzytkownik {
        private String imie;
        private String email;
    
        public Uzytkownik(String imie, String email) {
            this.imie = imie;
            this.email = email;
        }
    }
    
    public class BazaDanychUzytkownikow {
        public void zapisz(Uzytkownik uzytkownik) {
        // logika związana z zapisywaniem użytkownika do bazy danych
        }
    }
    
    public class EmailService {
        public void wyslijEmail(Uzytkownik uzytkownik) {
        // logika związana z wysyłaniem emaila
        }
    }

>W tym przypadku, każda klasa ma tylko jeden powód do zmiany. Klasa **Uzytkownik** jest odpowiedzialna za przechowywanie danych użytkownika. Klasa **BazaDanychUzytkownikow** jest odpowiedzialna za zapisywanie użytkowników do bazy danych. Klasa **EmailService** jest odpowiedzialna za wysyłanie e-maili. Każda z tych klas jest teraz zgodna z zasadą Single Responsibility.

#### How do you prevent developers from changing the value of a variable?

>Aby zapobiec zmianie wartości zmiennej przez programistów, możemy skorzystać z kilku technik. Jednym z popularnych podejść, zwłaszcza w językach programowania obiektowego takich jak Java, jest zastosowanie modyfikatora **final** oraz hermetyzacja (encapsulation).

>Modyfikator **final** zapobiega zmianie wartości zmiennej po jej zainicjowaniu. Przykładowo:

    public final int LICZBA = 10;

>W powyższym przykładzie **LICZBA** to stała, której wartości nie można zmienić po jej zainicjowaniu.

>Hermetyzacja (encapsulation) polega na ukrywaniu danych obiektu poprzez deklarację ich jako **private** i udostępnianiu dostępu do nich tylko za pomocą publicznych metod dostępowych, tzw. getterów i setterów. Możemy pominąć implementację settera dla pola, które nie powinno być modyfikowalne. Oto przykład:

    public class KlasaPrzykladowa {
        private final int liczba;
    
        public KlasaPrzykladowa(int liczba) {
            this.liczba = liczba;
        }
    
        public int getLiczba() {
            return this.liczba;
        }
    }

>W tym przypadku pole **liczba** jest prywatne i finalne, więc nie można go zmienić po zainicjowaniu (co odbywa się w konstruktorze). Dostęp do tego pola jest możliwy tylko za pomocą metody **getLiczba()**. Nie dostarczamy metody **setLiczba()**, co zapobiega modyfikacji tego pola po zainicjowaniu obiektu.

>Dzięki takiemu podejściu możemy zapewnić kontrolę nad tym, które pola naszych obiektów mogą być modyfikowane, a które powinny pozostać niezmienne.

#### How do you prevent developers from inheriting a class?

>W językach programowania obiektowego, takich jak Java, możemy zapobiegać dziedziczenia po klasie, stosując modyfikator **final**. Kiedy klasa jest oznaczona jako **final**, inne klasy nie mogą dziedziczyć po niej.

Oto przykład użycia modyfikatora **final** w Javie:

    public final class KlasaFinalna {
        // Kod klasy
    }

>Teraz, jeśli spróbujemy stworzyć nową klasę, która dziedziczy po **KlasaFinalna**, otrzymamy błąd kompilacji:

    public class InnaKlasa extends KlasaFinalna {  // Błąd: Nie można dziedziczyć po klasie oznaczonej jako final
        // Kod klasy
    }

>Oznaczenie klasy jako **final** jest silnym narzędziem, które należy używać z rozwagą. Może to ograniczyć elastyczność kodu i możliwość jego ponownego użycia, ponieważ uniemożliwia tworzenie podklas. Z drugiej strony, klasa final gwarantuje, że jej zachowanie nie zostanie zmienione przez klasy pochodne, co może być przydatne w przypadku klas, które nie są przeznaczone do bycia rozszerzanymi.

#### How do you prevent developers from overriding a method in a child class?

>Aby zapobiec nadpisywaniu metody w klasie pochodnej (child class), można zastosować modyfikator **final** do metody w klasie bazowej (parent class). Kiedy metoda jest oznaczona jako **final**, nie można jej nadpisać w klasie pochodnej.

Oto przykład użycia modyfikatora **final** w Javie:

    public class KlasaBazowa {
        public final void metodaFinalna() {
            System.out.println("Jestem metoda finalna i nie można mnie nadpisać.");
        }
    }

Jeśli teraz spróbujesz nadpisać **metodaFinalna()** w klasie pochodnej, spotkasz się z błędem kompilacji:

    public class KlasaPochodna extends KlasaBazowa {
        @Override
        public void metodaFinalna() {  // Błąd: Nie można nadpisać metody finalnej
            System.out.println("Próba nadpisania metody finalnej.");
        }
    }

>Modyfikator **final** jest użyteczny, gdy chcesz zagwarantować, że konkretne zachowanie metody nie zostanie zmienione w klasach pochodnych. Jednak, podobnie jak w przypadku oznaczania całych klas jako **final**, jego użycie powinno być dobrze przemyślane, aby nie ograniczać niepotrzebnie możliwości rozszerzenia i modyfikacji kodu.

#### How do you prevent developers from overriding a method in a subclass?

>Aby zapobiec nadpisywaniu metody w klasie pochodnej, można zastosować modyfikator **final** do metody w klasie bazowej. Kiedy metoda jest oznaczona jako **final**, nie można jej nadpisać w klasie pochodnej.

Oto przykład użycia modyfikatora **final** w Javie:


    public class KlasaBazowa {
        public final void metodaFinalna() {
        System.out.println("Jestem metoda finalna i nie można mnie nadpisać.");
        }
    }

Teraz, jeśli spróbujesz nadpisać **metodaFinalna()** w klasie pochodnej, spotkasz się z błędem kompilacji:

    public class KlasaPochodna extends KlasaBazowa {
        @Override
        public void metodaFinalna() {  // Błąd: Nie można nadpisać metody finalnej
        System.out.println("Próba nadpisania metody finalnej.");
        }
    }

>Modyfikator **final** jest przydatny, gdy chcesz zagwarantować, że konkretna implementacja metody nie zostanie zmieniona przez klasy pochodne. Ale podobnie jak przy oznaczaniu całej klasy jako **final**, jego użycie powinno być dobrze przemyślane, aby nie ograniczyć niepotrzebnie możliwości rozszerzenia kodu.

#### How do you prevent developers from subclassing a class?



#### What are access modifiers?



#### What are base class, subclass and superclass?



#### What are different types of arguments? (context: pass by value / pass by reference)



#### What are generic types and why are they used?



#### What are mutable and immutable types?



#### What are the differences between abstract classes and interfaces?



#### What are the differences between classes and objects?



#### What are the differences between overriding and overloading?



#### What are the differences between static and instance members?



#### What do S & D stand for in SOLID?



#### What do S & I stand for in SOLID?



#### What do S & O stand for in SOLID?



#### What does "this" keyword do?



#### What does it mean that an object is Immutable?
#### What is a class?
#### What is a constructor?
#### What is abstraction and why is it used?
#### What is an abstraction?
#### What is an interface?
#### What is an object oriented program?
#### What is an object?
#### What is casting? What is the difference between up vs downcasting?
#### What is encapsulation and why is it used?
#### What is Encapsulation? Explain the concept with a realistic example!
#### What is exception handling?
#### What is garbage collection and when does it happen?
#### What is inheritance?
#### What is Inheritance? Explain the concept with a realistic example!
#### What is method overloading?
#### What is OOP? Inheritance? Polymorphism? Abstraction? Encapsulation?
#### What is polymorphism and why is it used?
#### What is Polymorphism? Explain the concept with a realistic example!
#### What is the difference between == and equals method?
#### What is variable scoping?
#### Whether static method can use non static members?
#### What is a UML class diagram? What are the typical elements?