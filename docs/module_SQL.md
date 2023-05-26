# SQL

#### What do you know about database normalization?

>Database normalization is the process of organizing data in a database in such a way that it reduces redundancy and dependency. This helps to ensure data integrity and consistency and makes it easier to maintain and update the database.

>The normalization process involves dividing a database into two or more tables and defining relationships between them. The goal is to eliminate data duplication and ensure that each piece of data is stored in only one place in the database.

**There are several normal forms in database normalization, each with its own set of rules and requirements. The most commonly used normal forms are:**

* First Normal Form (1NF): This requires that each table has a primary key and that each column contains atomic (indivisible) values.

* Second Normal Form (2NF): This requires that each non-key column is dependent on the entire primary key and not just a part of it.

* Third Normal Form (3NF): This requires that each non-key column is dependent only on the primary key and not on any other non-key columns.

>There are additional normal forms beyond 3NF, such as Boyce-Codd Normal Form (BCNF) and Fourth Normal Form (4NF), but they are less commonly used.

>Normalization is important in database design because it helps to reduce data redundancy, which can lead to inconsistencies and data errors. It also makes it easier to maintain and update the database over time, as changes to one table do not affect other tables in the database. However, normalization can also result in more complex database schemas and slower database performance, so it's important to strike a balance between normalization and performance.


#### How can you connect your application to a database server? What are the possible ways?

>Aby połączyć swoją aplikację z serwerem bazy danych w Javie, potrzebujesz sterownika JDBC (Java Database Connectivity) dla konkretnej bazy danych, z którą chcesz się połączyć. JDBC to API, które umożliwia komunikację Javy z różnymi bazami danych, takimi jak MySQL, PostgreSQL, Oracle, SQLite itp.

Istnieje kilka sposobów na połączenie aplikacji z serwerem bazy danych. Oto kilka z nich:

> ## 1. Połączenie za pomocą JDBC:

        import java.sql.Connection;
        import java.sql.DriverManager;
        import java.sql.SQLException;

        public class DbConnect {
            public static void main(String[] args) {
                String url = "jdbc:mysql://localhost:3306/myDatabase";
                String username = "myUsername";
                String password = "myPassword";
        
                try (Connection connection = DriverManager.getConnection(url, username, password)) {
                    System.out.println("Połączenie z bazą danych powiodło się!");
                } catch (SQLException e) {
                    System.out.println("Połączenie z bazą danych nie powiodło się!");
                    e.printStackTrace();
                }
            }
        }

>Ten przykład pokazuje, jak nawiązać połączenie z bazą danych MySQL. Zauważ, że do tego potrzebny jest sterownik JDBC dla MySQL.

> ## 2. Połączenie za pomocą JPA (Java Persistence API) i Hibernate:

>JPA to specyfikacja, a Hibernate to jedna z jej implementacji. Hibernate jest frameworkiem, który ułatwia mapowanie obiektowo-relacyjne (ORM) i abstrahuje wiele szczegółów niskiego poziomu związanych z połączeniem z bazą danych.

    import javax.persistence.EntityManager;
    import javax.persistence.EntityManagerFactory;
    import javax.persistence.Persistence;

    public class App {
        public static void main(String[] args) {
            EntityManagerFactory emf = Persistence.createEntityManagerFactory("myPersistenceUnit");
            EntityManager em = emf.createEntityManager();
            
            em.getTransaction().begin();
    
            // operacje na bazie danych...
    
            em.getTransaction().commit();
    
            em.close();
            emf.close();
        }
    }

>Ten przykład pokazuje, jak nawiązać połączenie z bazą danych za pomocą Hibernate. Zauważ, że wymaga to pliku **persistence.xml** w katalogu **src/main/resources/META-INF**, który konfiguruje połączenie z bazą danych.

> ## 3. Połączenie za pomocą Spring Data JPA:

>Spring Data JPA jest częścią Spring Framework i ułatwia korzystanie z JPA poprzez dostarczanie gotowych do użycia repozytoriów i automatycznego konfigurowania Hibernate.

    import org.springframework.data.jpa.repository.JpaRepository;
    
    public interface UserRepository extends JpaRepository<User, Long> {
    }

>W tym przykładzie **UserRepository** jest repozytorium, które możemy użyć do wykonywania operacji na bazie danych związanych z użytkownikami. Spring Data JPA automatycznie dostarcza wiele standardowych metod, takich jak **findAll()**, **findById()**, **save()**, **delete()**, itp. Zauważ, że to wymaga konfiguracji Spring Boot i Spring Data JPA.


#### Indexes at database.

>Indeksy w bazie danych służą do przyspieszenia operacji wyszukiwania danych. Możemy to porównać do indeksu w książce - zamiast przeglądać całą książkę, aby znaleźć konkretną informację, możemy odnaleźć ją w indeksie i dowiedzieć się, na której stronie się znajduje.

>Indeks w bazie danych jest strukturą, która przechowuje wartości z wybranej kolumny (lub kolumn) w taki sposób, że ułatwia szybkie odnajdywanie rekordów. Bez indeksu, baza danych musiałaby przeszukać każdy rekord w tabeli, aby znaleźć te, które pasują do zapytania (co nazywamy "pełnym skanowaniem tabeli"). Ale z indeksem, baza danych może odnaleźć pasujące rekordy bardzo szybko.

>Można stworzyć indeks na kolumnie za pomocą polecenia **CREATE INDEX** w SQL. Na przykład, aby utworzyć indeks na kolumnie **nazwisko** w tabeli **osoby**, możemy użyć następującego polecenia:

      CREATE INDEX idx_osoby_nazwisko
      ON osoby (nazwisko);

