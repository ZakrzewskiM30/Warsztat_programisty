# Polecenia

Systemy uniksowe, takie jak Linux, oferują bogaty zestaw poleceń pozwalających na efektywną pracę w terminalu. Poniżej przedstawiono najważniejsze komendy służące do poruszania się po systemie plików, tworzenia, edycji oraz uzyskiwania pomocy.

## Zarządzanie plikami i katalogami

- mkdir – tworzy nowy katalog.

- cd – zmienia bieżący katalog roboczy.

    Przykład: 
    - cd /home/użytkownik, 
    - cd .. (powrót o katalog wyżej), 
    - cd (powrót do katalogu domowego)

- touch – tworzy nowy, pusty plik lub aktualizuje datę modyfikacji istniejącego.

- ls – wyświetla listę plików i katalogów w bieżącym katalogu.

- tree – pokazuje strukturę katalogów w formie drzewa.
Przykład: tree ~/Dokumenty

- cp – kopiuje pliki lub katalogi.

    Przykład: 
    - cp original.txt copy.txt

- mv – przenosi lub zmienia nazwę pliku/katalogu.
    
    Przykład: 
    - mv old.txt new.txt

- rm – usuwa pliki lub katalogi.


## Edytory tekstu

- vim – zaawansowany edytor tekstu, działający w trybie tekstowym. Wymaga znajomości skrótów klawiaturowych. [Tutorial](https://openvim.com/)

    Uruchomienie: vim plik.txt

- nano – prostszy w obsłudze edytor tekstu w terminalu, intuicyjny dla początkujących.

    Uruchomienie: nano plik.txt

## Pomoc i dokumentacja

- man – wyświetla podręcznik (manual) danego polecenia.

    Przykład: man ls

- --help – pokazuje krótką pomoc dotyczącą składni i opcji komendy.

    Przykład: ls --help

- info – prezentuje bardziej rozbudowaną dokumentację polecenia (często w formie drzewa tematów).
Przykład: info ls

## Ścieżki względne i bezwzględne

- Ścieżka bezwzględna – zaczyna się od znaku ~, który oznacza katalog domowy bieżącego użytkownika, lub od /, jeśli odnosi się do katalogu głównego systemu.

    Przykład: ~/Dokumenty/plik.txt

- Ścieżka względna – odnosi się do bieżącego katalogu roboczego.

    Przykład: ../plik.txt (plik w katalogu nadrzędnym)
