# Przepływ / Oferta handlowa

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem. Karty L1 CAT-01..04 istnieją i mają
własną treść; ta karta OBSZARU nie duplikuje ich pól, tylko szkicuje granice. To najsłabiej pokryty
protokołami obszar standardu: w rejestrze styków ma JEDEN protokół kanoniczny (protokół 4, Sprzedawalność),
i to tylko na odcinku dopuszczenia do sprzedaży. Reszta łańcucha (cena → kasa, promocja → kasa, akcja
handlowa → efekt) NIE ma protokołu kanonicznego i jest tu `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`, do
potwierdzenia polem 2 kart L1.

Dwie twarze obszaru. **Dopuszczenie do sprzedaży** (sprzedawalność pozycji jako warunek koszyka) opiera się
na protokole kanonicznym 4 (reguła regulacyjna z wersją, plan oferty, zamówienie klienta; projekcja
Dopuszczenie do sprzedaży, FAIL-CLOSED), więc mechanizm jest rozstrzygnięty. **Oferta wykonywalna** (cena
regularna, promocja jako część zakresu oferty, pomiar efektu akcji handlowej) NIE ma protokołu kanonicznego
dla łańcucha proces→proces, więc jest tu ZAŁOŻENIEM z opisu bytów i kamieniołomu.

**1. Cel biznesowy:** Doprowadzić decyzję handlową do wykonywalnej oferty w kasie i kanałach: od
wprowadzenia pozycji i jej dopuszczenia do sprzedaży, przez ustalenie ceny regularnej i promocji jako
części zakresu oferty, po pomiar efektu akcji handlowej. Wynik: pozycja dopuszczona w danym zakresie, cena
i promocja gotowe do konsumpcji przy koszyku, a wiedza o skuteczności mechanik zwrócona do kolejnych decyzji
handlowych i do planowania.

**2. Granice:**
- Start: pojawia się decyzja handlowa (wprowadzenie pozycji do asortymentu, ustalenie lub zmiana ceny
  regularnej, uruchomienie promocji albo akcji handlowej) → uruchamia budowę zakresu oferty; albo zmiana
  reguły regulacyjnej z wersją → przelicza dopuszczenie do sprzedaży.
- Koniec: (a) pozycja dopuszczona do sprzedaży w zadanym zakresie (lokalizacje, kanały, czas); (b) cena
  regularna i promocja obowiązują jako część zakresu oferty, gotowe do konsumpcji przy koszyku; (c) efekt
  akcji handlowej zmierzony, a wiedza o mechanikach zwrócona do decyzji handlowych i do planowania.
- NIE obejmuje: naliczenia ceny i korzyści w koszyku oraz finalizacji sprzedaży (→ Przepływ / Realizacja
  sprzedaży; dopuszczenie, cena i promocja konsumowane tam jako warunek koszyka); planowania ilości,
  alokacji i dostępności (→ Przepływ / Plan i dostępność); rozstrzygnięcia zwrotu promocyjnego (kupony,
  punkty) i zwrotu środków (→ Przepływ / Zwrot; → Przepływ / Płatności); naliczania i umarzania punktów
  lojalnościowych (→ Przepływ / Płatności, kandydat); skutku zmiany ceny na wycenie zapasu, rewaluacji
  (→ Proces przekrojowy / Zapas; → Proces przekrojowy / Księga; zależny od modelu wyceny, nie od tej karty); ustanowienia
  i wersjonowania reguły regulacyjnej (wejście, autorytet egzogeniczny).
- Wejście z: planowanie zakresu oferty jest wewnętrzne dla planu oferty i kategorii (główny pisarz stanu
  obszaru); reguła regulacyjna z wersją jako autorytet egzogeniczny (pierścień), konsumowana transakcyjnie.
  Handoff-out: Realizacja sprzedaży (cena i promocja jako wejście koszyka; dopuszczenie do sprzedaży wchodzi
  protokołem byt↔byt, KONSUMOWANE przy koszyku, nie handoffem proces→proces); Plan i dostępność (zapowiedź
  promocji jako sygnał popytu, powiązanie mirror z tamtej karty).

**3. Właściciel:** Zarządzanie ofertą i kategorią (category management / merchandising), ze
współodpowiedzialnością zespołu cen (pricing) na odcinku ceny regularnej oraz zespołu zgodności na odcinku
dopuszczenia do sprzedaży pod regułą regulacyjną z wersją.

