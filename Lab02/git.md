# Podstawy systemu kontroli wersji Git

Git to rozproszony system kontroli wersji stworzony przez [Linusa Torvaldsa](https://pl.wikipedia.org/wiki/Linus_Torvalds).
Służy do śledzenia zmian w plikach (najczęściej w kodzie źródłowym) oraz do współpracy wielu osób nad jednym projektem.

Dzięki Gitowi można:

- zapisywać kolejne wersje projektu,

- cofać się do wcześniejszych wersji,

- synchronizować zmiany między wieloma komputerami lub programistami poprzez zdalne repozytorium, np. GitLab.

## git clone

Służy do skopiowania (sklonowania) zdalnego repozytorium na komputer lokalny.
Polecenie tworzy lokalny katalog z pełną historią projektu.

Przykład:
```
git clone <adres-repozytorium>
```

Tworzy folder projekt z zawartością repozytorium GitLab.

__Uwaga__: To polecenie wykonuje się tylko raz – przy pierwszym pobraniu projektu.
Później korzysta się już z git pull, aby aktualizować repozytorium.

## git pull

Pobiera najnowsze zmiany ze zdalnego repozytorium i łączy je z lokalną kopią.

Przykład:
```
git pull
```

Aktualizuje lokalne pliki, aby były zgodne z najnowszą wersją na serwerze GitLab.

## git status

Wyświetla aktualny stan lokalnego repozytorium.
Pokazuje:

- które pliki zostały zmienione,

- które czekają na zatwierdzenie (staged),

- czy repozytorium jest zsynchronizowane ze zdalnym serwerem.

Przykład:
```
git status
```

Pomaga zorientować się, co zostało zmodyfikowane i co wymaga dodania (git add) lub zatwierdzenia (git commit).

## git add

Dodaje pliki do tzw. „staging area” (przechowalnia) – czyli przygotowuje je do zatwierdzenia (commitowania).
Nie zapisuje zmian jeszcze w historii – tylko oznacza, które pliki mają zostać uwzględnione.

Przykłady:
```
git add plik.txt        # dodanie konkretnego pliku
git add .               # dodanie wszystkich zmodyfikowanych plików
```
## git commit

Zatwierdza (utrwala) zmiany przygotowane przez git add w lokalnym repozytorium.
Każdy commit to zapis stanu projektu wraz z komentarzem opisującym zmiany.

Przykład:
```
git commit -m "Dodano nowy plik z instrukcją"
```

Tworzy nowy punkt w historii projektu.

## git push

Wysyła lokalne commity do zdalnego repozytorium (np. GitLab).
Dzięki temu inni użytkownicy mogą zobaczyć wprowadzone zmiany.

Przykład:
```
git push
```

Wysyła nowe commity na serwer.

## Podstawowy cykl pracy z Gitem

(Tylko raz, na początku) – sklonuj projekt:
```
git clone <adres-repozytorium>
```

Potem przejdź do katalogu projektu:
```bash
cd projekt
```

(Każdy kolejny cykl pracy) – Sprawdź stan repozytorium:
```
git status
```

Upewnij się, że nie masz niezatwierdzonych zmian. Jeśli są – zatwierdź je (git add, git commit) lub zapisz tymczasowo (git stash).

Pobierz najnowsze zmiany z repozytorium:
```
git pull
```

Wprowadź własne zmiany w plikach lokalnych

Dodaj zmodyfikowane pliki do śledzenia:
```
git add .
```

Zatwierdź zmiany lokalnie:
```
git commit -m "Opis wprowadzonych zmian"
```

Wyślij zmiany do zdalnego repozytorium:
```
git push
```
