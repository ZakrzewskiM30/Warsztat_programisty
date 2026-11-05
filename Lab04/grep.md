# Polecenie grep i podstawy wyrażeń regularnych
## Wprowadzenie

grep (ang. global regular expression print) to polecenie używane w systemach Unix/Linux do wyszukiwania tekstu w plikach lub danych przesyłanych przez potok.
Pozwala znaleźć wiersze zawierające określony wzorzec — prosty tekst lub wyrażenie regularne (tzw. pattern).

## Składnia
```
grep [opcje] wzorzec [plik...]
```

Przykład:
```
grep "error" system.log
```

wyszukuje wszystkie linie w pliku system.log, które zawierają słowo error.

## Najczęściej używane opcje
| Opcja | Działanie
| :-- | --:
| -i | ignoruje wielkość liter
| -n | pokazuje numer linii, w której znaleziono dopasowanie
| -v | wyświetla linie niezawierające wzorca
| -r lub -R | przeszukuje katalogi rekurencyjnie
| -c | zwraca liczbę linii zawierających wzorzec
| -l | wyświetla tylko nazwy plików, w których znaleziono dopasowanie
| -w | dopasowuje tylko całe słowa
| -E | włącza rozszerzone wyrażenia regularne (ERE)
| -A n | pokazuje n linii po dopasowaniu (After)
| -B n | pokazuje n linii przed dopasowaniem (Before)
| -C n | pokazuje n linii kontekstu (Before i After)
## Przykłady
```
grep -i "linux" dokument.txt        # wyszukaj "linux" ignorując wielkość liter
grep -n "bash" *.sh                 # pokaż numery linii z dopasowaniami
grep -v "^#" skrypt.sh              # pokaż tylko linie niebędące komentarzami
grep -r "TODO" .                    # wyszukaj "TODO" we wszystkich plikach katalogu
grep -c "error" log.txt             # policz wystąpienia słowa "error"
```
## Wyrażenia regularne (RegEx) w grep

Wyrażenia regularne pozwalają tworzyć elastyczne wzorce wyszukiwania.
grep domyślnie używa prostych wyrażeń regularnych (BRE), a opcja -E umożliwia rozszerzone wyrażenia regularne (ERE) (odpowiednik egrep).

## Znaki specjalne (BRE / ERE)
| Znak | Znaczenie | Przykład | Opis
| :-- | --- | --- | --:
| `.` | dowolny pojedynczy znak | `gr.p` | dopasuje grep, grap, gr1p
| `^` | początek linii | `^#` | linie zaczynające się od #
`$` | koniec linii | `a$` | linie kończące się literą a
`*` | zero lub więcej wystąpień elementu poprzedzającego | `lo*l` | dopasuje ll, lol, lool itd.
`[]`|dowolny znak z zestawu|`[0-9]`|dowolna cyfra
`[^...]`|dowolny znak spoza zestawu|`[^A-Z]`|nie wielka litera
`\`|znak ucieczki (escape) — traktuje następny znak dosłownie|`\.`|dopasowuje dosłowną kropkę .
`\|`|alternatywa (OR) — tylko w ERE lub z -E|`kot\|pies`|dopasowuje kot lub pies
`?`|zero lub jedno wystąpienie (ERE, -E)|`kolor?` | dopasuje kolo lub kolor|
`+`|jedno lub więcej wystąpień (ERE, -E)|`[0-9]+`|co najmniej jedna cyfra
`{n}`|zakres liczby wystąpień (ERE, -E)|`[A-Z]{2}`| 2 wielkie litery
`{n,}`|zakres liczby wystąpień (ERE, -E)|`[A-Z]{2,}`| 2 lub więcej wielkich liter
`{,m}`|zakres liczby wystąpień (ERE, -E)|`[A-Z]{,4}`| co najwyżej 4 wielkie litery
`{n,m}`|zakres liczby wystąpień (ERE, -E)|`[A-Z]{2,4}`|od 2 do 4 wielkich liter
`()`|grupowanie (ERE, -E) — używane do tworzenia podwyrażeń|`(ab)+`|jedno lub więcej powtórzeń ab
## Przykłady użycia wyrażeń regularnych
```
grep "^A" dane.txt              # linie zaczynające się od litery A
grep "txt$" lista.txt           # linie kończące się na "txt"
grep "[0-9]" raport.txt         # linie zawierające cyfry
grep -E "cat|dog" zwierzeta.txt # linie zawierające "cat" lub "dog"
grep -E "[A-Z]{3}" kod.txt      # trzy wielkie litery pod rząd
grep -E "^[^#]" skrypt.sh       # linie nie zaczynające się od komentarza
```
## grep w połączeniu z innymi poleceniami

grep często stosuje się w potokach, aby filtrować wyniki innych poleceń.
```
ls -l | grep "^d"                # pokaż tylko katalogi
cat dane.txt | grep "2025"       # wyszukaj linie zawierające "2025"
sort dane.txt | grep "Anna" s    # wyszukaj imię "Anna" po sortowaniu
```
## Wyszukiwanie rekurencyjne i w wielu plikach
```
grep -r "TODO" src/              # przeszukaj katalog rekurencyjnie
grep -n "main" *.c               # w wielu plikach jednocześnie
grep -rl "password" .            # tylko nazwy plików z dopasowaniem
```
## Wersja odwrotna – grep -v

Aby wykluczyć linie pasujące do wzorca:
```
grep -v "test" dane.txt          # pokaż tylko linie bez słowa "test"
```