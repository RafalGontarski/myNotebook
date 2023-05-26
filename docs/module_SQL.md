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



#### What are database transactions? When to use?



#### What are the differences between DELETE and DROP?



#### What are the differences between INNER JOIN and OUTER JOIN?



#### What are the differences between JOIN and UNION?



#### What are the differences between LEFT JOIN and RIGHT JOIN?



#### What are the differences between One to Many and Many to One relationships?



#### What are the differences between TRUNCATE and DROP?
#### What do you know about database normalization?



#### What is a clause?



#### What is a constraint?



#### What is a correlated query(sub query)?



#### What is a Primary Key and what is a Foreign Key?



#### What is an index and when is it used?



#### What is an ORM? What are the benefits, when to use?



#### What is an SQL Injection and how can it be caused?

>SQL Injection to rodzaj ataku na systemy informatyczne, który wykorzystuje luki w zabezpieczeniach związanych z interakcją z bazami danych. Atak polega na wprowadzeniu do zapytania SQL szkodliwego kodu, który może umożliwić nieautoryzowany dostęp do danych, ich modyfikację, a nawet usunięcie.

>Atak ten jest możliwy, gdy dane wprowadzane przez użytkownika są bezpośrednio wstawiane do zapytań SQL bez odpowiedniej walidacji lub sanitizacji.

Przykładowy kod, który jest narażony na atak SQL Injection:

    String userInput = "1; DROP TABLE STUDENCI;";
    String query = "SELECT * FROM STUDENCI WHERE ID=" + userInput;
    Statement statement = connection.createStatement();
    ResultSet resultSet = statement.executeQuery(query);

>Jeśli użytkownik wprowadzi "1; DROP TABLE STUDENCI;", to zapytanie SQL będzie wyglądać tak: "SELECT * FROM STUDENCI WHERE ID=1; DROP TABLE STUDENCI;". To spowoduje usunięcie tabeli STUDENCI po wykonaniu poprawnego zapytania SELECT.

>Jednym ze sposobów na ochronę przed atakiem SQL Injection jest użycie prepared statements, które automatycznie wykonują sanitizację danych wejściowych. Przykładowy kod wykorzystujący prepared statements:

    String userInput = "1; DROP TABLE STUDENCI;";
    String query = "SELECT * FROM STUDENCI WHERE ID=?";
    PreparedStatement preparedStatement = connection.prepareStatement(query);
    preparedStatement.setInt(1, Integer.parseInt(userInput));
    ResultSet resultSet = preparedStatement.executeQuery();

>W tym przypadku, nawet jeśli użytkownik wprowadził szkodliwy kod, jest on traktowany jako pojedynczy parametr zapytania, a nie jako część zapytania SQL, co uniemożliwia wykonanie szkodliwego kodu.

#### What is SQL Injection?



#### What is the trigger? Bring an example of using?



#### What kind of database relations do you know? How to define them?



#### What kind of JOIN types do you know in SQL? Could you give examples?



#### When do you use the DISTINCT keyword in SQL?