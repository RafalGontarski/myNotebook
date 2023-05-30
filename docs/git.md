# GIT

#### What are the differences between Git and GitHub? (Jakie są różnice między Git a GitHub?)

>Git i GitHub to dwa często stosowane narzędzia w rozwoju oprogramowania, ale mają różne zastosowania.

>Git jest rozproszonym systemem kontroli wersji (DVCS), który pomaga programistom zarządzać zmianami w kodzie na przestrzeni czasu. Umożliwia wielu programistom współpracę nad projektem, dostarczając zdecentralizowany repozytorium, w którym mogą dokonywać zmian, śledzić wersje i bezproblemowo łączyć swoją pracę. Git działa lokalnie na komputerze programisty, umożliwiając tworzenie gałęzi, zatwierdzanie zmian i zarządzanie historią kodu.

>GitHub natomiast jest usługą hostingową opartą na przeglądarce internetowej, która wykorzystuje Git. Dostarcza scentralizowane miejsce, w którym programiści mogą przechowywać i udostępniać swoje repozytoria Git. GitHub oferuje dodatkowe funkcje i możliwości na bazie Git, dzięki czemu jest platformą społecznościową dla kodowania. Zawiera funkcje takie jak śledzenie problemów, prośby o wprowadzenie zmian, przeglądy kodu i narzędzia do zarządzania projektami, które ułatwiają współpracę między członkami zespołu.

>Aby zobrazować różnicę, przyjrzyjmy się przykładowemu użyciu Git i GitHub:

    # Użycie Git
    # Inicjalizacja nowego repozytorium Git
    $ git init
    
    # Utworzenie nowego pliku
    $ touch main.py
    
    # Dodanie pliku do obszaru przygotowania
    $ git add main.py
    
    # Zatwierdzenie zmian w repozytorium
    $ git commit -m "Pierwsze zatwierdzenie"
    
    # Utworzenie nowej gałęzi
    $ git branch feature-branch
    
    # Przełączenie się na nową gałąź
    $ git checkout feature-branch
    
    # Dokonanie zmian w kodzie
    $ echo "print('Witaj, Świecie!')" >> main.py
    
    # Dodanie i zatwierdzenie zmian na gałęzi funkcji
    $ git add main.py
    $ git commit -m "Dodanie komunikatu powitalnego"
    
    # Połączenie gałęzi funkcji z główną gałęzią
    $ git checkout main
    $ git merge feature-branch
    
    # Przesłanie zmian do zdalnego repozytorium (np. na GitHub)
    $ git remote add origin <adres_repozytorium>
    $ git push -u origin main
    
    # Użycie GitHub
    # Utworzenie nowego repozytorium na GitHub
    
    # Sklonowanie zdalnego repozytorium na komputer lokalny
    $ git clone <adres_repozytorium>
    
    # Dokonanie zmian w kodzie (np. modyfikacja main.py)
    
    # Dodanie i zatwierdzenie zmian lokalnie
    $ git add main.py
    $ git commit -m "Modyfikacja komunik


#### What is a commit? (Co to jest zatwierdzenie?)

>Commit to termin używany w systemach kontroli wersji, takich jak Git. Commit, zwany również "zatwierdzeniem", to akt zapisania zmian w repozytorium. Kiedy dokonujesz commitu, zapisujesz swój kod w danej formie, którą można później przywrócić, jeżeli zajdzie taka potrzeba. Każdy commit jest zidentyfikowany przez unikalny identyfikator (SHA hash), który pozwala na śledzenie zmian.

>Załóżmy, że pracujesz nad projektem i właśnie dodałeś nową funkcjonalność do swojego pliku **main.py**. Możesz zobaczyć zmiany, które dokonałeś, używając polecenia **git diff**. Jeśli chcesz zatwierdzić te zmiany, najpierw musisz je dodać do obszaru staging za pomocą polecenia **git add main.py**. Następnie możesz dokonać commitu za pomocą polecenia **git commit -m "Dodano nową funkcjonalność"**. Teraz twoje zmiany są zapisane w historii projektu.

