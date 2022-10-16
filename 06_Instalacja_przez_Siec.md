# Instalacja/komunikacja przez sieć (po SSH)

**SSH** - Secure SHell
-  standard protokołów, które pozwalają nawiązać zdalne połączenie z innym komputerem

## Przygotowanie

1. Przygotuj kartę SD ze "świeżym" obrazem system Raspbian.
2. Umieść kartę SD w komputerze PC.
3. Wyłącz ukrywanie rozszerzeń znanych plików dla karty SD.

<img src="Images\opcje_folderow.png" />
<img src="Images\opcje_folderow2.png" />

## Wariant przewodowy

<img src="Images\rpi_6_siec_router_ethernet.png" />

1. Domyślnie zdalna praca jest na Raspberry Pi wyłączona dla bezpieczeństwa.
2. Trzeba ją włączyć i szybko zmienić hasło użytkownika.
3. Umieść kartę SD w komputerze PC.
4. Utwórz na karcie plik `SSH` (bez rozszerzenia!!!)
5. Tym samym umożliwiłeś dostęp zdalny do Raspberry Pi (po SSH).
6. Umieść kartę w Raspberry.
7. Podłącz Raspbery kablem ethernet do routera i uruchom.
8. Teraz musisz poznać adres IP przypisany przez router do Raspberry Pi.
9. Tutaj jest kilka sposobów...
    
    - zaloguj sie do routera jako admin i tam sprawdź
  
    - wpisz w konsoli na PC komendę `arp -a`
  
      - wyszukaj IP przypisanego do MAC `b8-27-eb...` (taki MAC ma zawsze Raspberry)
  
   - użyj dowolnego skanera adresów IP sieci (np. Advanced IP Scanner)
   
   - podłącz Raspberry przez UART do PC i wpisz komendę
     - `ifconfig` / `ifconfig eth0`

10. Podłącz się do Raspberry używając Putty
    
    <img src="Images\RPi_ssh_putty.png" />


## Wariant bezprzewodowy

<img src="Images\rpi_6_siec_router_wifi.png" />

1. Domyślnie zdalna praca jest na Raspberry Pi wyłączona dla bezpieczeństwa.
2. Trzeba ją włączyć i szybko zmienić hasło użytkownika.
3. Umieść kartę SD w komputerze PC.
4. Utwórz na karcie plik `SSH` (bez rozszerzenia!!!)
5. Tym samym umożliwiłeś dostęp zdalny do Raspberry Pi (po SSH).4. 
6. Utwórz na karcie plik `wpa_supplicant.conf` i wklej do niego:

    ```
    country=PL
    update_config=1
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    
    network={ 
        ssid="Nazwa sieci" 
        psk="haslo" 
        key_mgmt=WPA-PSK 
    }
    ```

    ... gdzie ...

    - SSID to identyfikator/nazwa sieci WiFi
    - PSK to hasło dostępu
    - Jako sposób uwierzytelniania wpisaliśmy WPA-PSK, co jest dosyć typowym ustawieniem, ale można użyć innych. Każdy musi podać sposób zabezpieczenia zgodny z siecią, do której chce podłączyć Raspberry Pi. Jeśli sieć nie byłaby w żaden sposób zabezpieczona (oczywiście nikt tak nie robi...), to w pole to należałoby wpisać "NONE"

7. Tym samym umożliwiłeś dostęp zdalny do Raspberry Pi (po SSH).
8. Umieść kartę w Raspberry.
9. Podłącz Raspbery kablem ethernet do routera i uruchom.
10. Teraz musisz poznać adres IP przypisany przez router do Raspberry Pi.
11. Tutaj jest kilka sposobów...
    
    - zaloguj sie do routera jako admin i tam sprawdź
  
    - wpisz w konsoli na PC komendę `arp -a`
  
      - wyszukaj IP przypisanego do MAC `b8-27-eb...` (taki MAC ma zawsze Raspberry)
  
   - użyj dowolnego skanera adresów IP sieci (np. Advanced IP Scanner)
   
   - podłącz Raspberry przez UART do PC i wpisz komendę
     - `ifconfig` / `ifconfig wlan0`

12. Podłącz się do Raspberry używając Putty
    
    <img src="Images\RPi_ssh_putty.png" />


## Bezpośrednie połączenie ethernet (PC-RPi)

## Wariant przewodowy

<img src="Images\rpi_6_siec_router_ethernet.png" />

1. Domyślnie zdalna praca jest na Raspberry Pi wyłączona dla bezpieczeństwa.
2. Trzeba ją włączyć i szybko zmienić hasło użytkownika.
3. Umieść kartę SD w komputerze PC.
4. Utwórz na karcie plik `SSH` (bez rozszerzenia!!!)
5. Tym samym umożliwiłeś dostęp zdalny do Raspberry Pi (po SSH).
6. Umieść kartę w Raspberry.
7. Podłącz Raspbery z PC kablem ethernet.
8. Podłącz zasilanie do Raspberry.
9. Otwórz Centrum sieci i udostępniania na PC (Network and Sharing Center).
10. Wybierz sieć za pomocą której łączysz się z internetem.
11. Wejdź we Właściwości -> Udostępnianie (Properties -> Sharing).

... **Internet Connection Sharing has been disabled by the Network Administrator - dokończyć kiedyś ... !!!**
