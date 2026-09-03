# [ORPR-SAL-01] Basket-to-Sale

| | |
|---|---|
| ID | ORPR-SAL-01 |
| Wersja karty | 1.0 |
| Status | released, stan wewnętrzny ORPR (decyzja wlasciciela 23.08) |
| Data redakcji | 22.08.2026 |
| Nośnik decyzji | wewnętrzny materiał roboczy |
| Recenzja wydaniowa | 3 niezalezne re-recenzje (Opus) + rekalibracja tagow do benchmarku repo; finalna recenzja = WYDAC (wewnętrzny materiał roboczy) |
| Regulatory matrix | v1.0.1, legal_as_of 2026-08-14; właściciel potwierdził aktualność zastosowania na 22.08.2026 |

Legenda źródeł: `[AUT-R 22.08]` oznacza decyzję właściciela, `[PROP+ 22.08]` przyjętą propozycję redakcyjną, `[R: ID]` wymaganie regulatory-matrix, a `[LIT: źródło, wersja, lokator]` publiczne źródło rynkowe. `[D! nazwa]` oznacza wejście obowiązkowe, a `[D: nazwa]` użycie albo wejście warunkowe danej.

**1. Cel biznesowy**

Przekształcić przedstawiony koszyk w sfinalizowaną sprzedaż, której kwota została zaakceptowana przez klienta i w pełni pokryta dopuszczonym rozliczeniem. [AUT-R 22.08] **Korekta 03.09** [AUT-R 03.09]: wynik fiskalny albo potwierdzone zwolnienie powstaje równolegle w SAL-02, po zakończeniu SAL-01, a nie jako jego warunek; poprzednie brzmienie łączyło oba wyniki w jeden cel i tworzyło cykl ze startem SAL-02 (recenzja Sola, delta `e58a313`, finding B1).

Proces prowadzi do tego samego rezultatu biznesowego w kasie obsługowej i kasie samoobsługowej (checkout stacjonarny, klient obecny). [PROP+ 22.08]

**2. Granice**

Proces zaczyna się, gdy klient przedstawia koszyk do finalizacji. [PROP+ 22.08]

Proces kończy się po uzyskaniu pełnego pokrycia kwoty należnej i wyemitowaniu zdarzenia sprzedaż-sfinalizowana. [AUT-R 22.08] **Korekta 03.09** [AUT-R 03.09]: wynik fiskalny lub potwierdzone zwolnienie nie jest warunkiem tego zakończenia; poprzednie brzmienie tworzyło cykl ze startem SAL-02 (recenzja Sola, delta `e58a313`, finding B1).

Zamówienie oczekujące na potwierdzenie nie jest sprzedażą w SAL-01. [PROP+ 22.08]

Sprzedaż na odległość (checkout cyfrowy, klient nieobecny) pozostaje poza SAL-01 i podlega odrębnej obsłudze. [PROP+ 22.08]

SAL-02 wykonuje fiskalizację równolegle z SAL-03, po zakończeniu SAL-01; jej wynik nie jest bramką zakończenia SAL-01. [AUT-R 22.08] **Korekta 03.09** [AUT-R 03.09] (recenzja Sola, delta `e58a313`, finding B1).

SAL-03 przejmuje skutek zapasowy wyłącznie dla pozycji oznaczonych jako zapasowe. [AUT-R 22.08]

PAY wykonuje rozliczenia, natomiast SAL-01 ocenia ich łączne pokrycie względem kwoty należnej. [PROP+ 22.08]

Zwrot pozostaje odrębnym rezultatem procesu RTN, nawet gdy sprzedaż i zwrot są rozliczane wspólnie. [PROP+ 22.08]

Operacje pieniężne bez sprzedaży pozostają poza SAL-01. [PROP+ 22.08]

Wydanie bez opłaty oraz utworzenie lub odwrócenie przyszłego uprawnienia pozostają poza SAL-01. [AUT-R 22.08]

Błąd fiskalny jest wyjątkiem SAL-02 następującym po zakończeniu SAL-01, nie stanem SAL-01; właścicielem przypadku pozostaje Sales Operations aż do finalizacji albo pełnego odwrócenia w SAL-02. [AUT-R 22.08] **Korekta 03.09** [AUT-R 03.09] (recenzja Sola, delta `e58a313`, finding B1).

**3. Właściciel**

Sales Operations. [AUT-R 23.08]