>Pamiętaj, że commit powinien być zrozumiały dla innych - więc dobrą praktyką jest pisanie klarownych i szczegółowych wiadomości commitów, które opisują, co zostało zmienione i dlaczego.

>Oto przykładowy kod, który pokazuje, jak możesz dokonać commitu za pomocą linii poleceń:

    # Najpierw zmieniamy plik
    echo "print('Hello, world!')" > main.py
    
    # Sprawdzamy status repozytorium
    git status
    
    # Dodajemy plik do obszaru staging
    git add main.py
    
    # Sprawdzamy status ponownie, aby upewnić się, że plik został dodany
    git status
    
    # Dokonujemy commitu
    git commit -m "Dodano powitanie 'Hello, world!' do main.py"
    
    # Sprawdzamy log commitów, aby zobaczyć naszą nową zmianę
    git log

>Zmieniliśmy plik **main.py**, dodaliśmy go do obszaru staging i dokonaliśmy commitu. Potem sprawdziliśmy log commitów, aby upewnić się, że nasz commit jest zapisany w historii projektu.

#### What are the differences between remote and local repositories? (Jakie są różnice między repozytoriami zdalnymi i lokalnymi?)

>Repozytoria lokalne i zdalne to dwa kluczowe elementy, które musisz zrozumieć, kiedy pracujesz z Git.

>Repozytorium lokalne to folder na twoim komputerze, który zawiera pliki twojego projektu oraz historię commitów. Repozytorium lokalne umożliwia wykonywanie różnych operacji Git bez dostępu do internetu. Możesz dokonywać zmian, commitować, przeglądać historię zmian i wiele więcej, bez potrzeby połączenia sieciowego.

>Repozytorium zdalne to wersja twojego projektu, która istnieje gdzieś w sieci, zazwyczaj na serwerze. Może to być na przykład serwer GitHub, GitLab, Bitbucket lub inny. Repozytorium zdalne umożliwia współpracę z innymi deweloperami. Możesz przesyłać (push) swoje zmiany do repozytorium zdalnego, a inni mogą pobierać (pull) te zmiany do swoich repozytoriów lokalnych.

>Poniżej znajduje się przykład, jak możesz pracować z repozytoriami lokalnymi i zdalnymi:

    # Tworzenie nowego repozytorium lokalnego
    git init
    
    # Dodawanie pliku do repozytorium
    echo "Hello, world!" > readme.md
    git add readme.md
    git commit -m "Initial commit"
    
    # Dodawanie repozytorium zdalnego (przykładowy adres URL)
    git remote add origin https://github.com/yourusername/yourrepository.git
    
    # Wysyłanie zmian do repozytorium zdalnego
    git push -u origin master

>W tym przykładzie najpierw tworzysz nowe repozytorium lokalne za pomocą **git init**. Następnie dodajesz plik **readme.md** do repozytorium i dokonujesz commitu. Potem dodajesz repozytorium zdalne za pomocą **git remote add**, gdzie **origin** to standardowa nazwa dla głównego repozytorium zdalnego, a URL to miejsce, gdzie znajduje się twoje repozytorium zdalne. Na końcu wysyłasz swoje zmiany do repozytorium zdalnego za pomocą **git push**.

#### What commands do you use to send your code to the remote repository? (Jakich poleceń używasz do wysyłania kodu do zdalnego repozytorium?)

>Aby wysłać swój kod do zdalnego repozytorium, musisz użyć polecenia **git push**. Ale zanim to zrobisz, musisz najpierw dodać swoje zmiany do repozytorium i zatwierdzić je, używając **git add** i **git commit**. Poniżej znajduje się przykładowy proces:

    # Tworzenie pliku
    echo "Hello, world!" > readme.md
    
    # Dodawanie pliku do repozytorium
    git add readme.md
    
    # Zatwierdzanie zmian
    git commit -m "Dodano readme.md"
    
    # Wysyłanie zmian do głównego gałęzi zdalnego repozytorium
    git push origin master

>W tym przykładzie **origin** to nazwa zdalnego repozytorium, a **master** to nazwa gałęzi, do której chcesz wysłać zmiany.

