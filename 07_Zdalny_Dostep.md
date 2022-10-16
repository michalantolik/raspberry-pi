# Dostęp zdalny VNC, SCP, klucze RSA

**VNC** - Virtual Network Computing
-  system przekazywania obrazu z wirtualnego bądź fizycznego środowiska graficznego

**SCP** - Secure Copy
-  bezpieczny transfer plików pomiędzy lokalnym a zdalnym lub między zdalnymi komputerami
-  wykorzystuje protokoł Secure Shell (SSH)
-  Skrót SCP odnosi się do dwóch powiązanych ze sobą rzeczy: protokołu SSH oraz polecenia `cp`

## Przygotowanie

1. Włącz Raspberry i podłącz do sieci.
2. Domyślnie zdalna praca jest na Raspberry Pi wyłączona dla bezpieczeństwa.
3. Trzeba ją włączyć i szybko zmienić hasło użytkownika.
4. Umieść kartę SD w komputerze PC.
5. Wyłącz ukrywanie rozszerzeń znanych plików dla karty SD.

    <img src="Images\opcje_folderow.png" />
    <img src="Images\opcje_folderow2.png" />

6. Utwórz na karcie plik `SSH` (bez rozszerzenia!!!)
7. Tym samym umożliwiłeś dostęp zdalny do Raspberry Pi (po SSH).

## Zdalne połączenie VNC

1. Połącz się z Raspberry w trybie tekstowym używając Putty (przez SSH).
2. Wpisz polecenie `sudo raspi-config`
3. Włącz obsługę VNC w Interfacing Options.
4. Ustaw rozdzielczość ekranu np. na 1280 x 720 *(żeby uniknąć opóźnień w pracy zdalnej)*.
5. Zainstaluj klienta VNC, np.: https://www.realvnc.com/
6. Uruchom klienta VNC, podaj IP Raspberry i połącz się.
7. Po chwili ujrzysz pulpit malinki.

## Zdalne połączenie Remote Desktop

1. Zainstaluj Remote Desktop Server na malince: `sudo apt-get install xrdp`
2. Połącz się przez Remote Desktop z PC podając IP.

## Zdalny dostęp do plików

1. Ściągnij WinSCP: https://winscp.net/ i uruchom
2. Połącz się z Raspberry podając IP, adres i użytkownika

    <img src="Images\WinSCP.png">

## Klucze RSA

1. Ściągnij **puttygen**: https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
2. Wygeneruj parę kluczy RSA.
3. Zapisz klucz prywatny na PC.
4. Uruchom WinSCP i włącz pokazywanie ukrytych plików

    <img src="Images\ShowHiddenFiles_WinSCP.png">

5. Utwórz folder `/home/pi/.ssh` na Raspberry jeśli nie istnieje.
6. Utwórz w nim plik `authorized_keys` i wklej do niego wygenerowany klucz publiczny
   - wklej bezpośrednio z puttygen (nie zapisuj na PC, bo może nie zadziałać !!!)

    <img src="Images\puttygen_public_rsa_key.png">

7. Uruchom *putty* i ustaw autentykację SSH kluczem prywatnym z PC

    <img src="Images\Putty_SSH_PrivateKey_Authentication.png">

8. Połącz się z malinką przez SSH używając **putty**.
9. Od tej chwili wystarczy, że podasz tylko nazwę użytkownika.
10. Hasło nie będzie potrzebne ...