>Indeksy mogą przyspieszać operacje odczytu, ale mogą spowalniać operacje zapisu (takie jak **INSERT**, **UPDATE** i **DELETE**), ponieważ baza danych musi aktualizować indeksy przy każdej zmianie danych. Dlatego warto rozważyć, które kolumny naprawdę potrzebują indeksów.

>Ważne jest, aby pamiętać, że indeksy są narzędziem, które może znacząco poprawić wydajność zapytań, ale wymaga również odpowiedniego planowania i zarządzania. Zbyt wiele indeksów, szczególnie w tabelach, które często ulegają zmianom, może prowadzić do spowolnienia systemu, zamiast przyspieszenia. Dlatego decyzja o dodaniu indeksu powinna być podejmowana po analizie wydajności i zrozumieniu potrzeb aplikacji.

#### The difference between WHERE and HAVING

>**WHERE** i **HAVING** są klauzulami w SQL, które są używane do filtrowania wyników zapytania. Chociaż obie są używane do filtrowania, różnią się tym, kiedy i jak są stosowane.

> ## WHERE

Klauzula **WHERE** jest używana do filtrowania wyników na etapie wiersza danych. Używamy jej, gdy chcemy ograniczyć wyniki zapytania na podstawie wartości w konkretnych kolumnach. Można jej używać z takimi operacjami jak **SELECT**, **UPDATE** i **DELETE**.

Przykład użycia **WHERE**:

      SELECT * FROM pracownicy WHERE pensja > 5000;

>W tym zapytaniu wybieramy wszystkie rekordy z tabeli **pracownicy**, gdzie pensja jest większa niż 5000.

> ## HAVING

> Klauzula **HAVING** jest używana do filtrowania wyników na etapie grupowania danych (tj. po użyciu **GROUP BY**). Klauzulę **HAVING** stosuje się głównie, gdy chcemy filtrować wyniki na podstawie warunku, który dotyczy agregatów, takich jak **SUM**, **AVG**, **COUNT**, **MAX**, **MIN** itp.

Przykład użycia **HAVING**:

      SELECT department_id, AVG(pensja) as srednia_pensja
      FROM pracownicy
      GROUP BY department_id
      HAVING AVG(pensja) > 5000;

>W tym zapytaniu grupujemy pracowników według **department_id**, obliczamy średnią pensję w każdym departamencie, a następnie wybieramy tylko te grupy, w których średnia pensja przekracza 5000.

>Podsumowując, kluczowa różnica polega na tym, że **WHERE** jest używane do filtrowania przed agregacją, a **HAVING** do filtrowania po agregacji.

#### What are aggregate functions in SQL? Give 3 examples.

>Funkcje agregujące w SQL są to typ funkcji, które wykonują obliczenia na zestawie wartości i zwracają pojedynczą wartość. Są one często używane w połączeniu z klauzulą GROUP BY w zapytaniu SQL, aby zgrupować zestaw wyników według jednego lub więcej kolumn.

Oto trzy przykłady funkcji agregujących:

1. **COUNT()**: Ta funkcja zwraca liczbę wierszy, które spełniają określone kryterium. Na przykład:

        SELECT COUNT(*) FROM pracownicy;

Zwróci liczbę wszystkich wierszy w tabeli "pracownicy".

2. **SUM()**: Ta funkcja zwraca sumę wartości określonej kolumny. Na przykład:

        SELECT SUM(placa) FROM pracownicy;

Zwróci sumę płac wszystkich pracowników.

3. **AVG()**: Ta funkcja zwraca średnią wartość określonej kolumny. Na przykład:

        SELECT AVG(placa) FROM pracownicy;

Zwróci średnią płacę pracowników.

>Inne funkcje agregujące w SQL obejmują **MIN()**, **MAX()**, **GROUP_CONCAT()**, **STDDEV()** i wiele innych.

#### What are database transactions? When to use?

>Transakcje baz danych to jednostka pracy wykonana w systemie zarządzania bazą danych (DBMS), która jest traktowana w sposób spójny i niepodzielny. Oznacza to, że albo wszystkie operacje w ramach transakcji są zakończone pomyślnie (commit), albo żadna z nich nie jest zakończona (rollback), w przypadku gdy wystąpi jakikolwiek błąd.

>Transakcje są istotne, gdy operacje na danych muszą być wykonywane jako całość. Na przykład, jeżeli przesyłasz pieniądze z jednego konta bankowego na drugie, chcesz, aby obie operacje (debit na jednym koncie i credit na drugim) zostały wykonane razem. Jeśli tylko jedna z nich by się powiodła, stan konta bankowego mógłby być niepoprawny.

Oto przykład transakcji w SQL:

        BEGIN TRANSACTION;

        UPDATE Konto SET Saldo = Saldo - 100 WHERE Id = 1; -- debit
        UPDATE Konto SET Saldo = Saldo + 100 WHERE Id = 2; -- credit
        
        IF @@ERROR = 0
        COMMIT TRANSACTION;
        ELSE
        ROLLBACK TRANSACTION;

>Ten kod to próba przelania 100 jednostek pieniężnych z konta o ID 1 na konto o ID 2. **BEGIN TRANSACTION** rozpoczyna transakcję, a **COMMIT TRANSACTION** zatwierdza transakcję. Jeśli wystąpi jakikolwiek błąd (sprawdzany za pomocą **@@ERROR**), **ROLLBACK TRANSACTION** anuluje transakcję, cofając wszystkie zmiany.

>Transakcje są również istotne dla zachowania integralności danych i zapewnienia spójności bazy danych. Transakcje baz danych opierają się na czterech właściwościach, znanych jako ACID (Atomicity, Consistency, Isolation, Durability), czyli Atomowość, Spójność, Izolacja, Trwałość.


