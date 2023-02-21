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
W zadaniu używałam środowiska DataGrip, w którym wykorzystywałam takie operatory/zapytania jak where, between, in, and/or, order by, create, name like.
### Subtask 3
1. Wyświetl tabelę actors w kolejności alfabetycznej sortując po kolumnie surname.

```sql
select * from actors
order by surname
```
![image](https://user-images.githubusercontent.com/63921367/218325605-57e92a4b-4ad8-4a1e-b53b-1cb27a8f9f94.png)

2. Wyświetl film, który powstał w 2019 roku.

```sql
select * from movies
where year_of_production = 2019
```
![image](https://user-images.githubusercontent.com/63921367/218325817-3fce181e-72c8-4da3-8879-9e6b8540ced7.png)

3. Wyświetl wszystkie filmy, które powstały między 1900, a 1999 rokiem.

```sql
select * from movies
where year_of_production between 1900 and 1999
```
![image](https://user-images.githubusercontent.com/63921367/218326147-8694db1e-dd32-4e5b-b70d-209ca7a0682d.png)

4. Wyświetl JEDYNIE tytuł i cenę filmów, które kosztują poniżej 7$

```sql
select title, price from movies
where price < 7
```
![image](https://user-images.githubusercontent.com/63921367/218326362-a2090af2-3a7b-4c6f-b45e-3af46b89456e.png)

5. Użyj operatora logicznego AND, aby wyświetlić aktorów o actor_id pomiędzy 4-7 (4 i 7 powinny się wyświetlać). NIE UŻYWAJ operatora BETWEEN.

```sql
select * from actors
where actor_id >= 4 and actor_id <= 7
```
![image](https://user-images.githubusercontent.com/63921367/218326967-b8157a27-2c5e-4962-97a5-9eeccd21b50f.png)

6. Wyświetl klientów o id 2,4,6 wykorzystaj do tego warunek logiczny.
```sql
select * from customers
where customer_id = 2 or customer_id = 4 or customer_id = 6
order by customer_id
```
![image](https://user-images.githubusercontent.com/63921367/218329681-5829db95-d696-415d-af03-dcb01a386fa8.png)

7. Wyświetl klientów o id 1,3,5 wykorzystaj do tego operator IN.

```sql
select * from customers
where customer_id in (1,3,5)
```
![image](https://user-images.githubusercontent.com/63921367/218330558-cf8fddb3-e6de-4085-9c57-d64b32642424.png)

8. Wyświetl dane wszystkich osób z tabeli ‘actors’, których imię zaczyna się od ciągu “An”.

```sql
select * from actors
where name like 'An%'
```
![image](https://user-images.githubusercontent.com/63921367/218330835-67fc7854-2fc0-440c-ab03-2be539bad112.png)

9. Wyświetl dane klienta, który nie ma podanego adresu email.
```sql
select * from customers
where email is null
```
![image](https://user-images.githubusercontent.com/63921367/218331152-7a8c08c7-7318-45ad-a172-99f1d5d3a216.png)

10. Wyświetl wszystkie filmy, których cena wynosi powyżej 9$ oraz ich ID mieści się pomiędzy 2 i 8 movie_id.
```sql
select * from movies
where price > 9 and movie_id between 2 and 8
```
![image](https://user-images.githubusercontent.com/63921367/218331560-1b9738f6-13d6-4aa9-b077-d10c22e13f73.png)

# Task 6
## Subtask 1
11. Popełniłam błąd wpisując nazwisko Ani Miler – wpisałam Muler. Znajdź i zastosuj funkcję, która poprawi mój karkołomny błąd 🙈

```sql
update customers
set surname = 'Miler'
where customer_id = 3
```
![image](https://user-images.githubusercontent.com/63921367/220200505-c21ce45d-2a2f-4679-80e3-5346f624172b.png)

12. Pobrałam za dużo pieniędzy od klienta, który kupił w ostatnim czasie film o id 4. Korzystając z funkcji join sprawdź, jak ma na imię klient i jakiego ma maila. W celu napisania mu wiadomości o pomyłce fantastycznej szefowej.

```sql
select name, surname, email from customers
join sale on customers.customer_id = sale.customer_id
where sale.movie_id= 4
```
![image](https://user-images.githubusercontent.com/63921367/220200882-07c55450-ff64-4a26-85b7-fa880a1a171d.png)


13. Na pewno zauważył_ś, że sprzedawca zapomniał wpisać emaila klientce Patrycji. Uzupełnij ten brak wpisując: pati@mail.com

```sql
update customers
set email = 'pati@mail.com'
where customer_id = 4
```
![image](https://user-images.githubusercontent.com/63921367/220201070-9ef099ae-9e2c-40e1-8170-886fee48d3b4.png)

14. Dla każdego zakupu wyświetl, imię i nazwisko klienta, który dokonał wypożyczenia oraz tytuł wypożyczonego filmu. (wykorzystaj do tego funkcję inner join, zastanów się wcześniej, które tabele Ci się przydadzą do wykonania ćwiczenia).

```sql
select c.name, c.surname, m.title from customers as c
join sale as s
on c.customer_id=s.customer_id
join movies as m on m.movie_id = s.movie_id
```
![image](https://user-images.githubusercontent.com/63921367/220201128-b2b437d5-2048-4def-9127-f4743b7fe552.png)


15. W celu anonimizacji danych, chcesz stworzyć pseudonimy swoich klientów. - Dodaj kolumnę o nazwie ‘pseudonym’ do tabeli customer,- Wypełnij kolumnę w taki sposób, aby pseudonim stworzył się z dwóch pierwszych liter imienia i ostatniej litery nazwiska. Np. Natalie Pilling → Nag

```sql
alter table customers
add pseudonim varchar(20)
update customers
set pseudonim = concat(left(customers.name, 2), right(customers.surname, 1))
```
![image](https://user-images.githubusercontent.com/63921367/220201288-671f72d8-2135-4d0d-8dde-c768c6b0dbf1.png)


16. Wyświetl tytuły filmów, które zostały zakupione, wyświetl tabelę w taki sposób, aby tytuły się nie powtarzały.

```sql
select title, count(*) as ilosc from movies m
join sale s on s.movie_id = m.movie_id
group by title
```
![image](https://user-images.githubusercontent.com/63921367/220201467-df35939d-74d6-4d81-83ad-cc41086968e3.png)


17. Wyświetl wspólną listę imion wszystkich aktorów i klientów, a wynik uporządkuj alfabetycznie. (Wykorzystaj do tego funkcji UNION)

```sql
select name from customers
union
select name from actors
order by name asc
```
![image](https://user-images.githubusercontent.com/63921367/220201535-d3f999b8-4baf-4cb9-a2fc-7f65a6cae136.png)


18. Polskę opanowała inflacja i nasz sklepik z filmami również dotknął ten problem. Podnieś cenę wszystkich filmów wyprodukowanych po 2000 roku o 2,5 $ (Pamiętaj, że dolar to domyślna jednostka- nie używaj jej nigdzie).

```sql
alter table movies
update movies
set price = price + 2.5
where year_of_production > 2000
```
![image](https://user-images.githubusercontent.com/63921367/220201602-e2a280c4-927c-4efc-8120-f37f4342b2e4.png)


19. Wyświetl imię i nazwisko aktora o id 4 i tytuł filmu, w którym zagrał

```sql
select a.name, a.surname, m.title from actors a
join "cast" c on c.actor_id = a.actor_id
join movies m on m.movie_id = c.movie_id
where a.actor_id = 4
```
![image](https://user-images.githubusercontent.com/63921367/220201666-8be7a29d-80a5-4a2c-a531-9ac3a2f399cb.png)


20. A gdzie nasza HONIA!? Dodaj do tabeli customers nową krotkę, gdzie customer_id = 7, name = Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa

```sql
insert 
into customers(customer_id, name, surname, email, pseudonim)
values (7,'Honia','Stuczka-Kucharska', 'honia@mail.com', 'Hoa')
```

![image](https://user-images.githubusercontent.com/63921367/220201741-c59aa84b-705c-45c8-afd1-10b10f081d81.png)

## Subtask 2
tu wpisac wynik testu
## Subtask 3
[link do mojego portfolio](https://github.com/AnastazjaKoziara/portfolioDareIT/blob/main/Portfolio.md)
