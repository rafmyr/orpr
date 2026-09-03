# Przepływ / Zakup do zapłaty

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

**1. Cel biznesowy:** Doprowadzić potrzebę zakupu do rozliczonej płatności wobec dostawcy: od
zamówienia, przez przyjęcie towaru i dopasowanie trójstronne, do zwolnienia zobowiązania i jego
zapłaty, z rozliczeniem należnych rabatów retro.

**2. Granice:**
- Start: istnieje zatwierdzone zapotrzebowanie oraz warunki kontraktowe z dostawcą → powstaje zamówienie.
- Koniec: dostawca opłacony, zobowiązanie zamknięte w księdze, rabaty retro rozliczone.
- NIE obejmuje: planowania ilości i alokacji (→ Przepływ / Plan i dostępność); negocjacji i zawarcia
  kontraktu z dostawcą (wejście); fizycznego składowania i wyceny zapasu poza faktem przyjęcia
  (→ Proces przekrojowy / Zapas); księgowań poza rozrachunkami zakupu (→ Proces przekrojowy / Księga).
- Wejście z: Plan i dostępność (zapotrzebowanie). Handoff-out: brak w obrębie przepływów biznesowych
  (rezultat terminalny: dostawca opłacony); rozrachunki i płatność korzystają z Proces przekrojowy / Księga
  oraz Proces przekrojowy / Rozliczenia kasowe.

**3. Właściciel:** Zakupy (procurement), ze współodpowiedzialnością Finansów na odcinku
zobowiązanie → zapłata.

**4. Aktorzy:** kupiec, magazynier (przyjęcie), specjalista ds. zobowiązań, kontroler/finanse,
specjalista ds. rabatów retro.

**5. Systemy (typy, vendor-neutral):** ERP zakupowy (zamówienia), WMS/ERP magazynowy (przyjęcia,
stan), silnik dopasowania trójstronnego, księga główna z rozrachunkami dostawców, moduł płatności
/ treasury, moduł rabatów retro.

**6. Wyzwalacze:** zatwierdzone zapotrzebowanie; harmonogram zamówień; próg zapasu (z planu);
przyjęcie dostawy (uruchamia dopasowanie); termin płatności (uruchamia wypłatę); okresowe naliczenie
rabatu retro.

## Uczestnicy L0 (nazwy czytelne)
Dostawca i kontrakt · Zamówienie zakupowe · Stan magazynowy i przyjęcia · Zobowiązanie do zapłaty ·
Księga · Płatności i rozliczenia · Rabaty retro.
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Zamówienie → przyjęcie towaru (fakt) → dopasowanie trójstronne (zamówienie × przyjęcie × faktura,
arbiter rozbieżności) → zwolnienie do zapłaty → payable i naliczenie (accrual) w księdze → wypłata
„opłacone". Zdarzenie zapłaty zamyka zobowiązanie i pozycję w księdze (samozamknięcie, moduł
płatności nie modyfikuje ich stanu). Rabaty retro czytają warunki dostawcy i zrealizowane wolumeny,
rozliczają się osobnym dokumentem (nie schodzą na cenę zakupu).

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od zapotrzebowania do zamówienia · `PRC-01`
- 02 Od dokumentu dostawy do przyjęcia · `PRC-02`
- 03 Od faktury do zobowiązania · `PRC-03`
- 04 Od zobowiązania do zapłaty · `FIN-04`
- 05 Od warunków handlowych do rozliczenia korzyści pozafakturowych · `PRC-04`

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. Krawędź wejścia z „Plan i dostępność"
ciągła (pole 2 tej karty); krawędzie wewnętrzne 01→04 przerywane (karty L1 PRC-01..05 jeszcze nie
istnieją). 05 poza sekwencją (czyta dane z 01 i 03, nie dostaje pałeczki).
```
[z: Plan i dostępność] ─▶ 01 Od zapotrzebowania do zamówienia
                          01 ⇢ 02 Od dokumentu dostawy do przyjęcia
                          02 ⇢ 03 Od faktury do zobowiązania
                          03 ⇢ 04 Od zobowiązania do zapłaty ─▶ [wynik: dostawca opłacony]
05 Od warunków handlowych do rozliczenia rabatów retro  · wejścia: dane z 01 i 03 (nie handoff)
```

## Styki L0↔L0 (rejestr sekcja B grupa 1: STK-01..12)
Warunki kontraktu → zamówienie / dopasowanie / rabaty (STK-01/02/03); zapowiedź dostawy (STK-04);
przyjęcie = druga strona dopasowania (STK-05); zamówienie = pierwsza strona (STK-06); zwolnienie do
zapłaty → księga (STK-07); zobowiązanie → wypłata (STK-08); zapłata zamyka zobowiązanie i księgę
(STK-09/10); rabaty: actuals i skutek księgowy (STK-11/12). Pełne brzmienie i typy:
`standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Reconciliation „zwolnione, jeszcze niezapłacone" (STK-07/08/09/10); klucz idempotencji zdarzenia
zapłaty (brak podwójnej wypłaty i podwójnego zamknięcia); kompensacje po stronie płatności buy-side;
strona podatkowa B2B (referencja dostawcy, konsumpcja w księdze); tolerancje i arbitraż dopasowania
trójstronnego; moment i odwrócenie naliczenia (accrual); drabinka rabatu retro (naliczenie →
roszczenie → rozliczenie, dowód wolumenów).
