# Katalog kart procesów

ORPR obejmuje 74 procesy. Publiczne repozytorium pokazuje sześć pełnych kart oraz 68 skrótów
zweryfikowanych kart. Skrót pozwala zrozumieć cel, granice i odpowiedzialność procesu, lecz nie
udostępnia pełnego materiału diagnostycznego i wdrożeniowego.

**Legenda:** `Pełna karta` oznacza kompletny publiczny przykład. `Skrót` oznacza publiczny opis
karty, której pełna wersja pozostaje poza repozytorium.

## Karty według obszarów

### Zakupy i płatności dla dostawców

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-PRC-01` | Od zapotrzebowania do zamówienia | `reviewed` | [Skrót](karty-publiczne/ORPR-PRC-01.md) |
| `ORPR-PRC-02` | Od dokumentu dostawy do przyjęcia | `reviewed` | [Skrót](karty-publiczne/ORPR-PRC-02.md) |
| `ORPR-PRC-03` | Od faktury do zobowiązania | `reviewed` | [Skrót](karty-publiczne/ORPR-PRC-03.md) |
| `ORPR-FIN-04` | Od zobowiązania do zapłaty | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-04.md) |
| `ORPR-PRC-04` | Od warunków handlowych do rozliczenia korzyści pozafakturowych | `reviewed` | [Skrót](karty-publiczne/ORPR-PRC-04.md) |

### Planowanie i dostępność

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-DEM-01` | Od popytu do zapotrzebowania netto | `reviewed` | [Skrót](karty-publiczne/ORPR-DEM-01.md) |
| `ORPR-DEM-02` | Od zapotrzebowania do zakupu (ścieżka ręczna) | `reviewed` | [Skrót](karty-publiczne/ORPR-DEM-02.md) |
| `ORPR-DEM-03` | Od sygnału popytu do prognozy | `reviewed` | [Skrót](karty-publiczne/ORPR-DEM-03.md) |
| `ORPR-DEM-04` | Od ograniczeń do alokacji | `reviewed` | [Skrót](karty-publiczne/ORPR-DEM-04.md) |
| `ORPR-DEM-05` | Od stanu zapasu do obiecywalnej dostępności | `reviewed` | [Skrót](karty-publiczne/ORPR-DEM-05.md) |

### Oferta handlowa

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-CAT-01` | Od pozycji do dopuszczenia do sprzedaży | `reviewed` | [Pełna karta](domeny/CAT/ORPR-CAT-01-item-to-sellable.md) |
| `ORPR-CAT-02` | Od ceny do kasy | `released` | [Pełna karta](domeny/CAT/ORPR-CAT-02-price-to-pos.md) |
| `ORPR-CAT-03` | Od promocji do kasy | `reviewed` | [Pełna karta](domeny/CAT/ORPR-CAT-03-promotion-to-pos.md) |
| `ORPR-CAT-04` | Od akcji handlowej do efektu | `reviewed` | [Pełna karta](domeny/CAT/ORPR-CAT-04-commercial-action-to-effect.md) |

### Realizacja sprzedaży

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-SAL-01` | Od koszyka do sprzedaży | `released` | [Pełna karta](domeny/SAL/ORPR-SAL-01-basket-to-sale.md) |
| `ORPR-SAL-02` | Od sprzedaży do dokumentu fiskalnego | `reviewed` | [Skrót](karty-publiczne/ORPR-SAL-02.md) |
| `ORPR-SAL-03` | Od sprzedaży do wydania towaru | `reviewed` | [Pełna karta](domeny/SAL/ORPR-SAL-03-sale-to-inventory-issue.md) |

### Płatności klientów

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-PAY-01` | Od kwoty do formy płatności | `reviewed` | [Skrót](karty-publiczne/ORPR-PAY-01.md) |
| `ORPR-PAY-02` | Od autoryzacji do przechwycenia | `reviewed` | [Skrót](karty-publiczne/ORPR-PAY-02.md) |
| `ORPR-PAY-03` | Od przechwyconych płatności do rozliczenia partii z operatorem | `reviewed` | [Skrót](karty-publiczne/ORPR-PAY-03.md) |

### Zwroty

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-RTN-01` | Od sprzedaży do anulowania | `reviewed` | [Skrót](karty-publiczne/ORPR-RTN-01.md) |
| `ORPR-RTN-02` | Od sprzedaży do zwrotu | `reviewed` | [Skrót](karty-publiczne/ORPR-RTN-02.md) |
| `ORPR-RTN-03` | Od zwrotu do zwrotu środków | `reviewed` | [Skrót](karty-publiczne/ORPR-RTN-03.md) |
| `ORPR-RTN-04` | Od zwrotu do rozdysponowania | `reviewed` | [Skrót](karty-publiczne/ORPR-RTN-04.md) |

