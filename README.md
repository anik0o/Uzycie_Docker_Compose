# Zadanie 2 - projekt z użyciem Docker Compose
## Budowa środowiska do rozwoju i uruchamiania aplikacji webowych.
W tym zadaniu należy zbudować prosty plik docker-compose.yml, który
pozwoli na uruchomienie znanej z innych zajęć, uslugi LEMP wraz z phpMyAdmin. Stack
LEMP składa się z następujących usług składowych: 
---- L – dla Linux; 
---- E – dla Nginx; 
---- M – dla MySQL; 
---- P – dla PHP. 
Wobec tego projekt powinien zawierać cztery kontenery (usługi): 
- jeden kontener dla Nginx; 
- jeden kontener dla PHP (PHP-FPM) https://php-fpm.org/ ; 
- jeden kontener dla MySQL; 
- jeden kontener dla phpMyAdmin.
- 
Projekt powinien spełniać następujące wymagania:
- serwery są budowane zgodnie z dokumentacją obrazów bazowych dostępnych na
DockerHub i umieszczonych tam plików Dockerfile (zbudowanie własnych obrazów a nie
wykorzystanie z gotowych obrazów będzie wyżej oceniane).
- serwery PHP, MySQL, phpMyAdmin są przyłączone do sieci backend a Nginx do
backend oraz frontend. Nginx ma wystawiony na świat zewnętrzy port 6666.
- serwer Nginx ma wyświetlać stronę startową php (index.php).
- serwer phpMyAdmin ma być dostępny na porcie 6001 i powinno być możliwe
zalogowanie się do niego i założenie testowej bazy.

Katalog zawierający projekt zawiera plik docker-compose oraz dwa foldery:

-str- folder zawierający plik index.php, czyli stronę, która będzie wyświetlana przez serwer po połączeniu z bazą danych<br>
-uslugi- folder zawierający pliki dockerfile do tworzenia danych usług

Dodatkowo w celu prawidłowego działania strony, został utworzony plik konfiguracyjny str.conf.

Po utworzeniu katalogów, plików dockerfile, pliku konfiguracyjnego strony oraz utworzeniu pliku docker-compose.yml,przeszłam do uruchomienia serwisu.
W tym celu i ze względu na posiadaną wersję Docker'a użyłam polecenia: `docker-compose up`.

 ![1](https://github.com/anik0o/images/blob/e5f54e69414e71945f41063948a1f7c1b8541505/compose-up.png)
 
 Następnie wykonałam:
 
 -sprawdzenie działania phpMyAdmin poprzez wejście w localhosta na porcie 6001 i przeprowadzenie testu działania bazy danych:
 ![3](https://github.com/anik0o/images/blob/b0ee488a617f62faa498db428f0d931fc410aabe/Zrzut%20ekranu%202021-12-11%20201046.png)
 ![4](https://github.com/anik0o/images/blob/b0ee488a617f62faa498db428f0d931fc410aabe/Zrzut%20ekranu%202021-12-11%20201100.png)

 -sprawdzenie działania strony na porcie 6666.
 
 ![5](https://github.com/anik0o/images/blob/b0ee488a617f62faa498db428f0d931fc410aabe/Zrzut%20ekranu%202021-12-11%20201140.png)
 
-wygenerowanie reprezentacji graficznej poleceniem: `docker container run --rm -it --name mgraph -v $(pwd):/input pmsipilot/docker-compose-viz render -m image docker-compose.yml`
![6](https://github.com/anik0o/composer/blob/371dcbb761aa90e163a7c9881e541d585afe1eeb/docker-compose.png)

