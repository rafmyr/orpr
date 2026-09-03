# Proces przekrojowy / Księga

Karta szkieletowa procesu przekrojowego (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + wołania z przepływów + styki + dług L1. Proces przekrojowy jest WOŁANY przez przepływy (konsumuje ich zdarzenia i sam zamyka swoje pozycje), nie przekazuje pałeczki. Głębia (pola 7-14, bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem. Brak dedykowanego protokołu kanonicznego dla wewnętrznych łańcuchów Księgi (FIN-01..03), więc ich wzajemne relacje pozostają `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`; potwierdzone są wyłącznie styki byt↔byt wołań z przepływów.

**1. Cel biznesowy:** Utrzymać autorytatywny obraz księgowy przedsiębiorstwa: doprowadzić zdarzenia z wielu przepływów (sprzedaż, zakup, rozliczenia, rabaty, lojalność, zapas) do zaksięgowanej, uzgodnionej pozycji, wyliczyć koszt własny, wycenić zobowiązanie podatkowe oraz zobowiązanie lojalnościowe własną metodą, a każdą swoją pozycję zamknąć samodzielnie na podstawie konsumowanych zdarzeń.

**2. Granice:**
- Start: brak własnego startu procesowego. Księga budzi się na skonsumowanym zdarzeniu wołającego (payable i naliczenie, settlement gotówkowy, należność klienta, accrual retro, zmiana kursu operacyjnego, fakt korekty lub straty zapasu, zdarzenie sprzedaży lub zakupu do podatku).
- Koniec: pozycja zaksięgowana i zamknięta samozamknięciem (np. zdarzenie PaidV1 zamyka payable), koszt własny odniesiony, zobowiązanie podatkowe i zobowiązanie lojalnościowe wycenione własną metodą; skutek księgowy jest rezultatem, nie pałeczką przekazywaną dalej.
- NIE obejmuje: operacyjnego rozliczenia płatności, tenderu i należności klienta (→ Przepływ / Płatności); zwolnienia zobowiązania wobec dostawcy i wypłaty (→ Przepływ / Zakup do zapłaty); naliczania i umarzania punktów oraz ustalania kursu operacyjnego (relacja z klientem, → Przepływ / Płatności i → Przepływ / Oferta handlowa); fizycznego stanu, wyceny i faktu wariancji zapasu poza ich skutkiem księgowym (→ Proces przekrojowy / Zapas); zamknięcia kasy i wpłaty do banku (→ Proces przekrojowy / Rozliczenia kasowe); uzgodnień i audytu poza księgą (→ Proces przekrojowy / Kontrola i zgodność).
- Wołana przez: Zakup do zapłaty, Płatności (rozliczenia i lojalność, źródło: relacja z klientem), Oferta handlowa, Zwrot, Proces przekrojowy / Zapas oraz zdarzenia sprzedaży i zakupu zasilające podatek (wykaz w sekcji „Wołania z przepływów").
- Zwraca do wołającego: skutek księgowy jako zdarzenie lub stan księgi (payable otwarte, potem zamknięte; skutek wyceny zobowiązania lojalnościowego; skutek księgowy należności i rabatu retro; podstan „prowizorycznie zamknięte" wobec Zwrotu). Księga nie oddaje pałeczki procesowej, zwraca rezultat księgowy konsumentowi.

**3. Właściciel:** Finanse / księgowość (autorytet-rejestr księgowy), ze współodpowiedzialnością Podatków na odcinku zobowiązania podatkowego oraz Finansów rozliczeń na odcinku wyceny zobowiązania lojalnościowego.

**4. Aktorzy:** księgowy (księga główna), kontroler / finanse, specjalista ds. kosztu własnego, specjalista ds. podatków, aktuariusz lub analityk wyceny zobowiązania lojalnościowego (breakage, effective-dating).

**5. Systemy (typy, vendor-neutral):** księga główna (general ledger) jako pierścień autorytetu księgowego, moduł kosztu własnego (COGS / wycena rozchodu), silnik podatkowy (naliczenie i zobowiązanie), moduł wyceny zobowiązania lojalnościowego (własna metoda: breakage, effective-dating), warstwa konsumpcji zdarzeń z kluczem idempotencji (ack, samozamknięcie pozycji).

**6. Wyzwalacze:** skonsumowane zdarzenie zwolnienia do zapłaty (payable i naliczenie przyjęcie-faktura); zdarzenie PaidV1 (zamyka payable); zdarzenie settlementu gotówkowego klienta; zdarzenie należności klienta (aging); zdarzenie accrual retro; zdarzenie zmiany kursu operacyjnego (lojalność); fakt korekty lub straty zapasu; zdarzenie sprzedaży lub zakupu do podatku; trigger reopen ze strony sprawy zwrotu.

## Uczestnicy L0 (nazwy czytelne)
Księga (księga główna, podatek, wycena zobowiązania lojalnościowego) · Zobowiązanie do zapłaty (wołający z Zakupu do zapłaty) · Settlement i należność klienta (wołający z Płatności) · Relacja z klientem i księga punktów (źródło kursu operacyjnego) · Rabaty retro (wołający z rabatów) · Sprawa zwrotu (wołający, trigger reopen) · Stan magazynowy i fakt wariancji (źródło korekt i strat do kosztu własnego).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Księga jest pierścieniem, czyli przekrojowym autorytetem księgowym. Nie ma własnego wejścia procesowego ani nie oddaje pałeczki: KONSUMUJE zdarzenia z wielu przepływów idempotentnie (ack, klucz idempotencji) i SAMA zamyka swoje pozycje. Kluczowy inwariant: żaden inny byt nie mutuje stanu księgi. Przykłady samozamknięcia: zdarzenie PaidV1 z rozliczenia zamyka payable po stronie księgi (moduł płatności nie modyfikuje pozycji księgi); zwolnienie do zapłaty otwiera payable i naliczenie przyjęcie-faktura z faktu przyjęcia.

Wycena zobowiązania lojalnościowego idzie WŁASNĄ metodą księgi: kurs OPERACYJNY (co dostaje klient) jest różny od założeń WYCENY księgi (breakage, effective-dating). Relacja z klientem emituje zdarzenie zmiany kursu operacyjnego, a księga własną metodą decyduje o skutku księgowym; relacja z klientem NIE steruje zobowiązaniem księgi.

Wobec Zwrotu księga jest NIE-TERMINALNA: utrzymuje podstan „prowizorycznie zamknięte" i wystawia trigger reopen dostępny dla orkiestratora zwrotu; sprawa zwrotu nie osiąga stanu ostatecznego, dopóki księga nie uzgodni skutku.

Podatek (proces „Od podatku do zobowiązania") konsumuje zdarzenia sprzedaży i zakupu i wycenia zobowiązanie podatkowe; koszt własny (proces „Od zapasu do kosztu własnego") konsumuje fakt korekty i straty zapasu.

`[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: wewnętrzne łańcuchy między FIN-01, FIN-02 i FIN-03 nie mają dedykowanego protokołu kanonicznego ani kart L1 z polem 2. Księga to autorytet-rejestr konsumujący zdarzenia z wielu przepływów, więc procesy w obszarze traktujemy jako w dużej mierze NIEZALEŻNE (każdy budzony własnym zdarzeniem), a nie jako sekwencję z przekazaniem pałeczki. Do walidacji w Etapie C.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od sprzedaży do księgi · `FIN-01`
- 02 Od zapasu do kosztu własnego · `FIN-02`
- 03 Od podatku do zobowiązania · `FIN-03`

## Wołania z przepływów (kto woła ten proces przekrojowy)
- Przepływ / Zakup do zapłaty: zwolnienie do zapłaty → payable i naliczenie przyjęcie-faktura z faktu przyjęcia (STK-07); zdarzenie PaidV1 → księga konsumuje i sama zamyka payable (STK-10).
- Przepływ / Zakup do zapłaty (rabaty retro): accrual retro (claimable, settled) → skutek księgowy należności (STK-12).
- Przepływ / Płatności: settlement gotówkowy klienta → księga (STK-30); należność klienta AR → księga z agingiem (STK-41).
- Przepływ / Płatności (lojalność, źródło: relacja z klientem; program lojalnościowy żyje w Płatnościach, nie w Ofercie): zdarzenie zmiany kursu operacyjnego → własna wycena zobowiązania lojalnościowego księgi, breakage i effective-dating (STK-29).
- Przepływ / Zwrot: skutek księgowy sprawy zwrotu; księga nie-terminalna, podstan „prowizorycznie zamknięte", trigger reopen po stronie sprawy zwrotu (STK-34).
- Proces przekrojowy / Zapas: fakt korekty i straty (inwentaryzacja, odpis) → wycena i koszt własny, procesy „Od inwentaryzacji do korekty" i „Od straty do odpisu" (INV-03/04). `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: brak dedykowanego STK zapas→księga w rejestrze; relacja wyprowadzona z opisu bytu FIN.
- Zdarzenia sprzedaży i zakupu → podatek (FIN-03 „Od podatku do zobowiązania" konsumuje je do wyceny zobowiązania podatkowego). `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: konsumpcja podatkowa opisana w bycie i długu L1 (party podatkowa B2B, sekcja D poz. 9), bez odrębnego STK z numerem.

## Diagram (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: proces przekrojowy nie przekazuje pałeczki, więc brak łańcucha proces→proces. Węzły FIN-01..03 stoją NIEZALEŻNIE (każdy budzony własnym zdarzeniem). Wołania z przepływów pokazujemy jako zdarzenia KONSUMOWANE, wchodzące do węzłów księgi. `⇢` przerywana = założenie do walidacji (brak protokołu wewnętrznego lub brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok sekwencji. Wołania byt↔byt (STK) opisano w sekcji „Wołania z przepływów"; tu jedynie kierunek konsumpcji.
```
[woła: Zakup do zapłaty · zwolnione-do-zapłaty, PaidV1]        ⇢ 01 Od sprzedaży do księgi
[woła: Płatności · settlement gotówkowy, należność klienta AR] ⇢ 01 Od sprzedaży do księgi
[woła: rabaty retro · accrual retro]                           ⇢ 01 Od sprzedaży do księgi
[woła: Płatności · zmiana kursu operacyjnego (lojalność)]      ⇢ 01 Od sprzedaży do księgi (własna wycena zobowiązania lojalnościowego)
[woła: Zwrot · skutek księgowy sprawy zwrotu]                  ⇢ 01 Od sprzedaży do księgi (nie-terminalny, trigger reopen)

[woła: Proces przekrojowy / Zapas · fakt korekty i straty]     ⇢ 02 Od zapasu do kosztu własnego

[woła: zdarzenia sprzedaży i zakupu]                           ⇢ 03 Od podatku do zobowiązania

01 · 02 · 03  ·  węzły niezależne (brak protokołu wewnętrznego; łańcuch między nimi = [ZAŁOŻENIE])
```

## Styki L0↔L0 (rejestr: STK z udziałem FIN)
Zwolnione-do-zapłaty → payable i accrual przyjęcie-faktura (STK-07); PaidV1, księga konsumuje i sama zamyka payable (STK-10); accrual retro → skutek księgowy należności (STK-12); zmiana kursu operacyjnego, księga własną metodą wyceny, breakage i effective-dating, relacja nie steruje zobowiązaniem księgi (STK-29); settlement gotówkowy klienta → księga (STK-30); księga nie-terminalna wobec zwrotu, trigger reopen (STK-34); należność klienta AR → księga z agingiem (STK-41). Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md` (byt FIN: 7 wystąpień jako źródło lub cel styku).

## Dług L1 (do Etapu C)
Klucz idempotencji konsumowanych zdarzeń (ack, brak podwójnego księgowania i podwójnego zamknięcia; STK-10). Reconciliation „zwolnione, jeszcze niezapłacone" po stronie księgi (STK-07/10). Kryterium podziału i granice między FIN-01, FIN-02 a FIN-03 oraz potwierdzenie ich niezależności lub łańcucha polem 2 kart L1 (obecnie `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`, brak protokołu wewnętrznego). Mechanizm reopen wobec sprawy zwrotu (podstan „prowizorycznie zamknięte", warunek uzgodnienia; STK-34). Własna metoda wyceny zobowiązania lojalnościowego: parametry breakage i reguła effective-dating (STK-29). Party podatkowa B2B: referencja po stronie relacji z klientem, konsumpcja w księdze (rejestr sekcja D poz. 9). Potwierdzenie i ewentualne nadanie numeru stykowi zapas→księga dla kosztu własnego (INV-03/04 → FIN-02), obecnie założenie z opisu bytu.
