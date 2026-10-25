# Praca z danymi tekstowymi w systemie Linux: przekierowania, potoki i podstawowe polecenia

Systemy Unix/Linux umożliwiają wygodną pracę z danymi tekstowymi, które można wyświetlać, zapisywać, łączyć i analizować bezpośrednio z poziomu terminala.
Kluczowym elementem jest tu możliwość sterowania przepływem danych między poleceniami – dzięki przekierowaniom i potokom.

## Przekierowania i potoki – podstawy przepływu danych

Każde polecenie w systemie Linux korzysta z trzech podstawowych strumieni danych:

| Strumień | Opis | Domyślne źródło/przeznaczenie |
|:--:|:--:|:--:|
| stdin	| dane wejściowe | klawiatura |
| stdout | dane wyjściowe | ekran |
| stderr | komunikaty błędów | ekran | 

Przekierowania i potoki pozwalają zmienić to domyślne zachowanie.

### Przekierowanie wyjścia (> i >>)

\> – przekierowuje standardowe wyjście do pliku (nadpisuje jego zawartość)

\>> – przekierowuje wyjście, ale dołącza dane na końcu pliku zamiast go nadpisywać

Schemat działania:
```
polecenie > plik.txt
polecenie >> plik.txt
```

Przekierowanie wyjścia zapisuje wynik działania polecenia do pliku, zamiast wyświetlać go na ekranie.

### Przekierowanie wejścia (<)

Pozwala wczytać dane z pliku zamiast z klawiatury.

Schemat działania:
```
polecenie < plik.txt
```

Dzięki temu polecenie może przetwarzać dane zapisane wcześniej w pliku.

### Potok (|)

Potok umożliwia połączenie kilku poleceń w jeden ciąg przetwarzania.
Wynik jednego polecenia staje się automatycznie wejściem kolejnego.

Schemat działania:
```
polecenie1 | polecenie2 | polecenie3
```

Potoki pozwalają łączyć proste programy w potężne łańcuchy operacji bez tworzenia plików pośrednich.

## Podstawowe polecenia pracy z tekstem
### echo

Wyświetla przekazany tekst lub zawartość zmiennej w terminalu.

Składnia:
```
echo [tekst]
```

Przykłady:
```
echo "Witaj w świecie Linuxa!"
echo "Aktualny katalog: $PWD"
```

#### Użyteczne opcje:

-n – nie dodaje znaku nowej linii

-e – interpretuje znaki specjalne, np. \n

### head

Wyświetla początkowe linie pliku.
Domyślnie: 10 pierwszych linii.

Przykłady:
```bash
head plik.txt
head -n 5 plik.txt
```
### tail

Wyświetla końcowe linie pliku.
Domyślnie: 10 ostatnich linii.

Przykłady:
```bash
tail plik.txt
tail -n 20 plik.txt
```

Przydatne do podglądania logów:
```bash
tail -f log.txt     # śledzi plik na żywo
```
### tr

Zamienia, usuwa lub filtruje znaki. Najczęściej używane do konwersji wielkości liter.

Przykłady:
```bash
echo "Ala Ma Kota" | tr 'A-Z' 'a-z'    # zamiana na małe litery
echo "a,b,c" | tr ',' ' '              # zamiana przecinków na spacje
echo "123abc" | tr -d '0-9'            # usunięcie cyfr
```
### cat

Wyświetla zawartość pliku lub łączy kilka plików w jeden.

Składnia:
```
cat [plik1] [plik2] ...
```

Przykłady:
```
cat tekst.txt
cat a.txt b.txt > polaczony.txt
```

Użycie z przekierowaniem:
```
cat > notatka.txt   # tworzy nowy plik i zapisuje dane z klawiatury
```
### sort

Sortuje linie tekstu w porządku alfabetycznym lub numerycznym.

Składnia:
```
sort [opcje] [plik]
```

Przykłady:
```
sort lista.txt
sort -r lista.txt
sort -n liczby.txt
```
### uniq

Usuwa duplikaty w sąsiadujących liniach.
Aby działało poprawnie, dane muszą być wcześniej posortowane.

Składnia:
```
uniq [opcje] [plik]
```

Przykłady:
```
sort dane.txt | uniq
sort dane.txt | uniq -c   # liczba wystąpień każdej linii
```
### cut

Wybiera określone kolumny lub fragmenty z każdej linii pliku.

Składnia:
```
cut [opcje] [plik]
```

Najczęściej używane opcje:

-f N – wybiera kolumnę numer N (pole)

-d ZNAK – określa znak rozdzielający kolumny (domyślnie TAB)

Przykłady:
```
cut -f 1 dane.tsv
cut -d ":" -f 1 /etc/passwd
```
### wc

Zlicza linie, słowa i znaki w pliku.

Składnia:
```
wc [opcje] [plik]
```

Przykłady:
```
wc tekst.txt
wc -l tekst.txt     # liczba linii
wc -w tekst.txt     # liczba słów
wc -c tekst.txt     # liczba bajtów
```
