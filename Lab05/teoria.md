## Aliasy

`alias`

Tworzy skrócone polecenia — szczególnie wygodne w codziennej pracy.

Przykłady:
```bash
alias ll='ls -l'
alias gs='git status'
```

Wyświetlenie wszystkich aliasów:
```bash
alias
```

Usunięcie aliasu:
```bash
unalias ll
```

Uwaga: aliasy są tylko tymczasowe — znikają po wylogowaniu, chyba że zapiszesz je w `.bashrc`.

## Plik ~/.bashrc — do czego służy?

Plik `.bashrc` (uwaga na kropkę!) to skrypt uruchamiany za każdym razem, gdy otwierasz nowe okno terminala Bash.

Można w nim umieścić:

aliasy,

zmienne środowiskowe,

ustawienia powłoki,

dodawanie katalogów do `PATH`,

funkcje powłoki.

Przykład fragmentu `.bashrc`:
```bash
alias ll='ls -l --color=auto'
export PATH="$PATH:$HOME/bin"
```
Pliki ukryte

Pliki zaczynające się od kropki (.) są ukryte w systemie Linux/Unix.
Nie pojawiają się przy zwykłym `ls`.

Wyświetlanie plików ukrytych:
```bash
ls -a
```

Przykłady typowych ukrytych plików:
```
.bashrc
.gitconfig
.ssh/
.cache/
```
## Rozszerzenie wiadomości o skryptach Bash
### Zmienne

W Bash zmienne tworzymy bez spacji:
```bash
x=10
imie="Ala"
```

Odczyt zmiennej:
```bash
echo $x
echo "Cześć, $imie!"
```
### Wyrażenia arytmetyczne — $(( ))

Bash umożliwia wykonywanie obliczeń za pomocą:
```
$(( wyrażenie ))
```

Przykłady:
```bash
a=5
b=3
echo $((a + b))
echo $((a * b))
```

Można również modyfikować zmienne:
```bash
i=0
i=$((i + 1))
```
### Podstawienie wyniku polecenia — $( )

Składnia:
```
$( polecenie )
```

pozwala wstawić wynik działania polecenia w miejsce tej konstrukcji.
Bash najpierw wykona polecenie, a następnie podstawi jego wynik jako tekst.

To najpopularniejszy sposób wykonywania poleceń wewnątrz innych poleceń lub przypisań.

Przykłady:
Przypisanie wyniku polecenia do zmiennej:
```bash
data=$(date)
echo "Aktualna data to: $data"
```
Liczenie plików w katalogu:
```bash
ile=$(ls | wc -l)
echo "Liczba plików: $ile"
```
Użycie w środku innego polecenia:
```bash
echo "Użytkownik: $(whoami)"
```
Porównanie `$(( ))` i `$( )`
Konstrukcja	Do czego służy

Przykład

`$(( ))`	obliczenia arytmetyczne	`echo $((2 + 3))`

`$( )`	podstawienie wyniku działania polecenia	`echo $(ls)`

To __dwa różne mechanizmy__ — pierwszy wykonuje matematykę, drugi uruchamia polecenie.

## Instrukcje warunkowe if

Podstawowy schemat:
```bash
if [ warunek ]; then
    polecenia
elif [ inny_warunek ]; then
    polecenia
else
    polecenia
fi
```
Przykłady:
Sprawdzanie istnienia pliku:
```bash
if [ -f plik.txt ]; then
    echo "Plik istnieje"
else
    echo "Brak pliku"
fi
```
Porównywanie liczb:
```bash
if [ $a -lt $b ]; then
    echo "a < b"
fi
```
Porównywanie tekstów:
```bash
if [ "$imie" = "Ala" ]; then
    echo "Cześć!"
fi
```

## Interakcja z użytkownikiem

Skrypty powłoki Bash bardzo często potrzebują danych wejściowych — zarówno tych przekazanych jako argumenty w wierszu poleceń, jak i wpisanych przez użytkownika podczas działania skryptu. Poniżej przedstawiono najważniejsze mechanizmy.

### 1. Argumenty przekazywane do skryptu

Jeśli uruchomimy skrypt w taki sposób:

`./skrypt.sh arg1 arg2 arg3`


to:
```
$0 – nazwa skryptu (np. ./skrypt.sh)

$1 – pierwszy argument (arg1)

$2 – drugi argument (arg2)

$3 – trzeci argument (arg3)

$# – liczba argumentów
```
Przykład

Skrypt args.sh:
```
#!/bin/bash

echo "Nazwa skryptu: $0"
echo "Pierwszy argument: $1"
echo "Liczba argumentów: $#"
echo "Wszystkie argumenty: $@"
```
Uruchomienie:
```
./args.sh Ala Kot 123
```
### 2. Pobieranie danych od użytkownika (read)

Polecenie read pozwala pobrać dane wpisane przez użytkownika podczas działania skryptu.

Podstawowe użycie
`read zmienna`


Skrypt zatrzyma się i będzie czekał, aż użytkownik wpisze tekst i naciśnie Enter.
Wpisana wartość trafi do zmiennej zmienna.

Przykład
```
#!/bin/bash

echo -n "Podaj napis: "
read napis

echo "Podałeś, $napis"
```
Kilka wartości jednocześnie

Jeśli użytkownik wpisze kilka słów rozdzielonych spacjami:
```
read a b c
```

to pierwsze słowo trafi do a, drugie do b, a cała reszta do c.

Opcje read przydatne na start
```
-p "tekst"	wypisuje komunikat przed pobraniem danych
-r	uniemożliwia interpretowanie backslashy jako znaków specjalnych
-s	ukrywa wpisywany tekst (przydatne np. do haseł)
```
Przykład z opcjami
```
read -p "Podaj login: " login
read -s -p "Podaj hasło: " haslo
echo
echo "Podano login: $login"
```
### 3. Łączenie argumentów i read

Często skrypt przyjmuje część danych jako argumenty, a część pobiera od użytkownika.

Przykład:
```
#!/bin/bash

plik=$1

if [ -z "$plik" ]; then
    read -p "Nie podano pliku. Podaj nazwę pliku: " plik
fi

echo "Wybrany plik to: $plik"

```
Skrypt zadziała zarówno tak:

`./skrypt.sh dane.txt`


jak i tak:

.`/skrypt.sh     # brak argumentu` skrypt użyje `read`
