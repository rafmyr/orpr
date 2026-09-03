# [ORPR-SAL-03] Sale-to-Inventory-Issue

| | |
|---|---|
| ID | ORPR-SAL-03 |
| Wersja karty | 0.1 |
| Status | reviewed |
| Regulatory matrix | regulatory-matrix v1.0.1, legal_as_of 2026-08-14, wartość odziedziczona z kart siostrzanych i wymagająca potwierdzenia |
| Klasa treści | rdzeń retail-neutralny |
| Clean-room | 2026-08-22: dyktando właściciela oraz źródła publiczne; bez materiałów klientów i pracodawców |

Legenda: `[AUT-R DD.MM]` oznacza wypowiedź właściciela z datą dyktanda; `[PROP]` oznacza propozycję redakcyjną oczekującą na decyzję; `[PROP+ DD.MM]` oznacza propozycję przyjętą; `[LIT: ...]` oznacza źródło publiczne z lokatorem; `[HIP]` oznacza hipotezę; `[do potwierdzenia]` oznacza fakt do sprawdzenia u źródła; `[do weryfikacji]` oznacza kandydata regulacyjnego bez potwierdzonego wiązania RM.

## Miejsce procesu w domenie SAL

SAL-01 kończy się udokumentowaniem sprzedaży. `[AUT-R 22.08]` **Korekta 2026-09-03** [ROZSTRZYGNIĘCIE WŁAŚCICIELA]: fiskalizacja jest osobnym procesem L1 (SAL-02, z własnym stanem wyjściowym `ST-DOKUMENT-FISKALNY`), nie częścią SAL-01 ani jego podprocesem L2. SAL-02 i SAL-03 konsumują ten sam stan `ST-SPRZEDAZ-SFINALIZOWANA` i są procesami równoległymi, nie łańcuchem; pytanie o kolejność między nimi nie ma zastosowania. **Korekta 03.09 (recenzja Sola, delta `e58a313`, finding B1):** wynik fiskalny nie jest bramką zakończenia SAL-01; poprzednie brzmienie tego akapitu twierdziło jednocześnie, że SAL-02 startuje po zakończeniu SAL-01 i że fiskalizacja jest bramką tego zakończenia, co jest cyklem. Zastępuje poprzednie zdanie `[AUT-R 22.08]` powyżej, utrzymane wyłącznie jako ślad korekty.

SAL-03 zaczyna się dla tych pozycji sprzedaży, które są zarządzane jako zapas. Proces prowadzi każdą sprzedaną ilość do wydania albo jawnego anulowania. `[PROP+ 22.08]`

Wydanie bez sprzedaży, realizacja bezpośrednio z zapasu zewnętrznego dostawcy oraz sprzedaż pozycji bez skutku zapasowego nie należą do SAL-03. `[PROP+ 22.08]`

## Model pojęciowy

### Dwa momenty skutku zapasowego

Udokumentowanie sprzedaży zobowiązuje zapas w konkretnej lokalizacji, zmniejsza ilość dostępną do kolejnej sprzedaży i może uruchomić replenishment, chociaż towar nadal fizycznie pozostaje w lokalizacji. `[AUT-R 22.08]`

Faktyczne wydanie klientowi albo przekazanie przewoźnikowi powoduje rozchód ze stanu ewidencyjnego. `[PROP+ 22.08]`

Anulowanie przed wydaniem zwalnia zobowiązanie oraz wytwarza zdarzenie kompensujące dla replenishmentu. `[PROP+ 22.08]`

Rozróżnienie sprzedaży od późniejszego wydania ma kotwicę w modelu ARTS: widok sprzedażowy zapasu wiąże ruch fizyczny z przejęciem towaru, a dla sprzedaży z dostawą albo odbiorem wyróżnia osobne potwierdzenie realizacji. `[LIT: ARTS Operational Data Model 7.3, Logical 02020 Item Inventory - Selling View, akapit Subject Area Concepts]`

### Jednostka realizacji

Jedna sprzedaż może zostać podzielona na wiele jednostek realizacji. Jednostka realizacji grupuje sprzedane ilości według lokalizacji źródłowej, sposobu wydania, terminu i aktualnego statusu. `[PROP+ 22.08]`

