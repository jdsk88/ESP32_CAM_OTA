OTA: wydania z repozytorium ESP32_CAM_OTA

Kod źródłowy trafia do ESP32_CAM, a artefakty aktualizacji do osobnego,
publicznego ESP32_CAM_OTA — urządzenie pobiera manifest.json bez logowania,
więc repozytorium z wydaniami musi pozostać publiczne.

Przestawione: OTA_RELEASES_REPO (adres, pod który puka firmware), RAW_BASE
w tools/release.py oraz RELEASES_REPO w workflow wydania. Zdalny "updates",
śledzony przez gałąź OTA_PUBLIC, wskazuje teraz na to samo repozytorium.

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>