#### What are the differences between DELETE and DROP?

>**DELETE** i **DROP** to dwa różne polecenia SQL, które są używane do usuwania danych z bazy danych, ale mają różne zastosowania i konsekwencje.

* **DELETE**: Polecenie **DELETE** jest używane do usunięcia wierszy z tabeli. Możesz określić, które wiersze chcesz usunąć za pomocą klauzuli **WHERE**. Jeśli nie użyjesz klauzuli **WHERE**, polecenie **DELETE** usunie wszystkie wiersze z tabeli, ale sama tabela wciąż będzie istniała. Po wykonaniu operacji **DELETE**, możesz cofnąć zmiany, o ile nie zatwierdzisz transakcji.

Przykładowe użycie:

        DELETE FROM pracownicy WHERE id_pracownika = 101;

* **DROP**: Polecenie **DROP** jest używane do usunięcia całych obiektów z bazy danych. Może to być tabela, baza danych, indeks, itp. Gdy użyjesz polecenia **DROP TABLE**, cała tabela wraz z jej danymi zostanie trwale usunięta z bazy danych. Po operacji **DROP** nie można cofnąć zmian, nawet jeśli operacja nie została zatwierdzona.

Przykładowe użycie:

        DROP TABLE pracownicy;

>Zasadniczo, **DELETE** jest poleceniem DML (Data Manipulation Language), które wpływa na wiersze w tabeli, a **DROP** jest poleceniem DDL (Data Definition Language), które wpływa na strukturę bazy danych. Podczas gdy **DELETE** pozwala na zachowanie struktury tabeli dla przyszłego użycia, **DROP** usuwa całą tabelę lub inną strukturę bazy danych bez możliwości odzyskania.

#### What are the differences between INNER JOIN and OUTER JOIN?

>**INNER JOIN** i **OUTER JOIN** to dwa typy operacji łączenia w SQL, które są używane do łączenia tabel na podstawie wspólnych kolumn. Wybór między **INNER JOIN** a **OUTER JOIN** zależy od tego, jakie dane chcesz otrzymać.

* **INNER JOIN**: **INNER JOIN** zwraca wiersze, gdy istnieje dopasowanie w obu tabelach. Innymi słowy, zwraca tylko te wiersze, dla których istnieje dopasowanie w obu tabelach na podstawie określonej kolumny lub kolumn.

Przykładowe użycie:

        SELECT Pracownicy.Imię, Projekty.NazwaProjektu
        FROM Pracownicy
        INNER JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

* **OUTER JOIN**: **OUTER JOIN** zwraca wszystkie wiersze z jednej tabeli i dopasowane wiersze z drugiej tabeli. Jeśli nie ma dopasowań, wynik to NULL po stronie, która nie ma dopasowania. Istnieją trzy typy OUTER JOIN: LEFT OUTER JOIN (lub po prostu LEFT JOIN), RIGHT OUTER JOIN (lub RIGHT JOIN) i FULL OUTER JOIN (lub FULL JOIN).

Przykładowe użycie:

#### What are the differences between JOIN and UNION?

>**INNER JOIN** i **OUTER JOIN** to dwa typy operacji łączenia w SQL, które są używane do łączenia tabel na podstawie wspólnych kolumn. Wybór między **INNER JOIN** a **OUTER JOIN** zależy od tego, jakie dane chcesz otrzymać.

* **INNER JOIN**: **INNER JOIN** zwraca wiersze, gdy istnieje dopasowanie w obu tabelach. Innymi słowy, zwraca tylko te wiersze, dla których istnieje dopasowanie w obu tabelach na podstawie określonej kolumny lub kolumn.

Przykładowe użycie:

    SELECT Pracownicy.Imię, Projekty.NazwaProjektu
    FROM Pracownicy
    INNER JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

* **OUTER JOIN**: **OUTER JOIN** zwraca wszystkie wiersze z jednej tabeli i dopasowane wiersze z drugiej tabeli. Jeśli nie ma dopasowań, wynik to NULL po stronie, która nie ma dopasowania. Istnieją trzy typy **OUTER JOIN**: **LEFT OUTER JOIN** (lub po prostu **LEFT JOIN**), **RIGHT OUTER JOIN** (lub **RIGHT JOIN**) i **FULL OUTER JOIN** (lub **FULL JOIN**).

Przykładowe użycie:

    SELECT Pracownicy.Imię, Projekty.NazwaProjektu
    FROM Pracownicy
    LEFT JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

>W tym przypadku **LEFT JOIN** zwraca wszystkie wiersze z tabeli Pracownicy i dopasowane wiersze z tabeli **Projekty**. Jeśli nie ma dopasowania, wynik to NULL po stronie tabeli **Projekty**.

Różnica między **INNER JOIN** a **OUTER JOIN** polega na tym, że **INNER JOIN** zwraca tylko wiersze, które mają dopasowania w obu tabelach, podczas gdy **OUTER JOIN** zwraca wszystkie wiersze z jednej tabeli i dopasowane wiersze z drugiej tabeli, a jeśli nie ma dopasowań, wynik to NULL.

#### What are the differences between LEFT JOIN and RIGHT JOIN?

>**LEFT JOIN** i **RIGHT JOIN** to dwa typy **OUTER JOIN** w SQL, które określają, jakie dane powinny być zwracane, gdy nie ma dopasowań między łączonymi tabelami.

* **LEFT JOIN**: **LEFT JOIN** zwraca wszystkie wiersze z lewej tabeli i dopasowane wiersze z prawej tabeli. Jeśli nie ma dopasowań, wynik to NULL po stronie prawej tabeli.

Przykładowe użycie:

    SELECT Pracownicy.Imię, Projekty.NazwaProjektu
    FROM Pracownicy
    LEFT JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

