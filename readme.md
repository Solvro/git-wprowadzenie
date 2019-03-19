# Git Prelelekcja

## Po co się używa Gita? Dlaczego warto

Git dba o to, by każdy uczestnik projektu miał zawsze jego najnowszą wersję. Git należy do rozproszonych systemów kontroli wersji, a więc oprócz tego, że projekt jest na serwerze, to każdy z uczestników projektu ma swoją lokalną wersję u siebie. Zatem jeśli serwer szlag trafi, to nic złego nie powinno się stać. Git potrafi sobie radzić także z takimi sytuacjami, jak edycja tego samego pliku przez dwie osoby. System po prostu postara się połączyć wprowadzone zmiany i jednej i drugiej osoby. Co więcej, Git przechowuje wszystkie wersje danego pliku, dlatego jeśli coś się popsuje, nie ma problemu by odzyskać poprzednią wersję. Dlatego chociażby dlatego warto używać Gita nawet jeśli pracuje się solo.

Pracując samemu:

1. Możliwość łatwego cofnięcia katastrofy
2. Eksperymentowanie bez niszczenia
3. Łatwa praca z wielu miejsc
4. Łatwe włączenie nowych osób
5. Dwie pieczenie na jednym ogniu (CV)

### Co to jest Git

Git to rozproszony system kontroli wersji, u którego podstaw leżą bardzo proste założenia. To jest jednak jego potęgą — elastyczność oraz kilka sprytnych pomysłów spowodowała że powstało narzędzie proste w użyciu, pasujące zarówno do prostych projektów jak i ogromnych przedsięwzięć (jak np. jądro systemu linux).

Git jest praktycznie wymaganą kompetencją w wielu firmach i ponieważ praca programisty opiera się na pracy w zespole, jest to technologia, którą powinieneś mieć opanowaną.

__SCM__ — to akronim od Source Code Management, czyli dosłownie kontrola kodu (w języku polskim funkcjonuje określenie system kontroli wersji); jest to system który pozwala na archiwizowanie i śledzenie zmian w kodzie, dzięki czemu możemy cofać się w historii lub podejrzeć, kto był autorem konkretnej zmiany

__Repozytorium__ — ‘kontener’ na określony zbiór kodu, najczęściej jeden projekt; repozytorium pozwala grupować kod i zmiany, dzięki czemu możemy przeglądać wszystkie zmiany wykonane w ramach jednego repozytorium, przyznawać uprawnienia do repozytoriów oraz pobierać / kopiować je

__Commit__ — jest to proces ‘wysłania’ na repozytorium określonych zmian w kodzie — jeśli pobierasz kod z repozytorium, następnie dokonujesz modyfikacji i wysyłasz te zmiany z powrotem do repozytorium, proces ten nosi nazwę commitowania, a same zmiany wysłane razem nazywamy commitem lub rewizją

__pull / push__ — odpowiednio pobranie i wysłanie zmian (jednego lub wielu commitów) z/do innego repozytorium

__diff__ — (ang. różnica) — jest to różnica pomiędzy różnymi rewizjami — dzięki temu możemy zobaczyć, które fragmenty uległy zmianie oraz w jaki sposób; pozwala to także zoptymalizować transfer danych pomiędzy repozytoriami

__fork__ — kopia repozytorium; szczególnie popularne w przypadku projektów open-source, dzięki czemu możemy skopiować cały projekt i rozwijać go niezależnie (np. dopasowując do naszych potrzeb)

__branch__ — odgałęzienie, wersja wewnątrz repozytorium; branche pozwalają na prace wielu osobom równocześnie, bez ciągłego wchodzenia sobie w drogę i nadpisywania zmian — każdy może pracować na swoim branchu, dopiero po zakończeniu pracy łącząc zmiany z innymi i rozwiązując problemy

__merge__ — połączenie wielu zmian z różnych źródeł, które może skutkować niekompatybilnymi zmianami wymagającymi ręcznych modyfikacji; merge pozwala łączyć prace wykonywane w różnych obszarach, które mogą się zazębiać, w jedną całość w sposób kontrolowany i świadomy

## Instalacja Gita

### Linux

Fedora:
> sudo yum install git-core

