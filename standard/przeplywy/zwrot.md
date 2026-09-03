# Przepływ / Zwrot

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

Obszar SAGA z rozstrzygniętym protokołem koordynacji. Rdzeń (od sprzedaży, przez zwrot fizyczny i zwrot
środków, po rozdysponowanie i uzgodnienie księgi) opiera się na protokole kanonicznym 2 (S3 zwrot,
rejestr sekcja C.2), więc koordynacja sprawy jest rozstrzygnięta. Wewnętrzny łańcuch procesów RTN-01..04
pozostaje założeniem (brak kart L1 z polem 2), a granica anulowania wobec zwrotu jest do potwierdzenia.

**1. Cel biznesowy:** Doprowadzić żądanie odwrócenia sprzedaży do domkniętej sprawy zwrotu: od anulowania
(przed wydaniem) albo zwrotu (po wydaniu), przez przyjęcie fizyczne towaru, zwrot środków i anulowanie
punktów, po rozdysponowanie zwróconego towaru i uzgodnienie skutku w księdze. Wynik: sprawa zwrotu
domknięta bez podwójnego zwrotu środków, skutki nieodwracalne rozwiązane w przód (forward-recovery),
księga uzgodniona.

**2. Granice:**
- Start: pojawia się żądanie anulowania sprzedaży (zwykle przed wydaniem) lub zwrotu (po wydaniu),
  odnoszące się do pierwotnego commitmentu z Realizacji sprzedaży → powstaje sprawa zwrotu z orkiestratorem.