Jedna pozycja sprzedaży może zostać rozdzielona pomiędzy kilka jednostek realizacji, a jedna jednostka może zawierać fragmenty kilku pozycji sprzedaży. `[LIT: ARTS Operational Data Model 7.3, Logical 02315 Retail Transaction - Customer Order View, sekcja Linking Customer Orders, Shipments and Retail Transactions]`

### Granularność zapasu

Obowiązkowy poziom rdzenia to SKU, ilość i lokalizacja. Większość sieci nie zarządza zapasem na poziomie partii. `[AUT-R 22.08]`

Partia, seria albo konkretny egzemplarz są wymiarami warunkowymi. Występują wtedy, gdy organizacja faktycznie nimi zarządza albo wymaga tego charakter pozycji. `[PROP+ 22.08]`

ARTS utrzymuje ilościową ewidencję zapasu na poziomie SKU i pozwala detalistom dobierać dodatkowe wymiary stanu zapasu. `[LIT: ARTS Operational Data Model 7.3, Inventory Stewardship, sekcja ARTS Data Model Unit Control View of Inventory]`

### Model operacyjny

Pełny wariant wielolokalizacyjny jest charakterystyczny głównie dla większych sieci właścicielskich. `[AUT-R 22.08]`

Europejski Kodeks Etyki Franczyzy opisuje franczyzodawcę i franczyzobiorców jako prawnie i finansowo odrębne, niezależne przedsiębiorstwa. `[LIT: European Franchise Federation, European Code of Ethics for Franchising 2016, sekcja 1, s. 2 oraz sekcja 2.2-2.3, s. 2-3]`

ARTS uzasadnia transfer wewnątrz detalisty tym, że przedsiębiorstwo detaliczne pozostaje finansowym i fizycznym właścicielem przemieszczanego zapasu. `[LIT: ARTS Operational Data Model 7.3, InventoryFact, opis IntransitCount]`

O zastosowaniu odcinka wielolokalizacyjnego rozstrzygają własność zapasu i umocowanie kontraktowe, a nie sama etykieta modelu franczyzowego. Przy odrębnych właścicielach zapasu podstawą jest realizacja lokalna; realizacja przez partnera wymaga uzgodnionego przekazania między podmiotami, a nie przesunięcia INV-02. Jeżeli zapas w wielu lokalizacjach ma jednego właściciela, wariant z INV-02 może pozostać dostępny. `[PROP+ 22.08]`

W SAL-03 modele M0-M3 mogą zmieniać nie tylko obsadę decyzji, lecz również obecność odcinka wielolokalizacyjnego. `[HIP]`

**1. Cel biznesowy:** doprowadzić udokumentowaną sprzedaż do wydania wszystkich sprzedanych ilości albo ich jawnego anulowania, zapewniając prawidłowy skutek na dostępności i stanie zapasu. `[PROP+ 22.08]`

**2. Granice:** proces zaczyna się od udokumentowanej sprzedaży zawierającej co najmniej jedną pozycję zarządzaną jako zapas i przypisaną do lokalizacji źródłowej. `[AUT-R 22.08]`

Proces kończy się, gdy każda sprzedana ilość osiągnęła stan końcowy `wydana` albo `anulowana`. `[PROP+ 22.08]`

SAL-03 obejmuje zobowiązanie zapasu, warunkowe przygotowanie realizacji, wydania częściowe, zmianę źródła tej samej pozycji oraz potwierdzenie wydania. `[PROP+ 22.08]`

SAL-03 nie ustala ceny, płatności ani treści dokumentu sprzedaży; nie wykonuje przesunięcia między lokalizacjami jednego właściciela ani przekazania własności lub odpowiedzialności między odrębnymi podmiotami; nie koryguje rozbieżności zapasu; nie księguje kosztu własnego; nie prowadzi zwrotu po wydaniu. Przekazania: SAL-01, INV-02, uzgodniona realizacja partnerska, INV-03, FIN-02 oraz domena RTN. `[PROP+ 22.08]`