### Sprzedaż internetowa i na odległość

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-ORD-01` | Od złożonego zamówienia zdalnego do przyjętego zamówienia klienta | `reviewed` | [Skrót](karty-publiczne/ORPR-ORD-01.md) |
| `ORPR-DLV-01` | Od przesyłki gotowej do ostatniej mili do potwierdzonego wyniku dostawy | `reviewed` | [Skrót](karty-publiczne/ORPR-DLV-01.md) |

### Obsługa klienta i reklamacje

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-SVC-01` | Od zgłoszonej sprawy klienta do przekazanego rozstrzygnięcia | `reviewed` | [Skrót](karty-publiczne/ORPR-SVC-01.md) |

### Zapas

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-INV-01` | Od przyjęcia do dostępności | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-01.md) |
| `ORPR-INV-02` | Od transferu do przyjęcia | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-02.md) |
| `ORPR-INV-03` | Od inwentaryzacji do korekty | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-03.md) |
| `ORPR-INV-04` | Od straty do odpisu | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-04.md) |
| `ORPR-INV-07` | Od przyjętego zamówienia do rezerwacji zapasu | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-07.md) |
| `ORPR-INV-08` | Od rozbieżności przesunięcia do uzgodnienia | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-08.md) |
| `ORPR-INV-09` | Od zdarzeń zapasowych do wiarygodnego stanu | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-09.md) |

### Księgowość

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-FIN-01` | Od sprzedaży do księgi | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-01.md) |
| `ORPR-FIN-02` | Od zapasu do kosztu własnego | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-02.md) |
| `ORPR-FIN-03` | Od podatku do zobowiązania | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-03.md) |

### Rozliczanie kas i utargu

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-CSH-01` | Od otwarcia do zamknięcia kasy | `reviewed` | [Skrót](karty-publiczne/ORPR-CSH-01.md) |
| `ORPR-CSH-02` | Od gotówki do wpłaty | `reviewed` | [Skrót](karty-publiczne/ORPR-CSH-02.md) |
| `ORPR-CSH-03` | Od przechwyconych płatności kartą do uzgodnienia wpływów dnia | `reviewed` | [Skrót](karty-publiczne/ORPR-CSH-03.md) |
| `ORPR-CSH-04` | Od rozliczenia do banku | `reviewed` | [Skrót](karty-publiczne/ORPR-CSH-04.md) |

### Kontrola i zgodność

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-CTL-01` | Od transakcji do uzgodnienia | `reviewed` | [Skrót](karty-publiczne/ORPR-CTL-01.md) |
| `ORPR-CTL-02` | Od wyjątku do rozwiązania | `reviewed` | [Skrót](karty-publiczne/ORPR-CTL-02.md) |
| `ORPR-CTL-03` | Od zdarzenia do audytu | `reviewed` | [Skrót](karty-publiczne/ORPR-CTL-03.md) |
| `ORPR-CTL-04` | Od planu kontroli do zarejestrowanej niezgodności | `reviewed` | [Skrót](karty-publiczne/ORPR-CTL-04.md) |

### Zarządzanie asortymentem i dostawcami

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-SUP-01` | Od potrzeby pozyskania do warunków handlowych | `reviewed` | [Skrót](karty-publiczne/ORPR-SUP-01.md) |
| `ORPR-AST-01` | Od potrzeby zmiany asortymentu do decyzji i danych produktu | `reviewed` | [Skrót](karty-publiczne/ORPR-AST-01.md) |
| `ORPR-AST-02` | Od kierunku do strategii kategorii | `reviewed` | [Skrót](karty-publiczne/ORPR-AST-02.md) |
| `ORPR-SUP-02` | Od zobowiązań dostawcy do pełnego rozliczenia | `reviewed` | [Skrót](karty-publiczne/ORPR-SUP-02.md) |
| `ORPR-AST-03` | Od potrzeby ekspozycji do planu przestrzeni i ekspozycji | `reviewed` | [Skrót](karty-publiczne/ORPR-AST-03.md) |

### Logistyka sieci

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-LOG-01` | Od zlecenia transportu do potwierdzonego odbioru | `reviewed` | [Skrót](karty-publiczne/ORPR-LOG-01.md) |
| `ORPR-LOG-02` | Od wymagań magazynu do gotowości operacyjnej magazynu | `reviewed` | [Skrót](karty-publiczne/ORPR-LOG-02.md) |