* **RIGHT JOIN**: **RIGHT JOIN** działa dokładnie na odwrót niż **LEFT JOIN**. Zwraca wszystkie wiersze z prawej tabeli i dopasowane wiersze z lewej tabeli. Jeśli nie ma dopasowań, wynik to NULL po stronie lewej tabeli.

Przykładowe użycie:

    SELECT Pracownicy.Imię, Projekty.NazwaProjektu
    FROM Pracownicy
    RIGHT JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

>Różnica między **LEFT JOIN** a **RIGHT JOIN** polega na tym, z której tabeli są zwracane wszystkie wiersze. **LEFT JOIN** zwraca wszystkie wiersze z lewej tabeli, niezależnie od tego, czy istnieją dopasowania w prawej tabeli, podczas gdy **RIGHT JOIN** zwraca wszystkie wiersze z prawej tabeli, niezależnie od tego, czy istnieją dopasowania w lewej tabeli. Wybór między **LEFT JOIN** a **RIGHT JOIN** zależy od tego, jakie dane chcesz otrzymać.

#### What are the differences between One to Many and Many to One relationships?

>Relacje "One to Many" i "Many to One" odnoszą się do typów związków między encjami w bazie danych. Wybór typu relacji zależy od natury danych, które reprezentują twoje tabele.

* **One to Many (1:N)**: Relacja "One to Many" istnieje, gdy pojedynczy rekord w jednej tabeli jest powiązany z wieloma rekordami w innej tabeli. Na przykład, jeden autor może napisać wiele książek, ale każda książka ma tylko jednego autora.

Przykładowa struktura tabeli:

    CREATE TABLE Autorzy (
        ID INT PRIMARY KEY,
        Imię VARCHAR(100)
    );
    
    CREATE TABLE Książki (
        ID INT PRIMARY KEY,
        Tytuł VARCHAR(100),
        ID_Autora INT,
        FOREIGN KEY (ID_Autora) REFERENCES Autorzy(ID)
    );

* **Many to One (N:1)**: Relacja "Many to One" to odwrotność relacji "One to Many". Wiele rekordów z jednej tabeli jest powiązanych z pojedynczym rekordem w innej tabeli. Przykładowo, wiele zamówień może być złożonych przez jednego klienta.

Przykładowa struktura tabeli:

    CREATE TABLE Klienci (
        ID INT PRIMARY KEY,
        Imię VARCHAR(100)
    );
    
    CREATE TABLE Zamówienia (
        ID INT PRIMARY KEY,
        Data DATE,
        ID_Klienta INT,
        FOREIGN KEY (ID_Klienta) REFERENCES Klienci(ID)
    );

>W praktyce "One to Many" i "Many to One" to dwa sposoby patrzenia na ten sam rodzaj relacji, w zależności od tego, z której perspektywy patrzymy. W przypadku relacji "One to Many" skupiamy się na encji, która może być powiązana z wieloma innymi (np. jeden autor, wiele książek), natomiast w przypadku relacji "Many to One" skupiamy się na wielu encjach, które mogą być powiązane z jedną inną (np. wiele książek, jeden autor).

#### What are the differences between TRUNCATE and DROP?

>**TRUNCATE** i **DROP** to dwa polecenia SQL używane do usuwania danych z bazy danych, ale różnią się w sposobie działania i skutkach.

* **TRUNCATE**: Polecenie **TRUNCATE** jest używane do usunięcia wszystkich wierszy z tabeli, ale zachowuje strukturę tabeli do przyszłego użycia. Jest to szybsze niż **DELETE**, ponieważ nie zapisuje danych w logu transakcji. **TRUNCATE** jest operacją DDL (Data Definition Language) i nie można jej cofnąć.

Przykładowe użycie:

    TRUNCATE TABLE Pracownicy;

* **DROP**: Polecenie **DROP** jest używane do usunięcia całych obiektów z bazy danych. Może to być tabela, baza danych, indeks, itp. Gdy użyjesz polecenia **DROP TABLE**, cała tabela wraz z jej danymi i strukturą zostanie trwale usunięta z bazy danych. Po operacji **DROP** nie można cofnąć zmian.

Przykładowe użycie:

    DROP TABLE Pracownicy;

>Podsumowując, różnica między **TRUNCATE** a **DROP** polega na tym, że **TRUNCATE** usuwa tylko dane z tabeli, ale zachowuje strukturę tabeli, podczas gdy **DROP** usuwa całą tabelę (struktura + dane). Ważne jest, aby używać tych poleceń z ostrożnością, ponieważ obie operacje są nieodwracalne.

#### What do you know about database normalization?

>Normalizacja bazy danych to proces projektowania bazy danych w celu zminimalizowania duplikacji danych, co prowadzi do lepszej integralności danych i ułatwia zarządzanie danymi.

>Normalizacja polega na podziale dużych tabel na mniejsze tabele i definiowaniu relacji między nimi. Każdy poziom normalizacji, nazywany formą normalną (FN), ma określone zasady, które muszą być spełnione:

* **Pierwsza forma normalna (1NF)**: W tabeli muszą istnieć proste (atomowe) wartości. Każda kolumna powinna zawierać tylko jedną wartość z domeny tej kolumny, a każdy rekord powinien być unikalny.

Przykładowa tabela spełniająca 1NF:

    CREATE TABLE Pracownicy (
        ID INT PRIMARY KEY,
        Imię VARCHAR(100),
        Nazwisko VARCHAR(100),
        Stanowisko VARCHAR(100)
    );

* **Druga forma normalna (2NF)**: Wszystkie kolumny niekluczowe muszą być w pełni zależne od całego klucza głównego. Dotyczy to tylko tabel, które mają złożone klucze główne.

