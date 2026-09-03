# Przepływ / Płatności

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

Obszar ma rozstrzygnięty rdzeń i jeden kandydat bez granicy. Rdzeń (od kwoty do zamkniętego rozliczenia,
z orkiestracją tendera i formą płatności punktowej) opiera się na protokołach kanonicznych 3 (Tender S17)
i 5 (Loyalty wycena) z rejestru styków, więc jest rozstrzygnięty. Program lojalnościowy jako proces
domenowy pozostaje kandydatem: jego początek, wynik i granica wobec Oferty handlowej, Realizacji
sprzedaży i Płatności nie są zatwierdzone, więc nie dostaje numeru ani stałego ID.

**1. Cel biznesowy:** Doprowadzić zobowiązanie klienta (kwotę do zapłaty) do zamkniętego rozliczenia:
od ustalenia formy płatności, przez autoryzację i przechwycenie tenderu (w tym blokadę i umorzenie
punktów oraz należność klienta), po rozliczenie zasilające księgę i rozliczenia kasowe. Wynik:
rozliczenie zamknięte, tender zcommitowany lub skompensowany, skutek księgowy przekazany.

**2. Granice:**
- Start: istnieje customer commitment z Realizacji sprzedaży (kwota do zapłaty), uruchamia ustalenie
  formy płatności i orkiestrację tenderu (wejście, STK-25).
- Koniec: tender zcommitowany lub skompensowany, rozliczenie (settlement) zamknięte, skutek księgowy
  i kasowy przekazany; przy formie punktowej liczba punktów zdekrementowana przez jedynego pisarza,
  a skutek wyceny rozstrzygnięty własną metodą księgi.
- NIE obejmuje: powstania koszyka, zobowiązania klienta i wydania towaru (→ Przepływ / Realizacja
  sprzedaży, wejście); anulowania sprzedaży i zwrotu wraz ze zwrotem środków (→ Przepływ / Zwrot;
  zwrot środków przychodzi do settlementu od orkiestratora zwrotu, poza tą kartą); księgowań poza skutkiem
  rozliczenia klienta (→ Proces przekrojowy / Księga); operacyjnego zamknięcia kasy i wpłaty do banku
  (→ Proces przekrojowy / Rozliczenia kasowe); dopuszczenia ceny i promocji do kasy (→ Przepływ / Oferta handlowa);
  zatwierdzenia granicy, początku i wyniku programu lojalnościowego jako procesu (kandydat, poniżej).
- Wejście z: Realizacja sprzedaży (customer commitment → settlement/tender, STK-25). Handoff-out:
  rezultat rozliczenia zasila Proces przekrojowy / Księga (settlement gotówkowy klienta oraz należność klienta,
  STK-30) i Proces przekrojowy / Rozliczenia kasowe (rozliczenie form bezgotówkowych i gotówkowych).

**3. Właściciel:** Finanse / rozliczenia (settlement i należność klienta AR), ze współodpowiedzialnością
relacji z klientem na odcinku księgi punktów i kursu operacyjnego.

**4. Aktorzy:** operator punktu sprzedaży (wybór formy płatności), specjalista ds. rozliczeń (settlement),
specjalista ds. należności klienta (kredyt klienta, raty, B2B), administrator programu lojalnościowego,
kontroler / finanse.

**5. Systemy (typy, vendor-neutral):** silnik form płatności i autoryzacji, przełącznik rozliczeniowy
(payment switch, schemat rozliczeniowy vendor-neutral), rejestr rozliczeń (settlement ledger) z
orkiestratorem tenderu, moduł należności klienta (AR: kredyt, raty, B2B), system relacji z klientem z
księgą punktów i kursem operacyjnym, księga główna z wyceną zobowiązania lojalnościowego, moduł
rozliczeń kasowych.

**6. Wyzwalacze:** powstanie customer commitment (kwota do zapłaty); wybór formy płatności; żądanie
autoryzacji tenderu; wygaśnięcie TTL holdu punktów (uruchamia release-hold); przechwycenie (capture);
zdarzenie zmiany kursu operacyjnego (lojalność); termin raty lub rozliczenia należności klienta;
przybycie zwrotu środków od orkiestratora zwrotu (wejście spoza tej karty).

## Uczestnicy L0 (nazwy czytelne)
Settlement, tender i należność klienta (AR) · Relacja z klientem i księga punktów · Księga ·
Zamówienie klienta i zobowiązanie (wejście z Realizacji sprzedaży).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Customer commitment z Realizacji sprzedaży wchodzi jako zobowiązanie do rozliczenia (settlement/tender,
STK-25) i uruchamia ustalenie formy płatności.

Tender (protokół kanoniczny 3, S17, rejestr sekcja C.3): settlement jest orkiestratorem tenderu. Relacja
z klientem autoryzuje i BLOKUJE punkty jako hold z TTL (komenda, STK-26) → settlement wykonuje capture
→ commit lub kompensacja (komenda release-hold, idempotencja po tender-id, STK-27). Liczbę punktów pisze
WYŁĄCZNIE relacja z klientem (dekrement przy commicie tenderu, STK-28); orkiestrator tenderu nigdy nie
pisze liczby punktów. Jest to protokół byt↔byt, więc NIE wchodzi na diagram proces→proces (opis tutaj).

