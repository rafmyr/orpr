# Proces przekrojowy / Kontrola i zgodność

Karta szkieletowa procesu przekrojowego (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + wołania z przepływów + styki + dług L1. Głębia (pola 7-14, bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

Proces przekrojowy, nie przepływ: jest WOŁANY przez przepływy i sam orkiestruje remediację wobec ich właścicieli. Autorytet zgodności jest PIERŚCIENIEM (ta sama klasa co `Proces przekrojowy / Księga`), przekrojowym wobec całości: EMITUJE regułę-z-wersją do wszystkich bytów L0 i ORKIESTRUJE remediację (nazwana rola z kompensacją, jak orkiestrator zwrotu). Strona REGUŁY SPRZEDAWALNOŚCI (emisja reguły-z-wersją, po której plan oferty przelicza dopuszczenie do sprzedaży) należy do `Przepływ / Oferta handlowa` (protokół 4); TU jest strona KONTROLI: uzgodnienie transakcji, obsługa wyjątku i remediacji jako orkiestrowanej sprawy oraz ślad audytowy zdarzeń zgodności. Uwaga zakresowa: „zgodność" znaczy tu compliance ogólny (polityki, reguły, obowiązki, audyt), nie regulacja sektorowa. Uzgodnienie transakcji (CTL-01) nie ma dedykowanego protokołu kanonicznego i jest tu `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`, kotwiczone w zdarzeniach zgodności.

**1. Cel biznesowy:** Utrzymać zgodność i rozliczalność całości procesów: doprowadzić transakcję do uzgodnienia wobec księgi i rozliczeń, wyjątek do rozwiązania przez orkiestrowaną remediację, a zdarzenie zgodności do udokumentowanego śladu audytowego. Wynik: reguła-z-wersją dostępna jako autorytet egzogeniczny do transakcyjnej konsumpcji przez wszystkie byty, transakcje uzgodnione, sprawy remediacji domknięte (skutki wykonane przez właścicieli procesów), a zdarzenia zgodności i findingi zebrane w compliance case ze śladem audytowym.

**2. Granice:**
- Start: pojawia się zdarzenie zgodności lub finding z dowolnego bytu L0 (zasila compliance case); albo rozbieżność transakcji wymagająca uzgodnienia; albo wyjątek wymagający remediacji (otwiera orkiestrowaną sprawę); albo zmiana reguły-z-wersją (emisja do wszystkich bytów).
- Koniec: (a) transakcja uzgodniona wobec księgi i rozliczeń; (b) sprawa remediacji domknięta (skutki wykonane przez właścicieli procesów lub skompensowane); (c) zdarzenie zgodności udokumentowane w compliance case i utrwalone w śladzie audytowym.
- NIE obejmuje: strony reguły sprzedawalności, czyli emisji reguły-z-wersją, po której plan oferty przelicza dopuszczenie do sprzedaży (→ `Przepływ / Oferta handlowa`, protokół 4; TU wyłącznie strona kontroli, remediacji i audytu); księgowań i wyceny skutku poza uzgodnieniem transakcji (→ `Proces przekrojowy / Księga`); wykonania skutków remediacji po stronie właścicieli procesów (autorytet zgodności zleca je komendą, wykonanie żyje w domenach właścicieli, poza tą kartą, jak w sadze zwrotu); merytorycznego ustanowienia treści polityki i reguły (autorytet egzogeniczny; TU konsumpcja transakcyjna i egzekwowanie zgodności).
- Wołana przez: wszystkie przepływy i procesy przekrojowe konsumują regułę-z-wersją jako autorytet egzogeniczny (STK-36, konsumpcja transakcyjna, kryterium K4) oraz emitują zdarzenia zgodności i findingi do compliance case (STK-38).
- Zwraca do wołającego: werdykt reguły-z-wersją do transakcyjnej konsumpcji na ścieżce czytania fail-closed (przeterminowany stempel wersji odrzucany po stronie czytelnika) oraz potwierdzenie przyjęcia zdarzenia do compliance case (ack). Ponadto, jako pierścień, autorytet zgodności EMITUJE regułę-z-wersją do wszystkich bytów L0 (STK-36) i ORKIESTRUJE remediację wobec właścicieli procesów (STK-37; skutki wykonują właściciele L0, nie sam pierścień, jak orkiestrator zwrotu).

**3. Właściciel:** Zespół zgodności (compliance), ze współodpowiedzialnością Finansów na odcinku uzgodnienia transakcji wobec księgi i rozliczeń oraz z ról audytu/kontroli na odcinku śladu audytowego. Remediacją steruje autorytet zgodności jako orkiestrator; skutki wykonują właściciele poszczególnych procesów.

**4. Aktorzy:** specjalista ds. zgodności (compliance), właściciel polityki i reguły-z-wersją, koordynator remediacji (orkiestrator sprawy), kontroler / audytor (uzgodnienie transakcji, ślad audytowy), właściciele procesów jako wykonawcy skutków remediacji.

**5. Systemy (typy, vendor-neutral):** autorytet reguły-z-wersją (polityka, wersjonowana reguła, obowiązek; egzogeniczny, konsumowany transakcyjnie fail-closed), rejestr compliance case (zdarzenia zgodności, findingi, ack), orkiestrator remediacji (silnik sprawy z detekcją awarii/timeout per krok i legiem kompensacji, jak saga), silnik uzgodnień transakcji wobec księgi i rozliczeń (reconciliation, `[ZAŁOŻENIE]` bez protokołu kanonicznego), rejestr śladu audytowego (niezmienny dziennik zdarzeń zgodności). Karta nie przesądza podziału tych zdolności między aplikacje ani dostawców.

**6. Wyzwalacze:** zmiana reguły-z-wersją (emisja jako autorytet egzogeniczny do wszystkich bytów); pojawienie się zdarzenia zgodności lub findingu (zasila compliance case); rozbieżność w uzgodnieniu transakcji wobec księgi lub rozliczeń; otwarcie wyjątku wymagającego remediacji; awaria lub timeout kroku remediacji (komenda kompensująca lub forward-recovery); cykl audytu lub żądanie śladu audytowego.

## Uczestnicy L0 (nazwy czytelne)
Autorytet zgodności i compliance case (polityka, reguła-z-wersją, obowiązek, remediacja; pierścień i orkiestrator remediacji) · Wszystkie byty L0 jako konsumenci reguły-z-wersją i emitenci zdarzeń zgodności i findingów · Księga (uzgodnienie skutku transakcji; pierścień) · Settlement i rozliczenia (transakcje do uzgodnienia) · Właściciele procesów jako wykonawcy skutków remediacji (wykonują sami na komendę orkiestratora, jak w sadze zwrotu).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Autorytet zgodności jest pierścieniem przekrojowym wobec całości. Cztery odcinki.

Reguła-z-wersją jako autorytet egzogeniczny (STK-36, autorytet fail-closed, kryterium K4). Autorytet zgodności EMITUJE regułę-z-wersją, a wszystkie byty L0 konsumują ją transakcyjnie na ścieżce czytania (przeterminowany stempel wersji odrzucany po stronie czytelnika). Strona sprzedawalności tego samego pierścienia (emisja reguły → plan oferty przelicza projekcję dopuszczenia do sprzedaży) należy do `Przepływ / Oferta handlowa` (protokół 4, sprzedawalność); TU pierścień występuje jako autorytet egzogeniczny konsumowany transakcyjnie przez wszystkie byty, a nie jako tor przeliczenia dopuszczenia.

Remediacja orkiestrowana (STK-37, komenda, jak saga zwrotu). Autorytet zgodności jest ORKIESTRATOREM remediacji: nazwana rola z legiem kompensacji, wykrywa awarie i timeout per krok, jest jedyną władzą komend kompensujących. Skutki wykonują WŁAŚCICIELE procesów (byty L0), nie sam pierścień, dokładnie jak w sadze zwrotu (orkiestrator zleca, uczestnicy wykonują i nie kompensują sami). Ponieważ to protokół byt↔byt (orkiestrator ↔ właściciel procesu), remediacja NIE wchodzi na diagram proces→proces; opisana jest tutaj.

Compliance case zasilany findingami (STK-38, zdarzenie). Wszystkie byty L0 emitują zdarzenia zgodności i findingi, konsumowane idempotentnie (ack) do compliance case. Case jest kotwicą śladu audytowego (CTL-03, „Od zdarzenia do audytu").

Uzgodnienie transakcji (CTL-01, „Od transakcji do uzgodnienia"). Reconciliation transakcji wobec księgi i rozliczeń. Brak dedykowanego protokołu kanonicznego; mechanizm kotwiczony w zdarzeniach zgodności (STK-38) i w uzgodnieniu wobec księgi i settlementu. `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od transakcji do uzgodnienia · `CTL-01`
- 02 Od wyjątku do rozwiązania · `CTL-02`
- 03 Od zdarzenia do audytu · `CTL-03`

## Wołania z przepływów (kto woła ten proces przekrojowy)
Proces przekrojowy wobec wszystkich przepływów i procesów przekrojowych, przez pierścień autorytetu zgodności. Trzy kanały:
- Reguła-z-wersją: autorytet zgodności → wszystkie byty L0 (STK-36, autorytet egzogeniczny konsumowany transakcyjnie fail-closed, kryterium K4). Wszyscy wołający czytają werdykt reguły przy transakcji.
- Zdarzenia zgodności i findingi: byty L0 → autorytet zgodności (STK-38, zdarzenie zasilające compliance case). Wołający emitują, case konsumuje idempotentnie (ack).
- Remediacja: autorytet zgodności → właściciele procesów (STK-37, komenda orkiestrowanej sprawy). Wychodzi z pierścienia do właścicieli; skutki wykonują właściciele L0 (jak w sadze zwrotu), pierścień orkiestruje z legiem kompensacji.
Strona reguły sprzedawalności (emisja → przeliczenie dopuszczenia w planie oferty) jest wołaniem obsługiwanym w `Przepływ / Oferta handlowa` (protokół 4), nie tutaj.

## Diagram (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii (rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok sekwencji. Emisja reguły-z-wersją (STK-36) i remediacja orkiestrowana (STK-37) to protokoły byt↔byt (pierścień/orkiestrator ↔ byty), więc NIE wchodzą na diagram proces→proces; opis w sekcji „Protokół / przepływ". Węzły CTL-01..03 pozostają raczej niezależne (osobne półki): brak potwierdzonego polem 2 przekazania pałeczki między nimi, więc żadnej krawędzi proces→proces nie rysujemy jako ciągłej. Kotwica CTL-01 (uzgodnienie) bez protokołu kanonicznego pozostaje przerywana.
```
01 Od transakcji do uzgodnienia   ·   osobna półka; reconciliation wobec księgi i rozliczeń  ⇢  [ZAŁOŻENIE: brak protokołu kanonicznego; kotwica w zdarzeniach zgodności]
02 Od wyjątku do rozwiązania      ·   osobna półka; remediacja jako orkiestrowana sprawa (byt↔byt, poza diagramem proces→proces; skutki wykonują właściciele procesów)
03 Od zdarzenia do audytu         ·   osobna półka; compliance case zasilany findingami, ślad audytowy
pierścień: reguła-z-wersją do wszystkich L0 (STK-36) oraz remediacja do właścicieli procesów (STK-37)  ·  protokół byt↔byt, poza diagramem proces→proces
```

## Styki L0↔L0 (rejestr sekcja B grupa 6: STK-36..38)
Pierścień regulacji i remediacji, autorytet zgodności jako orkiestrator. Reguła-z-wersją: autorytet zgodności → wszystkie byty L0, autorytet egzogeniczny konsumowany transakcyjnie (STK-36, autorytet fail-closed, kryterium K4; status [OPIS]). Remediacja: autorytet zgodności → właściciele procesów, orkiestrowana sprawa, skutki wykonują właściciele L0 jak w sadze zwrotu (STK-37, komenda; status [OPIS]). Findingi: byty L0 → autorytet zgodności, zdarzenia zgodności i findingi zasilające compliance case (STK-38, zdarzenie; status [PROP+ 24.08]). Odgraniczenie: strona reguły sprzedawalności (STK-17/18/19, protokół kanoniczny 4) należy do `Przepływ / Oferta handlowa`; TU strona kontroli, remediacji i audytu. Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Mechanizm uzgodnienia transakcji (CTL-01) bez protokołu kanonicznego: reconciliation wobec księgi i rozliczeń, kotwica w zdarzeniach zgodności (STK-38), do potwierdzenia polem 2 karty L1; dziś `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`. Inwentarz komend kompensacji orkiestratora remediacji (rejestr sekcja D poz. 1) i klucz idempotencji (capture-id plus operation-id, rejestr sekcja D poz. 2) dla sprawy remediacji (STK-37). Outbox/ack dostawy reguły-z-wersją jako autorytetu egzogenicznego do wszystkich bytów (STK-36; mechanizm pokrewny STK-17 z rejestru D poz. 5, tu w wariancie „do wszystkich L0"). Idempotentna konsumpcja findingów (ack) do compliance case (STK-38) i definicja niezmiennego śladu audytowego (CTL-03) oraz jego granica wobec compliance case. Granica strony reguły (sprzedawalność, `Przepływ / Oferta handlowa`, protokół 4) wobec strony kontroli (uzgodnienie, remediacja, audyt): do potwierdzenia polem 2 po obu stronach. Charakter styków: STK-36/37 [OPIS], STK-38 [PROP+ 24.08]; potwierdzenie i domknięcie mechanizmów polem 2 kart L1 CTL-01..03 (obecnie założenie z opisu bytów i kamieniołomu).