* **Trzecia forma normalna (3NF)**: Wszystkie kolumny niekluczowe muszą być zależne od klucza głównego, a nie od innych kolumn niekluczowych.

* Istnieją też bardziej zaawansowane formy normalne, takie jak BCNF, 4NF, 5NF, ale na poziomie juniora dewelopera najważniejsze jest zrozumienie pierwszych trzech form normalnych.

>Pomimo wielu zalet, normalizacja nie jest zawsze idealna. Może prowadzić do zwiększonej złożoności zapytań i wymagać więcej złączeń, co może wpłynąć na wydajność. Dlatego ważne jest, aby znaleźć odpowiednią równowagę między normalizacją a potrzebami wydajnościowymi.

#### What is a clause?

>W kontekście SQL, klauzula to część zapytania SQL, która służy do określenia pewnych warunków lub modyfikacji zwracanych danych. Zapytanie SQL składa się z jednej lub więcej klauzul.

Oto niektóre z najpopularniejszych klauzul w SQL:

* **SELECT**: Klauzula **SELECT** służy do wybierania danych z bazy danych.

Przykład:

    SELECT Imię, Nazwisko FROM Pracownicy;

* **FROM**: Klauzula **FROM** określa tabelę, z której pobierane są dane.

Przykład:

    SELECT Imię, Nazwisko FROM Pracownicy;

* **WHERE**: Klauzula **WHERE** służy do filtrowania wyników zapytania SQL.

Przykład:

    SELECT Imię, Nazwisko FROM Pracownicy WHERE Stanowisko = 'Developer';

* **GROUP BY**: Klauzula **GROUP BY** służy do grupowania wyników zapytania SQL na podstawie jednej lub więcej kolumn.

Przykład:

    SELECT Imię, Nazwisko FROM Pracownicy ORDER BY Nazwisko;

* **ORDER BY**: Klauzula **ORDER BY** służy do sortowania wyników zapytania SQL.

Przykład:

    SELECT Imię, Nazwisko FROM Pracownicy ORDER BY Nazwisko;

* **JOIN**: Klauzula **JOIN** służy do łączenia tabel na podstawie wspólnych kolumn.

Przykład:

    SELECT Pracownicy.Imię, Projekty.NazwaProjektu
    FROM Pracownicy
    INNER JOIN Projekty ON Pracownicy.ID = Projekty.IDPracownika;

>Wszystkie te klauzule służą do tworzenia złożonych zapytań SQL, które spełniają konkretne wymagania biznesowe.


#### What is a constraint?

>Ograniczenia (constraints) w SQL służą do określania zasad nałożonych na kolumny w tabeli. Są one używane do zapewnienia niezawodności i dokładności danych przechowywanych w tabeli. Oto kilka typów ograniczeń, które można zastosować w SQL:

* **PRIMARY KEY**: Unikalny identyfikator dla rekordu w tabeli. Każda tabela powinna mieć klucz główny, a każdy rekord powinien mieć unikalną wartość klucza głównego.

Przykład:

    CREATE TABLE Pracownicy (
        ID INT PRIMARY KEY,
        Imię VARCHAR(100),
        Nazwisko VARCHAR(100)
    );

* **FOREIGN KEY**: Służy do zapewnienia integralności referencyjnej. Wartość klucza obcego musi odpowiadać istniejącej wartości klucza głównego w innej tabeli.

Przykład:

    CREATE TABLE Zamówienia (
        ID INT PRIMARY KEY,
        IDPracownika INT,
        FOREIGN KEY (IDPracownika) REFERENCES Pracownicy(ID)
    );

* **UNIQUE**: Ograniczenie **UNIQUE** zapewnia, że wszystkie wartości w kolumnie są różne.

Przykład:

    CREATE TABLE Pracownicy (
        ID INT PRIMARY KEY,
        NumerPracownika INT UNIQUE,
        Imię VARCHAR(100),
        Nazwisko VARCHAR(100)
    );

* **NOT NULL**: Ograniczenie **NOT NULL** zapewnia, że kolumna nie może mieć wartości NULL.

Przykład:

    CREATE TABLE Pracownicy (
        ID INT NOT NULL,
        Imię VARCHAR(100) NOT NULL,
        Nazwisko VARCHAR(100) NOT NULL
    );

* **CHECK**: Ograniczenie **CHECK** pozwala określić precyzyjny warunek, który musi spełniać każda wartość w kolumnie.

Przykład:

    CREATE TABLE Pracownicy (
        ID INT PRIMARY KEY,
        Wiek INT CHECK (Wiek >= 18)
    );

>Ograniczenia są istotnym aspektem projektowania bazy danych, ponieważ pomagają zapewnić integralność i prawidłowość danych.

#### What is a correlated query(sub query)?

>Skojarzone zapytanie (correlated subquery) to zapytanie zagnieżdżone (subquery), które zależy od zewnętrznego zapytania. W przeciwieństwie do zwykłego zagnieżdżonego zapytania, skojarzone zapytanie nie jest samodzielnym zapytaniem: dla każdego wiersza zewnętrznego zapytania, skojarzone zapytanie jest wykonywane raz.

Przykład skojarzonego zapytania może wyglądać tak:

    SELECT Imię, Nazwisko 
    FROM Pracownicy p1
    WHERE Zarobki > (SELECT AVG(Zarobki)
                    FROM Pracownicy p2
                    WHERE p1.Departament = p2.Departament);

>W tym przykładzie zewnętrzne zapytanie przechodzi przez wszystkich pracowników (p1), a dla każdego z nich skojarzone zapytanie (p2) oblicza średnie zarobki pracowników w tym samym departamencie. Jeśli zarobki pracownika są wyższe niż średnie zarobki w jego departamencie, jego imię i nazwisko są zwracane przez zewnętrzne zapytanie.

