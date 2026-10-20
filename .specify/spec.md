# Specyfikacja Systemu ScanCy (.specify/spec.md)

**System:** ScanCy – Inteligentny Skaner i Rejestrator Samochodowy  
**Wersja Specyfikacji:** 1.0.0  
**Metodologia:** Specification-Driven Development (SDD) / GitHub Spec Kit  
**Standardy:** ISO/IEC 25002 (SQuaRE), INVEST, SysML Requirements  

---

## 1. Przegląd Systemu (System Overview)

ScanCy jest zaawansowanym systemem łączącym funkcję kamerki samochodowej (videorejestratora) oraz inteligentnego modułu analizy wideo w czasie rzeczywistym. System analizuje obraz drogi, identyfikuje tablice rejestracyjne, marki, modele i cechy szczególne pojazdów, ocenia prawdopodobieństwo nieoznakowanych patroli policji, a także umożliwia integrację z bazą pojazdów skradzionych oraz dedykowanymi bazami służb mundurowych.

---

## 2. Wymagania Funkcjonalne (Functional Requirements)

### REQ-FUN-001: Skanowanie Cywilne i Analiza Pojazdów
* **Opis:** System po uruchomieniu trybu skanowania wykrywa pojazdy przed samochodem, odczytuje tablicę rejestracyjną, rozpoznaje markę, model, rok, kolor oraz cechy szczególne (np. anteny, czyste ramki). Na tej podstawie szacuje prawdopodobieństwo nieoznakowanego radiowozu.
* **Powiązany Use Case:** UC-01 Skanowanie cywilne
* **Powiązana User Story:** US-01 (Kierowca)
* **Kryteria Akceptacji (Given-When-Then):**
  * **Given:** Kierowca posiada urządzenie ScanCy, a przed nim jedzie podejrzany pojazd.
  * **When:** Kierowca włączy opcję skanowania przyciskiem „START SKANOWANIA”.
  * **Then:** Na ekranie pojawiają się informacje o marce, modelu, kolorze, szczegółach pojazdu oraz procentowe prawdopodobieństwo, że pojazd to policja.

### REQ-FUN-002: Skanowanie Policyjne
* **Opis:** System oferuje rozszerzony tryb skanowania przeznaczony dla uprawnionych funkcjonariuszy policji, pozwalający na automatyczny wgląd w ubezpieczenie, status poszukiwania oraz dane właściciela bez konieczności fizycznego zatrzymywania pojazdu.
* **Powiązany Use Case:** UC-04 Skanowanie policyjne
* **Powiązana User Story:** US-02 (Policjant)
* **Kryteria Akceptacji (Given-When-Then):**
  * **Given:** Policjant w radiowozie posiadający urządzenie ScanCy widzi podejrzany pojazd przed sobą.
  * **When:** Opcja skanowania policyjnego jest włączona i zweryfikowana tożsamością użytkownika.
  * **Then:** Na ekranie pojawiają się szczegółowe informacje o samochodzie, aktualnym ubezpieczeniu OC, statusie poszukiwania oraz danych posiadacza.

### REQ-FUN-003: Zgłaszanie Kradzieży Pojazdu
* **Opis:** Dedykowana aplikacja mobilna/webowa umożliwia zalogowanemu użytkownikowi dodanie skradzionego pojazdu do ogólnej bazy danych ScanCy.
* **Powiązany Use Case:** UC-05 Zgłaszanie pojazdu
* **Powiązana User Story:** US-03 (Użytkownik Aplikacji)
* **Kryteria Akceptacji (Given-When-Then):**
  * **Given:** Osoba zalogowana w aplikacji ScanCy, której skradziono pojazd.
  * **When:** Wybrana zostanie opcja „Zgłoś kradzież pojazdu” i wprowdzone zostaną dane pojazdu (VIN, rejestracja, opis).
  * **Then:** Pojazd zostanie zgłoszony do bazy danych pojazdów zaginionych i udostępniony w sieci skanowania.

