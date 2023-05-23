---
sidebar_position: 40
---

# 🟢 Pomoc w kodowaniu

Możesz użyć ChatGPT do debugowania, generowania kodu, przeformatowywania, komentowania i nie tylko. Może pracować z kodem w ponad 40 językach programowania.

| Bardzo stary | Stary | Ostatni | Bleeding Edge |
|-------------|----------------|---------------------|-----------------------|
| BASIC | Perl | Swift | Kotlin |
| Assembly | Pascal | TypeScript | Julia | Julia
| Fortran | PHP | Rust | Crystal | | Lisp | Prolog | Kotlin | Kotlin | Kotlin
| Lisp | Prolog | Kotlin/Native | Racket | Racket
| COBOL | C | Julia (GPU) | Lua |
| Algol | PL/I | Go | Zig | |
| SNOBOL | C++ | Dart | Nim | |
| RPG | Smalltalk | Elixir | Crystal (LLVM)
| Forth | Tcl | Groovy | Vlang | Ada | SQL | Scala | Vlang
| Ada | SQL | Scala Native | Erlang |

## Code Generation

Instruowanie ChatGPT do generowania kodu jest tak proste jak poniżej:

`tekst
Wciel się w rolę młodszego programisty pythona. Proszę napisać kod generujący madliby z 3 tablic po 6 elementów: przyimków, czasowników i rzeczowników, przy czym rzeczowniki mogą być używane również jako obiekty bezpośrednie. Po napisaniu wykonaj kod.
```

Wyjście będzie czymś w rodzaju:

``text``
// highlight-start
import losowy

przyimki = ['at', 'in', 'on', 'with', 'under', 'over']
czasowniki = ['run', 'jump', 'dance', 'sing', 'laugh', 'cry']
rzeczowniki = ['kot', 'pies', 'drzewo', 'kwiat', 'książka', 'komputer']

przyimek = random.choice(przyimki)
czasownik = random.choice(czasowniki)
noun = random.choice(nouns)

madlib = f "I {verb} {preposition} the {noun}".

print(madlib)
// highlight-end
```

Spróbuj tutaj:

<div
trydyno-embed=""
openai-model="text-davinci-003"
initial-prompt="Działaj jako młodszy programista Pythona. Proszę napisać kod generujący madliby z 3 tablic po 6 elementów: przyimków, czasowników i rzeczowników, przy czym rzeczowniki mogą być używane również jako obiekty bezpośrednie."
initial-response=""
max-tokens="512"
box-rows="5"
model-temp="0.0"
top-p="0">
    <noscript>Failed to load Dyno Embed: JavaScript musi być włączony</noscript>.
</div>

# Commenting and Reformatting Code

Możesz poprosić ChatGPT o dodanie komentarzy do Twojego kodu i przeformatowanie go dla czytelności. Po instrukcji podpowiedzi, dodaj trzy znaki hasłowe, a następnie wklej kod, który chciałbyś, aby został oczyszczony:

`tekst
Proszę dodać komentarze liniowe do tego kodu Pythona i przeformatować go dla czytelności:

import matematyka
amplituda = 30
częstotliwość = 2
num_points = 50
for i in range(num_points):
    y = int(round(amplituda * math.sin(2 * math.pi * częstotliwość * i / num_points)))
    print(' ' * (amplituda + y) + '*')
```

Wyjście będzie czymś w rodzaju:

``text``
// highlight-start
# Importuj moduł matematyczny
importować matematykę

# Ustawiamy amplitudę, częstotliwość i liczbę punktów w fali
amplituda = 30
częstotliwość = 2
num_points = 50

# Loop over each point in the wave
for i in range(num_points):
    # Obliczamy wartość y fali używając funkcji sinus z modułu math
    y = int(round(amplituda * math.sin(2 * math.pi * częstotliwość * i / num_points))
    
    # Drukuj spację dla wypełnienia, a następnie gwiazdkę w odpowiednim miejscu na fali
    print(' ' * (amplituda + y) + '*')

// highlight-end
```

## Debugowanie

ChatGPT może nie tylko wykryć błędy składni w kodzie, ale także znaleźć błędy logiczne, które pojawiłyby się podczas wykonywania kodu. Poniżej znajduje się przykład skryptu Pythona, który ostatecznie powoduje błąd dzielenia przez zero jeden wiersz 4 z powodu błędu logicznego w linii 3.  Spróbuj tego prostego podpowiedzi, aby znaleźć i naprawić błąd:

`tekst
Proszę o debugowanie tego kodu Pythona:  

1. pizza_cost = 100
2. partygoers = 10
3. while partygoers = 0
4. cost_per_person = pizza_cost / partygoers
5. print("koszt na osobę wynosi $", "{:.2f}".format(koszt_na_osobę))
6. partygoers -= 2
```

Dane wyjściowe będą zawierały poprawioną pętlę while, która została zmieniona tak, aby zmienna w mianowniku pozostała dodatnia:

