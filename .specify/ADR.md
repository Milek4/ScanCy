# Decyzje Architektoniczne (ADR)

Rejestr kluczowych ustaleń technicznych w projekcie **ScanCy**.

---

## Spis decyzji

* [ADR-01: Wybór Pythona na główny język programowania](#adr-01) — `Zaakceptowany`
* [ADR-02: Zastosowanie SQL w projektowaniu bazy danych](#adr-02) — `Zaakceptowany`

---

<a id = adr-01> ADR-01: Wybór Pythona na główny język programowania</a> 

* **Status:** Zaakceptowany | **Data:** 2026-10-26 

### Kontekst
Potrzebowaliśmy ustalić jeden jezyk dla projektu.

### Decyzja
Wybieramy **Python**, ponieważ zaweira on biblioteki pozwalające przetwarzać zdjęcia w prosty sposób.

### Konsekwencje
* **+** Gotowe rozwiązania.
* **+** Prostota w pisaniu kodu.
* **-** Konieczność nauki nowego narzędzia przez zespół.
* **-** Uzależnienie całej architektury od tego rozwiązania.

---

<a id="adr-02">ADR-02: Zastosowanie SQL w projektowaniu bazy danych</a>

* **Status:** Zaakceptowany | **Data:** 2026-10-27 

### Kontekst
Musieliśmy zdecydować się w jakim standardzie stworzyć bazę danych.

### Decyzja
Wybieramy **SQL** ze względu na jego niezawodność i powszechne wsparcie wraz z dokumentacją.

### Konsekwencje
* **+** Niezawodność
* **+** Rozbudowane community
* **+** Przewidywalność
* **-** Skalowanie horyzontalne będzie bardziej skomplikowane niż w bazach NoSQL

---
<!-- Schemat decyzji
<a id="adr-N">ADR-N: [TYTUŁ] </a>

* **Status:**  | **Data:** 

### Kontekst


### Decyzja


### Konsekwencje
* **+** 

* **-** 
--> 

