# Decyzje Architektoniczne (ADR)

Rejestr kluczowych ustaleń technicznych w projekcie **ScanCy**.

---

## Spis decyzji

* [ADR-01: Wybór Pythona na główny język programowania](#adr-01) — `Zaakceptowany`
* [ADR-02: Zastosowanie SQL w projektowaniu bazy danych](#adr-02) — `Zaakceptowany`
* [ADR-03: Wdrożenie AI do automatycznego wypełniania formularza na podstawie zdjęć](#adr-03) — `Zaakceptowany`

---

## <a id = adr-01> ADR-01: Wybór Pythona na główny język programowania</a> 

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

## <a id="adr-02">ADR-02: Zastosowanie SQL w projektowaniu bazy danych</a>

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
## <a id="adr-03">ADR-03: Wdrożenie AI do automatycznego wypełniania formularza na podstawie zdjęć </a>

* **Status:** Proponowany | **Data:** 2026-11-03 

### Kontekst
Wdrożenie AI do wypełniania formularza danymi ze zdjęć dodałoby komfortu dla użytkowników 

### Rozważane alternatywy
* **Opcja A:** Wprowadzenie tego rozwiązania 
* **Opcja B:** Odrzucenie tego rozwiązania

## Proponowana decyzja
*Uwaga: Ta decyzja jest obecnie w fazie dyskusji i nie została jeszcze ostatecznie wdrożona.*

Proponujemy wybór **Wprowadzenia**, ponieważ wzbogaci to nasz produkt i zwiększy komfort klientów.
### Konsekwencje
* **+** Dodatkowa wartość systemu
* **+** Lepszy user expirience 
* **-** Dodatkowe koszty czasowe związane z implementacją

<!-- Schemat decyzji
## <a id="adr-N">ADR-N: [TYTUŁ] </a>

* **Status:**  Opcje: Proponowany | Zaakceptowany | Odrzucony | Zastąpiony przez ADR-XXXX | **Data:** 

### Kontekst


### Decyzja


### Konsekwencje
* **+** 

* **-** 
--> 