Poziom M0-M3 może zmienić obsadę uprawnień, lecz nie zmienia kroków ani wyniku procesu. [AUT-R 22.08]

**4. Aktorzy**

- klient; [PROP+ 22.08]
- operator sprzedaży; [PROP+ 22.08]
- rola zatwierdzająca wyjątek handlowy; [PROP+ 22.08]
- właściciel wyjątku po rozliczeniu; [PROP+ 22.08]
- SAL-02 jako wykonawca fiskalizacji; [PROP+ 22.08]
- SAL-03 jako odbiorca skutku zapasowego; [PROP+ 22.08]
- PAY jako wykonawca rozliczenia; [PROP+ 22.08]
- RTN jako właściciel wyniku zwrotu. [PROP+ 22.08]

**5. Systemy**

Klasy zdolności wspierających obejmują prowadzenie transakcji sprzedaży, kalkulację ceny i korzyści, rozliczenie płatności, fiskalizację, obsługę uprawnień oraz przekazanie skutku zapasowego. [PROP+ 22.08]

Karta nie przesądza podziału tych zdolności między aplikacje ani dostawców. [PROP+ 22.08]

**6. Wyzwalacze**

Podstawowym wyzwalaczem jest przedstawienie koszyka do finalizacji przez klienta. [PROP+ 22.08]

Ponowne wejście do aktywnej finalizacji może nastąpić po prawidłowym wznowieniu zawieszonej transakcji. [PROP+ 22.08]

**7. Wejścia**

Obowiązkowe:

- przedstawiony koszyk `[D! koszyk-przedstawiony]`; [PROP+ 22.08]
- typ finalizacji `[D! typ-finalizacji]`; [PROP+ 22.08]
- typ każdej pozycji `[D! typ-pozycji]`; [PROP+ 22.08]
- wynik ogólnej sprzedawalności każdej pozycji `[D! pozycja-sprzedawalna]`; [PROP+ 22.08]
- wynik dopuszczalności pozycji w tej transakcji `[D! dopuszczalnosc-transakcyjna]`; [PROP+ 22.08]
- informacje należne klientowi przed akceptacją `[D! informacja-ofertowa]`; [R: RTL-CONS-001]
- kwota należna przedstawiona klientowi `[D! kwota-nalezna]`; [PROP+ 22.08]
- akceptacja obowiązku zapłaty i kwoty `[D! akceptacja-klienta]`; [PROP+ 22.08]
- status nabywcy `[D! status-nabywcy]`; [PROP+ 22.08]
- dane wymagane do dokumentu `[D! dane-fiskalne]`; [R: FISC-007] [R: FISC-011]
- kwalifikacja fiskalna lub zwolnienie `[D! kwalifikacja-fiskalna]`; [R: RTL-FISC-001] [R: FISC-002]
- wyniki przyjętych rozliczeń `[D! wynik-rozliczenia]`. [PROP+ 22.08]

**Korekta 03.09** [AUT-R 03.09]: `[D! wynik-fiskalny]` usunięty z wejść obowiązkowych, bo jest wynikiem SAL-02, powstającym po zakończeniu SAL-01, nie jego wejściem; poprzednie brzmienie tworzyło cykl danych (recenzja Sola, delta `e58a313`, finding B1). Wiązanie `[R: FISC-005]` przechodzi do karty SAL-02.

Opcjonalne:

- potrzeba identyfikacji klienta `[D: potrzeba-identyfikacji]`; [PROP+ 22.08]
- identyfikacja klienta `[D: identyfikacja-klienta]`; [PROP+ 22.08]
- wynik promocji lub innej automatycznej korzyści `[D: wynik-promocji]`; [PROP+ 22.08]
- decyzja o rabacie ręcznym `[D: decyzja-rabat-reczny]`; [PROP+ 22.08]
- potwierdzenie prawidłowo eksponowanej niższej ceny `[D: dowod-ceny-eksponowanej]`; [PROP+ 22.08] [R: PRICE-005]
- istniejąca przedpłata `[D: przedplata]`; [PROP+ 22.08] [R: RTL-FISC-002]
- uprawnienie do rachunku odroczonego `[D: uprawnienie-odroczone]`; [PROP+ 22.08]
- polityka ryzyka dla trybu offline lub ręcznego `[D: polityka-ryzyka]`; [PROP+ 22.08]
- decyzja o podziale koszyka `[D: decyzja-podzialu]`; [PROP+ 22.08]
- zapis zawieszenia `[D: zapis-zawieszenia]`; [PROP+ 22.08]
- powiązany zwrot `[D: powiazany-zwrot]`; [PROP+ 22.08]
- cecha skutku zapasowego pozycji `[D: cecha-zapasowa]`. [PROP+ 22.08]