>Jeżeli pracujesz na innej gałęzi, powinieneś zastąpić **master** nazwą tej gałęzi. Na przykład, jeśli pracujesz na gałęzi o nazwie **feature**, użyłbyś polecenia **git push origin feature**.

>Pamiętaj, że przed pierwszym **push**, musisz skonfigurować zdalne repozytorium za pomocą polecenia **git remote add origin URL_REPOZYTORIUM**. Przykładowo, jeśli twoje repozytorium jest na GitHubie, URL mógłby wyglądać tak: **https://github.com/twoja_nazwa_użytkownika/nazwa_twojego_repozytorium.git**.

>Jednak jeżeli sklonowałeś repozytorium za pomocą git clone, zdalne repozytorium **origin** jest już ustawione i nie musisz go konfigurować za pomocą **git remote add**.

#### What are the differences between git fetch and git pull commands? (Jakie są różnice między poleceniami git fetch i git pull?)

>Komendy **git fetch** i **git pull** są używane do interakcji z zdalnym repozytorium, ale działają w nieco różny sposób.

>**git fetch** pobiera informacje o wszystkich zmianach, które zaszły w zdalnym repozytorium, ale nie wprowadza ich do twojego aktualnego brancha. To znaczy, że **fetch** pobiera dane o nowych commitach, branchach i tagach z zdalnego repozytorium, ale nie zmienia twojego lokalnego stanu kodu. Aby zaktualizować swój lokalny kod, musisz po wykonaniu **git fetch** użyć **it merge** albo **git rebase**, aby połączyć zmiany.

>Z drugiej strony, **git pull** jest w gruncie rzeczy skrótem dla wykonania **git fetch**, a następnie **git merge**. Pobiera on zmiany z zdalnego repozytorium i od razu łączy je z twoim lokalnym branchem.

Zobaczmy, jak to wygląda w praktyce:

    # Przykład użycia git fetch
    git fetch origin
    # Teraz możemy zobaczyć zmiany, które zaszły na zdalnym repozytorium
    git diff master origin/master
    # Aby zaktualizować nasz lokalny branch musimy zrobić merge
    git merge origin/master
    
    # Przykład użycia git pull
    git pull origin master

>W obu przypadkach **origin** to nazwa zdalnego repozytorium, a **master** to nazwa brancha.

Pamiętaj, że **git pull** może potencjalnie wprowadzić konflikty, jeśli twoja lokalna wersja kodu jest różna od tej na serwerze. Zawsze warto być świadomym tego, co dzieje się w twoim lokalnym repozytorium, zanim użyjesz **git pull**.

#### What is a merge conflict and how it can be resolved? (Co to jest konflikt scalania i jak można go rozwiązać?)

>Konflikt scalenia (merge conflict) w Git występuje, gdy dwa różne branch'e wprowadzają zmiany w tych samych liniach tego samego pliku, lub gdy jeden branch usuwa plik, podczas gdy drugi branch wprowadza do niego zmiany. Git nie jest w stanie automatycznie zdecydować, którą wersję zachować, i dlatego pojawia się konflikt scalenia.

>Aby rozwiązać konflikt, musisz zdecydować, którą wersję chcesz zachować: wersję z twojego branch'a, wersję z innego branch'a, czy może kombinację obu.

>Gdy wystąpi konflikt, Git zmodyfikuje pliki, które go zawierają, dodając specjalne znaczniki, które pokazują, które linie pochodzą z którego branch'a. Wygląda to mniej więcej tak:

     <<<<<<< HEAD
    This is some content from your branch.
    =======
    This is some content from the other branch.
    >>>>>>> branch-name

>Aby rozwiązać konflikt, musisz edytować plik, usunąć te znaczniki i zdecydować, która wersja powinna pozostać. Może to wyglądać tak:

    This is the resolved content that I decided to keep.

>Po rozwiązaniu konfliktów, musisz dodać plik do repozytorium i zatwierdzić go:

    git add filename
    git commit -m "Resolved merge conflict in filename"

>Warto zauważyć, że istnieją narzędzia do rozwiązywania konfliktów (zwane narzędziami do rozwiązywania konfliktów merge), które mogą ułatwić ten proces, szczególnie gdy jest wiele konfliktów do rozwiązania. Niektóre popularne narzędzia to KDiff3, Meld, P4Merge i wielu innych.

