# CubeScanner

  System wizyjny służący do sczytywania kolorów z poszczególnych ścian kostki i przesyłania tych informacji do robota stanowi aplikacja mobilna stworzona w języku Java przy wykorzystaniu środowiska programistycznego Android Studio.
  Serce programu stanowią dwa współgrające algorytmy – prosty oraz zaawansowany algorytm rozpoznawania. Pierwszy z nich korzysta ze ściśle określonych niezmiennych punktów natomiast drugi przetwarza obraz i w kolejnych krokach dąży do odszukania kostki i wyznaczenia środków kafelków danej ściany. Dalsza część która jest tożsama dla obu z nich wykorzystuje procesor rozpoznawania który otrzymuje na swoje wejście określone punkty które w domyśle stanowią środki kolejnych kafelków na kostce. Procesor w kolejnych krokach zbiera próbki kolorów i próbuje dopasować do nich wcześniej zdefiniowane wzorniki odpowiadające poszczególnym polom. Jego wyjście stanowią obiekty reprezentujące kolory ułożone w ściśle 
określonej kolejności przystosowanej do schematu działania wykorzystywanego przez Cube Solver’a.

Schemat działania aplikacji 
![cubeScanner](https://user-images.githubusercontent.com/101074920/158663407-6ae70641-c7aa-46d1-9e16-194ee0326751.png)

2. Prosty tryb rozpoznawania

![22](https://user-images.githubusercontent.com/101074920/158664854-a66b2e78-11dd-4668-ad48-3b9a9300b4a6.png)

3. Zaawansowany tryb rozpoznawania

3.1 Przygotowanie obrazu

- Pobranie obrazu z wykorzystaniem aparatu wbudowanego w urządzenie
- Przetworzenie na obraz w skali szarości
- Wyrównanie histogramu
- Usuwanie szumu
- Wykrywanie krawędzi przy wykorzystaniu algorytmu Canny'ego

![image](https://user-images.githubusercontent.com/101074920/158665456-c10e3730-b099-4405-a025-65dad25bb301.png)

- Pogrubienie krawędzi z wykorzystaniem operacji morfologicznych
- Szukanie linii z wykorzystaniem transformacji Hough'a

![image](https://user-images.githubusercontent.com/101074920/158665509-a120b827-8097-401b-9649-e8f73d56132a.png)

3.2 Operacje na wykrytych krawędziach dążące do wyznaczenia środków poszczególnych kafelków na kostce

- Wyciągnięcie informacji na temat poszczególnych linii
- Segregacja linii ze względu na kąt nachylenia (wstęp do szukania linii prostopadłych)

![image](https://user-images.githubusercontent.com/101074920/158675585-ca125012-e58b-46ce-bf64-ac2328d9f6dd.png)

- Szukanie punktów przecięcia linii prostopadłych i zbieranie ich w grupy

![image](https://user-images.githubusercontent.com/101074920/158675623-b81d68a8-503f-4aaa-b8cf-25533e2c6a9a.png)

- Scalanie grup punktów

![image](https://user-images.githubusercontent.com/101074920/158675666-d94c40f4-a112-498a-a0d4-cac5fc659e3a.png)

- Usuwanie błędów powstałych we wcześniejszych krokach 

![image](https://user-images.githubusercontent.com/101074920/158675703-f8dc6007-4744-4717-8c83-85af2ec65a87.png)

- Wyznaczenie dwóch prostopadłych linii z punktów reprezentujących narożniki kafelków

![image](https://user-images.githubusercontent.com/101074920/158675727-f74290a5-d339-4ccd-a36e-4abb8a118a65.png)

- Wyznaczenie pozostałych narożników kafelków 

![image](https://user-images.githubusercontent.com/101074920/158675801-9d2f4703-c6ea-4269-a655-85d43f85b8ca.png)

- Wyznaczenie środków kafelków

![image](https://user-images.githubusercontent.com/101074920/158675883-0458341b-28a0-434d-9063-63d12c5f978c.png)

![image](https://user-images.githubusercontent.com/101074920/158675829-d1fd99e6-fb6e-42a2-9eba-61e12d72b308.png)

Wyświetlenie, akceptacjai wysłanie informacji o kostce do Cube Solvera

![3](https://user-images.githubusercontent.com/101074920/158677421-1d59c671-d42c-4d38-8bab-923053db2198.png)