**8. Wyjścia**

Dokumentem wyjściowym jest sfinalizowana sprzedaż z pozycjami, kwotą i przyjętymi formami rozliczenia. [AUT-R 22.08] **Korekta 03.09** [AUT-R 03.09]: usunięto odwołanie do wyniku fiskalnego, bo powstaje on w SAL-02 po zakończeniu SAL-01 (recenzja Sola, delta `e58a313`, finding B1).

Zdarzenie sprzedaż-sfinalizowana jest niezmienne, a późniejsza korekta stanowi osobne zdarzenie powiązane. [AUT-R 22.08]

Dla pozycji z `[D: cecha-zapasowa]` proces emituje zdarzenie do SAL-03. [PROP+ 22.08]

Proces może również zakończyć się wynikiem zawieszona albo porzucona. [PROP+ 22.08] **Korekta 03.09** [AUT-R 03.09]: stan wyjątek-po-rozliczeniu usunięty stąd, bo dotyczy braku wyniku fiskalnego, zdarzenia SAL-02 po zakończeniu SAL-01, nie stanu SAL-01 (recenzja Sola, delta `e58a313`, finding B1).

**9. Bramki decyzyjne**

- `[D: typ-finalizacji]` musi oznaczać bezpośredni checkout prowadzący do sprzedaży. [PROP+ 22.08]
- Zamówienie oczekujące na późniejsze potwierdzenie jest wyłączone z SAL-01. [PROP+ 22.08]
- `[D: typ-pozycji]` musi oznaczać pozycję sprzedażową. [PROP+ 22.08]
- Wydanie bez opłaty nie może zostać przekształcone w pozycję sprzedaży o cenie zero. [AUT-R 22.08]
- Każda pozycja musi mieć dodatni wynik `[D: pozycja-sprzedawalna]` oraz `[D: dopuszczalnosc-transakcyjna]`. [PROP+ 22.08]
- Brak dopuszczalności blokuje finalizację do czasu usunięcia pozycji, jej zastąpienia albo porzucenia transakcji. [PROP+ 22.08]
- Pozycją sprzedaży może być towar, usługa, opłata, kaucja albo nowy instrument przedpłacony. [AUT-R 22.08]
- Wykorzystanie istniejącego instrumentu przedpłaconego jest formą rozliczenia obsługiwaną przez PAY. [PROP+ 22.08]
- `[D: informacja-ofertowa]` musi zostać udostępniona przed `[D: akceptacja-klienta]`. [R: RTL-CONS-001]
- Brak wymaganej informacji blokuje finalizację do czasu jej udostępnienia. [R: RTL-CONS-001]
- Identyfikacja klienta jest wymagana tylko wtedy, gdy wynika to z `[D: potrzeba-identyfikacji]`. [AUT-R 22.08]
- Przy braku takiej potrzeby sprzedaż pozostaje anonimowa i nie otrzymuje korzyści zależnej od klienta. [AUT-R 22.08]
- Zakres `[D: identyfikacja-klienta]` jest ograniczony do danych koniecznych dla danego celu. [R: PRIV-003]
- Przy pozyskiwaniu danych musi być przypisana właściwa wersja informacji o ich przetwarzaniu albo udokumentowana podstawa wyjątku. [R: RTL-PRIV-001]
- `[D: wynik-promocji]` jest konsumowany jako wynik CAT-03. [AUT-R 22.08]
- `[D: decyzja-rabat-reczny]` jest odrębną decyzją handlową i nie zastępuje kwalifikacji promocji. [AUT-R 22.08]
- Rabat ręczny przekraczający limit roli wnioskującej wymaga zatwierdzenia przez rolę o wyższym limicie; samoakceptacja ponad własny limit jest niedozwolona. [AUT-R 22.08]
- Potwierdzona prawidłowo eksponowana niższa cena z `[D: dowod-ceny-eksponowanej]` musi zostać zastosowana. [AUT-R 22.08] [R: PRICE-005]
- Rola weryfikująca potwierdza dowód, lecz nie wybiera wyższej ceny. [PROP+ 22.08]
- `[D: decyzja-podzialu]` musi zostać wykonana przed przyjęciem rozliczenia. [PROP+ 22.08]
- Każdy koszyk powstały z podziału jest liczony, akceptowany i finalizowany jako osobna sprzedaż. [PROP+ 22.08]
- Rozpoczęcie rozliczenia zamraża `[D: kwota-nalezna]`. [AUT-R 22.08]
- Zmiana koszyka, ceny, klienta albo korzyści po tym momencie wymaga odwrócenia lub uzgodnienia przyjętych rozliczeń, ponownego przeliczenia i nowej `[D: akceptacja-klienta]`. [AUT-R 22.08]
- Pełne pokrycie oznacza, że suma zaakceptowanych form rozliczenia pomniejszona o wydaną resztę lub udzielony kredyt jest równa `[D: kwota-nalezna]`. [PROP+ 22.08]
- Rozliczenie oczekujące nie tworzy pokrycia. [PROP+ 22.08]
- Rozliczenie offline, ręczne lub lokalnie zaakceptowane tworzy pokrycie wyłącznie w granicach `[D: polityka-ryzyka]`. [PROP+ 22.08]
- Późniejsze niepowodzenie rozliczenia uprzednio prawidłowo przyjętego jest wyjątkiem po sprzedaży. [PROP+ 22.08]
- Rachunek odroczony jest równoważną formą rozliczenia, jeśli istnieje `[D: uprawnienie-odroczone]`. [AUT-R 22.08]
- Rachunek odroczony tworzy pokrycie wyłącznie do wysokości limitu przypisanego na koncie klienta; kwota ponad ten limit nie tworzy pokrycia. [AUT-R 22.08]
- `[D: przedplata]` jest istniejącym pokryciem pochodzącym z procesu zamówienia, rezerwacji lub przedpłaty. [PROP+ 22.08]
- SAL-01 nie przyjmuje ponownie tej samej przedpłaty i nie inicjuje jej ponownej fiskalizacji. [PROP+ 22.08] [R: RTL-FISC-002]
- `[D: status-nabywcy]`, `[D: dane-fiskalne]` i `[D: kwalifikacja-fiskalna]` muszą być ustalone przed przekazaniem do SAL-02. [AUT-R 22.08] [R: RTL-FISC-001] [R: FISC-002] [R: FISC-007]
- Dane dokumentu muszą zostać przedstawione do kontroli przed jego fiskalnym zatwierdzeniem. [R: FISC-010]
- Numer identyfikacji podatkowej nabywcy musi być podany przed zatwierdzeniem dokumentu, jeśli ma się na nim znaleźć. [R: FISC-011]
- Nie wolno wystawić później faktury dla podatnika na podstawie paragonu bez tego numeru. [R: FISC-013]
- SAL-02 nie może zmienić `[D: kwota-nalezna]` zaakceptowanej w SAL-01. [AUT-R 22.08]
- **Korekta 03.09** [AUT-R 03.09]: sześć reguł tego miejsca (moment powstania wyniku fiskalnego względem przyjęcia należności, warunek dla rachunku odroczonego, zakaz kończenia sprzedaży bez wyniku fiskalnego, stan wyjątek-po-rozliczeniu i jego właściciel) przeniesionych do karty SAL-02, bo opisywały zdarzenia następujące po zakończeniu SAL-01, nie warunek jego zakończenia; poprzednie brzmienie tworzyło cykl (recenzja Sola, delta `e58a313`, finding B1).
- Sprzedaż i `[D: powiazany-zwrot]` pozostają dwoma wynikami, nawet gdy mają jedno rozliczenie netto. [PROP+ 22.08]
- Zawieszenie jest dozwolone przed finalizacją tylko bez aktywnego rozliczenia i z kompletnym `[D: zapis-zawieszenia]`. [PROP+ 22.08]
- Wygaśnięcie zawieszenia daje wynik porzucona, a nie anulowanie sfinalizowanej sprzedaży. [PROP+ 22.08]