>Skojarzone zapytania mogą być mocy, ale są też zazwyczaj mniej wydajne niż inne konstrukcje, takie jak JOIN. Powodem jest to, że skojarzone zapytanie musi być wykonane dla każdego wiersza zwracanego przez zewnętrzne zapytanie.

#### What is a Primary Key and what is a Foreign Key?

>**Primary Key (Klucz główny)** to unikalny identyfikator rekordu w tabeli bazy danych. Każda tabela powinna mieć klucz główny, a każdy rekord powinien mieć unikalną wartość klucza głównego. Klucz główny nie może mieć wartości NULL.

Przykład użycia klucza głównego:

    CREATE TABLE Pracownicy (
        ID INT PRIMARY KEY,
        Imię VARCHAR(100),
        Nazwisko VARCHAR(100),
        Stanowisko VARCHAR(100)
    );

>**Foreign Key (Klucz obcy)** to kolumna lub zestaw kolumn, które są używane do łączenia jednej tabeli z inną. Wartość klucza obcego w jednej tabeli powinna odpowiadać wartości klucza głównego w innej tabeli.

Przykład użycia klucza obcego:

    CREATE TABLE Zamówienia (
        ID INT PRIMARY KEY,
        IDPracownika INT,
        FOREIGN KEY (IDPracownika) REFERENCES Pracownicy(ID)
    );

>W tym przykładzie **IDPracownika** w tabeli **Zamówienia** jest kluczem obcym, który odwołuje się do klucza głównego **ID** w tabeli **Pracownicy**.

>Klucz główny i klucz obcy są istotnymi elementami projektowania relacyjnej bazy danych, które pomagają zapewnić integralność danych i tworzyć relacje między tabelami.

#### What is an index and when is it used?

>Indeks w bazie danych to struktura, która pomaga przyspieszyć operacje na danych, takie jak wyszukiwanie, sortowanie czy łączenie (join). Można to porównać do indeksu w książce - zamiast przeszukiwać każdą stronę, aby znaleźć konkretną informację, możemy skorzystać z indeksu, który wskazuje nam, gdzie znajduje się poszukiwana informacja.

>Indeksy tworzy się na jednej lub więcej kolumnach tabeli. W przypadku dużych tabel, indeksy mogą znacznie przyspieszyć zapytania.

Przykład tworzenia indeksu:

    CREATE INDEX idx_pracownicy_nazwisko
    ON Pracownicy (Nazwisko);

>W tym przykładzie tworzymy indeks **idx_pracownicy_nazwisko** na kolumnie **Nazwisko** w tabeli **Pracownicy**. Dzięki temu zapytania wyszukujące pracowników po nazwisku mogą być szybsze.

>Indeksy powinny być używane, gdy często wykonujesz zapytania, które przeszukują lub sortują dane według konkretnej kolumny. Pamiętaj jednak, że indeksy zajmują dodatkową przestrzeń dyskową i mogą spowolnić operacje modyfikacji danych (np. INSERT, UPDATE, DELETE), ponieważ indeksy również muszą być aktualizowane. Dlatego ważne jest, aby znaleźć odpowiednią równowagę między liczbą indeksów a wydajnością operacji na danych.

#### What is an ORM? What are the benefits, when to use?

>ORM (Object-Relational Mapping) to technika programowania, która umożliwia konwersję (mapowanie) między relacyjnymi bazami danych a obiektowymi modelami danych w programowaniu.

>ORM to rodzaj warstwy abstrakcji, która pozwala programistom na pracę z danymi jako z obiektami i instancjami klas. Dzięki temu można pisać kod, który jest znacznie bardziej czytelny i łatwiejszy do utrzymania, niż bezpośredni kod SQL.

Przykładowa implementacja ORM może wyglądać tak (na przykładzie Django ORM w Pythonie):

    from django.db import models

    class Pracownik(models.Model):
    imie = models.CharField(max_length=100)
    nazwisko = models.CharField(max_length=100)
    stanowisko = models.CharField(max_length=100)
    
    # Tworzenie nowego pracownika
    nowy_pracownik = Pracownik(imie='Jan', nazwisko='Kowalski', stanowisko='Developer')
    nowy_pracownik.save()
    
    # Wyszukiwanie pracowników
    developerzy = Pracownik.objects.filter(stanowisko='Developer')

Zalety korzystania z ORM obejmują:

1. **Abstrakcja**: ORM pozwala na manipulowanie danymi jak obiektami, co jest bardziej naturalne dla programistów obiektowych.

2. **Bezpieczeństwo**: Większość bibliotek ORM ma wbudowane mechanizmy ochrony przed atakami SQL Injection.

3. **Nieznaczność języka**: Dzięki ORM nie musisz znać składni SQL, aby manipulować danymi.

4. **Zgodność z różnymi bazami danych**: Dzięki warstwie abstrakcji ORM, zmiana bazy danych (np. z MySQL na PostgreSQL) jest prostsza i nie wymaga zmiany całego kodu.

5. **Automatyzacja**: ORM potrafi automatycznie tworzyć tabele i relacje między nimi na podstawie definicji modeli.

>Kiedy używać ORM? ORM jest szczególnie przydatne w dużych aplikacjach, gdzie ilość zapytań do bazy danych jest duża i gdzie utrzymanie bezpośredniego kodu SQL byłoby trudne. Niemniej jednak, decyzja o użyciu ORM powinna być podjęta z uwzględnieniem specyfiki projektu, ponieważ ORM może wprowadzać pewne złożoności i potencjalne problemy wydajnościowe.

#### What is an SQL Injection and how can it be caused?

