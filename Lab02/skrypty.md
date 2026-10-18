# Uprawnienia i podstawy skryptów Bash w systemie Linux

W systemie Linux bezpieczeństwo i kontrola dostępu do plików opierają się na uprawnieniach. Jednym z najczęściej używanych poleceń do ich zmiany jest chmod. W połączeniu z prostymi skryptami Bash pozwala ono automatyzować codzienne zadania.

## Polecenie chmod

Polecenie chmod (ang. change mode) służy do zmiany uprawnień plików i katalogów.
Uprawnienia określają, kto może czytać (r), zapisywać (w) i wykonywać (x) dany plik.

### Podstawowe tryby nadawania uprawnień

#### Tryb symboliczny – wykorzystuje litery:

u – użytkownik (owner),

g – grupa,

o – inni użytkownicy,

a – wszyscy.

Przykłady:

```bash
chmod u+x skrypt.sh
```
dodaje prawo wykonywania dla właściciela.

```bash
chmod go-rw plik.txt
```

usuwa prawo odczytu i zapisu dla grupy i innych.

#### Tryb numeryczny (ósemkowy) – każda cyfra określa zestaw uprawnień:

4 = odczyt (r)

2 = zapis (w)

1 = wykonanie (x)

Wartości sumują się, np.:

7 = rwx

6 = rw-

5 = r-x

Przykład:
```bash
    chmod 755 skrypt.sh
```
powoduje, że właściciel może czytać, zapisywać i wykonywać; grupa i inni – tylko czytać i wykonywać.

## Tworzenie prostego skryptu Bash

Skrypt Bash to plik tekstowy zawierający zestaw poleceń, które terminal wykonuje kolejno.

Utwórz plik skryptu:
```bash
touch skrypt.sh
```

Otwórz plik w edytorze:
```bash
nano skrypt.sh
```

Dodaj tzw. shebang (nagłówek interpretera) i kilka prostych poleceń:
```bash
#!/bin/bash
mkdir ~/Test
cd ~/Test
touch plik1.txt
ls -l
```

Zmień uprawnienia, by skrypt był wykonywalny:
```bash
chmod +x skrypt.sh
```
System Linux wymaga jawnego nadania prawa wykonywania (x), aby zapobiec przypadkowemu uruchamianiu plików.
Bez tego skrypt będzie traktowany jak zwykły tekst, a nie program.

Nagłówek interpretera (#!/bin/bash) nie zawsze jest konieczny.

Jeśli uruchamiasz skrypt jawnie przez interpreter, np.
```bash
bash skrypt.sh
```
nagłówek interpretera nie jest potrzebny, bo system już wie, że ma użyć powłoki Bash.

Jeśli uruchamiasz skrypt bezpośrednio poleceniem
```bash
./skrypt.sh
```

Nagłówek interpretera jest wymagany, w środowiskach z wieloma powłokami ponieważ system musi wiedzieć, który program ma zinterpretować plik.

Warto go również dodawać w skryptach używanych w automatyzacji (cron, systemd) oraz w projektach przenośnych, by zapewnić spójne działanie na różnych systemach.