**4. Aktorzy:** kupiec kategorii / category manager, specjalista ds. asortymentu i danych pozycji,
specjalista ds. cen (pricing), specjalista ds. promocji i akcji handlowych, specjalista ds. zgodności
(reguła regulacyjna z wersją), analityk efektu akcji handlowej.

**5. Systemy (typy, vendor-neutral):** system zarządzania danymi pozycji (master data / PIM), system planu
oferty i kategorii (offer and category planning), silnik cennika i matrycy marżowej, silnik promocji
i mechanik handlowych, autorytet reguły regulacyjnej z wersją z projekcją Dopuszczenie do sprzedaży (Offer
Eligibility), rejestr nośnika ceny (metka, etykieta półkowa, ekspozycja w kanale), system pomiaru efektu
akcji handlowej (analityka). Karta nie przesądza podziału tych zdolności między aplikacje ani dostawców.

**6. Wyzwalacze:** decyzja o wprowadzeniu pozycji do asortymentu; ustalenie lub zmiana ceny regularnej;
uruchomienie promocji albo akcji handlowej; zmiana reguły regulacyjnej z wersją (przelicza dopuszczenie do
sprzedaży); cykl pomiaru efektu akcji handlowej; wycofanie pozycji i następstwo.

## Uczestnicy L0 (nazwy czytelne)
Plan oferty i kategorii (oferta, plan kategorii, cena regularna, promocja jako część zakresu oferty; główny
pisarz stanu obszaru) · Fakt produktu · Lokalizacja · Reguła regulacyjna z wersją (pierścień, autorytet
egzogeniczny) · Dopuszczenie do sprzedaży (projekcja ⊗ Offer Eligibility, host: plan oferty; nie byt L0) ·
Zamówienie klienta i finalizacja sprzedaży (konsument werdyktu, wyjście do Realizacji sprzedaży) · Licznik
konsumpcji / limit (księga-licznik L1 pod regułą regulacyjną, nie byt L0).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Dwa tory.

Tor dopuszczenia do sprzedaży (protokół kanoniczny 4, rejestr sekcja C.4): reguła regulacyjna z wersją
zmienia się → outbox/ack (gwarancja dostawy) → plan oferty przelicza projekcję Dopuszczenie do sprzedaży
(⊗, host: plan oferty) = f(fakt produktu × lokalizacja × reguła × czas × zakres oferty) → zamówienie
klienta czyta werdykt sprzedawalności FAIL-CLOSED (odrzuca przeterminowany stempel wersji). Licznik
konsumpcji / limit sprawdzany write-through fail-closed, a zdarzenie wydania konsumuje licznik
(check-and-decrement); wyłącznym pisarzem licznika jest księga-licznik pod regułą regulacyjną, zamówienie
klienta go nie inkrementuje. Inwariant sprzedawalności egzekwowany na ścieżce CZYTANIA fail-closed;
projekcja wykrywa po fakcie, nie egzekwuje. Dopuszczenie należy głównie do tego obszaru i jest KONSUMOWANE
w Realizacji sprzedaży jako warunek przy koszyku (protokół byt↔byt, nie handoff proces→proces).

Tor oferty wykonywalnej (ZAŁOŻENIE z opisu bytów i kamieniołomu, bez protokołu kanonicznego): plan oferty
i kategorii jest głównym pisarzem zakresu oferty i składa w nim cenę regularną oraz promocję. Dane pozycji
(z dopuszczenia) są wejściem wyceny i promocji; cena regularna i promocja jako część zakresu oferty zasilają
koszyk jako cena i korzyść, konsumowane w Realizacji sprzedaży. Mechanizm ceny (cennik, matryca marżowa,
nośnik ceny) i promocji (mechanika, okno obowiązywania) NIE jest tu rozstrzygnięty protokołem; szczegół
żyje w kartach L1 CAT-02 i CAT-03. `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`.