**3. Właściciel:** Order Fulfillment / Realizacja zamówień. `[PROP+ 22.08]`

Właściciel odpowiada za doprowadzenie każdej ilości do wydania albo anulowania, niezależnie od tego, która lokalizacja lub funkcja wykonuje poszczególne czynności.

**4. Aktorzy:** klient albo uprawniony odbierający; pracownik lokalizacji przygotowującej lub wydającej; kierownik sklepu; Order Fulfillment; Inventory Operations; funkcja organizująca wysyłkę; przewoźnik; właściciele procesów INV-02, INV-03 i RTN przy odpowiednich przekazaniach.

**5. Systemy:** rejestr sprzedaży; zarządzanie realizacją zamówień; ewidencja i dostępność zapasu; obsługa operacji lokalizacji; obsługa przesunięć; obsługa wysyłki. Karta L1 nie przesądza technologii ani sposobu integracji.

**6. Wyzwalacze:** udokumentowanie sprzedaży pozycji zarządzanej jako zapas, ze wskazaną lokalizacją źródłową. `[AUT-R 22.08]` Zdarzenia wpływające na aktywny przebieg: zakończenie przesunięcia, zmiana źródła, częściowe wydanie, upływ terminu, anulowanie sprzedaży, korekta zapasu oraz odzyskanie ciągłości operacyjnej.

**7. Wejścia (dokumenty i dane):**

- obowiązkowe:
  - udokumentowana sprzedaż [D! sprzedaz-udokumentowana];
  - pozycja sprzedaży z identyfikatorem SKU [D! pozycja-sprzedazy];
  - ilość sprzedana i dotąd nierozstrzygnięta [D! ilosc-sprzedana];
  - przypisana lokalizacja źródłowa [D! lokalizacja-zrodlowa];
  - stan i dostępność SKU w lokalizacji [D! dostepnosc-zapasu];
  - termin wydania albo nadania [D! termin-realizacji];
- warunkowe:
  - instrukcja sposobu wydania lub wysyłki [D! instrukcja-realizacji];
  - umocowanie do realizacji z zapasu należącego do innego podmiotu [D! umocowanie-partnerskie];
  - wymaganie identyfikacji partii, serii lub egzemplarza [D! wymaganie-sledzenia];
  - dane uprawnionego odbierającego [D! uprawnienie-odbiorcy];
  - potwierdzony wynik przesunięcia z INV-02 [D! wynik-przesuniecia];
  - zatwierdzona korekta zapasu z INV-03 [D! korekta-zapasu];
  - zdarzenie anulowania sprzedaży z RTN-01 [D! anulowanie-sprzedazy];
  - potwierdzenie wydania klientowi albo przekazania przewoźnikowi [D! potwierdzenie-wydania];
  - zdarzenia wykonane podczas utraty łączności, przeznaczone do późniejszego uzgodnienia [D! zdarzenia-do-uzgodnienia].

**8. Wyjścia:** zobowiązanie zapasu; zmiana dostępności i sygnał replenishmentowy; jednostka realizacji; potwierdzone wydanie; rozchód powiązany z pozycją sprzedaży; zwolnienie zobowiązania i zdarzenie kompensujące; przekazania do INV-02, uzgodnionej realizacji partnerskiej, INV-03, FIN-02 i RTN; wyjątek przeterminowanej realizacji; zamknięcie SAL-03.

**9. Bramki decyzyjne:**

### Warunki wejścia

- [D: sprzedaz-udokumentowana] istnieje i zawiera co najmniej jedną pozycję zarządzaną jako zapas.
- Każda [D: pozycja-sprzedazy] ma określoną [D: ilosc-sprzedana] oraz [D: lokalizacja-zrodlowa].
- [D: dostepnosc-zapasu] pozwala utworzyć zobowiązanie bez powstania stanu ujemnego. `[AUT-R 22.08]`
- Każda jednostka realizacji ma [D: termin-realizacji]. `[AUT-R 22.08]`

### Kontrole przebiegu