**10. Skutki**

Stock: NIE bezpośrednio, ponieważ SAL-01 tylko przekazuje do SAL-03 pozycje z `[D: cecha-zapasowa]`. [PROP+ 22.08]

Pieniądze: TAK, ponieważ proces potwierdza pełne pokrycie kwoty przez wyniki PAY, przedpłatę lub uprawniony rachunek odroczony. [PROP+ 22.08]

Księgowość: TAK jako zdarzenie źródłowe sprzedaży, lecz dekretacja i rozrachunki nie należą do SAL-01. [PROP+ 22.08]

Nowy instrument przedpłacony może być pozycją sprzedaży, ale jego wartość tworzy zobowiązanie do przyszłego świadczenia. [PROP+ 22.08]

**11. Warianty i wyjątki kluczowe**

Wariant kanału zmienia sposób wykonania, ale nie warunki wyniku sprzedaży. [PROP+ 22.08]

Podzielona płatność pozostaje jednym rozliczeniem jednej sprzedaży. [AUT-R 22.08]

Podzielony koszyk tworzy niezależne sprzedaże. [PROP+ 22.08]

Sprzedaż z przedpłatą wykorzystuje wcześniejsze pokrycie bez duplikowania płatności ani fiskalizacji. [PROP+ 22.08]