>Pamiętaj, że najlepszym sposobem na uniknięcie konfliktów scalenia jest regularne aktualizowanie swojego branch'a z głównym branch'em (zazwyczaj "master" lub "main"), aby twoje zmiany były na bieżąco z innymi zmianami w projekcie.

#### What is a branch? (Co to jest oddział?(gałęź))

>Gałąź (branch) to funkcja w systemie kontroli wersji, takim jak Git, która pozwala rozwijać funkcje izolowane od siebie. Każda gałąź reprezentuje niezależną linię rozwoju. Możesz pracować na swojej gałęzi bez wpływania na główną linię rozwoju (zwykle nazywaną **master** lub **main**).

>Gdy skończysz pracę na swojej gałęzi, możesz połączyć ją z główną gałęzią za pomocą operacji zwaną scaleniem (merge). Jeśli twoja gałąź wprowadza konflikty z główną gałęzią, będziesz musiał je rozwiązać przed scaleniem.

Poniżej znajduje się przykładowy proces pracy z gałęziami:

    # Tworzenie nowej gałęzi
    git branch moja-nowa-gałęź
    
    # Przełączanie się na nową gałąź
    git checkout moja-nowa-gałęź
    
    # Teraz jesteśmy na gałęzi 'moja-nowa-gałęź' i możemy wprowadzać zmiany
    
    echo "Nowa funkcja" > new_feature.txt
    git add new_feature.txt
    git commit -m "Dodano nową funkcję"
    
    # Wróć do gałęzi master
    git checkout master
    
    # Scal gałąź 'moja-nowa-gałęź' do 'master'
    git merge moja-nowa-gałęź

>W tym przykładzie tworzymy nową gałąź **moja-nowa-gałęź**, przełączamy się na nią, dodajemy nowy plik, commitujemy go, a następnie wracamy do gałęzi **master** i scalamy **moja-nowa-gałęź** z **master**.

>Warto zauważyć, że możemy utworzyć nową gałąź i od razu się na nią przełączyć, używając polecenia **git checkout -b nazwa_gałęzi**.

#### What is a pull/merge request and why is it used? (Co to jest żądanie ściągnięcia/scalenia i dlaczego jest używane?)

>Pull request (nazywany też merge request w niektórych systemach, takich jak GitLab) to funkcja dostępna w wielu systemach kontroli wersji, które działają na zasadzie hostingu, takich jak GitHub, Bitbucket czy GitLab.

>Pull request jest prośbą o scalenie jednej gałęzi do innej. Zwykle jest używany w kontekście pracy zespołowej, gdy chcesz wprowadzić zmiany, które dokonałeś w swoim branchu, do głównej gałęzi projektu. Pull request daje innym członkom zespołu możliwość przeglądania i dyskutowania nad proponowanymi zmianami przed ich scaleniem.

>Poniżej znajduje się przykładowy proces tworzenia pull request na GitHubie, ale proces będzie bardzo podobny dla innych systemów:

1. Tworzysz nową gałąź i dokonujesz w niej swoich zmian.

        git checkout -b my-feature-branch
        echo "My new feature" > feature.txt
        git add feature.txt
        git commit -m "Add new feature"

2. Następnie wysyłasz swoją gałąź do zdalnego repozytorium.
    
        git push origin my-feature-branch

3. Teraz możesz utworzyć pull request. Wchodzisz na stronę swojego repozytorium na GitHubie, przechodzisz do zakładki "Pull requests" i klikasz "New pull request". Wybierasz gałąź, którą chcesz scalić (w tym przypadku **my-feature-branch**), a następnie gałąź, do której chcesz scalić (zazwyczaj **master** lub **main**).

4. Wpisujesz opis swojego pull requesta, w którym wyjaśniasz, co robią twoje zmiany. Możesz też @mentionować innych członków zespołu, jeśli chcesz, aby go przeglądali. Następnie klikasz "Create pull request".

5. Inni członkowie zespołu mogą teraz przeglądać twój pull request, komentować go i sugerować zmiany. Jeśli wszystko jest w porządku, mogą go zaakceptować i scalić z główną gałęzią.