Debianowe:
> sudo apt-get install git

### Mac

http://sourceforge.net/projects/git-osx-installer/

### Windows

http://msysgit.github.com/

## Klient Gita

Osobiście, szczerze was zachęcam do korzystania z oryginalnego Git Basha, albo, w przypadku systemów unixowych - z konsoli wbudowanej w system. Uważam, że warto się przełamać do używania konsoli i nie jest to narzędzie tak skomplikowane jak się wydaje, pozwala ponadto dużo szybciej załapać o co w tym Gicie chodzi i jak to wszystko działa. Dla tych jednak, którzy na samą myśl o wklepywaniu literek do commandline dostają dreszczy, powstało wiele narzędzi takich jak SmarGit, SourceTree, lub GitKraken.

## Repozytorium Git

Na wykładzie korzystać będziemy z najpopularniejszej chyba platformy - GitHuba. Polecam oswoić się z nią, jest to również wizytówka ciebie jako programisty. Możesz na GitHuba wstawiać swoje projekty, od niedawna GitHub oferuje darmowe repozytoria prywatne, więc możesz też tam trzymać na przykład zadania na zajęcia. Warto zdawać sobie sprawe z tego ze GitHub nie równa się Git i istnieje więcej tego typu platform - np Gitlab czy Bitbucket.

## Jednorazowa konfiguracja

> git config --global user.name "John Doe"  
> git config --global user.email "john.doe@solvro.pl"

## Tworzenie nowego repozytorium / klonowanie isniejącego

### Inicjacja repozytorium

> git init

To polecenie stworzy nowy podkatalog o nazwie .git, zawierający wszystkie niezbędne pliki — szkielet repozytorium Gita. W tym momencie żadna część twojego projektu nie jest jeszcze śledzona.

Aby rozpocząć kontrolę wersji istniejących plików powinieneś rozpocząć ich śledzenie i utworzyć początkową rewizję. Możesz tego dokonać kilkoma poleceniami add (dodaj) wybierając pojedyncze pliki, które chcesz śledzić, a następnie zatwierdzając zmiany poleceniem commit:

> git add README  
> git add \*.js  
> git add .  
> git commit -m "komentarz dla commita"  

### Stworzenie repzytorium na GitHubie - poruszanie się po platformie, remote add

> git remote add origin https://github.com/okkindel/sample.git
> git push origin master

### Sklonowanie repozutorium, wypchnięcie kolejnego pliku

> git clone https://github.com/okkindel/sample.git

## Praca z Gitem

Sprawdzanie stanu plików:

Podstawowe narzędzie używane do sprawdzenia stanu plików to polecenie git status. Jeśli uruchomisz je bezpośrednio po sklonowaniu repozytorium, zobaczysz wynik podobny do poniższego:

> git status  

```
On branch master
nothing to commit, working tree clean
```

Oznacza to, że posiadasz czysty katalog roboczy — innymi słowy nie zawiera on śledzonych i zmodyfikowanych plików. Git nie widzi także żadnych plików nieśledzonych, w przeciwnym wypadku wyświetliłby ich listę. W końcu polecenie pokazuje również gałąź, na której aktualnie pracujesz. Póki co, jest to zawsze master, wartość domyślna.

#### Dodanie pliku, status, śledzenie, status

Powiedzmy, że dodajesz do repozytorium nowy, prosty plik. Jeżeli nie istniał on wcześniej, po uruchomieniu git status zobaczysz go jako plik nieśledzony, jak poniżej. Widać, że twój nowy plik nie jest jeszcze śledzony, ponieważ znajduje się pod nagłówkiem „Untracked files” (Nieśledzone pliki) w informacji o stanie. Nieśledzony oznacza, że Git widzi plik, którego nie miałeś w poprzedniej migawce (zatwierdzonej kopii); Git nie zacznie umieszczać go w przyszłych migawkach, dopóki sam mu tego nie polecisz. Zachowuje się tak, by uchronić cię od przypadkowego umieszczenia w migawkach wyników działania programu lub innych plików, których nie miałeś zamiaru tam dodawać.