>SQL Injection to rodzaj ataku na systemy informatyczne, który wykorzystuje luki w zabezpieczeniach związanych z interakcją z bazami danych. Atak polega na wprowadzeniu do zapytania SQL szkodliwego kodu, który może umożliwić nieautoryzowany dostęp do danych, ich modyfikację, a nawet usunięcie.

>Atak ten jest możliwy, gdy dane wprowadzane przez użytkownika są bezpośrednio wstawiane do zapytań SQL bez odpowiedniej walidacji lub sanitizacji.

Przykładowy kod, który jest narażony na atak SQL Injection:

    String userInput = "1; DROP TABLE STUDENCI;";
    String query = "SELECT * FROM STUDENCI WHERE ID=" + userInput;
    Statement statement = connection.createStatement();
    ResultSet resultSet = statement.executeQuery(query);

>Jeśli użytkownik wprowadzi **"1; DROP TABLE STUDENCI;"**, to zapytanie SQL będzie wyglądać tak: **"SELECT * FROM STUDENCI WHERE ID=1; DROP TABLE STUDENCI;"**. To spowoduje usunięcie tabeli STUDENCI po wykonaniu poprawnego zapytania SELECT.

>Jednym ze sposobów na ochronę przed atakiem SQL Injection jest użycie prepared statements, które automatycznie wykonują sanitizację danych wejściowych. Przykładowy kod wykorzystujący prepared statements:

    String userInput = "1; DROP TABLE STUDENCI;";
    String query = "SELECT * FROM STUDENCI WHERE ID=?";
    PreparedStatement preparedStatement = connection.prepareStatement(query);
    preparedStatement.setInt(1, Integer.parseInt(userInput));
    ResultSet resultSet = preparedStatement.executeQuery();

>W tym przypadku, nawet jeśli użytkownik wprowadził szkodliwy kod, jest on traktowany jako pojedynczy parametr zapytania, a nie jako część zapytania SQL, co uniemożliwia wykonanie szkodliwego kodu.

#### What is SQL Injection?

>SQL Injection to technika ataku, która polega na manipulowaniu zapytaniami SQL, poprzez wprowadzanie szkodliwych danych przez użytkownika. Te dane mogą prowadzić do nieautoryzowanego dostępu, uszkodzenia danych, a nawet całkowitej utraty bazy danych.

>Atak SQL Injection może nastąpić, gdy dane wejściowe od użytkownika są nieprawidłowo sanitowane i są bezpośrednio łączone do zapytania SQL.

Przykładowy scenariusz ataku SQL Injection:

Załóżmy, że mamy formularz logowania, który przyjmuje nazwę użytkownika i hasło. Zapytanie SQL może wyglądać tak:

    query = "SELECT * FROM users WHERE username = '" + username + "' AND password = '" + password + "'";

Jeśli atakujący wprowadzi jako nazwę użytkownika **"admin' --"**, zapytanie SQL staje się:

    query = "SELECT * FROM users WHERE username = 'admin' --' AND password = ''";

>Część **--** to komentarz w SQL, więc wszystko po tym jest ignorowane. Zatem atakujący zalogował się jako administrator bez podawania hasła.

Aby zapobiec atakom SQL Injection, zaleca się stosowanie technik takich jak:

* **Parametrów zapytania** (ang. Prepared Statements) / **Zapytań parametryzowanych**: Polega to na tworzeniu zapytań SQL, w których dane wejściowe są traktowane jako parametry, a nie bezpośrednią część zapytania.

Przykład w języku Python (z użyciem biblioteki sqlite3):

    username = "admin' --"
    password = ""
    
    # Używanie zapytań parametryzowanych
    cursor.execute("SELECT * FROM users WHERE username = ? AND password = ?", (username, password))

* **Sanityzacja danych wejściowych**: Zawsze sprawdzaj i oczyść dane wejściowe, aby upewnić się, że nie zawierają one niebezpiecznych sekwencji. Wiele języków programowania i frameworków oferuje narzędzia do sanityzacji danych.

* **Limitowanie uprawnień**: Zawsze używaj minimalnych uprawnień dla połączenia z bazą danych. Użytkownik bazy danych powinien mieć tylko te uprawnienia, które są absolutnie konieczne do wykonania danego zadania.

* **Używanie ORM**: Object-Relational Mapping (ORM) jest techniką, która często oferuje wbudowaną ochronę przed atakami SQL Injection.

#### What is the trigger? Bring an example of using?

>Trigger, czyli wyzwalacz, to specjalny rodzaj procedury przechowywanej, która jest automatycznie wywoływana (uruchamiana) przez serwer baz danych w odpowiedzi na określone zdarzenia na konkretnej tabeli lub widoku w bazie danych. Zdarzenia te mogą obejmować operacje INSERT, UPDATE i DELETE.

>Triggery są używane do utrzymania integralności bazy danych, automatyzacji pewnych operacji na danych lub implementowania pewnych reguł biznesowych na poziomie bazy danych.

Oto przykład wykorzystania triggera w SQL:

    CREATE TRIGGER aktualizacja_godziny_modyfikacji
    BEFORE UPDATE
    ON Pracownicy
    FOR EACH ROW
    BEGIN
        SET NEW.godzina_modyfikacji = NOW();
    END;

>Ten trigger zostanie automatycznie uruchomiony przed każdą operacją UPDATE na tabeli **Pracownicy**. Jego zadaniem jest ustawienie pola **godzina_modyfikacji** na aktualną datę i godzinę (wartość zwróconą przez funkcję **NOW()**).

Ważne jest, aby pamiętać, że nadużywanie triggerów może prowadzić do złożoności w zarządzaniu bazą danych i problemów z wydajnością, ponieważ każde uruchomienie triggera wymaga dodatkowych zasobów. Dlatego zawsze warto rozważyć, czy dana operacja nie mogłaby być lepiej zaimplementowana po stronie aplikacji.