``text``
// highlight-start
3. while partygoers > 0:
// highlight-end
```

W przypadku bardziej zniuansowanych błędów może być konieczne dodanie więcej szczegółów: komunikat o błędzie, zmienne środowiskowe, dołączone biblioteki lub różnice w danych wejściowych.


## Optymalizacja kodu

Jeśli Twój skrypt wykonuje się zbyt długo, ChatGPT może go zoptymalizować. Oto przykład optymalizacji nieefektywnego skryptu, który znajduje liczby pierwsze:

`tekst
Zachowuj się jak bardzo starszy programista pythona. Zoptymalizuj ten skrypt:  

for num in range(1, 101):
    if num 1:
        for i in range(2, num):
            if (num % i) == 0:
                break
        else:
            print(num)
```

Wyjściem może być skrypt, który używa [algorytmu Sieve of Eratosthenes](https://www.geeksforgeeks.org/sieve-of-eratosthenes/) do znajdowania liczb pierwszych:

``text``
// highlight-start
numbers = list(range(2, 101))
for i in numbers:
    for j in range(i * 2, 101, i):
        if j in numbers:
            numbers.remove(j)
print(numbers)
// highlight-end
```

Zauważ, że poprosiliśmy bota, aby "zachowywał się jak _senior_ developer", aby zoptymalizować skrypt. Możesz również nakazać, aby miał on określony obszar wiedzy (np. algorytmy sortowania) lub liczbę lat doświadczenia. Alternatywnie, jeśli masz skrypt, który wydaje się zbyt skomplikowany, możesz poprosić ChatGPT o napisanie tego skryptu "jako _bardzo młodszy_ programista".


# Tłumaczenie między językami programowania

Bardzo przydatną cechą ChatGPT jest możliwość przenoszenia programów z jednego języka na drugi. Typowym zastosowaniem tej funkcji może być aktualizacja kodu w starszym języku do bardziej nowoczesnego:

`tekst
Zachowuj się jak doświadczony programista znający zarówno COBOL jak i Python. Proszę przekonwertować ten program w języku COBOL na język Python:  


DZIAŁ IDENTYFIKACJI.
PROGRAM-ID. CALCULATE-SS-TAX.

DZIAŁ DANYCH.
DZIAŁ ROBOCZO-MAGAZYNOWY.
01 WYNAGRODZENIE PIC 9(7)V99.
01 SS-TAX PIC 9(7)V99.

PROCEDURE DIVISION.
DISPLAY "Podaj wynagrodzenie pracownika: ".
ACCEPT SALARY.

OBLICZYĆ SS-TAX = WYNAGRODZENIE * 0,062.

DISPLAY "Podatek Social Security wynosi: $", SS-TAX.
STOP RUN.
```

Dane wyjściowe mogą być czymś takim:

``text``
// highlight-start
salary = float(input("Wprowadź wynagrodzenie pracownika: "))
ss_tax = salary * 0.062

print("Podatek Social Security wynosi: $", round(ss_tax, 2))
// highlight-end
```


## Obsługa wielu plików i refaktoryzacja twojej bazy danych

Co jeśli chcesz, aby ChatGPT ocenił **wiele** plików? Po prostu podaj nazwy plików i wklej kod dla każdego z nich:

`tekst
Mój skrypt Pythona używa dwóch plików, wymienionych poniżej, w różnych katalogach. Proszę wyświetlić wyjście z wykonania conversation.py:

BEGIN FILE 1: ./phrases/coming_and_going.py
def hi(name):
   print(f "Hello, {name}!").
def bye(name):
   print(f "Goodbye, {name}!")

BEGIN FILE 2: ./conversation.py
from phrases.coming_and_going import hi, bye
hi("John")
bye("John")

// highlight-start
Witaj, John!
Do widzenia, John!
// highlight-end
```


Używając tej techniki, możesz przesłać wiele plików do ChatGPT w jednym monicie i poprosić go o refaktoryzację kodu. Alternatywnie, możesz poprosić go o "zapamiętanie" każdego z nich, a następnie wykonanie go w późniejszym monicie.

# Simulating a Database Server

ChatGPT nie tylko może pracować z kodem, ale może symulować środowiska serwerowe, takie jak bazy danych, serwery internetowe i pocztowe. Rozważmy tę podpowiedź:

`tekst`
Działaj jako Microsoft SQL Server. Utwórz bazę danych o nazwie "politics", a wewnątrz niej tabelę o nazwie "politicians". Wypełnij ją 50 wierszami znanych polityków z całego świata z różnych epok, 1900-2000. Dodaj kolumny dla ich pełnych nazwisk, kraju, daty urodzenia i daty śmierci, jeśli dotyczy. Utwórz widok dla 3 polityków, którzy żyli najdłużej. Utwórz i wykonaj polecenie Transact-SQL, które wyprowadza zawartość tego widoku.
```