Pętla uczenia (akcja handlowa do efektu, CAT-04): pomiar efektu akcji handlowej czyta dane z dopuszczenia,
ceny i promocji, a jego WYNIK (wiedza o skuteczności mechanik) wraca do decyzji handlowych (01/02/03) i do
planowania jako wejście. To PĘTLA UCZENIA (czyta dane, nie oddaje pałeczki), a nie handoff proces→proces.
Mechanizm pomiaru bez protokołu kanonicznego. `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od pozycji do dopuszczenia do sprzedaży · `CAT-01`
- 02 Od ceny do kasy · `CAT-02`
- 03 Od promocji do kasy · `CAT-03`
- 04 Od akcji handlowej do efektu · `CAT-04`

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2 potwierdzającym handoff proces→proces); bez rombów, bez swimlane.
`NN` to numer porządkowy, nie krok sekwencji. Dopuszczenie do sprzedaży (protokół 4, sprzedawalność) to
protokół byt↔byt, więc NIE wchodzi na diagram proces→proces (opis w sekcji „Protokół / przepływ").
Karty L1 CAT-01..04 istnieją, ale wiążą procesy relacją konsumpcji danych (np. dane pozycji jako wejście
wyceny), a nie potwierdzonym polem 2 przekazaniem pałeczki proces→proces; krawędzie wewnętrzne pozostają
więc przerywane. Krawędź handoff-out do Realizacji sprzedaży przerywana (mirror: karta SAL rysuje wejście
z Oferty handlowej jako `⇢`). 04 poza sekwencją (pętla uczenia).
```
01 Od pozycji do dopuszczenia do sprzedaży
        01 ⇢ 02 Od ceny do kasy         ·   dane pozycji jako wejście wyceny (założenie)
        01 ⇢ 03 Od promocji do kasy     ·   dane pozycji jako wejście promocji (założenie)
        02 ⇢ [handoff: Realizacja sprzedaży · cena do koszyka]
        03 ⇢ [handoff: Realizacja sprzedaży · promocja do koszyka]
04 Od akcji handlowej do efektu  ·  wejścia: dane z 01/02/03 (pętla uczenia, nie handoff); wynik ⇢ 01/02/03 i do planowania
Dopuszczenie do sprzedaży (protokół 4, sprzedawalność)  ·  protokół byt↔byt, poza diagramem proces→proces; KONSUMOWANE w Realizacji sprzedaży
```

## Styki L0↔L0 (rejestr sekcja B grupa 3: STK-17..24)
Dopuszczenie: zmiana reguły-z-wersją przelicza projekcję (STK-17, host projekcji: plan oferty); werdykt
sprzedawalności FAIL-CLOSED, odrzuca przeterminowany stempel wersji (STK-18); sprzedawalność = f(fakt
produktu × lokalizacja × reguła × czas × zakres oferty) (STK-19). Wejścia projekcji: zakres oferty i plan
kategorii jako wejście przez projekcję (STK-23); fakt produktu jako referencja (STK-24). Powiązania (należą
bardziej do Realizacji sprzedaży, tu tylko wspomniane): odczyt licznika konsumpcji fail-closed (STK-20)
i wydanie konsumuje licznik, check-and-decrement (STK-21) oraz rozchód on-hand jako komenda do stanu
magazynowego (STK-22). Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Cały tor oferty wykonywalnej bez protokołu kanonicznego (cena → kasa, promocja → kasa, akcja handlowa →
efekt): łańcuch założony z opisu bytów i kamieniołomu, do potwierdzenia polem 2 kart L1 CAT-02, CAT-03,
CAT-04. Charakter krawędzi 01→02/03: relacja konsumpcji danych (dane pozycji jako wejście wyceny i promocji)
kontra handoff proces→proces; do formalizacji polem 2, dziś przerywana. Kompletność fail-closed resolvera
sprzedawalności (STK-18/19/20, rejestr sekcja D poz. 4) oraz outbox/ack dostawy zmiany reguły (STK-17,
rejestr D poz. 5). Mechanizm licznika konsumpcji / limitu jako księgi-licznika pod regułą regulacyjną
(pisarz licznika, check-and-decrement; STK-20/21) i granica wobec Realizacji sprzedaży, gdzie licznik jest
konsumowany przy wydaniu. Pętla uczenia CAT-04: definicja miary efektu, host projekcji pomiaru i sposób
zwrotu wiedzy do 01/02/03 oraz do planowania (czyta dane, nie oddaje pałeczki). Granica handoff-out do
Realizacji sprzedaży (cena i promocja do koszyka) kontra byt↔byt dopuszczenia: do potwierdzenia polem 2 po
obu stronach. Skutek zmiany ceny na wycenie zapasu (rewaluacja) poza tą kartą, zależny od modelu wyceny
(→ Proces przekrojowy / Zapas; → Proces przekrojowy / Księga). Zwrot promocyjny (kupony, punkty) rozstrzygany w Zwrocie
i Płatnościach, nie tu.