>Pull requesty są kluczowym elementem pracy zespołowej przy użyciu Git. Umożliwiają code review, co pomaga utrzymać jakość kodu, poprawiać umiejętności programistyczne i zapewniać, że wszyscy członkowie zespołu są na bieżąco z tym, co dzieje się w projekcie.


#### What are the differences between a merge and a rebase? (Jakie są różnice między scalaniem a rebase?)

>Operacje **merge** i **rebase** to dwie różne metody łączenia zmian z jednej gałęzi do innej w systemie kontroli wersji Git. Obie metody mają swoje zastosowania i skutki, a wybór między nimi zależy od konkretnego przypadku.

>**git merge** bierze zawartość punktu końcowego dwóch gałęzi i próbuje je automatycznie złączyć. Tworzy nowy commit, który zawiera zmiany z obu gałęzi.

Przykład użycia **git merge**:

    git checkout master
    git merge feature-branch

>Z drugiej strony **git rebase** przenosi lub "aplikuje" zmiany z jednej gałęzi do innej. W przeciwieństwie do scalania, **rebase** "przepisuje" historię commitów, tworząc nowe commity dla każdego commitu z oryginalnej gałęzi.

Przykład użycia **git rebase**:

    git checkout feature-branch
    git rebase master

Główna różnica między tymi dwiema metodami polega na tym, jak są prezentowane zmiany w historii projektu:

* **merge** tworzy nowy commit, który łączy zmiany z dwóch gałęzi, co prowadzi do nie liniowej historii projektu.
* **rebase** przepisuje historię commitów, co prowadzi do liniowej historii projektu.

>Wybór między **merge** a **rebase** zależy od wielu czynników, takich jak zasady zespołu, złożoność projektu, a także twoje osobiste preferencje. Niektórzy wolą **rebase** ze względu na jego zdolność do utrzymania liniowej historii, co może ułatwić śledzenie zmian. Inni wolą **merge**, który zachowuje oryginalną historię i pozwala łatwiej zrozumieć, jak doszło do zmian w projekcie.

>Ważne jest, aby zrozumieć, że **rebase** może być bardziej skomplikowany dla początkujących i może prowadzić do problemów, jeśli używany jest niepoprawnie, szczególnie gdy pracujesz z innymi w zdalnym repozytorium. Dlatego zawsze warto dobrze zrozumieć, co robi rebase, zanim zaczniesz go używać w swoich projektach.

#### What are the differences between git revert and git reset commands? (Jakie są różnice między poleceniami git revert i git reset?)

>**git revert** i **git reset** to dwie różne operacje w systemie kontroli wersji Git, które umożliwiają cofanie zmian. Chociaż obie operacje mają podobny cel, działają w zasadniczo różny sposób i są używane w różnych kontekstach.

>**git revert** jest operacją, która tworzy nowy commit, który odwraca zmiany wprowadzone w określonym commicie. Jest to operacja bezpieczna do używania w publicznych gałęziach, ponieważ nie zmienia istniejącej historii commitów.

Przykład użycia **git revert**:

    git revert <commit_id>

>**git reset**, z drugiej strony, jest używany do zmiany stanu Twojego repozytorium do konkretnego commitu. Istnieją trzy tryby resetu (**soft**, **mixed**, **hard**), które decydują, co się dzieje z indeksem i drzewem roboczym.

>Przykładowo, **git reset --hard** jest operacją destrukcyjną, która porzuci wszystkie niezatwierdzone zmiany i przesunie wskaźnik HEAD do określonego commitu. Powinno być używane ostrożnie, ponieważ utracone zmiany są nieodwracalne.

Przykład użycia **git reset**:

    git reset --hard <commit_id>

Podsumowując:

* **git revert** jest operacją bezpieczną, która odwraca zmiany wprowadzone w konkretnym commicie, tworząc nowy commit.
* **git reset** jest potężnym narzędziem, które pozwala na zmianę stanu repozytorium do konkretnego commitu. Może być destrukcyjne w zależności od użytego trybu (soft, mixed, hard) i powinno być używane z ostrożnością.