# Multi Tasking

#### What is difference betwen Asynchrony and Concurrency?
#### What is a thread? What types of threads do you know?
#### What is a deadlock?

>Deadlock, znany też jako zakleszczenie, to sytuacja w systemach operacyjnych lub bazach danych, w której dwa lub więcej procesów jest zablokowanych, ponieważ każdy z nich czeka na zasób, który jest blokowany przez inny proces.

>Deadlocki najczęściej występują w sytuacjach, gdzie mamy do czynienia z konkurencyjnym dostępem do zasobów, czyli gdy dwa lub więcej procesów jednocześnie próbuje uzyskać dostęp do tego samego zasobu, który nie może być dzielony.

>Wystąpienie deadlocka zwykle wynika z następujących warunków:

1. **Mutual exclusion**: Zasób nie może być dzielony i jest dostępny tylko dla jednego procesu na raz.
2. **Hold and wait**: Proces trzyma przynajmniej jeden zasób i czeka na inne.
3. **No preemption**: Zasób nie może być odebrany siłą od procesu, który go posiada.
4. **Circular wait**: Istnieje cykl procesów, gdzie każdy proces czeka na zasób, który jest trzymany przez następny proces w cyklu.

Poniżej jest przykład prostego deadlocka w Javie:

    public class DeadlockExample {

        private static Object resource1 = new Object();
        private static Object resource2 = new Object();
    
        public static void main(String[] args) {
    
            Thread thread1 = new Thread(() -> {
                synchronized (resource1) {
                    System.out.println("Thread 1: locked resource 1");
                    try { Thread.sleep(100);} catch (Exception e) {}
                    synchronized (resource2) {
                        System.out.println("Thread 1: locked resource 2");
                    }
                }
            });
    
            Thread thread2 = new Thread(() -> {
                synchronized (resource2) {
                    System.out.println("Thread 2: locked resource 2");
                    try { Thread.sleep(100);} catch (Exception e) {}
                    synchronized (resource1) {
                        System.out.println("Thread 2: locked resource 1");
                    }
                }
            });
    
            thread1.start();
            thread2.start();
        }
    }

>W tym przykładzie, **thread1** próbuje zablokować **resource1** a następnie **resource2**, podczas gdy **thread2** próbuje zablokować **resource2** a następnie **resource1**. Jeżeli oba wątki zaczynają jednocześnie, może dojść do sytuacji gdzie **thread1** zablokuje **resource1**, a **thread2** zablokuje **resource2**, co skutkuje deadlockiem, gdyż każdy z wątków czeka na zasób zablokowany przez drugi wątek.

#### When you need to use threads in an application?
#### What is the difference between synchronous and asynchronous execution?
#### In what kind of situations can deadlocks occur?
#### What is Synchronization?