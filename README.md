## Task 1 
### Subtask 1
8 pkt
### Subtask 3
Hej, nazywam się Anastazja i właśnie tworzę swoje porfolio challenge Dare IT. *Dlaczego to robię?* Żeby wyjść ze swoich ramek i pokazać sobie że mogę nauczyć się czegoś nowego, co może zmienić moją kariere.  

Wielokrotnie IT ~*(aka mąż-programista)*~ szepcze mi do ucha więc chciałam w końcu spróbować z czym to się je. Ścieżek rozwoju jest bardzo dużo i cięzko sobie od razu coś upolować, stwierdziłam więc że dobrym wprowadzeniem do świata IT będzie tester oprogramowania.  


No cóż, powodzenia sobie życzę!
### Subtask 4
* Aplikacja służy do zarządzania graczami, meczami piłkiu nożnej, Pozwala na prowadzenie statystyk (za pomocą raportów oraz tabeli z graczami), dzięki którym można usprawnić funkcjonowanie drużyny/klubu/platformy. Taka aplikacja jest przydatna dla klubów piłkarskich w celu łatwiejszego zarządzania graczami, meczami i ogólnego zarządzania klubu.  

* W aplikacji **na stronie głównej** możemy monitorować statystyki ogólne klubu, ilość rozegranych meczy/graczy/raportów. Dzięki linkom pomocniczym można łatwo przejść do utworzenia nowego gracza (co prawda brakuje tej opcji w zakładce gracze; w linkach pomocniczych powinny być linki do tworzenia meczu/raportu). Dodatkowo jest opcja przetłumaczenia aplikacji na język angielski.
  * W **zakładce gracze** można przejrzeć wszystkich dodanych graczy, wyszukać konkretnego gracza poprzez wyszukiwarkę na górnym pasku strony lub poprzez odpowiednie filtry (po kliknięciu reset filtrów nie pojawia się początkowa lista graczy); można wygenerować listę graczy w plik csv lub wydrukować listę wybranych graczy (wygląd tabeli jest zupełnie inny niż na stronie), dodatkowo można sterować parametrami tabeli do wyświetlenia listy.
  * W **zakładce konkretnego gracza** (można go wybrać w zakładce gracze lub utworzyć nowego) można przypisać mu meczy, założyć raport oraz zaimplementować całą rozgrywkę w zakładce „rozpocznij mecz”. Przez brak spójności designu każdej zakładki, użytkownik może pogubić się co w którym miejscu może zrobić. Po wejściu w konkretnego gracza nie powinno się od razu wchodzić w tryb edycji gracza.
    * **Zakładka mecze** służy do zbierania informacji o różnych meczach, ich wynikach, przedstawiana w postaci tabeli. Szkoda że nie można jej wygenerować w plik/wydrukować/wyszukać jak w zakładce gracze. Dodatkowo w tabeli jest kolumna ‚akcja’ w której można edytować stworzony mecz, stworzyć raport albo rozpocząć mecz.
    * Funkcja **rozpocznij mecz** służy do wirtualnej rozgrywki meczu, przepisaniu goli/faula,rozpoczęcie kolejnej polowy meczu. Bezpośrednio można zapisać zmiany do raportu które idą do statystyki. Ta funkcja nie działa prawidłowo i brakuje ogólnej logiki w jaki sposób cała rozgrywka ma być zapisana. Brak pokrycia danych w meczu a w rozpocznij mecz, można stworzyć więcej niż 2 połowy meczu, więcej niż 90 min.
    * **Zakładka raport** służy do wyświetlania raportów z konkretnych meczy, można dodać raport (aczkolwiek ta funkcja nie działa w tej zakładzie - bug, przekierowuje na zakładkę z meczami). Podczas implementacji meczu informacja o wynikach trafia do raportu, gdzie zbierana jest statystyka. Sam raport ma złą skalę wyświetlania niedostosowana do całej aplikacji, przez co wygląda niechlujnie. Brakuje możliwości ściągnięcia/wydrukowania raportu.
* Ocena interfejsu: Nieprzejrzysta aplikacja w której ciężko jest zrozumieć co można w niej zrobić i jak wyciągnąć przydatne informacje dla klienta. (Chaos) Niespójny design (mieszanie języków przycisków i komunikatów, różny rodzaj komunikatów, różne kolory), opis aplikacji na głównej stronie nie jest wyeksponowany, zła walidacja systemu (fronted nie komunikuje błędów, gdy backed pokazuje błąd). Wyszukiwarka obecna tylko w zakładce gracze, wygląd raportu niedostosowany do strony aplikacji.
* Aplikacja nie jest intuicyjna,
  * Brakuje podpowiedzi systemu jakie kroki można wykonać. 
  * Sposób tworzenia meczu/raportu jest niezrozumiały i niespójny, dane nie pokrywają się ze sobą. 
  * Po wprowadzeniu zmian aplikacja nie wychodzi z trybu edycji, mimo tego że komunikat mówi co innego. Przejście między zakładkami nie jest spójne, w zakładce gracza wchodzisz od razu w tryb edycji.  