#### What kind of database relations do you know? How to define them?

>Relacje między tabelami w bazie danych służą do łączenia danych z różnych tabel i są kluczowym elementem relacyjnych baz danych. Istnieją trzy podstawowe typy relacji:

1. **Jedno do jednego (One-to-One)**: Każdy rekord w tabeli A jest powiązany z co najwyżej jednym rekordem w tabeli B. Na przykład, każdy pracownik w firmie może mieć przypisaną jedną kartę dostępu.

2. **Jedno do wielu (One-to-Many / Many-to-One)**: Jeden rekord z tabeli A może być powiązany z wieloma rekordami z tabeli B (i odwrotnie). Na przykład, jeden departament może mieć wielu pracowników.

3. **Wiele do wielu (Many-to-Many)**: Wiele rekordów z tabeli A może być powiązane z wieloma rekordami z tabeli B. Na przykład, jeden student może uczęszczać na wiele kursów, a jeden kurs może być odwiedzany przez wielu studentów.

>Definiowanie relacji między tabelami w bazie danych odbywa się za pomocą kluczy obcych (foreign keys). Klucz obcy to kolumna (lub zestaw kolumn), której wartości odnoszą się do klucza głównego w innej tabeli.

>Przykładowo, moglibyśmy zdefiniować relacje między tabelami **Pracownik** i **Departament** następująco:

    CREATE TABLE Departament (
    ID int NOT NULL,
    Nazwa varchar(255),
    PRIMARY KEY (ID)
    );
    
    CREATE TABLE Pracownik (
    ID int NOT NULL,
    Imie varchar(255),
    Nazwisko varchar(255),
    DepartamentID int,
    PRIMARY KEY (ID),
    FOREIGN KEY (DepartamentID) REFERENCES Departament(ID)
    );

>W tym przykładzie, **DepartamentID** w tabeli **Pracownik** jest kluczem obcym, który odnosi się do klucza głównego **ID** w tabeli **Departament**. Tworzy to relację One-to-Many między **Departament** a **Pracownik**: jeden departament może mieć wielu pracowników, ale każdy pracownik jest przypisany do dokładnie jednego departamentu.

#### What kind of JOIN types do you know in SQL? Could you give examples?

>W SQL występuje kilka typów operacji JOIN, które służą do łączenia wierszy z dwóch lub więcej tabel. Oto najczęściej używane typy JOIN w SQL:

1. **INNER JOIN**: Zwraca wiersze, gdy istnieje pasujący rekord w obu tabelach.

       SELECT Pracownicy.imie, Pracownicy.nazwisko, Departament.nazwa
       FROM Pracownicy
       INNER JOIN Departament ON Pracownicy.departament_id = Departament.id;

2. **LEFT JOIN (or LEFT OUTER JOIN)**: Zwraca wszystkie wiersze z lewej tabeli i pasujące wiersze z prawej tabeli. Jeśli nie ma dopasowania, wynik to NULL po prawej stronie.

       SELECT Pracownicy.imie, Pracownicy.nazwisko, Departament.nazwa
       FROM Pracownicy
       LEFT JOIN Departament ON Pracownicy.departament_id = Departament.id;

3. **RIGHT JOIN (or RIGHT OUTER JOIN)**: Zwraca wszystkie wiersze z prawej tabeli i pasujące wiersze z lewej tabeli. Jeśli nie ma dopasowania, wynik to NULL po lewej stronie.

        SELECT Pracownicy.imie, Pracownicy.nazwisko, Departament.nazwa
        FROM Pracownicy
        RIGHT JOIN Departament ON Pracownicy.departament_id = Departament.id;

4. **FULL JOIN (or FULL OUTER JOIN)**: Zwraca wiersze, gdy istnieje dopasowanie w jednej z tabel.

        SELECT Pracownicy.imie, Pracownicy.nazwisko, Departament.nazwa
        FROM Pracownicy
        FULL JOIN Departament ON Pracownicy.departament_id = Departament.id;

>Pamiętaj, że nie wszystkie systemy zarządzania bazami danych (DBMS) obsługują wszystkie typy JOIN. Na przykład MySQL nie obsługuje operacji FULL JOIN, ale można ją symulować za pomocą kombinacji LEFT i RIGHT JOIN.

#### When do you use the DISTINCT keyword in SQL?

>Słowo kluczowe **DISTINCT** w SQL jest używane do wyeliminowania duplikatów z wyników zapytania.

Załóżmy, że mamy tabelę **Pracownicy** z następującymi danymi:

ID	Imię	  Nazwisko	  Departament
1	Jan	      Kowalski	  Sprzedaż
2	Maria	  Nowak	      Sprzedaż
3	Paweł	  Kowalski	  IT
4	Agnieszka Kowalska	  Sprzedaż

Jeśli chcesz zobaczyć wszystkie unikalne departamenty, w których pracują pracownicy, możesz użyć **DISTINCT**:

    SELECT DISTINCT Departament FROM Pracownicy;

>Wynikiem tego zapytania będzie:

Departament
Sprzedaż
IT

Pamiętaj, że **DISTINCT** działa na całym zestawie kolumn wybranych w zapytaniu SELECT, a nie tylko na jednej kolumnie. Na przykład, jeśli zapytanie będzie wyglądać tak:

    SELECT DISTINCT Imię, Nazwisko FROM Pracownicy;

>To zwróci nam wszystkie unikalne kombinacje imienia i nazwiska. W przypadku naszej tabeli, to będą wszystkie rekordy, ponieważ każdy pracownik ma unikalne imię i nazwisko.