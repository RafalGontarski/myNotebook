# ALGORITHM

#### How does Binary Search work? (Jak działa wyszukiwanie binarne?)

>Wyszukiwanie binarne to algorytm wyszukiwania wydajny dla posortowanych list (lub tablic). Algorytm działa poprzez dzielenie wyszukiwanego obszaru na dwie części na podstawie elementu w środku i eliminowanie nieodpowiedniej połowy, dopóki poszukiwany element nie zostanie odnaleziony.

Oto przykładowa implementacja algorytmu wyszukiwania binarnego w Javie:

    public class BinarySearch {
        int binarySearch(int arr[], int x) {
            int l = 0, r = arr.length - 1;
            while (l <= r) {
                int m = l + (r - l) / 2;
    
                // Sprawdź, czy x jest obecny na środku
                if (arr[m] == x)
                    return m;
    
                // Jeżeli x większy, ignorujemy lewą połowę
                if (arr[m] < x)
                    l = m + 1;
    
                // W przeciwnym wypadku ignorujemy prawą połowę
                else
                    r = m - 1;
            }
    
            // Jeżeli doszliśmy do tego punktu, elementu nie ma w tablicy
            return -1;
        }
    }

>Tutaj, metoda **binarySearch** przyjmuje tablicę **arr[]** i wartość **x**, której szukamy. Jeżeli wartość **x** jest obecna w tablicy, metoda zwraca indeks tego elementu. Jeżeli **x** nie jest obecny, zwracany jest **-1**.

>Zwróć uwagę, że ten algorytm zakłada, że tablica jest posortowana. Jeżeli tablica nie jest posortowana, wyniki mogą być niepoprawne. Wyszukiwanie binarne jest bardzo wydajne i ma złożoność obliczeniową O(log n), gdzie n jest rozmiarem tablicy.

#### What is “Stack overflow”? (Co to jest „przepełnienie stosu”?)

>"Stack overflow" to błąd, który występuje, gdy stos, struktura danych używana do przechowywania informacji o wywołaniach funkcji w programie, jest pełny. Każde wywołanie funkcji w programie powoduje dodanie nowego rekordu na stosie, zwanej ramką stosu. Ta ramka zawiera informacje takie jak lokalne zmienne funkcji, parametry wywołań i adres powrotu.

>Jeżeli program wywołuje zbyt wiele funkcji jednocześnie (co zazwyczaj jest wynikiem rekursji bez warunku zakończenia), stos może zostać przepełniony, co prowadzi do błędu "stack overflow".

Oto przykład w języku Java, który prowadzi do błędu "stack overflow" przez zbyt wiele wywołań rekurencyjnych:

    public class StackOverflowDemo {
        public static void recursiveCall() {
            recursiveCall();
        }
    
        public static void main(String[] args) {
            recursiveCall();
        }
    }

>W tym przykładzie funkcja **recursiveCall** wywołuje samą siebie nieskończonie wiele razy. Ponieważ dla każdego wywołania jest tworzona nowa ramka stosu, stos szybko się zapełnia, co prowadzi do błędu "stack overflow".

>Należy pamiętać, że "stack overflow" to poważny błąd, który zazwyczaj prowadzi do awarii programu, więc należy unikać sytuacji, które mogą prowadzić do tego błędu. W szczególności, jeżeli korzystasz z rekursji, zawsze upewnij się, że istnieje warunek zakończenia, który zatrzyma rekursję po osiągnięciu określonego stanu.

#### What is algorythimc complexity? (Co to jest złożoność algorytmu?)

>Złożoność algorytmiczna, często nazywana złożonością czasową, to koncepcja w informatyce, która opisuje efektywność algorytmu w kontekście ilości danych, które algorytm musi przetworzyć. Jest to kluczowy aspekt w wyborze odpowiedniego algorytmu dla danego zadania.

>Istnieją dwa główne rodzaje złożoności algorytmicznej:

1. Złożoność czasowa: Ile czasu potrzeba algorytmowi na wykonanie obliczeń w zależności od rozmiaru danych wejściowych.

2. Złożoność przestrzenna: Ile pamięci potrzebuje algorytm do przetworzenia danych wejściowych.

>Najczęściej używaną miarą złożoności algorytmicznej jest notacja "Big O", która opisuje górne ograniczenie złożoności w najgorszym przypadku. Na przykład, algorytm z złożonością O(n) potrzebuje czasu proporcjonalnego do rozmiaru danych wejściowych, a algorytm z złożonością O(1) potrzebuje stałego czasu, niezależnie od rozmiaru danych wejściowych.

Oto przykład w języku Java. Prosty algorytm do znalezienia największego elementu w tablicy ma złożoność O(n), gdzie n to rozmiar tablicy:

    public class Main {
        public static void main(String[] args) {
            int[] array = {1, 4, 3, 6, 7, 0};
            System.out.println(findMax(array));
        }
    
        static int findMax(int[] array) {
            int max = array[0];
            for(int i = 1; i < array.length; i++) {
                if(array[i] > max) {
                    max = array[i];
                }
            }
            return max;
        }
    }

>W powyższym kodzie funkcja **findMax** przechodzi przez każdy element tablicy dokładnie raz, więc złożoność czasowa jest proporcjonalna do rozmiaru tablicy.

#### What is linked list? (Co to jest lista połączona?)

>Lista łączona (LinkedList) to struktura danych, która składa się z grupy elementów, zwanych węzłami, w których każdy element zawiera referencję (łącze) do następnego elementu w sekwencji. Każdy węzeł na liście łączonej zawiera dwa elementy: dane i referencję do następnego węzła na liście.

>Java posiada wbudowaną klasę LinkedList, która implementuje interfejs List i Deque, co oznacza, że możemy korzystać z LinkedList jako stosu, kolejki lub podwójnej kolejki.