Sprzedaż na rachunek odroczony wykorzystuje zatwierdzone uprawnienie jako formę pokrycia. [PROP+ 22.08]

Stany procesu to: przedstawiona, weryfikacja, oczekiwanie-na-decyzję, kwota-zaakceptowana, rozliczenie, zawieszona, porzucona i sfinalizowana. [PROP+ 22.08] **Korekta 03.09** [AUT-R 03.09]: usunięto oczekiwanie-na-fiskalizację i wyjątek-po-rozliczeniu, bo to stany SAL-02 następujące po sfinalizowana, nie stany SAL-01 (recenzja Sola, delta `e58a313`, finding B1).

**12. Bezpieczniki prawne (PL)**

Źródło pakietu: regulatory-matrix v1.0.1, legal_as_of 2026-08-14, content_status qualified_with_known_gaps. [R: metadata]

Właściciel macierzy polecił przyjąć pakiet jako aktualny na 22.08.2026. [PROP+ 22.08]

Właściciel potwierdził aktywność RTL-CONS-001 na 22.08.2026 mimo temporal_state unresolved i braku daty effective_from w pakiecie. RTL-DIST-001 nie jest wiązany w SAL-01 (sprzedaż na odległość poza zakresem; wiązanie w rejestrze tematów odłożonych GAP-SAL-01-02). [PROP+ 22.08]

Żadne z poniższych wiązań nie ma przypisanego aktywnego GAP-u ani defektu P0 w pakiecie consumer. [R: metadata]

| ID | Norma i lokator | Pewność i stan w RM | Rola w karcie |
|---|---|---|---|
| PRICE-005 | SRC-PRICE-INFO-2014, art. 5 | verified, active | zastosowanie potwierdzonej ceny korzystniejszej |
| PRIV-003 | SRC-EU-GDPR-2016-679, art. 5 ust. 1 lit. c i art. 25 ust. 1-2 | qualified, active | minimalizacja danych |
| RTL-PRIV-001 | SRC-EU-GDPR-2016-679, art. 12-14 | qualified, active | wersja informacji przy pozyskiwaniu danych |
| RTL-FISC-001 | SRC-VAT-2004, art. 111 ust. 1 i 1b | qualified, active | kwalifikacja do ewidencji |
| FISC-002 | SRC-VAT-2004, art. 111 ust. 8 i art. 145a ust. 17; akty wykonawcze wskazane w RM | qualified, active do 31.12.2027 | kwalifikacja zwolnienia |
| FISC-005 | SRC-FISC-CASH-2025-845, § 6 ust. 1 pkt 1; SRC-VAT-2004, art. 111 ust. 3a pkt 1 | qualified, active | paragon najpóźniej przy przyjęciu należności |
| FISC-007 | SRC-FISC-CASH-2025-845, § 8 ust. 1-3; SRC-FISC-TECH-2021-1759, § 22 pkt 1-31 | qualified, active | komplet danych dokumentu |
| FISC-010 | SRC-FISC-CASH-2025-845, § 6 ust. 1 pkt 10 | qualified, active | kontrola przed zatwierdzeniem |
| FISC-011 | SRC-FISC-TECH-2021-1759, § 22 pkt 24 | qualified, active | NIP przed zatwierdzeniem |
| FISC-013 | SRC-VAT-2004, art. 106b ust. 5-7 | qualified, active | zakaz późniejszej faktury dla podatnika z paragonu bez NIP |
| RTL-FISC-002 | SRC-FISC-CASH-2025-845, § 6 ust. 1 pkt 2 lit. a-b | qualified, active | właściwy moment fiskalizacji przedpłaty |
| RTL-CONS-001 | SRC-CONSUMER-RIGHTS-2014, art. 8 | qualified, unresolved w RM; aktywność potwierdzona przez właściciela | informacja przed akceptacją w placówce |

