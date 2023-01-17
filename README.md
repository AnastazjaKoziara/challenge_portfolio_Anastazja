## Task 1 
### Subtask 1
8 pkt
### Subtask 3
Hej, nazywam się Anastazja i właśnie tworzę swoje porfolio challenge Dare IT. *Dlaczego to robię?* Żeby wyjść ze swoich ramek i pokazać sobie że mogę nauczyć się czegoś nowego, co może zmienić moją kariere.  

Wielokrotnie IT ~*(aka mąż-programista)*~ szepcze mi do ucha więc chciałam w końcu spróbować z czym to się je. Ścieżek rozwoju jest bardzo dużo i cięzko sobie od razu coś upolować, stwierdziłam więc że dobrym wprowadzeniem do świata IT będzie tester oprogramowania.  


No cóż, powodzenia sobie życzę!
### Substask 4
* Aplikacja służy do zarządzania graczami, meczami pliku nożnej, Pozwala na prowadzenie statystyk (za pomocą raportów oraz tabeli z graczami), dzięki którym można usprawnić funkcjonowanie drużyny/klubu/platformy. Taka aplikacja jest przydatna dla klubów piłkarskich w celu łatwiejszego zarządzania graczami, meczami i ogólnego zarządzania klubu.  

* W aplikacji na stronie głównej możemy monitorować statystyki ogólne klubu, ilość rozegranych meczy/graczy/raportów. Dzięki linkom pomocniczym można łatwo przejść do utworzenia nowego gracza (co prawda brakuje tej opcji w zakładce gracze; w linkach pomocniczych powinny być linki do tworzenia meczu/raportu). Dodatkowo jest opcja przetłumaczenia aplikacji na język angielski.
* W zakładce gracze można przejrzeć wszystkich dodanych graczy, wyszukać konkretnego gracza poprzez wyszukiwarkę na górnym pasku strony lub poprzez odpowiednie filtry (po kliknięciu reset filtrów nie pojawia się początkowa lista graczy); można wygenerować listę graczy w plik csv lub wydrukować listę wybranych graczy (wygląd tabeli jest zupełnie inny niż na stronie), dodatkowo można sterować parametrami tabeli do wyświetlenia listy.
W zakładce konkretnego gracza (można go wybrać w zakładce gracze lub utworzyć nowego) można przypisać mu meczy, założyć raport oraz zaimplementować całą rozgrywkę w zakładce „rozpocznij mecz”. Przez brak spójności designu każdej zakładki, użytkownik może pogubić się co w którym miejscu może zrobić. Po wejściu w konkretnego gracza nie powinno się od razu wchodzić w tryb edycji gracza.
Zakładka mecze służy do zbierania informacji o różnych meczach, ich wynikach, przedstawiana w postaci tabeli. Szkoda że nie można jej wygenerować w plik/wydrukować/wyszukać jak w zakładce gracze. Dodatkowo w tabeli jest kolumna ‚akcja’ w której można edytować stworzony mecz, stworzyć raport albo rozpocząć mecz.
Funkcja rozpocznij mecz służy do wirtualnej rozgrywki meczu, przepisaniu goli/faula,rozpoczęcie kolejnej polowy meczu. Bezpośrednio można zapisać zmiany do raportu które idą do statystyki. Ta funkcja nie działa prawidłowo i brakuje ogólnej logiki w jaki sposób cała rozgrywka ma być zapisana. Brak pokrycia danych w meczu a w rozpocznij mecz, można stworzyć więcej niż 2 połowy meczu, więcej niż 90 min.
Zakładka raport służy do wyświetlania raportów z konkretnych meczy, można dodać raport (aczkolwiek ta funkcja nie działa w tej zakładzie - bug, przekierowuje na zakładkę z meczami). Podczas implementacji meczu informacja o wynikach trafia do raportu, gdzie zbierana jest statystyka. Sam raport ma złą skalę wyświetlania niedostosowana do całej aplikacji, przez co wygląda niechlujnie. Brakuje możliwości ściągnięcia/wydrukowania raportu.
Ocena interfejsu: Nieprzejrzysta aplikacja w której ciężko jest zrozumieć co można w niej zrobić i jak wyciągnąć przydatne informacje dla klienta. (Chaos) Niespójny design (mieszanie języków przycisków i komunikatów, różny rodzaj komunikatów, różne kolory), opis aplikacji na głównej stronie nie jest wyeksponowany, zła walidacja systemu (fronted nie komunikuje błędów, gdy backed pokazuje błąd). Wyszukiwarka obecna tylko w zakładce gracze, wygląd raportu niedostosowany do strony aplikacji.
Aplikacja nie jest intuicyjna,
 brakuje podpowiedzi systemu jakie kroki można wykonać. 
Sposób tworzenia meczu/raportu jest niezrozumiały i niespójny, dane nie pokrywają się ze sobą. 
Po wprowadzeniu zmian aplikacja nie wychodzi z trybu edycji, mimo tego że komunikat mówi co innego. Przejście między zakładkami nie jest spójne, w zakładce gracza wchodzisz od razu w tryb edycji.