### Marketing i relacje z klientami

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-CRM-01` | Od kontaktu z klientem do mierzalnej relacji | `reviewed` | [Skrót](karty-publiczne/ORPR-CRM-01.md) |
| `ORPR-MKT-01` | Od celu komunikacyjnego do zmierzonego efektu kampanii | `reviewed` | [Skrót](karty-publiczne/ORPR-MKT-01.md) |
| `ORPR-BRD-01` | Od potrzeby marki do zatwierdzonego standardu | `reviewed` | [Skrót](karty-publiczne/ORPR-BRD-01.md) |

### Operacje i utrzymanie lokalizacji

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-INV-05` | Od uzupełnienia do półki | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-05.md) |
| `ORPR-INV-06` | Od braku towaru do rozwiązania | `reviewed` | [Skrót](karty-publiczne/ORPR-INV-06.md) |

### Rozwój sieci i lokalizacji

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-LOC-01` | Od potrzeby lokalizacyjnej do decyzji o portfelu lokalizacji | `reviewed` | [Skrót](karty-publiczne/ORPR-LOC-01.md) |
| `ORPR-LOC-02` | Od decyzji lokalizacyjnej do domkniętej zmiany lokalizacji | `reviewed` | [Skrót](karty-publiczne/ORPR-LOC-02.md) |

### Planowanie i zarządzanie finansami

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-FIN-05` | Od założeń do zatwierdzonego planu finansowego | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-05.md) |
| `ORPR-FIN-06` | Od prognozy przepływów do decyzji o płynności | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-06.md) |
| `ORPR-FIN-07` | Od wyników okresu do wniosków zarządczych | `reviewed` | [Skrót](karty-publiczne/ORPR-FIN-07.md) |

### Pracownicy i kadry

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-HRM-01` | Od potrzeby obsady do zapewnionej obsady | `reviewed` | [Skrót](karty-publiczne/ORPR-HRM-01.md) |
| `ORPR-HRM-02` | Od luki kompetencyjnej do potwierdzonych kompetencji | `reviewed` | [Skrót](karty-publiczne/ORPR-HRM-02.md) |
| `ORPR-HRM-03` | Od zdarzenia zatrudnieniowego do aktualnego stanu zatrudnienia | `reviewed` | [Skrót](karty-publiczne/ORPR-HRM-03.md) |

### Technologia i systemy

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-SYS-01` | Od potrzeby systemowej do udostępnionego systemu | `reviewed` | [Skrót](karty-publiczne/ORPR-SYS-01.md) |
| `ORPR-SYS-02` | Od udostępnionego systemu do potwierdzonej dostępności i bezpieczeństwa | `reviewed` | [Skrót](karty-publiczne/ORPR-SYS-02.md) |
| `ORPR-SYS-03` | Od ryzyka przerwy do przetestowanej gotowości odtworzeniowej | `reviewed` | [Skrót](karty-publiczne/ORPR-SYS-03.md) |

### Prawo i umowy

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-LEG-01` | Od uzgodnionych warunków do prawnie skutecznej umowy | `reviewed` | [Skrót](karty-publiczne/ORPR-LEG-01.md) |
| `ORPR-LEG-02` | Od sprawy prawnej do formalnego zamknięcia | `reviewed` | [Skrót](karty-publiczne/ORPR-LEG-02.md) |

### Zarządzanie i nadzór nad firmą

| ID | Proces | Stan pełnej karty | Dostęp publiczny |
|---|---|---|---|
| `ORPR-GOV-01` | Od potrzeby ustalenia kierunku do zatwierdzonych celów i decyzji | `reviewed` | [Skrót](karty-publiczne/ORPR-GOV-01.md) |
| `ORPR-GOV-02` | Od informacji o wynikach i ryzykach do zamkniętego przeglądu zarządczego | `reviewed` | [Skrót](karty-publiczne/ORPR-GOV-02.md) |
| `ORPR-GOV-03` | Od potrzeby relacji z interesariuszami do zrealizowanych obowiązków relacyjnych | `reviewed` | [Skrót](karty-publiczne/ORPR-GOV-03.md) |
| `ORPR-GOV-04` | Od strategii i szans rozwojowych do zweryfikowanego portfela rozwoju | `reviewed` | [Skrót](karty-publiczne/ORPR-GOV-04.md) |

## Jak korzystać z katalogu

Zacznij od obszaru i otwórz kartę procesu. Skrót pomoże zdecydować, czy temat wymaga pogłębionej
analizy. Pełny zakres ORPR, Regulatory Matrix i sposób kontaktu opisuje
[główny README](../README.md).