**13. Powiązanie w górę i mierniki**

Value stream: Sell Goods and Services. [PROP+ 22.08]

Mierniki podstawowe to współczynnik finalizacji, czas finalizacji, udział sprzedaży zakończonych bez wyjątku, częstość i wartość wyjątków handlowych, odwrócenia spowodowane błędem SAL-01 oraz naruszenia integralności z celem zero. [PROP+ 22.08]

Mierniki diagnostyczne to wiek transakcji zawieszonych, odrzucenia płatności oraz czas rozwiązania wyjątku po rozliczeniu. [PROP+ 22.08]

APQC rozdziela sprzedaż w placówce (21427) i sprzedaż cyfrową (21429) na osobne procesy; ORPR-SAL-01 obejmuje wyłącznie checkout stacjonarny, a sprzedaż na odległość jest przedmiotem odrębnej obsługi (rejestr tematów odłożonych GAP-SAL-01-02). [PROP+ 22.08] [LIT: APQC PCF Cross-Industry v7.4, dokument K014750, procesy 21427 i 21429]

ARTS RetailTransaction, SaleReturnTransaction oraz TenderLineItem stanowią kotwice pojęciowe dla transakcji, odrębności sprzedaży i zwrotu oraz form rozliczenia. [PROP+ 22.08] [LIT: ARTS Retail Data Model 7.3, RetailTransaction i TenderLineItem]

GS1 wspiera identyfikację i przetwarzanie danych pozycji na wejściu, ale nie definiuje całego procesu finalizacji sprzedaży. [PROP+ 22.08] [LIT: GS1 2D Barcodes at Retail Point-of-Sale Implementation Guideline 1.1.0, sekcje 2.2, 6.2 i 7.7]

## 14. Bank pytań analityka

### A. Do biznesu

A1. Która rola zatwierdza rabat ręczny? *(Dlaczego ważne: ustala odpowiedzialność za wyjątek handlowy.)*

A2. Jaki limit rabatu ma każda rola zatwierdzająca? *(Dlaczego ważne: oddziela standardową obsługę od eskalacji.)*

A3. Które pozycje są sprzedażą, a które wydaniem bez opłaty? *(Dlaczego ważne: chroni granicę sprzedaży i gratisu.)*

A4. Która rola potwierdza dowód niższej ceny eksponowanej? *(Dlaczego ważne: zapewnia właściciela decyzji cenowej.)*

A5. Do którego momentu klient może zażądać podziału koszyka? *(Dlaczego ważne: podział po rozliczeniu narusza spójność kwoty.)*

A6. Na którym etapie ustala się status nabywcy? *(Dlaczego ważne: dane dokumentu muszą być gotowe przed fiskalizacją.)*

A7. Która rola prowadzi wyjątek po rozliczeniu? *(Dlaczego ważne: przyjęta płatność nie może pozostać bez właściciela.)*

A8. Czy sprzedaż i zwrot są zawsze rejestrowane jako dwa wyniki? *(Dlaczego ważne: wspólne rozliczenie nie może zatrzeć natury zdarzeń.)*

A9. W których przypadkach identyfikacja klienta jest obowiązkowa? *(Dlaczego ważne: sprzedaż anonimowa ma pozostać domyślna poza uzasadnionym celem.)*

A10. Jak długo ważne jest zawieszenie transakcji? *(Dlaczego ważne: stan oczekujący potrzebuje jawnej daty wygaśnięcia.)*

### B. Do legacy

B1. Co dzieje się po wykryciu pozycji niedopuszczalnej w tej transakcji? *(Dlaczego ważne: proces nie może przejść dalej przez milczące pominięcie błędu.)*

B2. Co dzieje się po potwierdzeniu prawidłowo eksponowanej niższej ceny? *(Dlaczego ważne: wykrywa praktykę utrzymywania ceny wyższej mimo dowodu.)*

