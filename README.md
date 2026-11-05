# Czujnik sieci: Monitoring urządzeń i łącza z powiadomieniami na Telegram oraz SMS

Projekt semestralny realizowany w ramach przedmiotu Innowacyjny Projekt Indywidualny na uczelni Uniwersytet Dolnośląski DSW.

* Student: Patryk Widłowski
* Nr indeksu: 56152
* Prowadzący: mgr Dariusz Jędryczek
* Semestr: zimowy 2026/2027

---

## 1. Problem techniczny i cel projektu (SMART)
W małych firmach lub biurach awarie sprzętu sieciowego i Internetu zauważa się dopiero wtedy, gdy praca staje w miejscu. Dodatkowo przy awarii samego łącza stacjonarnego zwykłe maile z powiadomieniami nie wychodzą na zewnątrz, a rozbudowane systemy korporacyjne są za drogie w utrzymaniu.

Cel projektu: Do 24 stycznia 2027 r. przygotować kompletną dokumentację wdrożenia systemu monitoringu Uptime Kuma na minikomputerze x86 podłączonym do zasilacza UPS i modemu LTE. System ma sprawdzać co 30 sekund działanie minimum 8 punktów w sieci (router, switch, dysk NAS, kamery IP, drukarki, zewnętrzny DNS oraz dostęp do stron) i w razie problemu wysłać alert na Telegram w czasie do 45 sekund, a przy braku Internetu wysłać zapasowego SMS-a.

## 2. Sprzęt i narzędzia
* Sprzęt: minikomputer x86 (Intel N100, 16 GB RAM, SSD), zasilacz UPS APC 650VA, modem USB LTE z kartą SIM
* System i kontenery: Linux Debian 12, Docker, Docker Compose
* Oprogramowanie: Uptime Kuma (narzędzie open source)
* Kanały alertów: bot na Telegramie (główny) oraz skrypt SMS przez modem USB (zapasowy)
* Narzędzia projektowe: Draw.io, GitHub, Markdown

## 3. Zakres projektu (MoSCoW)
* Must have: przygotowanie środowiska w Dockerze z autostartem, monitoring 8 kluczowych punktów w sieci, zapasowe powiadomienia SMS przez wpięty modem LTE, czas wysłania alertu do 45 sekund, podtrzymanie zasilania z UPS.
* Should have: podłączenie UPS pod usługę NUT (alert SMS o braku prądu 230V i bezpieczne zamykanie systemu), sprawdzanie ważności certyfikatów SSL, automatyczna kopia zapasowa bazy danych na zewnętrzny nośnik, historia dostępności sieci do ewentualnych reklamacji SLA.
* Could have: prosta podstrona statusowa dla pracowników w sieci lokalnej, wysyłanie alertów na firmowy kanał Discord lub Teams.
* Won't have: instalowanie dużych systemów enterprise (Zabbix/Prometheus), pisanie własnej dedykowanej aplikacji mobilnej, płatny serwer w chmurze bez wglądu w sieć lokalną LAN.

## 4. Struktura repozytorium
* /docs: dokumentacja projektowa i raporty
* /diagrams: schematy sieciowe i diagramy blokowe (.drawio, .png)
* /configs: pliki konfiguracyjne (docker-compose.yml oraz skrypty powiadomień)
