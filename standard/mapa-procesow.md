# Mapa procesów ORPR (nawigacja)

Status: publiczna mapa nawigacyjna wydania `v0.1.x`, zatwierdzona przez właściciela standardu.
Obejmuje 74 procesy w 22 obszarach oraz jednego kandydata bez nadanego identyfikatora.

To jest warstwa nawigacyjna: spis obszarów i procesów, a nie diagram kolejności wykonania.
Przekazania między procesami, bramki i wywołania procesów przekrojowych są opisane w kartach oraz
w [`rejestrze styków L0`](mapowania/rejestr-stykow-L0.md).

Notacja identyfikatorów jest zamrożona od `v0.1.0`. Kody domen, takie jak `CAT` i `SAL`, są częścią
stabilnego identyfikatora technicznego; obszary poniżej służą do nawigacji biznesowej.

## A. Zasady notacji

Gramatyka ścieżki procesu:

```
<rodzaj> / <obszar> / <NN> · <Od X do Y> · <stałe ID techniczne>
rodzaj ∈ { Przepływ, Proces przekrojowy }
```

Reguły:

1. Obszar identyfikujemy nazwą, nie numerem. Dzięki temu adres jest czytelny bez dodatkowego klucza,
   np. `Zakupy i płatności dla dostawców / 01` albo `Księgowość / 01`.
2. `NN` to dwucyfrowy numer porządkowy w obszarze, NIE krok sekwencji. Nadawany zgodnie
   z naturalną kolejnością tam, gdzie istnieje. Kolejność wykonania pokazują strzałki i handoffy,
   nie numer.
3. Nazwa procesu ma formę zdania `Od X do Y` (np. `Od zapotrzebowania do zamówienia`). Strzałka `→`
   oznacza wyłącznie przekazanie między procesami, dlatego nie występuje wewnątrz nazwy procesu.
4. Proces ma jedno miejsce główne na mapie; inne obszary linkują, nie duplikują.
5. Stałe ID techniczne (`ORPR-CAT-04`, na mapie skrót `CAT-04`) jest stabilne — przeniesienie
   procesu między obszarami go NIE zmienia. To NIE jest alias historyczny: to trwały identyfikator
   używany w plikach, odwołaniach i automatyzacji. Adres nawigacyjny (`Oferta handlowa / 04`) może
   się zmienić po przebudowie mapy; stałe ID techniczne — nie.
6. Kody bytów (`LEX`, `SFT`, `FIN`...) NIE wchodzą do ścieżki nawigacyjnej; żyją w modelu
   technicznym (rejestr styków), na mapie najwyżej jako opcjonalny tag.
7. Kandydat bez zatwierdzonej granicy nie dostaje numeru ani stałego ID: `Kandydat · <nazwa>`.
8. Dwie kategorie procesów to „Przepływy biznesowe" i „Procesy przekrojowe"; w ścieżce rodzaj to
   „Przepływ" albo „Proces przekrojowy".
9. Stałe ID techniczne są niezmienne od `v0.1.0`. Zmiana wymaga nowego wydania i jawnego oznaczenia
   wycofywanego identyfikatora.

Trójpodział znaczeń (sedno czytelności):

| Pytanie | Odpowiada |
|---|---|
| Który to stabilny obiekt standardu? | stałe ID techniczne `ORPR-CAT-04` |
| Gdzie go znajdę na aktualnej mapie? | ścieżka `Oferta handlowa / 04` |
| Co ten proces robi? | `Od akcji handlowej do efektu` |

## B. Mapa procesów

Adres czytelny dla człowieka składa się z nazwy obszaru i `NN` przy procesie. Skrót w nawiasie po
nazwie to stałe ID techniczne bez prefiksu `ORPR-`. Znacznik `(#n)` przy nagłówku jest numerem
porządkowym obszaru w tym wydaniu i nie jest częścią adresu nawigacyjnego.

### Przepływy biznesowe

