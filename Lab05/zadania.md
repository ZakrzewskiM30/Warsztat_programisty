# ZADANIA – Skrypty Bash

## 0. Przygotowanie środowiska

Utwórz katalog Lab05 i przejdź do niego:

mkdir Lab05
cd Lab05


### 1. alias – szybkie skróty

Utwórz alias `ll`, który wyświetla listę plików z długim formatem i ukrytymi plikami.

Sprawdź, jak Bash interpretuje alias przy pomocy `type ll`.

Dodaj alias z punktu 1 do swojego pliku `.bashrc`.

Przeładuj powłokę lub wykonaj:

`source ~/.bashrc`

### 2. Eksperyment z .bashrc

Wyświetl zawartość pliku .bashrc w swoim katalogu domowym.

Dodaj do niego komendę, która przy każdym otwarciu terminala wypisze tekst:
```
Witaj w sesji BASH!
```

Zrestartuj terminal i sprawdź efekt.

### 3. Skrypt z podstawowymi zmiennymi

Utwórz plik `skrypt1.sh`:

Poproś użytkownika o imię (read imie).

Wyświetl komunikat:
```
Witaj, <imię>!
```

Uruchom skrypt.

### 4. Wyrażenia arytmetyczne

Rozbuduj `skrypt1.sh`:

Poproś użytkownika o dwie liczby.

Oblicz ich sumę, różnicę, iloczyn i iloraz za pomocą $(( )).

Wyświetl wyniki.

### 5. Podstawianie wyniku polecenia – $( )

Napisz skrypt czas.sh, który:

Pobiera aktualną datę do zmiennej:
```
data=$(date)
```
Wyświetla komunikat:

`Teraz jest: <data>`


Zapisuje tę samą datę do pliku `czas.log`.

### 6. Instrukcje warunkowe – proste

Napisz skrypt `sprawdz_plik.sh`, który:

Oczekuje jednego argumentu – nazwy pliku.

Jeśli plik istnieje, wypisuje:

`Plik istnieje`


Jeśli nie istnieje, wypisuje:

`Brak pliku`


Uwaga: użyj `[ -f "$1" ]`.

### 7. Instrukcje warunkowe + arytmetyka

Skrypt `porownaj.sh`:

Pobiera dwie liczby od użytkownika.

Porównuje je:

jeśli pierwsza jest większa `wypisz A > B`,

jeśli druga większa `wypisz A < B`,

jeśli równe `wypisz A = B`.

### 8. Mini-zadanie: „Co dziś robimy?”

Skrypt `menu.sh`:

Wyświetla menu:
```
1) Wyświetl datę
2) Wyświetl aktualny katalog
3) Wyświetl liczbę plików
```

Użytkownik wpisuje liczbę 1–3.

Skrypt wykonuje odpowiednią komendę (skorzystaj z `$( )`):

`date`

`pwd`

`ls | wc -l`

### 9. Zadanie podsumowujące – nieco trudniejsze

Napisz skrypt `analityk.sh`, który:

Przyjmuje jako argument nazwę pliku tekstowego.

Sprawdza:

- czy plik istnieje,

- czy nie jest pusty.

Jeśli wszystko OK, wypisuje:

- liczbę linii w pliku,

- liczbę słów,

- liczbę znaków,

używając wc.