- Zobowiązanie powstaje w lokalizacji wskazanej przez [D: lokalizacja-zrodlowa], zmniejsza dostępność i wytwarza sygnał replenishmentowy. `[AUT-R 22.08]`
- Zmiana lokalizacji źródłowej jest dozwolona dla tej samej pozycji i ilości. Poprzednie zobowiązanie zostaje zwolnione, a nowe powstaje w nowej lokalizacji. Cena pozostaje bez zmian. `[AUT-R 22.08]`
- Jeżeli potrzebne jest fizyczne przesunięcie zapasu pozostającego u jednego właściciela, SAL-03 czeka na [D: wynik-przesuniecia]; przebieg przesunięcia należy do INV-02. `[PROP+ 22.08]`
- Zobowiązanie lub wydanie zapasu należącego do innego podmiotu jest dopuszczalne wyłącznie na podstawie [D: umocowanie-partnerskie]. Przekazanie własności, odpowiedzialności i rozliczenie między podmiotami nie należą do INV-02 ani do rdzenia SAL-03. `[PROP+ 22.08]`
- Przygotowanie realizacji jest odcinkiem warunkowym: może być niewidoczne przy wydaniu natychmiastowym, a przy odbiorze późniejszym albo wysyłce przebiega zgodnie z [D: instrukcja-realizacji] i obejmuje przygotowanie wymagane do wydania. `[PROP+ 22.08]`
- Rozchód nie powstaje bez [D: potwierdzenie-wydania]. Sam status sprzedaży nie jest potwierdzeniem fizycznego wydania. `[AUT-R 22.08]`
- W wariancie wysyłkowym momentem wydania jest przekazanie przesyłki przewoźnikowi. Doręczenie pozostaje poza SAL-03. `[AUT-R 22.08]`
- Przy wydaniu odroczonym odbierający musi spełnić [D: uprawnienie-odbiorcy]. Przy sprzedaży i wydaniu natychmiastowym identyfikacja nie jest wymagana wyłącznie z powodu wydania. `[PROP+ 22.08]`
- Konkretna partia, seria albo egzemplarz są wybierane podczas przygotowania lub wydania tylko wtedy, gdy [D: wymaganie-sledzenia] tego wymaga. `[AUT-R 22.08]`
- Wydanie może być częściowe. Suma ilości wydanych, anulowanych i nadal zobowiązanych nie może przekroczyć [D: ilosc-sprzedana].
- Stan ujemny jest zabroniony. Rozbieżność między zapasem fizycznym i ewidencyjnym zatrzymuje wydanie do czasu otrzymania [D: korekta-zapasu] z INV-03. `[AUT-R 22.08]`
- [D: anulowanie-sprzedazy] zwalnia niewydaną ilość oraz wytwarza zdarzenie kompensujące dla replenishmentu. `[PROP+ 22.08]`
- Brak łączności nie musi zatrzymywać wydania, jeżeli lokalizacja ma wiarygodne potwierdzenie sprzedaży i dostępności. [D: zdarzenia-do-uzgodnienia] muszą zostać później uzgodnione. `[AUT-R 22.08]`
- Po przekroczeniu [D: termin-realizacji] proces wchodzi w obsługę wyjątku. Sam upływ terminu nie zwalnia zobowiązania; uprawniona rola jawnie wybiera dalszą realizację, zmianę źródła albo anulowanie sprzedaży. Dopiero anulowanie zwalnia niewydaną ilość i wytwarza zdarzenie kompensujące dla replenishmentu. `[PROP+ 22.08]`

### Warunki wyjścia

- Każda ilość z [D: ilosc-sprzedana] ma stan końcowy `wydana` albo `anulowana`.
- Każda ilość `wydana` ma [D: potwierdzenie-wydania] oraz jednoznaczne powiązanie z pozycją sprzedaży, SKU i lokalizacją.
- Każda ilość `anulowana` ma [D: anulowanie-sprzedazy], zwolnione zobowiązanie i zdarzenie kompensujące.
- Nie istnieje nierozstrzygnięta ilość ani otwarte zobowiązanie bez terminu.