**Zakupy i płatności dla dostawców** (#1)
- 01 Od zapotrzebowania do zamówienia · `PRC-01`
- 02 Od dokumentu dostawy do przyjęcia · `PRC-02`
- 03 Od faktury do zobowiązania · `PRC-03`
- 04 Od zobowiązania do zapłaty · `FIN-04`
- 05 Od warunków handlowych do rozliczenia korzyści pozafakturowych · `PRC-04`

**Planowanie i dostępność** (#2)
- 01 Od popytu do zapotrzebowania netto · `DEM-01`
- 02 Od zapotrzebowania do zakupu (ścieżka ręczna) · `DEM-02`
- 03 Od sygnału popytu do prognozy · `DEM-03`
- 04 Od ograniczeń do alokacji · `DEM-04`
- 05 Od stanu zapasu do obiecywalnej dostępności · `DEM-05`

**Oferta handlowa** (#3)
- 01 Od pozycji do dopuszczenia do sprzedaży · `CAT-01`
- 02 Od ceny do kasy · `CAT-02` *(status: `released`)*
- 03 Od promocji do kasy · `CAT-03`
- 04 Od akcji handlowej do efektu · `CAT-04`

**Realizacja sprzedaży** (#4)
- 01 Od koszyka do sprzedaży · `SAL-01` *(status: `released`)*
- 02 Od sprzedaży do dokumentu fiskalnego · `SAL-02`
- 03 Od sprzedaży do wydania towaru · `SAL-03`

**Płatności klientów** (#5)
- 01 Od kwoty do formy płatności · `PAY-01`
- 02 Od autoryzacji do przechwycenia · `PAY-02`
- 03 Od przechwyconych płatności do rozliczenia partii z operatorem · `PAY-03`

**Zwroty** (#6)
- 01 Od sprzedaży do anulowania · `RTN-01`
- 02 Od sprzedaży do zwrotu · `RTN-02`
- 03 Od zwrotu do zwrotu środków · `RTN-03`
- 04 Od zwrotu do rozdysponowania · `RTN-04`

**Sprzedaż internetowa i na odległość** (#13)
- 01 Od złożonego zamówienia zdalnego do przyjętego zamówienia klienta · `ORD-01`
- 02 Od przesyłki gotowej do ostatniej mili do potwierdzonego wyniku dostawy · `DLV-01`

**Obsługa klienta i reklamacje** (#14)
- 01 Od zgłoszonej sprawy klienta do przekazanego rozstrzygnięcia · `SVC-01`

### Procesy przekrojowe

**Zapas** (#7)
- 01 Od przyjęcia do dostępności · `INV-01`
- 02 Od transferu do przyjęcia · `INV-02`
- 03 Od inwentaryzacji do korekty · `INV-03`
- 04 Od straty do odpisu · `INV-04`
- 05 Od przyjętego zamówienia do rezerwacji zapasu · `INV-07`
- 06 Od rozbieżności przesunięcia do uzgodnienia · `INV-08`
- 07 Od zdarzeń zapasowych do wiarygodnego stanu · `INV-09`

**Księgowość** (#8)
- 01 Od sprzedaży do księgi · `FIN-01`
- 02 Od zapasu do kosztu własnego · `FIN-02`
- 03 Od podatku do zobowiązania · `FIN-03`

**Rozliczanie kas i utargu** (#9)
- 01 Od otwarcia do zamknięcia kasy · `CSH-01`
- 02 Od gotówki do wpłaty · `CSH-02`
- 03 Od przechwyconych płatności kartą do uzgodnienia wpływów dnia · `CSH-03`
- 04 Od rozliczenia do banku · `CSH-04`

**Kontrola i zgodność** (#10)
- 01 Od transakcji do uzgodnienia · `CTL-01`
- 02 Od wyjątku do rozwiązania · `CTL-02`
- 03 Od zdarzenia do audytu · `CTL-03`
- 04 Od planu kontroli do zarejestrowanej niezgodności · `CTL-04`

**Zarządzanie asortymentem i dostawcami** (#11)
- 01 Od potrzeby pozyskania do warunków handlowych · `SUP-01`
- 02 Od potrzeby zmiany asortymentu do decyzji i danych produktu · `AST-01`
- 03 Od kierunku do strategii kategorii · `AST-02`
- 04 Od zobowiązań dostawcy do pełnego rozliczenia · `SUP-02`
- 05 Od potrzeby ekspozycji do planu przestrzeni i ekspozycji · `AST-03`

**Logistyka sieci** (#12)
- 01 Od zlecenia transportu do potwierdzonego odbioru · `LOG-01`
- 02 Od wymagań magazynu do gotowości operacyjnej magazynu · `LOG-02`

**Marketing i relacje z klientami** (#15)
- 01 Od kontaktu z klientem do mierzalnej relacji · `CRM-01`
- 02 Od celu komunikacyjnego do zmierzonego efektu kampanii · `MKT-01`
- 03 Od potrzeby marki do zatwierdzonego standardu · `BRD-01`
- Kandydat · Program lojalnościowy: naliczanie i umarzanie punktów *(bez numeru i stałego ID do
  czasu zatwierdzenia początku, wyniku i granicy procesu)*.

**Operacje i utrzymanie lokalizacji** (#16)
- 01 Od uzupełnienia do półki · `INV-05`
- 02 Od braku towaru do rozwiązania · `INV-06`

**Rozwój sieci i lokalizacji** (#17)
- 01 Od potrzeby lokalizacyjnej do decyzji o portfelu lokalizacji · `LOC-01`
- 02 Od decyzji lokalizacyjnej do domkniętej zmiany lokalizacji · `LOC-02`

**Planowanie i zarządzanie finansami** (#18)
- 01 Od założeń do zatwierdzonego planu finansowego · `FIN-05`
- 02 Od prognozy przepływów do decyzji o płynności · `FIN-06`
- 03 Od wyników okresu do wniosków zarządczych · `FIN-07`

**Pracownicy i kadry** (#19)
- 01 Od potrzeby obsady do zapewnionej obsady · `HRM-01`
- 02 Od luki kompetencyjnej do potwierdzonych kompetencji · `HRM-02`
- 03 Od zdarzenia zatrudnieniowego do aktualnego stanu zatrudnienia · `HRM-03`

**Technologia i systemy** (#20)
- 01 Od potrzeby systemowej do udostępnionego systemu · `SYS-01`
- 02 Od udostępnionego systemu do potwierdzonej dostępności i bezpieczeństwa · `SYS-02`
- 03 Od ryzyka przerwy do przetestowanej gotowości odtworzeniowej · `SYS-03`

**Prawo i umowy** (#21)
- 01 Od uzgodnionych warunków do prawnie skutecznej umowy · `LEG-01`
- 02 Od sprawy prawnej do formalnego zamknięcia · `LEG-02`

**Zarządzanie i nadzór nad firmą** (#22)
- 01 Od potrzeby ustalenia kierunku do zatwierdzonych celów i decyzji · `GOV-01`
- 02 Od informacji o wynikach i ryzykach do zamkniętego przeglądu zarządczego · `GOV-02`
- 03 Od potrzeby relacji z interesariuszami do zrealizowanych obowiązków relacyjnych · `GOV-03`
- 04 Od strategii i szans rozwojowych do zweryfikowanego portfela rozwoju · `GOV-04`

## C. Kontrola liczb

Liczby poniżej wynikają bezpośrednio z sekcji B tego pliku.

- Przepływy biznesowe (8 obszarów): 5 + 5 + 4 + 3 + 3 + 4 + 2 + 1 = **27 procesów**
  (#1: 5, #2: 5, #3: 4, #4: 3, #5: 3, #6: 4, #13: 2, #14: 1).
- Procesy przekrojowe (14 obszarów): 7 + 3 + 4 + 4 + 5 + 2 + 3 + 2 + 2 + 3 + 3 + 3 + 2 + 4 =
  **47 procesów** (#7: 7, #8: 3, #9: 4, #10: 4, #11: 5, #12: 2, #15: 3, #16: 2, #17: 2, #18: 3,
  #19: 3, #20: 3, #21: 2, #22: 4).
- Razem: **74 istniejące + 1 kandydat** (program lojalnościowy, obszar #15).
- Kandydat lojalnościowy wymaga początku, wyniku i granicy
  wobec Oferty handlowej / Realizacji sprzedaży / Płatności klientów zanim dostanie numer.

## D. Znaczenie linii i układ mapy (semantyka wizualna)

Reguły wizualne dla diagramów obszarów:

1. Linia ciągła — przekazanie POTWIERDZONE w karcie procesu (pole 2 „komu oddaje pałeczkę").
2. Linia przerywana — propozycja przekazania WYMAGAJĄCA walidacji (hipoteza z silnika/rejestru styków).
3. Brak linii — relacja lub miejsce w sekwencji NIE zostały potwierdzone.
4. Proces należący do obszaru, ale bez potwierdzonego przekazania, zostaje na osobnej PÓŁCE
   wewnątrz obszaru. Nie łączymy go linią hipotetyczną.
5. Procesy przekrojowe NIE mają na mapie globalnej linii do przepływów biznesowych. Użycie procesu
   przekrojowego przez konkretny proces pokazujemy dopiero w widoku obszaru lub procesu, po potwierdzeniu
   w kartach.
6. Bez rombów BPMN i bez swimlane'ów po bytach. Mapa pozostaje na poziomie proces–proces i ma być
   czytelna bez klucza domen.

Ta mapa nie rysuje sekwencji. Potwierdzone i proponowane przekazania można analizować w opisach
przepływów oraz w rejestrze styków L0.

## E. Relacja do modelu technicznego

- Byty L0 (16), styki (`STK-01..44`) i projekcje opisuje
  [`rejestr styków L0`](mapowania/rejestr-stykow-L0.md).
- Karta procesu wiąże się z bytami po NAZWIE w polu uczestników; kody bytów nie wchodzą do ścieżki.
- Opisy przepływów łączą procesy, bramki i wywołania procesów przekrojowych na poziomie
  odpowiednim dla publicznego wydania.

---