B3. Co dzieje się z korzyściami po zmianie identyfikacji klienta? *(Dlaczego ważne: wszystkie świadczenia zależne od klienta wymagają ponownego wyliczenia.)*

B4. Czy płatność oczekująca jest liczona jako pokrycie? *(Dlaczego ważne: status oczekujący nie potwierdza przyjęcia środków.)*

B5. Czy zmiana kwoty blokuje finalizację do uzgodnienia rozliczeń, ponownego przeliczenia i ponownej akceptacji klienta? *(Dlaczego ważne: kwota i płatność muszą pozostać uzgodnione.)*

B6. Jak wcześniejsza przedpłata jest konsumowana w sprzedaży? *(Dlaczego ważne: wykrywa ponowne pobranie albo ponowną fiskalizację.)*

B7. Kiedy zapisywany jest numer identyfikacji podatkowej nabywcy? *(Dlaczego ważne: zapis po zatwierdzeniu dokumentu jest spóźniony.)*

B8. Jaki stan otrzymuje transakcja po błędzie fiskalnym następującym po płatności? *(Dlaczego ważne: wyjątek musi pozostać widoczny do finalizacji lub odwrócenia.)*

B9. Co dzieje się po wygaśnięciu zawieszenia? *(Dlaczego ważne: porzucenie nie może udawać anulowania sprzedaży.)*

B10. Jak obsługiwane jest późniejsze odrzucenie rozliczenia zaakceptowanego offline? *(Dlaczego ważne: ryzyko po sprzedaży wymaga odrębnej obsługi.)*

B11. Które pozycje powodują przekazanie skutku do SAL-03? *(Dlaczego ważne: nie każda pozycja sprzedaży jest pozycją zapasową.)*

B12. Jak rejestrowana jest korekta sfinalizowanej sprzedaży? *(Dlaczego ważne: zapis pierwotny musi pozostać niezmienny.)*

### C. Do vendora

Dla każdego pytania C odpowiedź musi zawierać wynik, lokator w dokumentacji oraz poziom, na którym zachowanie jest konfigurowalne. [PROP+ 22.08]

C1. Czy rozwiązanie blokuje finalizację przy niedopuszczalnej pozycji? *(Dlaczego ważne: samo ostrzeżenie nie egzekwuje bramki.)*

C2. Czy rozwiązanie wymusza zastosowanie potwierdzonej niższej ceny eksponowanej? *(Dlaczego ważne: swobodny wybór ceny wyższej narusza przyjętą regułę.)*

C3. Czy rozwiązanie oblicza pełne pokrycie po uwzględnieniu reszty i kredytu? *(Dlaczego ważne: suma nominałów nie zawsze jest pokryciem netto.)*

C4. Czy rozwiązanie potrafi wykorzystać istniejącą przedpłatę bez ponownego jej przyjęcia? *(Dlaczego ważne: zapobiega podwójnemu rozliczeniu.)*

C5. Czy rozwiązanie pozwala zakończyć sprzedaż anonimową, gdy identyfikacja nie jest wymagana? *(Dlaczego ważne: brak danych klienta nie może być sztucznym blokerem.)*

C6. Czy rozwiązanie odrzuca typ pozycji oznaczający wydanie bez opłaty? *(Dlaczego ważne: cena zero nie powinna tworzyć fikcyjnej sprzedaży.)*

C7. Czy rozwiązanie zachowuje odrębne wyniki sprzedaży i zwrotu przy wspólnym rozliczeniu? *(Dlaczego ważne: kwota netto nie może zastąpić dwóch zdarzeń gospodarczych.)*

C8. Czy fiskalizacja może zmienić kwotę zaakceptowaną przez klienta? *(Dlaczego ważne: SAL-02 ma dokumentować, a nie ponownie wyceniać sprzedaż.)*

C9. Czy rozwiązanie utrzymuje stan wyjątku po rozliczeniu do finalizacji albo odwrócenia? *(Dlaczego ważne: przyjęte środki wymagają ciągłości odpowiedzialności.)*

C10. Czy wiele form płatności pozostaje jednym rozliczeniem jednej sprzedaży? *(Dlaczego ważne: liczba tenderów nie może mnożyć transakcji.)*

C11. Czy rozwiązanie odróżnia bezpośredni checkout od zamówienia oczekującego na potwierdzenie? *(Dlaczego ważne: tylko pierwszy rezultat należy do SAL-01.)*

