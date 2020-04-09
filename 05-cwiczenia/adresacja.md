## Struktura adresu IP

```192.168.100.192```
```255.255.255.0```




### Jak policzyć?

 Adres IP na binarny , potem maska na binarny (255.255.255.0) -> (11111111 11111111 11111111 0 ) 
 Liczba jedynek w masce = 24, wiec 24 bity na adres sieci
 W sumie 32, 32 - 24 = 8 bitow na adres hostów
 
 
#### Adres sieci

1. zamieniamy dec na binarne
2. mnozenie binarne maski i adresu
3. na dziesietne

#### Adres rozgłoszeniowy

1. odwrotnosc maski
2. negacja
3. dodanie do adresu sieci


## Podział na równą ilość podsieci

```2^S >= n```

Chcemy 7 -> 2^3 >= 7

Maska -> 255.255.255.11100000 -> 255.255.255.224 -> /27


## Wprowadzenie
## 
## | dziesiętnie |  binarnie   | 
| ``10``  |  | 
| ``92``  | | 
| ``37``  | | 
| ``240`` | | 
| ``192`` | | 
| ``255`` | | 
| ``128`` | | 
| ``168`` | | 

## 
## | binarnie |  dziesiętnie   | 
| ``00100000``  |  | 
| ``11111000``  | | 
| ``10100000``  | | 
| ``00110000`` | | 
| ``10101100`` | | 
| ``01000000`` | | 
| ``11111100`` | | 
| ``01100010`` | | 
 
## Notacja CIDR
##  
## | maska |  /(X) x - liczba bitów   | 
| ``255.255.255.0``   | | 
| ``255.128.0.0``     | | 
| ``255.255.252.0``   | | 
| ``255.255.254.0``   | | 
| ``255.255.255.240`` | | 
| ``255.240.0.0``     | | 
## 
## | CIDR |  Maska   | 
| ``/8``    | | 
| ``/20``   | | 
| ``/30``   | | 
| ``/16``   | | 
| ``/27``   | | 
| ``/11``   | | 


## Liczba hostów
## 
## | sieć |  liczba   | 
| ``10.0.0.0/8``    | | 
| ``172.16.0.0/16``   | | 
| ``192.168.1.0/24``   | | 
| ``192.168.1.0/27``   | | 
| ``192.168.1.0/29``   | | 
| ``192.168.1.0/31``   | | 

* liczba 0 w masce?


## Parametry na podstawie adresu

Mając dany adres hosta i maskę znajdź:
  * adres sieci
  * początkowy adres hosta w sieci
  * liczbę hostów w zadanej podsieci ```2^(32 bity - bity maski maska) - 2 (siec i broadcast)```
  * końcowy zakres adresu hosta w sieci
  * adres rozgłoszeniowy
##   ## 

## | Parametr |  wartość   | 
| ``ip``    | 192.168.1.145| 
| ``maska``   | 255.255.255.128 | 
| ``adres sieci``   | |
| ``liczba hostów``   | |
| ``host - min``   | | 
| ``host - max``   | | 
| ``broadcast``   | | 
 
## Zadanie

0. Znajdz wszystkie parametry sieci dla hosta o adresie 172.16.128.64 / 16

maska /16 = 255.255.0.0
adres sieci:
        host  10101100 00010000 10000000 01000000
        maska 11111111 11111111 00000000 00000000
     AND      ___________________________________
              10101100 00010000 00000000 00000000
              172     . 16      .    0   .   0  = ADRES SIECI
              
adres rozgloszeniowy:

       maska 11111111 11111111 00000000 00000000
         NEG 00000000 00000000 11111111 11111111
               0     . 0       .  255  .   255
       + siec 172     . 16      .  0    .   0 
            ___________________________________
             172      . 16      . 255    . 255 = ADRES ROZGLOSZENIOWY
             
             
MAX hostów = 2^(32 - 16) - 2 = 2^16 - 2 = 65 534
pierwszy host = 172.16.0.1
ostatni host = 172.16.255.254


##   
## | Parametr |  wartość   | 
| ``ip``    | 192.168.1.145| 
| ``maska``   | 255.255.255.128 | 
| ``adres sieci``   | |
| ``liczba hostów``   | |
| ``host - min``   | | 
| ``host - max``   | | 
| ``broadcast``   | | 

1.
  * Podziel sieć ```192.168.1.0``` na 16 równych podsieci
##   
## | Adres sieci |  zakres hostów   | Adres Rozgłoszeniowy |
| ``192.168.1.0``    | | |
| ````   | | |
| ````   | | |
| ````   | | |
| ````   | | |
| ````   | | |

2. 
  * Podziel sieć ``172.16.0.0/16`` na 6 równych podsieci.

3. 
  * Podziel sieć ``192.168.1.0/24``, tak aby każda podsieć miała 11 użytkowników.

4. 
  * Podziel sieć ``10.0.0.0/8`` na 5 podsieci. 
    * Podsieć A ma posiadać 100 000 użytkowników,
    * B – 10 000 użytkowników
    * C – 3 000 użytkowników
    * D – 500 użytkowników
    * E – 2 użytkowników.
    
## Wizualizacja

![krakow siec akademicka](cracow-core.jpeg)


## Materiały

    * http://www.cyfronet.krakow.pl/sieci/13152,artykul,charakterystyka_sieci.html
    * https://www.computerworld.pl/news/Sieci-szkieletowe-polskich-operatorow,394360.html
    * https://cidr.xyz/