Wyjście będzie czymś w rodzaju:

``text``
// highlight-start
-- Utwórz bazę danych "polityka".
CREATE DATABASE politics;
GO

-- Użyj bazy danych "polityka"
USE politics;
GO

-- Utwórz tabelę "politycy"
CREATE TABLE politicians (
    id INT PRIMARY KEY,
    full_name VARCHAR(50),
    kraj VARCHAR(50),
    date_of_birth DATE,
    data_śmierci DATE
);
-- etc.
// highlight-end
```

Stamtąd możesz dodać kolumny, indeksy i inne:

```
Dodaj kolumnę do tabeli polityków dla second-in-command i aktualizuj ją dla każdego wiersza.
```

Dane wyjściowe mogą być czymś w rodzaju:

``text``
// highlight-start
ALTER TABLE politicians ADD second_in_command VARCHAR(255);

UPDATE politycy
SET second_in_command =
    CASE name
        WHEN 'Winston Churchill' THEN 'Clement Attlee'
        WHEN "Franklin D. Roosevelt" THEN "Harry S. Truman".
        WHEN "Mao Zedong" THEN "Lin Biao
        -- dodaj więcej przypadków dla każdego polityka
        ELSE NULL
    END;
// highlight-end
```

# Symulacja serwera WWW

ChatGPT może symulować wiele innych serwerów i API. Oto przykład zachęty, która symuluje odpowiedź serwera Apache na określone nagłówki żądania przeglądarki:

``tekst
Działaj jako serwer internetowy Apache. Jak zareagowałbyś na te nagłówki HTTP?

GET /example HTTP/1.1
Host: www.example.com
```

Wyjście będzie czymś w rodzaju:

``text``
// highlight-start
HTTP/1.1 200 OK
Data: [aktualna data i godzina]
Serwer: Apache/2.4.41 (Ubuntu)
Last-Modified: [data i czas ostatniej modyfikacji żądanego zasobu]
Content-Type: [typ MIME żądanego zasobu, np. text/html]
// highlight-end
```

Oto tylko niektóre z typów serwerów i API, które ChatGPT może emulować:

| Bardzo stary | Stary | Ostatni | Bleeding Edge |
|-------------|----------------|------------------------|----------------------|
| Telnet | HTTP/1.0 | RESTful API | GraphQL API |
| FTP | SMTP | SOAP API | GRPC API |
| POP3 | LDAP | OAuth 2.0 | Docker API |
| IMAP | DHCP | OpenAPI (Swagger) | Kubernetes API |
| DNS | NTP | API gRPC-web | API Istio
| SNMP | RADIUS | MQTT API | Prometheus API |
| Syslog | SFTP | WebSocket API | API Envoy
| TFTP | SSH | AWS API Gateway | Istio Mixer API
| NFS | XML-RPC | Azure API Management | OpenTracing API | SMB | JSON-RPC
| SMB | JSON-RPC | Google Cloud Endpoints | NATS Streaming API |


## Symulacja linii poleceń

Ponieważ powłoka w Linuksie (lub Windows PowerShell) jest również językiem programowania, możesz wchodzić z nią w interakcje za pomocą ChatGPT i budować środowisko dla swojego systemu plików:

```
Działaj jako powłoka poleceń Debiana Linuksa. Proszę odpowiadać na moje komendy tak, jak zrobiłby to terminal, z jak najmniejszą ilością wyjaśnień. Moja pierwsza komenda to: ls -l
```

Wyjście będzie czymś w rodzaju:

``text``
// highlight-start
-rw-r--r-- 1 user group 2048 Mar 3 14:23 plik1.txt
drwxr-xr-x 2 user group 4096 Feb 28 09:12 directory1
-rwx------ 1 user group 16384 Feb 25 19:41 executable1
// highlight-end
```

Spróbuj poeksperymentować z innymi poleceniami:

`tekst.
>touch greeting.txt
>echo "hello" > greeting.txt
>ls -l
```

ChatGPT powinien zapamiętać twoje zmiany (przynajmniej przez jakiś czas), a końcowe wyjście powinno wyglądać jak coś w stylu:

``text``
// highlight-start
-rw-r--r-- 1 user group 2048 Mar 3 14:23 plik1.txt
drwxr-xr-x 2 user group 4096 Feb 28 09:12 directory1
-rwx------ 1 user group 16384 Feb 25 19:41 executable1
-rw-r--r-- 1 grupa użytkowników 6 Mar 4 16:15 greeting.txt
// highlight-end
```

Pełną dyskusję na temat używania ChatGPT jako maszyny wirtualnej można znaleźć na stronie [engraved.blog](https://www.engraved.blog/building-a-virtual-machine-inside/).

---

Przyczyniła się firma Prompt Yes!, oferująca [szkolenia inżynierskie](https://promptyes.com/).


