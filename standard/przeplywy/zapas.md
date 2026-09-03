# Proces przekrojowy / Zapas

Karta szkieletowa procesu przekrojowego (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + wołania z przepływów + styki + dług L1. Głębia (pola 7-14, bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

To jest PROCES PRZEKROJOWY, nie przepływ biznesowy: jest WOŁANY przez przepływy biznesowe i zwraca im stan lub potwierdzenie, rzadko oddaje pałeczkę dalej. Rdzeniem jest jeden dobrze zdefiniowany byt L0, wyłączny pisarz stanu magazynowego (on-hand), ruchu fizycznego oraz faktu wariancji i straty. Rejestr styków NIE zawiera protokołu kanonicznego dla wewnętrznych łańcuchów Zapasu (protokoły 1-6 dotyczą rezerwacji, zwrotu, tendera, sprzedawalności, wyceny lojalności i zakupu do zapłaty, żaden nie jest „Zapas"), więc relacje między procesami INV-01..04 są tu ZAŁOŻENIEM z opisu bytów i kamieniołomu. Uczciwie: to proces przekrojowy typu rejestr stanu, a jego procesy (przyjęcie, transfer, inwentaryzacja, strata) to w dużej mierze niezależne czynności, nie liniowy łańcuch.

**1. Cel biznesowy:** Prowadzić autorytatywny stan magazynowy (on-hand) i ruch fizyczny towaru oraz produkować fakt wariancji i straty: od przyjęcia i przesunięcia, przez zliczenie rzeczywiste, po korektę i odpis. Wynik: jeden wiarygodny stan on-hand, na którym opierają się dostępność, rozchód, wycena i księga. Proces przekrojowy nie inicjuje przepływów biznesowych, tylko obsługuje ich wołania i zwraca im stan lub potwierdzenie.

**2. Granice:**
- Start: pojawia się zdarzenie ruchu fizycznego lub sygnał zliczenia: fakt przyjęcia (z zakupu lub zwrotu), zlecenie przesunięcia, komenda rozchodu, uruchomienie inwentaryzacji, wykrycie straty lub uszkodzenia.
- Koniec: stan on-hand zaktualizowany i potwierdzony wołającemu; przyjęcie doprowadzone do dostępności; transfer domknięty przyjęciem w miejscu docelowym; wariancja zliczenia zaksięgowana jako korekta; strata doprowadzona do odpisu.
- NIE obejmuje: planowania ilości, prognozy, alokacji i rezerwacji dostępności (→ Przepływ / Plan i dostępność); zakupu, dopasowania trójstronnego i zapłaty dostawcy poza faktem przyjęcia (→ Przepływ / Zakup do zapłaty); finalizacji sprzedaży poza faktem rozchodu (→ Przepływ / Realizacja sprzedaży); obsługi sprawy zwrotu poza faktem przyjęcia zwróconego towaru (→ Przepływ / Zwrot); dekretacji, kosztu własnego i wyceny zapasu w księdze (→ Proces przekrojowy / Księga).
- Wołana przez: Zakup do zapłaty (fakt przyjęcia towaru), Plan i dostępność (odczyt on-hand do admisji i alokacji oraz projekcja ATP), Realizacja sprzedaży (rozchód on-hand przy wydaniu), Zwrot (przyjęcie zwrotu fizycznego), Zamówienie zakupowe (zapowiedź dostawy, inbound). Ujęte w sekcji „Wołania z przepływów".
- Zwraca do wołającego: aktualny stan on-hand (odczyt), potwierdzenie przyjęcia, potwierdzenie rozchodu, potwierdzenie przyjęcia zwrotu, fakt korekty lub odpisu. Proces przekrojowy zwraca stan i potwierdzenie, nie oddaje pałeczki dalej; skutki księgowe wariancji, straty i wyceny konsumuje Proces przekrojowy / Księga po swojej stronie.

**3. Właściciel:** Operacje magazynowe i zapas (inventory operations), ze współodpowiedzialnością operacji lokalizacji na odcinku zliczenia rzeczywistego i rozpoznania straty.

**4. Aktorzy:** magazynier (przyjęcie, wydanie), operator przesunięć, pracownik lokalizacji (zliczenie, zgłoszenie straty i uszkodzenia), kontroler zapasu, kierownik lokalizacji, rola zatwierdzająca odpis.

**5. Systemy (typy, vendor-neutral):** ewidencja stanu magazynowego (on-hand ledger jako wyłączny rejestr stanu), system zarządzania magazynem (przyjęcia, przesunięcia, wydania), moduł inwentaryzacji i korekt, moduł strat i odpisów, źródło zdarzeń ruchu fizycznego. Karta nie przesądza podziału tych zdolności między aplikacje ani dostawców.

**6. Wyzwalacze:** fakt przyjęcia dostawy (z zakupu); zapowiedź dostawy jako oczekiwane przyjęcie (inbound); zlecenie i domknięcie przesunięcia; komenda rozchodu przy wydaniu towaru; komenda przyjęcia zwrotu fizycznego; cykl lub doraźne uruchomienie inwentaryzacji; wykrycie straty, ubytku lub uszkodzenia; odczyt on-hand na żądanie planu podaży.

## Uczestnicy L0 (nazwy czytelne)
Stan magazynowy (on-hand, ruch fizyczny, fakt wariancji i straty) · Zamówienie zakupowe (zapowiedź dostawy) · Zobowiązanie do zapłaty (druga strona dopasowania) · Plan podaży i dostępność (odczyt stanu) · Zamówienie klienta i finalizacja sprzedaży (komenda rozchodu) · Sprawa zwrotu (komenda przyjęcia).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Rdzeń: stan magazynowy jest prowadzony przez JEDEN byt L0, wyłącznego pisarza on-hand, ruchu fizycznego oraz faktu wariancji i straty. Każda zmiana stanu przechodzi przez tego pisarza; wołający zlecają ruch lub czytają stan, ale nie piszą on-hand sami. Dostępność (projekcja ATP) CZYTA on-hand tego bytu i nie zapisuje; ATP = on-hand minus zarezerwowane (plan podaży) minus zaalokowane (plan podaży) plus inbound. Egzekucja inwariantu należy do pisarza na ścieżce zapisu, projekcja wykrywa po fakcie, nie egzekwuje.

Wewnętrzne relacje procesów `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: rejestr styków nie ma protokołu kanonicznego dla łańcucha proces→proces w Zapasie. Procesy są tu traktowane jako w dużej mierze NIEZALEŻNE czynności zbiegające się na wspólnym stanie on-hand:
- Przyjęcie: fakt przyjęcia zwiększa on-hand i doprowadza pozycję do dostępności; fakt przyjęcia jest zarazem drugą stroną dopasowania po stronie Zakupu.
- Transfer: przesunięcie zmniejsza on-hand w źródle i domyka się przyjęciem w miejscu docelowym; potencjalne złączenie transferu z przyjęciem lub dostępnością jest ZAŁOŻENIEM do walidacji polem 2 kart L1.
- Inwentaryzacja: zliczenie rzeczywiste porównane ze stanem wytwarza wariancję, która schodzi jako korekta on-hand oraz fakt do księgi.
- Strata: rozpoznanie ubytku lub uszkodzenia wytwarza fakt straty i doprowadza go do odpisu; skutek księgowy konsumuje Proces przekrojowy / Księga.

We wszystkich czterech przypadkach proces przekrojowy zwraca wołającemu stan lub potwierdzenie, nie przekazuje pałeczki kolejnemu przepływowi.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od przyjęcia do dostępności · `INV-01`
- 02 Od transferu do przyjęcia · `INV-02`
- 03 Od inwentaryzacji do korekty · `INV-03`
- 04 Od straty do odpisu · `INV-04`

## Wołania z przepływów (kto woła ten proces przekrojowy)
- **Zakup do zapłaty** (`Zakup do zapłaty / 02`): fakt przyjęcia towaru; stan magazynowy jako wyłączny pisarz on-hand emituje fakt przyjęcia, będący drugą stroną dopasowania trójstronnego (STK-05). Zwrot do wołającego: potwierdzenie przyjęcia jako wejście dopasowania.
- **Zamówienie zakupowe (inbound)**: zapowiedź dostawy jako oczekiwane przyjęcie zasila stan magazynowy (STK-04). Zwrot: uwzględnienie inbound w projekcji ATP.
- **Plan i dostępność** (`Plan i dostępność / 01`, `/04`): odczyt on-hand do decyzji admisji i alokacji (STK-16); projekcja ATP czyta stan on-hand (rejestr sekcja E, ATP = on-hand minus zarezerwowane minus zaalokowane plus inbound). Odczyt, nie zapis. Zwrot: autorytatywny stan on-hand.
- **Realizacja sprzedaży** (`Realizacja sprzedaży / 03`): zamówienie klienta ZLECA rozchód (issue) przy wydaniu, a stan magazynowy wykonuje go jako wyłączny pisarz on-hand (STK-22, komenda; wołanie procesu przekrojowego odłożone, rejestr decyzji projektowych). Zwrot: potwierdzenie rozchodu.
- **Zwrot** (`Zwrot / 04`): sprawa zwrotu ZLECA przyjęcie zwróconego towaru fizycznego do on-hand (STK-32, komenda). Zwrot: potwierdzenie przyjęcia zwrotu do orkiestratora sagi zwrotu.

## Diagram (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: dla procesu przekrojowego węzły są raczej niezależne (nie łańcuch); brak protokołu kanonicznego → wewnętrzne krawędzie są ZAŁOŻENIEM. Semantyka linii (rejestr decyzji projektowych): `─▶` ciągła = potwierdzone polem 2 karty; `⇢` przerywana = założenie do walidacji; bez rombów, bez swimlane. Wołania z przepływów wchodzą jako komendy lub odczyty do wspólnego stanu on-hand, nie jako handoff proces→proces; proces przekrojowy ZWRACA stan lub potwierdzenie (nie oddaje pałeczki). `NN` to numer porządkowy, nie krok sekwencji.
```
[woła: Zakup do zapłaty · fakt przyjęcia]      ⇢  01 Od przyjęcia do dostępności   ⇢ [zwrot: potwierdzenie przyjęcia; on-hand +]
[woła: Zamówienie zakupowe · inbound]          ⇢  01 (oczekiwane przyjęcie)         ⇢ [zwrot: inbound do ATP]
[woła: Realizacja sprzedaży · rozchód/issue]   ⇢  (rozchód on-hand, komenda)        ⇢ [zwrot: potwierdzenie rozchodu; on-hand -]
[woła: Zwrot · przyjęcie zwrotu fizycznego]    ⇢  (przyjęcie zwrotu, komenda)       ⇢ [zwrot: potwierdzenie przyjęcia]
[woła: Plan i dostępność · odczyt on-hand]     ⇢  (odczyt stanu; projekcja ATP)     ⇢ [zwrot: autorytatywny on-hand]

02 Od transferu do przyjęcia    ·   węzeł niezależny; 02 ⇢ 01 założenie: transfer domyka się przyjęciem/dostępnością
03 Od inwentaryzacji do korekty ·   węzeł niezależny; korekta on-hand + fakt do Proces przekrojowy / Księga (nie handoff)
04 Od straty do odpisu          ·   węzeł niezależny; fakt straty do odpisu; skutek księgowy konsumuje Proces przekrojowy / Księga
```

## Styki L0↔L0 (rejestr: STK z udziałem stanu magazynowego)
Inbound: zapowiedź dostawy z zamówienia zakupowego jako oczekiwane przyjęcie (STK-04, zdarzenie). Przyjęcie: fakt przyjęcia jako druga strona dopasowania trójstronnego po stronie Zakupu (STK-05, zdarzenie). Odczyt: plan podaży czyta on-hand do decyzji admisji i alokacji (STK-16, stan, `[PROP+ 24.08]`). Rozchód: zamówienie klienta zleca issue, stan magazynowy wykonuje go jako wyłączny pisarz on-hand (STK-22, komenda). Zwrot: sprawa zwrotu zleca przyjęcie zwróconego towaru do on-hand (STK-32, komenda, `[PROP+ 24.08]`). Projekcja ATP (rejestr sekcja E) = on-hand minus zarezerwowane minus zaalokowane plus inbound (czyta stan, nie pisze). Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Brak protokołu kanonicznego dla wewnętrznych łańcuchów Zapasu: relacje INV-01..04 (przyjęcie, transfer, inwentaryzacja, strata) założone z opisu bytów i kamieniołomu, do potwierdzenia lub zaprzeczenia polem 2 kart L1; do rozstrzygnięcia, czy to niezależne czynności czy istnieje realny łańcuch (np. transfer domykany przyjęciem, `INV-02` do `INV-01`). Rozchód jako komenda do stanu magazynowego (STK-22): klucz idempotencji oraz in-transit do klienta (rejestr sekcja D poz. 7). Przyjęcie zwrotu (STK-32) i przyjęcie z dostawy (STK-05): idempotencja przyjęcia, granica wobec sagi zwrotu i wobec dopasowania trójstronnego. Odczyt on-hand oraz spójność projekcji ATP (STK-16, rejestr sekcja E): ATP to projekcja, rezerwacja idzie na availability ledger planu podaży, nie na on-hand. In-transit i inbound do dostępności (rejestr sekcja D poz. 7). Granica transferu wobec realizacji partnerskiej i zmiany źródła (styk z `SAL-03`) oraz wobec rozwiązania braku w planie (substytucja i transfer, `INV-06`). Wołanie procesu przekrojowego przez przepływy (Realizacja sprzedaży, Zwrot) odłożone jako mechanizm (rejestr decyzji projektowych): granica wołanie kontra handoff do formalizacji. Skutek księgowy korekty i straty (INV-03, INV-04) wobec Proces przekrojowy / Księga: moment i kierunek faktu do wyceny, poza tą kartą.