Aby rozpocząć śledzenie nowego pliku, użyj polecenia git add. Jeśli uruchomisz teraz ponownie polecenie status, zobaczysz, że twój plik jest już śledzony i znalazł się pod nagłówkiem 'zmiany do zatwierdzenia'.

```
okkindel@hajduk  ~/Dokumenty/SOLVRO/Prelekcje/dump   master  git status
	On branch master
	nothing to commit, working tree clean
okkindel@hajduk  ~/Dokumenty/SOLVRO/Prelekcje/dump   master  touch file1
okkindel@hajduk  ~/Dokumenty/SOLVRO/Prelekcje/dump   master  git status
	On branch master
	Untracked files:
  	(use "git add <file>..." to include in what will be committed)
    file1
	nothing added to commit but untracked files present (use "git add" to track)
okkindel@hajduk  ~/Dokumenty/SOLVRO/Prelekcje/dump   master  git add file1
okkindel@hajduk  ~/Dokumenty/SOLVRO/Prelekcje/dump   master ✚  git status
	On branch master
	Changes to be committed:
  	(use "git reset HEAD <file>..." to unstage)
	nowy plik:     file1
```

#### Zmodyfikowanie istniejącego pliku, śledzenie

Zmodyfikujmy teraz plik, który był już śledzony. Jeśli zmienisz śledzony wcześniej plik, a następnie uruchomisz polecenie status, zobaczysz coś podobnego:

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        nowy plik:     file1

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        zmodyfikowany: LICENCE.md
```

Plik pojawia się w sekcji „Changes not staged for commit“ (Zmienione ale nie zaktualizowane), co oznacza, że śledzony plik został zmodyfikowany, ale zmiany nie trafiły jeszcze do poczekalni. Aby je tam wysłać, uruchom polecenie git add (jest to wielozadaniowe polecenie — używa się go do rozpoczynania śledzenia nowych plików, umieszczania ich w poczekalni, oraz innych zadań, takich jak oznaczanie rozwiązanych konfliktów scalania). Uruchom zatem git add by umieścić plik w poczekalni, a następnie ponownie wykonaj git status:

```
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        zmodyfikowany: LICENCE.md
        nowy plik:     file1