| Miejsce                | Bug/błąd                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Logowanie użytkownika  | Po wpisaniu błędnych danych komunikat wyświetla się po angl                                                                                                                                                                                                                                                                                                                                                                                           |
| Tworzenie gracza       | Brakuje informacji o nieprawidłowym mailu na frontedzie (bad request 400) przez co nie można zapisać gracza; Pozwala wpisać litery w rubryce telefon; Możliwe jest wpisanie liczb w nazwisko; W link można wpisać cokolwiek zamiast linka; Data urodzenia rok bez ograniczeń; Ujemne wagi i wzrost; Dodanie województwa jest zbędne w przypadku gracza z zagranicy, lepiej dodać miasto. (Dodatkowy bug, bez wpisania województwa nie da się stworzyć raportu) |
| Gracze                 | Brak możliwości stworzenia nowego gracza; Po kliknięciu w reset filtrów filtry nie resetują się i dalej są zaaplikowane.                                                                                                                                                                                                                                                                                                                                      |
| Mecze                  | Czas gry może być większy/ujemy niż mówią zasady piłki nożnej (90min); Data meczu może być z kosmosu                                                                                                                                                                                                                                                                                                                                                          |
| Rozpocznij mecz        | Można tworzyć więcej niż dwie połowy meczu.  Nie można usunąć wizualizacji meczu.                                                                                                                                                                                                                                                                                                                                                                          |
| Raport                 | Nie da się utworzyć raportu z tej zakładki, dopiero w ‚akcjach’ w zakładce mecz; Złe formatowanie nie dostosowane do strony; Trzeba mieć wpisane województwo w zakładce gracz aby móc stworzyć raport.                                                                                                                                                                                                                                                         |

## Task 2
### Subtask 1
[link do pierwszego Subtaska](https://docs.google.com/document/d/1-LxBmxplgwzAGSX8HORxdZ5LnNG31-Q93l3-Fi9UWec/edit)
### Subtask 2
[link do drugiego Substaska](https://docs.google.com/document/d/10bNge783LsWz-32eG6C7gvWYqc84nqkCOY9B1lcOfuQ/edit)
### Subtask 3
*Po co piszemy test case'y?* Otóż po to żeby zaoszczedzić czas i pieniądze. Dzięki temu że mamy opracowany test plan zawierający poszczególne test case'y, mamy pojęcie co należy przetestować i ile wstępnie czasu zajmie nam przetestowanie danego systemu. Pozwała nam na to że jakość kodu będzie lepsza, szybciej można znaleźć błędy i niezgodności z wymaganiami klienta.

## Task 3 
### Subtask 1/2
[link do zadania pierwszego](https://docs.google.com/document/d/1jsj0UDc3ec0bWikfQd6gex8oy_MpalZYruu2kycnST4/edit)
### Subtask 3
[link do raportu z TC](https://docs.google.com/document/d/11dnmWwF_C0Fhx4me-KE3ad4AoGZyQzSsT5fX8kmROI0/edit)

## Task 4 
### Subtask 1/2
[link do zadania](https://docs.google.com/document/d/1VGrpD5gJUm7ip7QO9TK_xTItLgEuZ27xNknjRGEB7B4/edit)
### Subtask 3
1. Aplikacja OLX jest aplikacją pozwalająca sprzedawać/kupować towary/usługi pomiędzy osobami prywatnymi jak i firmami na terenie całej Polski lub lokalnie. Można w niej przeglądać różne ogłoszenia (na postawie wybranych kategorii lub wybranych dla ciebie).
2. Użytkownikiem tej aplikacji jest osoba poszukująca towaru/usługi albo osoba która chce sprzedać/oddać za darmo/zamienić jakiś swój towar.

3. Dla mnie aplikacja jest user-friendly dlatego że szybko można w niej zrozumieć na co mogę sobie pozwolić i w jaki sposób mogę jej używać (często są podpowiedzi/komunikaty które mówią o możliwościach). Aczkolwiek niektóre komunikaty są mało dopracowane, np związane z tym że podaje złe wartości w wyszukiwarce/ogłoszeniu, brakuje podświetlenia na czerwono że coś mnie ominęło w wypełnianiu pół.

4. Dla mnie w tej aplikacji jest trochę za dużo informacji/ogłoszeń które mnie przytłaczają. Wchodzę na główną stronę i zalewa mnie mnóstwo ogłoszeń, może dlatego ze OLX miało przypominać Instagram? Jestem przyzwyczajonym użytkownikiem Allegro, gdzie ogłoszenia są podzielone na kategorie, i są dużymi kwadratami, i dopiero jak w nie klikniesz to masz ogłoszenia z danej kategorii. Wydaje mi się zbędnym posiadania na stronie głównej wszystkich ogłoszeń z różnych kategorii, bo wygląda to niechlujnie i zniechęca. Wydaje mi się że przy tym modelu wyglądu aplikacji można np ew pokazywać tylko lokalne oferty na stronie głównej, skoro mają być z różnych kategorii.
5. Moim zdaniem aplikacje webową łatwiej się testuje ponieważ można zobaczyć DevTools’y dzięki czemu łatwiej dostrzec czy działa prawidłowo walidacja na frontendzie/backendzie. Jeśli chodzi o aplikacje webowe na urządzeniach mobilnych gorzej się prezentują gdyż mają ograniczony wachlarz funkcjonalności (brak korzystania z aparatu/kalendarza/latarki), Zato testując aplikację natywną musisz posiadać dużą liczbę urządzeń/albo symulatory żeby móc przetestować każde środowisko. Aplikację natywną zawsze badasz pod kątem frontendu bo nie masz dostępu do żadnych backendowych treści.    

## Task 5 
### Subtask 1/2
### Subtask 3