- Koniec: sprawa zwrotu domknięta: zwrot środków wykonany lub skompensowany, towar przyjęty i rozdysponowany,
  punkty/kupony anulowane, a księga uzgodniona (podstan „prowizorycznie zamknięte" ustąpił stanowi ostatecznemu).
- NIE obejmuje: powstania koszyka, zobowiązania klienta i wydania towaru (→ Przepływ / Realizacja sprzedaży,
  wejście); wykonania zwrotu środków po stronie rozliczeń (→ Przepływ / Płatności; orkiestrator zwrotu zleca
  je settlementowi jako komendę, wykonanie poza tą kartą); fizycznego składowania, transferu, wyceny i odpisu
  zapasu poza faktem przyjęcia i granicą rozdysponowania (→ Proces przekrojowy / Zapas); księgowań poza uzgodnieniem
  skutku sprawy zwrotu (→ Proces przekrojowy / Księga); operacyjnego zamknięcia kasy (→ Proces przekrojowy / Rozliczenia kasowe).
- Wejście z: Realizacja sprzedaży (pierwotna sprzedaż i customer commitment, do którego odnosi się zwrot,
  STK-35). Handoff-out (jako komendy orkiestratora, protokół byt↔byt, nie proces→proces): zwrot środków →
  Płatności (settlement, STK-31); przyjęcie fizyczne → Proces przekrojowy / Zapas (on-hand, STK-32); anulowanie punktów/kuponów
  → relacja z klientem (STK-33); skutek księgowy → Proces przekrojowy / Księga (FIN nie-terminalny, STK-34).

**3. Właściciel:** Obsługa zwrotów (returns), ze współodpowiedzialnością Finansów na odcinku zwrotu środków
i uzgodnienia księgi oraz operacji lokalizacji na odcinku przyjęcia i rozdysponowania towaru.

**4. Aktorzy:** operator punktu sprzedaży (przyjęcie anulowania/zwrotu), koordynator sprawy zwrotu
(orkiestrator), specjalista ds. rozliczeń (zwrot środków), pracownik lokalizacji (przyjęcie fizyczne
towaru, rozdysponowanie), kontroler / finanse (uzgodnienie księgi).

**5. Systemy (typy, vendor-neutral):** orkiestrator sprawy zwrotu (silnik sagi z detekcją awarii/timeout
per krok), rejestr rozliczeń (settlement) ze strażnikiem capture-id wspólnym z chargeback, ERP/WMS magazynowy
(przyjęcie zwrotu, on-hand), system relacji z klientem z księgą punktów i kuponami, księga główna z podstanem
prowizorycznym i triggerem reopen, moduł rozdysponowania zwróconego towaru.

**6. Wyzwalacze:** żądanie anulowania sprzedaży (przed wydaniem); żądanie zwrotu (po wydaniu); przyjęcie
fizyczne zwróconego towaru; awaria lub timeout kroku sagi (uruchamia komendę kompensującą lub
forward-recovery); brak uzgodnienia księgi (podstan „prowizorycznie zamknięte"); trigger reopen księgi
przez orkiestratora; decyzja o rozdysponowaniu zwróconego towaru (ponowna sprzedaż, odpis, utylizacja).

## Uczestnicy L0 (nazwy czytelne)
Sprawa zwrotu i orkiestrator sagi · Settlement i strażnik capture-id (wspólny z chargeback) · Stan magazynowy
(on-hand) · Relacja z klientem i księga punktów · Księga · Zamówienie klienta i pierwotny commitment (wejście
z Realizacji sprzedaży).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Sprawa zwrotu odnosi się do pierwotnego commitmentu/transakcji z Realizacji sprzedaży (STK-35, wejście)
i powstaje jako sprawa z ORKIESTRATOREM (protokół kanoniczny 2, S3 zwrot, rejestr sekcja C.2).

Orkiestracja (saga). Orkiestrator sprawy zwrotu jest jedyną władzą komend kompensujących: wykrywa awarie
i timeout per krok, a uczestnicy NIE kompensują sami. Kroki wykonywane są jako komendy do uczestników:
zwrot środków do settlementu (STK-31), przyjęcie fizyczne zwrotu do stanu magazynowego (STK-32), anulowanie
punktów/kuponów do relacji z klientem (STK-33). Ponieważ to protokół byt↔byt (orkiestrator ↔ uczestnik),
kroki te NIE wchodzą na diagram proces→proces; opisane są tutaj.

Strażnik pieniądza (idempotencja). Zwrot środków i idempotencja opierają się na CAPTURE-ID wspólnym z torem
chargeback: settlement prowadzi kwotę-zwróconą-per-capture, a zwrot środków i chargeback rezerwują wobec
remaining-returnable, więc nie dochodzi do podwójnego zwrotu środków (STK-31).

Skutki nieodwracalne. Tam, gdzie kroku nie da się cofnąć (np. rozdysponowany towar, zdarzenie po stronie
klienta), sprawa idzie w pivot / forward-recovery, nie w rollback.

Księga nie-terminalna. Skutek księgowy jest niezakończony: sprawa NIE osiąga stanu ostatecznego, dopóki
księga nie uzgodni (podstan „prowizorycznie zamknięte"). Księga ma trigger reopen uruchamiany przez
orkiestratora (STK-34), więc uzgodnienie księgi jest ostatnią bramą domknięcia sprawy.

Rozdysponowanie. Co dalej ze zwróconym towarem (ponowna sprzedaż, odpis, utylizacja) rozstrzyga proces
rozdysponowania (RTN-04); granica wobec Proces przekrojowy / Zapas (przyjęcie, odpis, transfer) jest do formalizacji
`[ZAŁOŻENIE z opisu bytów i kamieniołomu]`.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od sprzedaży do anulowania · `RTN-01`
- 02 Od sprzedaży do zwrotu · `RTN-02`
- 03 Od zwrotu do zwrotu środków · `RTN-03`
- 04 Od zwrotu do rozdysponowania · `RTN-04`

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok
sekwencji. Komendy orkiestratora do settlementu, zapasu i księgi (saga, protokół 2) to protokół byt↔byt,
więc NIE wchodzą na diagram proces→proces (opis w sekcji „Protokół / przepływ"). Krawędź wejścia z Realizacji
sprzedaży przerywana (źródło nie deklaruje handoffu do Zwrotu; sprawa zwrotu odnosi się do pierwotnego
commitmentu przez STK-35, to referencja, nie potwierdzone przekazanie); krawędzie wewnętrzne przerywane
(karty L1 RTN-01..04 jeszcze nie istnieją). 01 jako osobna ścieżka (anulowanie, zwykle przed wydaniem);
02 rozgałęzia się na 03 i 04.
```
[z: Realizacja sprzedaży · pierwotny commitment] ⇢ 01 Od sprzedaży do anulowania   ·   osobna ścieżka (anulowanie przed wydaniem)
[z: Realizacja sprzedaży · pierwotny commitment] ⇢ 02 Od sprzedaży do zwrotu
                                                    02 ⇢ 03 Od zwrotu do zwrotu środków ─▶ [wynik: sprawa zwrotu domknięta, księga uzgodniona]
                                                    02 ⇢ 04 Od zwrotu do rozdysponowania   ·   [wynik: towar rozdysponowany; granica wobec Proces przekrojowy / Zapas]
granica 01 vs 02 (anulowanie przed wydaniem / zwrot po wydaniu) = [ZAŁOŻENIE z opisu bytów i kamieniołomu]
```

## Styki L0↔L0 (rejestr sekcja B grupa 5: STK-31..35)
Saga S3, orkiestrator sprawy zwrotu jako jedyna władza komend kompensujących. Zwrot środków: orkiestrator →
settlement, strażnik capture-id wspólny z chargeback, remaining-returnable, brak podwójnego zwrotu środków
(STK-31, komenda). Przyjęcie fizyczne: orkiestrator → stan magazynowy, zwrot fizyczny → on-hand (STK-32,
komenda). Anulowanie punktów/kuponów: orkiestrator → relacja z klientem (STK-33, komenda). Księga
nie-terminalna: orkiestrator ↔ księga, podstan „prowizorycznie zamknięte", trigger reopen przez orkiestratora
(STK-34, zdarzenie). Odniesienie do pierwotnej transakcji: orkiestrator → zamówienie klienta, sprawa zwrotu
odnosi się do pierwotnego commitmentu/transakcji (STK-35, wejście z Realizacji sprzedaży). Pełne brzmienie,
typy i protokół 2: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Inwentarz komend kompensacji orkiestratora sprawy zwrotu (rejestr sekcja D poz. 1) i klucz idempotencji
(capture-id plus operation-id, rejestr sekcja D poz. 2): brak podwójnego zwrotu środków na wspólnym torze
z chargeback. Reconciliation „przyjęte, jeszcze nieuzgodnione w księdze" oraz warunek domknięcia przez
podstan „prowizorycznie zamknięte" i trigger reopen (STK-34). Katalog skutków nieodwracalnych kwalifikujących
się do pivot / forward-recovery (nie rollback). Granica anulowania (RTN-01) wobec zwrotu (RTN-02): anulowanie
zwykle przed wydaniem/fiskalizacją (odwrócenie transakcji), zwrot po wydaniu (towar wraca); rozstrzygnięcie
kryterium `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`. Rozdysponowanie (RTN-04): ponowna sprzedaż, odpis,
utylizacja i granica wobec Proces przekrojowy / Zapas (przyjęcie `INV-01`, odpis `INV-04`, transfer `INV-02`); wołanie
procesu przekrojowego do formalizacji. Kryterium podziału i potwierdzenie łańcucha RTN-01..04 polem 2 kart L1
(obecnie założenie z opisu bytów i kamieniołomu).