**10. Skutki:** stock: TAK. Udokumentowanie sprzedaży zmniejsza dostępność przez zobowiązanie, a wydanie zmniejsza stan ewidencyjny. `[AUT-R 22.08]` | pieniądze: NIE. Cena i płatność powstają poza SAL-03. `[PROP+ 22.08]` | księgowość: NIE bezpośrednio. SAL-03 przekazuje zdarzenie rozchodu do FIN-02 Inventory-to-COGS. `[PROP+ 22.08]`

**11. Warianty i wyjątki kluczowe:** wydanie natychmiastowe; odbiór późniejszy; realizacja mieszana; warunkowa realizacja wielolokalizacyjna u jednego właściciela zapasu; lokalna realizacja przy odrębnych właścicielach bez umocowania partnerskiego; realizacja partnerska na podstawie uzgodnienia między podmiotami; przesunięcie prowadzone przez INV-02; zmiana źródła tej samej pozycji; rozbieżność zapasu obsługiwana przez INV-03; brak łączności z późniejszym uzgodnieniem; warunkowa identyfikacja partii, serii lub egzemplarza; anulowanie przed wydaniem; ruch zwrotny po wydaniu prowadzony przez RTN.

**12. Bezpieczniki prawne (PL):** regulatory-matrix nie była dostępna. Wersja `regulatory-matrix v1.0.1, legal_as_of 2026-08-14` została odziedziczona i wymaga potwierdzenia.

| ID | Kandydat | Pewność w RM | Rola w karcie |
|---|---|---|---|
| GAP-SAL03-01 | uprawnienie odbierającego przy wydaniu odroczonym | brak dostępu | do weryfikacji |
| GAP-SAL03-02 | dowód przekazania przewoźnikowi lub odbierającemu | brak dostępu | do weryfikacji |
| GAP-SAL03-03 | termin i skutki niewydania opłaconego towaru | brak dostępu | do weryfikacji |
| GAP-SAL03-04 | identyfikacja partii, serii albo egzemplarza przy wydaniu | brak dostępu | do weryfikacji tylko dla odpowiednich klas pozycji |

**13. Powiązanie w górę:** value stream: Store Operations / Order Fulfillment. Typowe KPI pozostają do opracowania po potwierdzeniu, że mierzą rezultat procesu, a nie technologię wykonania.

## 14. Bank pytań analityka

### A. Do biznesu

A1. Który model M0-M3 opisuje relację między centralą i lokalizacjami? *(Dlaczego ważne: rozstrzyga, czy odcinek wielolokalizacyjny istnieje.)*

A2. Która funkcja odpowiada za doprowadzenie każdej sprzedanej ilości do wydania albo anulowania? *(Dlaczego ważne: bez jednego właściciela częściowe realizacje pozostają bez rozstrzygnięcia.)*

A3. Które sposoby realizacji występują: wydanie natychmiastowe, odbiór późniejszy, wysyłka czy model mieszany? *(Dlaczego ważne: określa odcinki warunkowe procesu.)*

A4. W którym momencie sprzedaż zobowiązuje zapas i uruchamia replenishment? *(Dlaczego ważne: zapobiega ponownej sprzedaży tej samej dostępności.)*

A5. Czy każda pozycja ma lokalizację źródłową przy udokumentowaniu sprzedaży? *(Dlaczego ważne: zobowiązanie musi obciążyć konkretny zapas.)*

A6. Kiedy można zmienić lokalizację źródłową tej samej pozycji? *(Dlaczego ważne: ustala prawo do przeplanowania realizacji bez zmiany sprzedaży.)*

A7. Czy lokalizacje mogą odmówić udziału w realizacji wielolokalizacyjnej? *(Dlaczego ważne: odróżnia wspólną sieć realizacji od niezależnych zapasów.)*

A8. Czy jedna pozycja sprzedaży może zostać wydana częściami? *(Dlaczego ważne: wymusza rozliczenie ilości na poziomie jednostek realizacji.)*

A9. Jaki termin obowiązuje dla każdej klasy odbioru lub wysyłki? *(Dlaczego ważne: zapas nie może pozostać zablokowany bezterminowo.)*