Loyalty wycena (protokół kanoniczny 5, rejestr sekcja C.5): kurs OPERACYJNY (co dostaje klient) jest
różny od założeń WYCENY księgi (breakage, effective-dating). Relacja z klientem emituje zdarzenie zmiany
kursu operacyjnego (STK-29), a księga własną metodą decyduje o skutku księgowym; relacja z klientem NIE
steruje zobowiązaniem księgi.

Rozliczenie i skutek: settlement gotówkowy klienta zasila księgę (STK-30) oraz rozliczenia kasowe.
Należność klienta (AR: kredyt klienta, raty, B2B) mieszka w tym samym bycie co settlement (rozszerzenie
24.08): limit kredytowy jest czytany przez zamówienie klienta w bramie sprzedawalności, a autorem
polityki limitu jest relacja z klientem (STK-40); należność otwarta rozlicza się z agingiem i
harmonogramem rat, a jej skutek księgowy trafia do księgi (STK-41).

Zwrot środków przy zwrocie przychodzi do settlementu od orkiestratora zwrotu (poza tą kartą),
ze strażnikiem capture-id wspólnym z chargeback; ta karta go nie orkiestruje.

`[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: wewnętrzna sekwencja procesów PAY-01, PAY-02, PAY-03 nie
ma jeszcze kart L1 z polem 2, więc ich łańcuch jest założeniem do walidacji; potwierdzony jest wyłącznie
styk byt↔byt tenderu, wyceny i wejścia z Realizacji.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od kwoty do formy płatności · `PAY-01`
- 02 Od autoryzacji do przechwycenia · `PAY-02`
- 03 Od przechwyconych płatności do rozliczenia partii z operatorem · `PAY-03` (drugi wyzwalacz: `ST-TERMIN-OCZEKIWANEGO-RAPORTU` `(EXTERNAL)`, bez nowego procesu)
- Kandydat · Program lojalnościowy: naliczanie i umarzanie punktów (bez numeru i bez stałego ID; początek, wynik i granica wobec Oferty handlowej, Realizacji sprzedaży i Płatności niezatwierdzone, do zatwierdzenia przed nadaniem numeru)

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok
sekwencji. Tender (protokół 3) i wycena lojalnościowa (protokół 5) to protokoły byt↔byt, więc NIE
wchodzą na diagram proces→proces (opis w sekcji „Protokół / przepływ"). Krawędź wejścia z Realizacji
sprzedaży ciągła (pole 2 tej karty deklaruje wejście z customer commitment); krawędzie wewnętrzne
przerywane (karty L1 PAY-01..03 jeszcze nie istnieją). Kandydat lojalnościowy poza sekwencją, bez linii
(granica niezatwierdzona).
```
[z: Realizacja sprzedaży · customer commitment] ─▶ 01 Od kwoty do formy płatności
                                                   01 ⇢ 02 Od autoryzacji do przechwycenia
                                                   02 ⇢ 03 Od przechwyconych płatności do rozliczenia partii z operatorem ─▶ [wynik: rozliczenie zamknięte, do Proces przekrojowy / Księga i Proces przekrojowy / Rozliczenia kasowe]
Kandydat · Program lojalnościowy (naliczanie i umarzanie punktów)  ·  poza sekwencją, granica niezatwierdzona (tender i wycena = styk byt↔byt, nie proces→proces)
```

## Styki L0↔L0 (rejestr sekcja B grupa 4: STK-25..30)
Wejście: customer commitment → settlement/tender (STK-25, wejście z Realizacji sprzedaży). Tender S17:
żądanie autoryzacji i blokady punktów jako hold z TTL (STK-26, komenda); leg kompensacji release-hold
z idempotencją tender-id (STK-27, komenda); relacja z klientem jedynym pisarzem dekrementu liczby
punktów przy commicie tenderu, settlement nigdy nie pisze liczby (STK-28). Loyalty wycena: zdarzenie
zmiany kursu operacyjnego, księga własną metodą wyceny (breakage, effective-dating), relacja nie steruje
zobowiązaniem księgi (STK-29). Skutek kasowy: settlement gotówkowy klienta → księga (STK-30). Pełne
brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

Powiązane spoza grupy 4 (należność klienta, AR; rejestr grupa 7): limit kredytowy czytany przez
zamówienie klienta, autor polityki limitu = relacja z klientem (STK-40); należność klienta → księga
z agingiem (STK-41); rozliczenie należności otwarta → rozliczona, aging i harmonogram rat (STK-39).

## Dług L1 (do Etapu C)
Inwentarz komend kompensacji orkiestratora tenderu (release-hold i inne; klucz idempotencji tender-id
plus operation-id). Reconciliation „przechwycone, jeszcze nierozliczone" oraz spójność commit vs
kompensacja tenderu. Mechanizm STK-40: jak zamówienie klienta czyta limit kredytowy relacji z klientem
fail-closed (autor polityki rozstrzygnięty 24.08, mechanizm otwarty). Strona podatkowa B2B należności
klienta (relacja z klientem referuje, księga konsumuje; rejestr sekcja D poz. 9). Granica wobec zwrotu
środków z Przepływu / Zwrot: strażnik capture-id wspólny z chargeback, remaining-returnable (STK-31,
poza tą kartą). Kandydat lojalnościowy: zatwierdzenie początku, wyniku i granicy wobec Oferty handlowej,
Realizacji sprzedaży i Płatności przed nadaniem numeru i stałego ID (kryterium z mapy sekcja C).
Kryterium podziału PAY-01 vs PAY-02 vs PAY-03 i potwierdzenie ich łańcucha polem 2 kart L1
(obecnie założenie z opisu bytów i kamieniołomu).
