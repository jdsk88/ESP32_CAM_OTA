- doświetlenie daje się wyłączyć: samo wyzerowanie wypełnienia PWM nie gasiło
  lampy (rdzeń Arduino przy wypełnieniu 0 nie zatrzymuje kanału i wyjście
  potrafi zostać w stanie wysokim), więc wyłączenie odbiera teraz pin układowi
  PWM i wymusza stan niski
- naprawa tymczasowego dzwonka na przycisku IO0: uruchomienie kamery
  przejmowało GPIO0 i kasowało odczyt pinu, przez co zaraz po starcie padał
  jeden fałszywy dzwonek, a późniejsze naciśnięcia nie były w ogóle widziane
- przycisk IO0 na podstawce ESP32-CAM-MB działa jako tymczasowy dzwonek, więc
  całą ścieżkę połączenia można wypróbować przed podłączeniem przycisku do
  GPIO13. To rozwiązanie na czas testów: GPIO0 prowadzi zegar kamery, więc
  naciśnięcie zwiera pracujące wyjście — po zamontowaniu ustaw
  `DOOR_BUTTON_USE_IO0` na 0 (`include/config.h`)
- dzwonek otwiera na panelu 10" pełnoekranowe połączenie z obrazem i
  przyciskami Odbierz / Wycisz / Odrzuć (panel od wersji 1.10.0)
- obraz przechodzi do nowego widza: o strumień może poprosić przeglądarka albo
  panel 10" i dostaje go natychmiast — dzwonek sam zamyka poprzednie
  połączenie, zamiast odmawiać komunikatem o zajętym strumieniu. Żaden klient
  nie musi o nic prosić, decyduje samo urządzenie
- serwer obrazu przepisany na własne gniazdo z osobnym zadaniem: nasłuch i
  wysyłka klatek działają równolegle, więc nowe żądanie jest widziane od razu.
  Przy okazji zdjęcie (`/snapshot`) nie przerywa już trwającego podglądu,
  a firmware zajmuje o ~27 kB mniej
- nowa karta „Kamera" w aplikacji: kompaktowy podgląd na żywo w lewym górnym
  rogu, a wokół niego — z prawej i pod spodem — komplet regulacji obrazu, więc
  efekt każdej zmiany widać od razu; zmiany zapisują się same (suwaki dopiero
  po puszczeniu, żeby nie zasypywać pamięci zapisami)
- przycisk „Ustawienia fabryczne kamery" przywraca wszystkie parametry obrazu
  łącznie z rozdzielczością, jakością i obrotami
