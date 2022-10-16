# Instalacja/komunikacja przez UART

**UART** - Uniwersalny asynchroniczny nadajnik-odbiornik
-  od ang. **U**niversal **A**synchronous **R**eceiver - **T**ransmitter
- układ scalony służący do asynchronicznego przekazywania i odbierania informacji poprzez port szeregowy

**Korzystając z łączności przez UART mamy szansę na ...**
- ... na uratowanie uszkodzonego systemu i przywrócenie go do działania.

**Konwerter używany do komunikacji z Raspberry Pi musi pracować
z napięciem 3.3V** ...
- ... stosowanie wersji 5V grozi uszkodzeniem płytki!

## Instalacja z obrazu systemu
1. Ściągnij obraz systemu Raspbian: *https://www.raspberrypi.org/software/*
2. Ściągnij Etcher do nagrania obrazu Raspbiana na kartę SD: *https://www.balena.io/etcher/*
     - ... lub Rufus jeżeli Etcher nie zadziała: https://rufus.ie/
3. Wsuń kartę SD w czytnik USB.
4. Podłącz czytnik z kartą SD do PC.
5. Nagraj obraz Raspbiana na kartę SD używają Etchera.
6. Wyciągnij kartę SD z PC i podłącz jeszcze raz
    - System pokaże wykrycie 2/3 dysków/pamięci
    - Nie zgodź się na formatowanie! - *usunąłbyś Raspbiana z karty SD*
7. Odszukaj partycję plik `config.txt` na partycji `boot` systemu
8. Włącz obsługę UART dodając na końcu pliku linijkę `enable_uart=1`
9. Zapisz zmiany w pliku i przełóż kartę do Raspberry Pi.
10. Załóż zworkę na piny 2 i 4 RPi dla bezpieczeństwa (5V).
11. **Ustaw konwerter UART w tryb 3.3V używając zworki. WAŻNE !!!**
12. Podłącz linie GND, TX, RX konwertera do pinów Rpi (TX i RX na krzyż).
13. Połącz RPi do PC przez konwerter UART.
14. Sprawdź w menedżerze urządzeń do którego portu został przypisany konwerter UART

<img src="Images\Port_Konwertera_UART.png" />

15.  Ściągnij i uruchom program Putty: https://www.putty.org/
16.  Skonfiguruj połączenie szeregowe z Raspberry Pi

<img src="Images\Putty_Serial_Port.png" />
<img src="Images\Putty_Serial_Port_2.png" />

17. Sprawdź raz jeszcze poprawność podłączenia przewodów i zworek.
18. Podłącz zasilacz do Raspberry Pi.
20. Kliknij "Open" w Putty żeby połączyć się z Raspberry Pi (poczekaj chwilę).
21. Rozpocznie się konfiguracja systemu Raspbian (ok. 5 minut).

## Logowanie i podstawowa konfiguracja

1. Po zakończonej konfiguracji zaloguj się jako użytkownik "pi" z hasłem "raspberry".
2. Uruchom `sudo raspi-config`
   - Zmień hasło
   - Ustaw Local, Timezone, Keyboard

<img src="Images\Locale.png" />
<img src="Images\Locale2.png" />

## Testowo - dla nauki ...

1. Wyczyść zawartość konsoli: `clear`
2. Wyłącz Raspberry: `sudo shutdown now` ...
3. ... lub uruchom ponownie: `sudo reboot`