Oto prosty przykład użycia LinkedList w Javie:

    import java.util.LinkedList;

    public class Main {
    public static void main(String[] args) {
        LinkedList<String> names = new LinkedList<>();
    
            // Dodajemy elementy do listy
            names.add("Adam");
            names.add("Bartek");
            names.add("Cezary");
    
            // Wyświetlamy elementy listy
            for(String name : names) {
                System.out.println(name);
            }
    
            // Usuwamy element z listy
            names.remove("Bartek");
    
            System.out.println("Po usunięciu Bartka:");
    
            // Wyświetlamy elementy listy po usunięciu jednego elementu
            for(String name : names) {
                System.out.println(name);
            }
        }
    }

>Ten kod tworzy nową listę łączoną o nazwie **names**, dodaje trzy imiona do listy, a następnie usuwa jedno z nich.

>Listy łączone są szczególnie przydatne, gdy planujemy często dodawać lub usuwać elementy z listy, ponieważ operacje te są bardzo efektywne w porównaniu do innych struktur danych, takich jak tablice. Jednak ich główną wadą jest to, że dostęp do konkretnego elementu na liście wymaga przejścia przez wszystkie poprzednie elementy, co może być nieefektywne dla dużych list.

#### What is QuickSort? Describe the main logic of this sorting algorithm. (Co to jest QuickSort? Opisz główną logikę tego algorytmu sortowania.)

>QuickSort to algorytm sortowania, który działa na zasadzie "dziel i zwyciężaj". Jest to jeden z najszybszych algorytmów sortowania dla dużych zestawów danych.

Zasada działania QuickSort:

1. Wybierz element, który nazwiemy pivotem.
2. Podziel dane na dwie części. Pierwsza zawiera elementy mniejsze od pivota, a druga elementy większe od pivota.
3. Wywołaj funkcję QuickSort rekurencyjnie dla obu części.
4. Połącz wyniki.

Poniżej znajduje się przykładowa implementacja algorytmu QuickSort w Javie:

    public class QuickSort {
        int partition(int arr[], int low, int high) {
            int pivot = arr[high]; 
            int i = (low-1); 
            for (int j=low; j<high; j++) {
                if (arr[j] < pivot) {
                    i++;
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
            int temp = arr[i+1];
            arr[i+1] = arr[high];
            arr[high] = temp;
            return i+1;
        }
    
        void sort(int arr[], int low, int high) {
            if (low < high) {
                int pi = partition(arr, low, high);
                sort(arr, low, pi-1);
                sort(arr, pi+1, high);
            }
        }
    
        public static void main(String args[]) {
            int arr[] = {10, 7, 8, 9, 1, 5};
            int n = arr.length;
            QuickSort ob = new QuickSort();
            ob.sort(arr, 0, n-1);
            System.out.println("Posortowana tablica");
            for(int i=0; i<n; ++i)
                System.out.print(arr[i]+" ");
        }
    }

>W tym kodzie mamy funkcję **partition()**, która dzieli tablicę na dwie części w oparciu o element pivot. Następnie mamy funkcję **sort()**, która wywołuje **partition()** i rekurencyjnie sortuje obie części tablicy.

>Algorytm QuickSort ma złożoność czasową O(n log n) w przypadku średnim i najlepszym, ale jego najgorsza złożoność czasowa to O(n^2), co następuje, gdy dane wejściowe są już posortowane. Mimo to, QuickSort jest preferowany dla dużych zestawów danych ze względu na swoją szybkość w praktyce.

#### What is the difference between Stack and Queue data structure? (Jaka jest różnica między strukturą danych Stack i Queue?)

>Stack (stos) i Queue (kolejka) to dwie podstawowe struktury danych stosowane w programowaniu.

>Stack jest strukturą danych typu LIFO (Last In, First Out), co oznacza, że ostatni element dodany do stosu będzie pierwszym elementem, który zostanie usunięty. Można to porównać do stosu talerzy: możemy dodać talerz na górę stosu (push) i możemy usunąć talerz z góry stosu (pop).

>Queue (kolejka) natomiast jest strukturą danych typu FIFO (First In, First Out), co oznacza, że pierwszy element dodany do kolejki będzie pierwszym elementem, który zostanie usunięty. To jak w rzeczywistym świecie kolejka w sklepie: pierwsza osoba, która stanęła w kolejce, jest pierwszą osobą, która jest obsługiwana.

Poniżej znajdują się przykładowe implementacje Stack i Queue w Javie:

**Stack**:

    import java.util.Stack;

    public class StackExample {
        public static void main(String[] args) {
            Stack<String> stack = new Stack<>();
            stack.push("Jeden");
            stack.push("Dwa");
            stack.push("Trzy");
            System.out.println(stack.pop()); // Wypisze "Trzy"
        }
    }

**Queue**:

    import java.util.LinkedList;
    import java.util.Queue;
    
    public class QueueExample {
        public static void main(String[] args) {
            Queue<String> queue = new LinkedList<>();
            queue.add("Jeden");
            queue.add("Dwa");
            queue.add("Trzy");
            System.out.println(queue.remove()); // Wypisze "Jeden"
        }
    }

>Jak widać, różnica między stosami a kolejkami polega na kolejności, w jakiej elementy są usuwane: w stosach jest to LIFO (Last In, First Out), a w kolejkach FIFO (First In, First Out).


#### What kinds of sorting mechanis do you know? What are the differences between them? (Jakie znasz rodzaje mechanizmów sortowania? Jakie są między nimi różnice?)

>

#### When would you use LinkedList over an ArrayList? (Kiedy użyłbyś LinkedList zamiast ArrayList?)

>