A10. Co biznesowo dzieje się po przekroczeniu terminu niewydanej realizacji? *(Dlaczego ważne: rozstrzyga dalszą realizację albo anulowanie.)*

A11. Kiedy wymagane jest potwierdzenie uprawnienia odbierającego? *(Dlaczego ważne: ogranicza wydanie niewłaściwej osobie.)*

A12. Dla których pozycji trzeba wskazać partię, serię albo egzemplarz? *(Dlaczego ważne: rdzeń pozostaje na SKU, ale nie gubi wymaganej identyfikowalności.)*

A13. Kto może zainicjować korektę, gdy towar istnieje fizycznie, lecz ewidencja nie pozwala na wydanie? *(Dlaczego ważne: zapobiega obchodzeniu zakazu stanu ujemnego.)*

A14. Które wydania bez sprzedaży występują i jaki proces jest ich właścicielem? *(Dlaczego ważne: nie wolno mieszać powodów zmiany zapasu.)*

A15. Czy występuje realizacja bezpośrednio z zapasu zewnętrznego dostawcy? *(Dlaczego ważne: taki wariant nie powoduje rozchodu własnego zapasu.)*

A16. Jakie minimum informacji pozwala kontynuować wydanie przy braku łączności? *(Dlaczego ważne: ciągłość nie może oznaczać wydawania bez potwierdzenia sprzedaży i dostępności.)*

A17. Kto jest właścicielem zapasu w każdej lokalizacji mogącej realizować sprzedaż? *(Dlaczego ważne: ta sama marka sieci nie oznacza wspólnej własności zapasu.)*

A18. Jakie umocowanie pozwala jednemu podmiotowi zobowiązać lub wydać zapas należący do innego podmiotu? *(Dlaczego ważne: realizacji partnerskiej nie wolno traktować jak wewnętrznego przesunięcia.)*

### B. Do legacy

B1. Jakie stany odróżniają zapas dostępny, zobowiązany i wydany? *(Dlaczego ważne: wykrywa utożsamienie sprzedaży z rozchodem.)*

B2. Czy udokumentowanie sprzedaży pomniejsza dostępność w konkretnej lokalizacji? *(Dlaczego ważne: brak zobowiązania umożliwia ponowną sprzedaż.)*

B3. Jakie zdarzenie faktycznie zmniejsza stan ewidencyjny? *(Dlaczego ważne: rozchód powinien wynikać z wydania.)*

B4. Czy system zachowuje osobne statusy dla części tej samej pozycji sprzedaży? *(Dlaczego ważne: realizacja częściowa nie może zamknąć całości.)*

B5. Co dzieje się z poprzednim zobowiązaniem po zmianie lokalizacji? *(Dlaczego ważne: pozostawione zobowiązanie zaniża dostępność.)*

B6. Jak SAL-03 rozpoznaje zakończenie przesunięcia przez INV-02? *(Dlaczego ważne: nie można wydać towaru przed przyjęciem.)*

B7. Co dzieje się, gdy ilość fizyczna jest większa niż ewidencyjna? *(Dlaczego ważne: wykrywa stan ujemny albo ukrytą korektę.)*

B8. Jak są obsługiwane zobowiązania po terminie? *(Dlaczego ważne: ujawnia trwale zablokowany zapas.)*

B9. Czy anulowanie zwalnia zapas i koryguje replenishment? *(Dlaczego ważne: bez kompensacji zapotrzebowanie pozostaje zawyżone.)*

B10. Czy rozchód można powiązać z konkretną ilością pozycji sprzedaży? *(Dlaczego ważne: zapis zbiorczy nie może zerwać śladu biznesowego.)*

B11. Jak uzgadniane są wydania wykonane podczas braku łączności? *(Dlaczego ważne: brak uzgodnienia rozjeżdża dostępność i stan.)*

B12. Czy przebieg odróżnia przesunięcie zapasu jednego właściciela od realizacji przez odrębny podmiot? *(Dlaczego ważne: oba przypadki mają inne granice odpowiedzialności i rozliczenia.)*

### C. Do vendora

C1. Czy rozwiązanie rozdziela dostępność, zobowiązanie i stan ewidencyjny? *(Dlaczego ważne: jedna liczba nie obsłuży odroczonego wydania.)*

