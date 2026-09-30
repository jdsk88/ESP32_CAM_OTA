- Integracja z panelem 10" (ESP-NOW): domofon przedstawia się jako urządzenie
  kategorii audio-wideo i cyklicznie raportuje stan — rygiel, licznik
  dzwonków oraz **czy jest połączony z WiFi** (z siłą sygnału).
- Nowa komenda `wifi` z panelu: gdy domofon nie ma sieci, panel (dotykiem lub
  przez swoje web UI) wysyła nazwę i hasło sieci szyfrowanym łączem ESP-NOW,
  a domofon dołącza do routera w trybie AP+STA.
- Dzwonek sygnalizowany panelowi liczbowo (licznik `rings`), więc panel może
  zagrać powiadomienie natychmiast po naciśnięciu przycisku.