```

#### Powtórne zmodyfikowanie istniejącego pliku

Oba pliki znajdują się już w poczekalni i zostaną uwzględnione podczas kolejnego zatwierdzenia zmian. Załóżmy, że w tym momencie przypomniałeś sobie o dodatkowej małej zmianie, którą koniecznie chcesz wprowadzić do pliku jeszcze przed zatwierdzeniem. Otwierasz go zatem, wprowadzasz zmianę i jesteś gotowy do zatwierdzenia. Uruchom jednak git status raz jeszcze.

Co do licha? Plik widnieje teraz jednocześnie w poczekalni i poza nią. Jak to możliwe? Okazuje się, że Git umieszcza plik w poczekalni dokładnie z taką zawartością, jak w momencie uruchomienia polecenia git add. Jeśli w tej chwili zatwierdzisz zmiany, zostanie użyta wersja dokładnie z momentu uruchomienia polecenia git add, nie zaś ta, którą widzisz w katalogu roboczym w momencie wydania polecenia git commit. Jeśli modyfikujesz plik po uruchomieniu git add, musisz ponownie użyć git add, aby najnowsze zmiany zostały umieszczone w poczekalni

### Wyłączenie śledzenia

Jeżeli się rozmyślimy i nie chcemy jednak śledzić naszego pliku aby go potem commitować możemy użyć polecenia git reset:

> git reset file

## Ignorowanie plików

Często spotkasz się z klasą plików, w przypadku których nie chcesz, by Git automatycznie dodawał je do repozytorium, czy nawet pokazywał je jako nieśledzone. Są to ogólnie pliki generowane automatycznie, takie jak dzienniki zdarzeń, czy pliki tworzone w czasie budowania projektu. W takich wypadkach tworzysz plik zawierający listę wzorców do nich pasujących i nazywasz go .gitignore.

## Zatwierdzanie zmian

Teraz, kiedy twoja poczekalnia zawiera dokładnie to, co powinna, możesz zatwierdzić swoje zmiany. Pamiętaj, że wszystko czego nie ma jeszcze w poczekalni — każdy plik, który utworzyłeś lub zmodyfikowałeś, a na którym później nie uruchomiłeś polecenia git add — nie zostanie uwzględnione wśród zatwierdzanych zmian. Pozostanie wyłącznie w postaci zmodyfikowanych plików na twoim dysku.

W tym wypadku, kiedy ostatnio uruchamiałeś git status, zobaczyłeś, że wszystkie twoje zmiany są już w poczekalni, więc jesteś gotowy do ich zatwierdzenia. Najprostszy sposób zatwierdzenia zmian to wpisanie git commit:

> git commit

Zostanie uruchomiony edytor tekstu. Po opuszczeniu edytora, Git stworzy nową migawkę opatrzoną twoim opisem zmian (uprzednio usuwając z niego komentarze i podsumowanie zmian). Alternatywnie opis rewizji możesz podać już wydając polecenie commit, poprzedzając go flagą -m. 

Sama operacja rewizji zwróciła dodatkowo garść informacji, między innymi, gałąź do której dorzuciłeś zmiany (master), ich sumę kontrolną SHA-1, ilość zmienionych plików oraz statystyki dodanych i usuniętych linii kodu.

Aby następnie wypchnąć zaakceptowane zmiany na zewnętrzne repozytorium (w naszym przypadku GitHub), użyj polecenia push:

> git push

Polecenie to zbiera wszystkie zatwoerdzone migawki i zapisuje je w skonfigurowanym wcześniej repozytorium.

## Usuwanie plików

Aby usunąć plik z Gita, należy go najpierw wyrzucić ze zbioru plików śledzonych, a następnie zatwierdzić zmiany. Służy do tego polecenie git rm, które dodatkowo usuwa plik z katalogu roboczego. Nie zobaczysz go już zatem w sekcji plików nieśledzonych przy następnej okazji.

Jeżeli po prostu usuniesz plik z katalogu roboczego i wykonasz polecenie git status zobaczysz go w sekcji "Zmienione ale nie zaktualizowane" (Changes not staged for commit) (czyli, poza poczekalnią).

### Cofanie zmian w zmodyfikowanym pliku

Z pomocą przybywa raz jeszcze polecenie git status. Git konkretnie wskazuje jak pozbyć się dokonanych zmian. Zróbmy zatem co każe Git:

> git checkout -- file

Możesz teraz przeczytać, że zmiany zostały cofnięte. Powinieneś sobie już także zdawać sprawę, że jest to dość niebezpieczne polecenie: wszelkie zmiany jakie wykonałeś w pliku przepadają - w rzeczy samej został on nadpisany poprzednią wersją. Nigdy nie używaj tego polecenia dopóki nie jesteś absolutnie pewny, że nie chcesz i nie potrzebujesz już danego pliku.

## Podgląd historii

Po kilku rewizjach, lub w przypadku sklonowanego repozytorium zawierającego już własną historię, przyjdzie czas, że będziesz chciał spojrzeć w przeszłość i sprawdzić dokonane zmiany. Najprostszym, a zarazem najsilniejszym, służącym do tego narzędziem jest git log.

> git log

Komenda ta przyda nam się jeszcze później.

## Praca ze zdalnym repozytorium

W momencie, gdy chcemy wypchnąć zmiany na zewnętrzne repozytorium, okazuje się, że ktoś wprowadził swoje zmiany przed nami. Świadczy o tym wpis

```
To https://github.com/okkindel/sample.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/okkindel/sample.git'
podpowiedź: Updates were rejected because the remote contains work that you do
podpowiedź: not have locally. This is usually caused by another repository pushing
podpowiedź: to the same ref. You may want to first integrate the remote changes
podpowiedź: (e.g., 'git pull ...') before pushing again.
podpowiedź: See the 'Note about fast-forwards' in 'git push --help' for details.
```

Po raz kolejny najlepiej będzie zrobić, to co podpowiada nam program. Użyjemy polecenia git pull:

> git pull

Jeśli znajdujesz się w gałęzi master i uruchomisz polecenie git pull, zmiany ze zdalnego repozytorium zaraz po pobraniu automatycznie zostaną scalone z gałęzią master w twoim, lokalnym repozytorium.

## Gałęzie

Prawie każdy system kontroli wersji posiada wsparcie dla gałęzi. Rozgałęzienie oznacza odbicie od głównego pnia linii rozwoju i kontynuację pracy bez wprowadzania tam bałaganu. W wielu narzędziach kontroli wersji jest to proces dość kosztowny, często wymagający utworzenia nowej kopii katalogu z kodem, co w przypadku dużych projektów może zająć sporo czasu.

Niektórzy uważają model gałęzi Gita za jego „killer feature” i z całą pewnością wyróżnia go spośród innych narzędzi tego typu. Co w nim specjalnego? Sposób, w jaki Git obsługuje gałęzie, jest niesamowicie lekki, przez co tworzenie nowych gałęzi jest niemalże natychmiastowe, a przełączanie się pomiędzy nimi trwa niewiele dłużej. W odróżnieniu od wielu innych systemów, Git zachęca do częstego rozgałęziania i scalania projektu, nawet kilkukrotnie w ciągu jednego dnia. Zrozumienie i opanowanie tego wyjątkowego i potężnego mechanizmu może dosłownie zmienić sposób, w jaki pracujesz.

Jak utworzyć nową gałąź? Jest to bardzo proste i wymaga jedynie wpisania jednej komendy:

> git branch testing

Skąd Git wie, na której gałęzi się aktualnie znajdujesz? Utrzymuje on specjalny wskaźnik o nazwie HEAD. W Gicie jest to wskaźnik na lokalną gałąź, na której właśnie się znajdujesz. W tym wypadku, wciąż jesteś na gałęzi master. Polecenie git branch utworzyło jedynie nową gałąź, ale nie przełączyło cię na nią.

Aby przełączyć się na istniejącą gałąź, używasz polecenia git checkout. Przełączmy się zatem do nowo utworzonej gałęzi testing:

> git checkout testing

Istnieje sposób na utworzenie nowej gałęzi i jednoczesne przełączenie się na nią. Robimy to komendą:

> git checkout -b testing

Nowa gałąź zawiera migawkę z momentu tworzenia tej gałęzi, oznaca to, że od tej chwili na obu gałęziach możemy tworzyć zupełnie różne zmiany a Git będzie rozpatrywał je osobno dla każdej gałęzi.

### Podgląd wszystkich gałęzi

Polecenie:

> git branch

pozwala na wylistowanie nazw wszystkich lokalnych gałęzi. Aby zobaczyć wszystkie gałęzie w repozytorium, polecenie to musimy poprzedzić komendą:

> git pull

## Scalanie gałęzi

* Pod warunkiem, że nie ma konfliktu zmian pomiędzy galęziami

	> git merge nazwa_gałęzi

* Rozwiązywanie konflików na przykładzie VS Code

Jeżeli chcemy przełączyć się na inną gałąź podczas pisania kodu, Git poinformuje nas, że mamy niezaakceptowane zmiany. Mamy w tym momencie 3 wyjścia:

1. Usunięcie swoich zmian od czasu ostatniego commita:

	> git reset --hard

2. Zaakceptowanie wszystkich zmian:

	> git add .  
	> git commit -m "commit message"  

3. Skopiowanie zmian do schowka:

	> git stash

	aby przywrócić zmiany, po ponownym przełączeniu się na odpowiednią gałąź wpisujemy

	> git stash pop

## Poruszanie się po historii repozytorium

Polecenie

> git log

listuje wszystkie commity na zadanym branchu. Przełączać możemy się nie tylko pomiędzy gałęziami ale również pomiędzy commitami w historii. W tym celu kopiujemy hash commita z historii i używamy komendy:

> git checkout hash

Możemy się również przełączyć o zadaną ilość migawek do tyłu.

> git checkout HEAD~2

Możemy z takiej pozycji utworzyć nowego brancha. Aby wrócić do najświeższych zmian, możemy przełączyć się spowrotem na gałąź, np:

> git checkout master

## Merge requesty

*Na przykładzie GitHuba*

## Przydatne programy

- zsh + ohmyzsh + git plugin
- fuzzy finder
- zsh autocomplete
- fuck

## skróty w git plugin dla zsh

- g
- gp
- gcmsg
- gst
- glg