### REQ-FUN-004: Monitorowanie i Nagrywanie w Pętli
* **Opis:** System posiada tryb ciągłego monitorowania przedniego pasa drogi, zapisując buforowany materiał w pętli (ostatnia 1 minuta).
* **Powiązany Use Case:** UC-03 Monitorowanie
* **Powiązana User Story:** US-04 (Kierowca / Policjant)
* **Kryteria Akceptacji (Given-When-Then):**
  * **Given:** Kierowca lub policjant chcą zabezpieczyć bufor nagrania sprzed wystąpienia zdarzenia drogowego.
  * **When:** Włączy tryb monitorowania naciskając odpowiedni przycisk na ekranie.
  * **Then:** Kamera z przodu samochodu nagrywa i ciągle nadpisuje bufor ze stałym czasem trwania 1 minuty.

### REQ-FUN-005: Nagrywanie Zdarzenia Drogowego
* **Opis:** Użytkownik ma możliwość trwałego zapisania materiału wideo ze zdarzenia drogowego (z dołączeniem zbuforowanej minuty z trybu monitorowania).
* **Powiązany Use Case:** UC-02 Nagrywanie
* **Powiązana User Story:** US-05 (Kierowca / Policjant)
* **Kryteria Akceptacji (Given-When-Then):**
  * **Given:** Użytkownik jest świadkiem lub uczestnikiem zdarzenia drogowego.
  * **When:** Włączy tryb nagrywania zdarzenia dedykowanym przyciskiem.
  * **Then:** Kamera zapisał wideo w trwałej pamięci i przestanie nadpisywać zbuforowaną wcześniej minutę.

---

## 3. Wymagania Niefunkcjonalne (Non-Functional Requirements – ISO/IEC 25002)

| ID Wymagania | Kategoria ISO/IEC 25002 | Opis Wymagania | Metryka i Cel (Metric & Target) |
| :--- | :--- | :--- | :--- |
| **REQ-NFR-PERF-001** | **Performance Efficiency** (Wydajność) | Czas przetwarzania klatki i detekcji OCR/ML z kamery na żywo. | **Latency** $\le 500\text{ ms}$; **Framerate** $\ge 15\text{ FPS}$. |
| **REQ-NFR-REL-001** | **Reliability** (Niezawodność) | Stabilność pracy wbudowanej kamerki podczas wielogodzinnej jazdy. | **MTBF** (Mean Time Between Failures) $\ge 720\text{ h}$. |
| **REQ-NFR-REL-002** | **Reliability** (Naprawialność) | Samoczynny powrót systemu do stanu gotowości po awarii zasilania/procesu. | **MTTR** (Mean Time To Repair) $\le 15\text{ s}$. |
| **REQ-NFR-AVAIL-001** | **Availability** (Dostępność) | Dostępność usług backendowych i synchrozacji z bazą zaginionych aut. | **Uptime SLA** $\ge 99.9\%$ w skali roku. |
| **REQ-NFR-SEC-001** | **Security** (Poufność i Ochrona) | Szyfrowanie danych i ograniczony dostęp do funkcji policyjnych. | Szyfrowanie **AES-256** w pamięci lokalnej, **TLS 1.3** w chmurze; autoryzacja tokenem **JWT**. |
| **REQ-NFR-USE-001** | **Usability** (Użyteczność) | Bezpieczeństwo i eronomia interfejsu dotykowego podczas prowadzenia pojazdu. | **Time-To-Task** (czas uruchomienia nagrywania/skanu 1-kliknięciem) $\le 1.0\text{ s}$. |

---

## 4. Macierz Śledzenia (Traceability Matrix)

| Identyfikator Wymagania | User Story | Use Case | Komponent Systemu |
| :--- | :--- | :--- | :--- |
| `REQ-FUN-001` | US-01 | UC-01 (Skanowanie cywilne) | Urządzenie Samochodowe (Skaner AI/ANPR) |
| `REQ-FUN-002` | US-02 | UC-04 (Skanowanie policyjne) | Urządzenie Samochodowe (Moduł Służb) |
| `REQ-FUN-003` | US-03 | UC-05 (Zgłaszanie pojazdu) | Aplikacja Mobilna / Backend Cloud |
| `REQ-FUN-004` | US-04 | UC-03 (Monitorowanie) | Urządzenie Samochodowe (Rejestrator Bufora) |
| `REQ-FUN-005` | US-05 | UC-02 (Nagrywanie) | Urządzenie Samochodowe (Pamięć Trwała) |