C2. Czy pozycję sprzedaży można podzielić między kilka jednostek realizacji i lokalizacji? *(Dlaczego ważne: potrzebne dla wydań częściowych.)*

C3. Czy zmiana źródła zwalnia poprzednie zobowiązanie? *(Dlaczego ważne: chroni dostępność starej lokalizacji.)*

C4. Czy przesunięcie między lokalizacjami ma własne potwierdzenie przyjęcia? *(Dlaczego ważne: rozdziela SAL-03 od INV-02.)*

C5. Czy rozchód wymaga potwierdzenia wydania klientowi albo przewoźnikowi? *(Dlaczego ważne: status sprzedaży nie dowodzi ruchu fizycznego.)*

C6. Czy można zablokować stan ujemny i dopuścić zatwierdzoną korektę kierownika? *(Dlaczego ważne: rozdziela wydanie od korekty.)*

C7. Czy partie, serie i egzemplarze są konfigurowalne per klasa pozycji? *(Dlaczego ważne: nie wolno narzucić jednej granularności.)*

C8. Czy anulowanie zwalnia zobowiązanie i emituje kompensację? *(Dlaczego ważne: oba skutki muszą być symetryczne.)*

C9. Czy każda jednostka realizacji ma termin i jawny stan po jego przekroczeniu? *(Dlaczego ważne: wykrywa bezterminowe realizacje.)*

C10. Czy system utrzymuje bilans ilości wydanych, anulowanych i zobowiązanych wobec ilości sprzedanej? *(Dlaczego ważne: suma musi pozostać zamknięta.)*

C11. Czy po braku łączności można uzgodnić wszystkie zdarzenia wydania? *(Dlaczego ważne: ciągłość wymaga domknięcia ewidencji.)*

C12. Czy rozwiązanie potrafi wymagać umocowania przed zobowiązaniem zapasu należącego do innego podmiotu? *(Dlaczego ważne: dostępność techniczna nie jest prawem do dysponowania zapasem.)*

### Czerwone flagi

F1. Sprzedaż nie zmniejsza dostępności i ta sama ilość może zostać sprzedana ponownie. Pytania: A4, B2, C1.

F2. Sprzedaż zmniejsza stan ewidencyjny mimo późniejszego odbioru. Pytania: B1, B3, C1.

F3. Pozycja ma jeden status mimo wydania częściowego. Pytania: A8, B4, C2.

F4. Zmiana źródła pozostawia zobowiązanie w starej lokalizacji. Pytania: A6, B5, C3.

F5. SAL-03 wykonuje przesunięcie bez osobnego INV-02. Pytania: B6, C4.

F6. Rozchód powstaje bez potwierdzenia wydania. Pytania: B3, C5.

F7. Wydanie tworzy stan ujemny. Pytania: A13, B7, C6.

F8. Korekta stanu jest ukryta w wydaniu. Pytania: A13, B7, C6.

F9. Rezerwacje po terminie pozostają otwarte bez decyzji. Pytania: A9, A10, B8, C9.

F10. Anulowanie nie zwalnia zapasu albo nie koryguje replenishmentu. Pytania: B9, C8.

F11. Każda pozycja jest obowiązkowo zarządzana na poziomie partii. Pytania: A12, C7.

F12. Wymagana partia albo seria nie jest zapisana przy wydaniu. Pytania: A12, C7.

F13. Wydanie odroczone trafia do osoby bez uprawnienia. Pytania: A11, C5.

F14. Wydania wykonane bez łączności nie są później uzgadniane. Pytania: A16, B11, C11.

F15. Sprzedaż jest zamknięta z ilością bez stanu `wydana` albo `anulowana`. Pytania: B4, C10.

F16. Wydanie bez sprzedaży albo z zapasu zewnętrznego jest rozliczane jako SAL-03. Pytania: A14, A15.

F17. Ruch albo realizacja między odrębnymi właścicielami zapasu jest traktowana jak zwykłe przesunięcie INV-02. Pytania: A17, A18, B12, C12.
