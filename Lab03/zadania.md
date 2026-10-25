# Zadanie 0 (Przygotowanie środowiska)

Otwórz lokalne repozytorium główne przedmiotu, z którym pracowałeś w poprzednich laboratoriach.

W jego katalogu głównym utwórz nowy podkatalog:
```
mkdir Lab03
cd Lab03
```

Każde zadanie wykonuj w osobnym podkatalogu (Zadanie1, Zadanie2, … ).
W każdym z nich umieść:

skrypt z rozwiązaniem → rozwiazanie.sh,

krótkie podsumowanie → opis.txt.

Po zakończeniu każdego zadania dodaj zmiany do repozytorium i wyślij je na repozytorium zdalne:
```
git add .
git commit -m "Lab03 – Zadanie X"
git push
```
# Zadanie 1 (Wyświetlanie i zapisywanie danych)

Utwórz skrypt rozwiazanie.sh, który:

- wyświetla komunikat:
```
Laboratorium 3 – Przekierowania i potoki,
```
- zapisuje ten sam komunikat do pliku komunikat.txt przy użyciu przekierowania >,

- następnie dopisuje kolejną linię do pliku za pomocą >>.

Wyświetl zawartość pliku w terminalu i zanotuj w opis.txt różnicę między > a >>.

# Zadanie 2 – Tworzenie i łączenie plików

Utwórz trzy pliki tekstowe:
```
echo "kot" > plik1.txt
echo "pies" > plik2.txt
echo "ptak" > plik3.txt
```

Połącz ich zawartość w jeden plik zwierzeta.txt za pomocą cat i przekierowania.

Sprawdź liczbę linii w pliku zwierzeta.txt poleceniem wc -l.

Zapisz wyniki i obserwacje w opis.txt.

# Zadanie 3 (Sortowanie i usuwanie duplikatów)

Utwórz plik lista.txt z nazwami zawierającymi powtórzenia, np.:
```
jabłko
banan
jabłko
gruszka
banan
pomarańcza
```

- Posortuj dane i zapisz wynik do posortowane.txt.

- Usuń duplikaty i zapisz wynik do unikatowe.txt.

- Wypisz liczbę unikatowych słów w terminalu przy użyciu potoku z wc -l.

# Zadanie 4 (Jedno polecenie więcej)

Powtórz zadanie 3, ale wykonaj wszystkie kroki (sortowanie, usunięcie duplikatów, policzenie liczby linii) w jednym potoku.

Utwórz nowy katalog Zadanie4 i skopiuj do niego plik lista.txt.

Za pomocą jednego potoku:

- posortuj dane,

- usuń duplikaty,

- policz ich liczbę,

- zapisz wynik do liczba.txt,

- przy tym zachowaj także pośrednie dane (np. listę unikatowych nazw) w innym pliku.

Możesz użyć polecenia `tee`, które pozwala zapisywać dane i jednocześnie przekazywać je dalej w potoku.

Jeśli nie znasz składni tee, spróbuj ją odnaleźć w manualu:
```
man tee
```
lub
```
tee --help
```

W opis.txt opisz, jakich poleceń użyłeś i do czego służyło tee.

__Celem tego zadania jest przećwiczenie korzystania z dokumentacji systemowej, nie zapamiętanie składni.__

# Zadanie 5 (Praca z kolumnami danych)

Utwórz plik uzytkownicy.txt w formacie:
```
Jan;Kowalski;jan@example.com
Anna;Nowak;anna@example.com
Piotr;Wiśniewski;piotr@example.com
```

Za pomocą cut wyświetl tylko imiona (pierwsza kolumna, separator ;).

Zapisz wynik do imiona.txt.

W terminalu policz liczbę wierszy w imiona.txt.

# Zadanie 6 (Łączenie poleceń w potoku)

Utwórz plik oceny.txt:
```
Jan;5
Anna;4
Piotr;5
Jan;3
Anna;5
```

Utwórz potok poleceń, który:

- wybiera imiona,

- sortuje,

- usuwa duplikaty,

- liczy ich liczbę,

- zapisuje wynik do wynik.txt.

W opis.txt opisz krok po kroku, co dzieje się w Twoim potoku.

# Zadanie 7 (Podsumowanie)

W katalogu Lab04 utwórz plik podsumowanie.txt, w którym:

- wyjaśnisz różnice między >, >>, <, |,

- wymienisz polecenia użyte w ćwiczeniu,

- wskażesz, które uznałeś za najbardziej przydatne.

Dodaj i wyślij plik na repozytorium zdalne.
