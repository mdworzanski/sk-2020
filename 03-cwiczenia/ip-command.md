## Zarządzanie interfejsami z wykorzystamiem programu IP

* stan interfejsu
    * interfejs up
    * interfejs down
* adresacja
    * dodaj adres
    * zmień adres
    * usuń adres
    * wyczyść adresy
* routing
    * pobierz trasę dla adresu
    
* adresacja fizyczna
    * pokaż adresy interfejsów dostępnych w sieci
    * pokaż adresy dla konkretnego interfejsu
     


### ip 

| subcommand    |  polecenie   | opis  |
| ------------- |:-------------| :---------------| 
|   ``addr``    |                               | informacje o adresacji i własnościach interfejsów |
|               |   ``ip addr``                 | informacja o wszystkich interfejsach              |
|               |   ``ip addr show dev enp0s3`` | informacja o konkretnym interfejsie               |
|               |   ``ip addr add 192.168.1.1/24 dev em1`` | dodaje adres 192.168.1.1/24 do interfejsu em1               |
|               |   ``ip addr del 192.168.1.1/24 dev em1`` | usuwa adres 192.168.1.1/24 z interfejsu em1                |
|   ``link``    |                               | zarządza i wyświetla stan wszystkich intefejsów|
|               |   ``ip link`` | informacje o wszystkich interfejsach              |
|               |   ``ip link show dev em1`` | informacje o interfejsie o nazwie em1              |
|               |   ``ip -s link`` | statystyki interfejsu            |
|               |   ``ip link set`` | zmienia status interfejsu            |
|               |   ``ip link set em1 up`` | zmienia status interfejsu em1 na online            |
|               |   ``ip link set em1 down`` | zmienia status interfejsu em1 na offline            |
|   ``route``   |  | wyświetla i zmienia tablice routingu|
|               |   ``ip route`` | informacje o wszystkich tablicach routingu             |
|               |   ``ip route add default via 192.168.1.1 dev em1`` | dodaje domyślny routing przez lokalną bramę 192.168.1.1 która może być połączona przez interfejs em1            |
|               |   ``ip route add 192.168.1.0/24 via 192.168.1.1`` | dodaje routing do sieci  192.168.1.0/24 przez bramę 192.168.1.1            |
|               |   ``ip route delete 192.168.1.0/24 via 192.168.1.1`` | usuwa routing do sieci 192.168.1.0/24 przez bramę 192.168.1.1             |
|               |   ``ip route replace 192.168.1.0/24 dev em1`` | zmienia (lub dodaje jeśli nie zdefiniowano) routing do sieci 192.168.1.0/24 przez interface em1           |
|               |   ``ip route get  192.168.1.5`` | wyświetla tablicę routingu do sieci  192.168.1.5             |
|   ``maddr``   |  | zarządza i wyświetla adresy IP multicast|
|               |   ``ip maddr`` | informacje o IP multicast dla wszystkich interfejsów           |
|               |   ``ip maddr show dev em1`` | informacje o IP multicast dla interfejsu em1            |
|   ``neigh``   |  | zarządza i wyświetla tablice sąsiedztwa |
|               | ``ip neigh``  | pokazuje tablice sąsiedztwa |
|               | ``ip neigh show dev em1``  | pokazuje tablice sąsiedztwa dla interfejsu em1 |
|   ``help``    |  | lista komend i argumentów do każdej z subkomend|
|      | ``ip help`` | |
|      | ``ip addr help`` | |
|      | ``ip link help`` | |
|      | ``ip neigh help`` | |




### Zadanie

![zadanie 3](sieci-3.0.svg)

1.
   * Przygotuj konfigurację sieci zgodnie z powyższym diagramem, 
   * Przetestuj połączenie poleceniem ping
   * Przetestuj połączenie z internetem
   * Sprawdź trasę dla połączeń z adresem IP z poza Twojej sieci lokalnej np. 1.1.1.1

1.1
   * Zmodyfikuj połączenia sieciowe zgodnie z poniższym schematem
   * Ponownie sprawdź trasę dla adresu z poza Twojej sieci lokalnej
  
![zadanie 3](sieci-3.1.png)

2.
   * Zainstaluj na komputerze ``PC0`` serwer ``HTTP`` np. ``nginx`` 
   * skonfiguruj program ``nginx`` tak aby wyświetlał zawartość katalogu ``/var/www``
   * przeładuj konfigurację
   * utwórz własny plik ``index.html`` zawierający tekst
   * Przetestuj komunikację z ``localhost``  wykorzystując konsolowego klienta ``HTTP``, program ``curl``
3.
   * Sprawdź który port został zarezerwowany dla komunikacji przez progrmam ``nginx``
   * np. program ``netstat``

4.
   * Przetestuj komunikację z serwerem HTTP z poziomu komputera ``PC2``
   * czy jest dostepne polecenie curl?
   * np. ``curl {adres_ip_pc_2}``
   * Wykonaj test dla połączenia na innym porcie niż ``80``, np ``curl {adres_ip_pc_2}:8080``
   * czy odpowiedź jest analogiczna jak dla testu z zadania ``2``?

5.
   * Rozbuduj sieć o kolejny komputer ``PC3`` zgodnie z diagramem
   
![zadanie 3](sieci-3.2.png)

6. 
   * Na komputerze ``PC3`` utwórzy plik index.html w katalogu ``/var/www``
   * Na komputerze ``PC3`` uruchom serwer protokołu ``HTTP`` tym razem wykorzystujac python
   * ``python3 -m http.server --directory /var/www --bind 127.0.0.1``
   * Przenieś wykonanie programu do tła ``ctrl + z`` ``bg``
   * Sprawdź połączenie wykorzystując ``curl localhost:port``
   * Sprawdź połączenie wykorzystując ``curl adres_ip:port``
   * Sprawdź zarezerwowane porty korzystając z polecenia ``netstat``
   
7. 
    * Na komputerze ``PC3`` zmodyfikuj sposób uruchamiania serwera http w taki sposób aby możliwe było wyświetlenie strony z komputerów ``PC1`` oraz ``PC2`` 
    * Przeprowadź test takiej komunikacji

8.
   * Na komputerze ``PC0`` zainstaluj i uruchom w tle program ``chat-server`` z cwiczeń 2
   * Sprawdź zarezerwowane porty korzystając z polecenia ``netstat``
   * Na komputerach ``PC1`` oraz ``PC2`` zainstaluj program ``chat-client``
   * Połącz się z serwerem dostępnym pod adresem IP ``PC0``