### Czerwone flagi

F1. Niedopuszczalna `[D: pozycja-sprzedawalna]` albo `[D: dopuszczalnosc-transakcyjna]` przechodzi do finalizacji. Pytania: B1, C1. [PROP+ 22.08]

F2. Potwierdzony `[D: dowod-ceny-eksponowanej]` nie zmienia `[D: kwota-nalezna]` na korzystniejszą. Pytania: A4, B2, C2. [PROP+ 22.08] [R: PRICE-005]

F3. Zmiana `[D: identyfikacja-klienta]` nie przelicza `[D: wynik-promocji]` zależnego od klienta. Pytania: B3. [PROP+ 22.08]

F4. Oczekujący `[D: wynik-rozliczenia]` jest liczony jako pokrycie `[D: kwota-nalezna]`. Pytania: B4, C3. [PROP+ 22.08]

F5. `[D: kwota-nalezna]` zmienia się po rozpoczęciu rozliczenia bez uzgodnienia `[D: wynik-rozliczenia]` i nowej `[D: akceptacja-klienta]`. Pytania: B5. [PROP+ 22.08]

F6. `[D: przedplata]` jest pobierana albo ujmowana w `[D: wynik-fiskalny]` drugi raz. Pytania: B6, C4. [PROP+ 22.08] [R: RTL-FISC-002]

F7. `[D: dane-fiskalne]` nabywcy są dodawane dopiero po zatwierdzeniu dokumentu. Pytania: A6, B7. [PROP+ 22.08] [R: FISC-011] [R: FISC-013]

F8. Błąd `[D: wynik-fiskalny]` po przyjętym `[D: wynik-rozliczenia]` pozostawia transakcję bez właściciela. Pytania: A7, B8, C9. [PROP+ 22.08]

F9. Sprzedaż anonimowa jest blokowana mimo braku `[D: potrzeba-identyfikacji]`. Pytania: A9, C5. [PROP+ 22.08] [R: PRIV-003]

F10. `[D: powiazany-zwrot]` i sprzedaż są zapisane jako jedna sprzedaż netto. Pytania: A8, C7. [PROP+ 22.08]

F11. `[D: typ-pozycji]` oznaczający wydanie bez opłaty jest zapisany jako pozycja sprzedaży o cenie zero. Pytania: A3, C6. [PROP+ 22.08]

F12. Wygaśnięcie `[D: zapis-zawieszenia]` finalizuje albo anuluje nieistniejącą sprzedaż. Pytania: A10, B9. [PROP+ 22.08]

F13. `[D: wynik-fiskalny]` zmienia zaakceptowaną `[D: kwota-nalezna]`. Pytania: C8. [PROP+ 22.08]

F14. Wiele pozytywnych `[D: wynik-rozliczenia]` tworzy wiele sprzedaży. Pytania: C10. [PROP+ 22.08]

F15. `[D: typ-finalizacji]` oznaczający zamówienie oczekujące jest wykazywany jako sprzedaż SAL-01. Pytania: C11. [PROP+ 22.08]

## Źródła publiczne

1. Oracle Retail Xstore, Sale Tenders: https://docs.oracle.com/en/industries/retail/retail-xstore-point-of-service/21.0/rpxug/sale-tenders.htm
2. SAP Customer Checkout, Sales Receipts: https://help.sap.com/docs/SAP_CUSTOMER_CHECKOUT_CLOUD_POS/b1b79e86443b4a1e85bf299e1b58be70/d4825363974c4f569480f54c14f2a354.html
3. ARTS Retail Data Model 7.3, RetailTransaction: https://www.omg.org/retail-depository/arts-odm-73/retail_transaction.htm
4. ARTS Retail Data Model 7.3, TenderLineItem: https://www.omg.org/retail-depository/arts-odm-73/%7B2B6FA1B6-5860-42C7-BBC1-A122C059B2CE%7D%2B00000000.html
5. Microsoft Dynamics 365 Commerce, Suspend and recall transactions: https://learn.microsoft.com/en-us/dynamics365/commerce/pos-suspend-recall-transactions
6. GS1, 2D Barcodes at Retail Point-of-Sale, release 1.1.0: https://ref.gs1.org/guidelines/2d-in-retail/
7. Regulatory matrix consumer package: https://github.com/rafmyr/regulatory-matrix/tree/main/consumer
