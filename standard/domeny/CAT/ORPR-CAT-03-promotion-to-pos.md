# [ORPR-CAT-03] Promotion-to-POS
Podtytuł roboczy (PL): od decyzji handlowej o promocji do jej aktywacji, obowiązywania i wygaśnięcia w POS oraz kanałach.

| | |
|---|---|
| ID | ORPR-CAT-03 (wg standard/mapa-procesow.md; freeze notacji: obowiązuje od v0.1.0) |
| Wersja karty | 0.12 (dwunasta) |
| Status | **reviewed** (19.08.2026). Twierdzenia rozstrzygnięte przez właściciela w arkuszu decyzyjnym, bank pytań i flagi podniesione do poziomu CAT-01 i CAT-02 na bazie researchu 19.08. Do `released` brakuje niezależnej recenzji wydaniowej wg KONSTYTUCJI sekcja 6 |
| Zmiany w 0.5 (19.08.2026) | podłoże cenowe oddane do ORPR-CAT-02 (decyzja właściciela, opcja A, P13); usunięte duplikaty pytań A1-A2, B3, C4; naprawione naruszenie P15 w polu 9 (instancje branżowe zastąpione pojęciem-klasą) |
| Zmiany w 0.6 (19.08.2026) | terminologia zrównana z CAT-02: „cena bazowa" -> **„cena regularna"** (termin główny standardu); doprecyzowana granica dla sprzedaży ze stratą jako taktyki handlowej |
| Zmiany w 0.7 (19.08.2026) | arkusz decyzyjny właściciela: oś wstępna modelu relacji sieć-lokalizacja wchodzi do promocji; omnichannel i forecast przeklasyfikowane na warunkowe; oferty targetowane dopuszczalne przy jawnym oznaczeniu; zwrot promocyjny linkuje do CAT-02, punkty i kupony anulowane; wszystkie gołe `[AUT]` rozstrzygnięte |
| Zmiany w 0.8 (19.08.2026) | **bank pytań 30 -> 121, wszystkie z uzasadnieniem; czerwone flagi 11 -> 35; priorytety P0-P4**. Podstawa: research 19.08 (35 anty-wzorców z lokatorami, 31 źródeł publicznych), wewnętrzny materiał badawczy |
| **Tagi `[AUT-R]` / `[PROP]`** | **ROZSTRZYGNIĘTE 19.08.2026.** Karta powstała w sesji 2 pod jednym tagiem `[AUT]`, bez zapisu, co pochodzi od właściciela. Autorstwa NIE rekonstruowaliśmy z pamięci, bo to byłoby zgadywanie. Zamiast tego arkusz decyzyjny pytał o **treść**: `[AUT-R 19.08, potwierdzone]` oznacza twierdzenie potwierdzone przez właściciela 19.08, a nie zrekonstruowaną datę dyktanda. Cztery pozycje przyniosły korektę merytoryczną, nie samo zatwierdzenie. Arkusz (nośnik SHA-pinnowany, Faza 3 20.08): wewnętrzny materiał roboczy |
| Zmiany w 0.9 (19.08.2026) | naprawa po recenzji wydaniowej: **wprowadzona klasa `[LIT: ...]` i dopisane 23 lokatory** przy flagach niosących największe ryzyko nadinterpretacji; sześć flag researchowych (F13, F17-F21) lokatora jeszcze nie ma, mimo że research go dostarczył; cztery asercje prawa i rachunkowości (F26, F27, F28, F34) przeniesione do `[do weryfikacji]` z jawnym „karta nie przesądza"; poprawione umocowanie rachunkowe w polu 10 (IAS 2 § 11 zamiast niepotwierdzonego lokatora IFRS 15); **rozstrzyganie konfliktów opisane jako wymaganie ORPR, nie odczyt z ARTS**; F11, F7 i F2 dostały pytania faktycznie wykrywające; przywrócone hedge zgubione przy przejściu research na kartę (F14, F15, F22, F24, F35); pole 7 deklaruje historię ceny, listę kategorii ograniczonych i regułę zaokrąglenia; bank 121 -> 137 pytań, w tym pokrycie osi kwalifikacji (eligibility) |
| Zmiany w 0.10 (19.08.2026) | naprawa po recenzji wydaniowej FABLE: bank policzony na **137 pytań** zamiast raportowanych 139 (licznik zliczał wystąpienia zamiast unikatów i brał zawinięte listy referencji we flagach za pytania); **trzy GAP-y zapowiedziane w polu 12 dopisane do wewnętrznego rejestru tematów odłożonych** (UCPD, VAT-gratis, punkty-IFRS); uzasadnienia A51, A36, A37 i A39 przestały asertować prawo i rachunkowość, przeniesione na `[do weryfikacji]` spójnie z flagami F26, F27 i F28 (poprzednia naprawa objęła flagi, nie objęła pytań, z których flagi wyrosły); pole 7 deklaruje wykluczenia i listę pozycji nieobjętych promocją, konsumowane przez pole 9 i F18 |
| Zmiany w 0.11 (20.08.2026) | naprawa po recenzji delty FABLE: A51 odsyłało do F26 (gratis i VAT) zamiast wyłącznie do F27 (punkty lojalnościowe) - poprawione; pole 10 dostało **lustrzany zapis przymusu asortymentowego**, czyli jedyne wymaganie, które ta karta stawia ORPR-CAT-01 (dotąd CAT-01 twierdziła, że ono tu jest, a nie było) |
| Zmiany w 0.12 (20.08.2026) | naprawa po recenzji delty: lustrzany zapis przymusu asortymentowego w polu 10 nosił tag `[AUT-R 19.08, potwierdzone]`, którego legenda tej karty wiąże z arkuszem decyzyjnym, a w arkuszu tego twierdzenia nie ma. Atrybucja poprawiona: źródłem jest dyktando właściciela zapisane w ORPR-CAT-01. Treść zdania bez zmian, zmieniła się wyłącznie klasa tagu |
| Klasa treści | rdzeń retail-neutralny; warstwa branżowa w profile/ (P15) |
| Źródło treści | dyktando właściciela z praktyki (sesja 2, potwierdzone punktowo 19.08.2026); wzbogacenie: recenzja + research 18.08.2026 (źródła: wewnętrzny materiał badawczy) |
| Bezpieczniki R | regulatory-matrix v1.0.1, legal_as_of 2026-08-14 (patrz pole 12) |
| Crosswalk | standard/mapowania/crosswalk-frameworki.md (APQC / ARTS-NRF / GS1) |
| Clean-room | 2026-08-18: wiedza dziedzinowa i prawo powszechne; zero materiałów klientów i pracodawców |

> Uwaga recenzyjna: `[AUT-R 19.08, potwierdzone]` to twierdzenie potwierdzone przez właściciela w arkuszu decyzyjnym 19.08.2026; `[PROP+ 19.08]` to propozycja redakcyjna, której właściciel nie potwierdza z pierwszej ręki, ale ją przyjmuje. `[R: ...]` to wiązania z regulatory-matrix (verified strukturalnie, nie opinia prawna). `[do weryfikacji]` to kandydaci do zgłoszenia maintainerowi RM, NIE asertowani jako prawo. `[LIT: źródło, wersja, lokator]` to źródło publiczne z lokatorem, weryfikowalne przez recenzenta, nie przez właściciela; ta sama klasa co w ORPR-CAT-01 i ORPR-CAT-02. `[AUT: ...]` nie jest klasą tej karty i nie występuje.
>
> **Zakres tagu `[PROP+ 19.08, research]`, rozstrzygnięty 19.08.2026.** Recenzja wydaniowa zgłosiła,
> że 24 flagi noszą ten tag, choć właściciel zaakceptował zakres pracy („podnosimy"), a nie każde
> twierdzenie z osobna. **Właściciel rozstrzygnął: tag zostaje, twierdzenia przyjmuje**
> [AUT-R 19.08, potwierdzone]. Czytelnik ma więc rozumieć `[PROP+ ..., research]` jako: twierdzenie
> pochodzi z researchu z lokatorem, właściciel nie jest jego źródłem pierwszoosobowym, ale bierze
> je na siebie.

## Model pojęciowy promocji w sieci (kontekst dla analityka)

### Oś wstępna: model relacji sieć-lokalizacja wyznacza, KTO PROWADZI politykę promocyjną

To jest pierwsza zmienna do ustalenia, przed czymkolwiek innym. Ta sama oś rządzi kierunkiem
przepływu ceny w ORPR-CAT-02 (oś 1) i decyzją asortymentową w ORPR-CAT-01 (oś wstępna). W promocji
odwraca się identycznie [AUT-R 19.08, potwierdzone]:

| Model relacji | Kto prowadzi politykę promocyjną | Rola drugiej strony |
|---|---|---|
| sieć własna, franczyza twarda | centrala: **centralny cennik i centralny silnik promocyjny** | lokalizacja: **nakładki lokalne** na tym, co pozwala centrala |
| franczyza miękka, sieć partnerska | lokalizacja: **własne cenniki i własna polityka promocyjna** | centrala: promocje centralne, pod które lokalizacja **koryguje wybrane ceny i promocje** |

Konsekwencja projektowa: w modelu miękkim „centralna promocja" nie jest promocją nałożoną na sklep,
tylko **zaproszeniem, które sklep wykonuje u siebie**. Analityk, który założy jeden model, zaprojektuje
zły model uprawnień i złą architekturę dystrybucji. To jest trzecia karta, w której ta sama oś
wywraca się samodzielnie.
**Macierz obsady bramek dla wszystkich modeli: `standard/mapowania/modele-operacyjne.md`.**
Tam stoi test klasyfikacyjny (trzy pytania), pełna macierz bramka razy model dla trzech kart domeny
CAT oraz rejestr odcinków warunkowych. Ta karta nie powtarza macierzy [PROP+ 19.08, redakcja].


Warstwy do rozpoznania u klienta:

- **Podłoże cenowe (cennik wielopoziomowy, matryca marżowa, poziomy polityki cenowej):** opisane
  w karcie **ORPR-CAT-02 Price-to-POS**, która jest właścicielem ceny regularnej. Ta karta linkuje
  zamiast powtarzać (decyzja właściciela 19.08.2026, P13). Z CAT-02 przychodzą tu dwie rzeczy:
  cena regularna jako punkt startowy mechaniki oraz historia ceny jako jedyne źródło ceny odniesienia
  przy ogłaszaniu obniżki [R: PRICE-001..003].
- **Omnichannel: warunkowo, nie z definicji.** Tam, gdzie detalista faktycznie prowadzi sprzedaż
  wielokanałową, silnik zwykle obsługuje wszystkie kanały. **Nie jest to jednak reguła rynku**:
  część sieci nie ma kanału cyfrowego w ogóle, a część prowadzi go na osobnym silniku
  [AUT-R 19.08, potwierdzone]. Pytanie o to jest wejściowe, nie uzupełniające.
- **Powiązanie z forecastem: odcinek warunkowy.** Tam, gdzie forecast istnieje, promocja jest
  planowana pod marżę brutto i generuje wskazania zakupowe. **Zakładać należy jednak, że większość
  sieci handlowych forecastu nie ma** [AUT-R 19.08, potwierdzone]. Karta opisuje ten odcinek jako
  warunkowy: analityk najpierw ustala, czy forecast w ogóle istnieje, a dopiero potem pyta o jego
  sprzężenie z promocją. Odwrotna kolejność produkuje wymagania na proces, którego nie ma.
- **Widok modelu danych (ARTS/NRF):** promocja to nie „krok procesu", lecz **trzy byty odczytane
  wprost z modelu**: **reguła** (PriceDerivationRule) + **modyfikator** (RetailPriceModifier) +
  **kwalifikacja** (Eligibility, osobna oś). Powinny być osobnymi, wersjonowanymi, audytowalnymi
  obiektami; wymaga tego też R (PRICE-001: historia ceny odniesienia). [C: crosswalk]
  **Czwarty element, rozstrzyganie konfliktów, jest wymaganiem ORPR wykraczającym poza model danych
  ARTS**: w przeszukanym materiale nie znaleziono encji ani obszaru, który by go opisywał. Karta
  stawia go jako własne wymaganie, nie jako odczyt ze standardu [PROP+ 19.08, naprawa po recenzji
  wydaniowej].

## Cykl życia promocji (value stream „Promocja")

definicja -> publikacja i konfiguracja w POS/kanałach -> obowiązywanie i sprzedaż -> raportowanie
skuteczności -> rozliczenie z producentem (rabat retro). Ta karta (CAT-03) opisuje odcinek do
wygaśnięcia w POS.

Dwa dalsze odcinki dostały **własne identyfikatory 19.08.2026** i celowo **nie są kartami
promocyjnymi**, bo obie klasy procesów obsługują więcej niż promocję (standard/mapa-procesow.md,
sekcja „Procesy dopisane ponad kamieniołom"):
- **ORPR-CAT-04 Commercial-Action-to-Effect**: pomiar efektu zamkniętej akcji handlowej i werdykt
  o powtórzeniu. Ta sama mechanika dotyczy zmiany ceny regularnej (CAT-02) i zmiany asortymentu
  (CAT-01), więc proces jest szerszy niż promocja; promocja jest jednym z wyzwalaczy. CAT-03
  dostarcza mu raport skuteczności (pole 8) i definicję akcji jako założenie odniesienia;
- **ORPR-PRC-04 Trade-Terms-to-Settlement**: rozliczenie warunków handlowych z dostawcą, w tym rabat
  retro odsprzedażowy, premie od skuteczności i usługi obudowujące kontrakt. Umieszczone w domenie
  zakupów, nie w CAT, bo korzyść pozafakturowa bywa wyzwalana celem wolumenowym albo opłatą za
  obecność w asortymencie, bez żadnej promocji w tle.

Obie karty niezredagowane; wpisy z warunkiem podjęcia w wewnętrznym rejestrze tematów odłożonych.

**1. Cel biznesowy:** przełożyć zatwierdzoną decyzję handlową o promocji na obowiązującą w oznaczonym
oknie mechanikę w POS i kanałach wszystkich objętych lokalizacji, w ramach wspólnej polityki
handlowej sieci, tak by kasa naliczała promocję poprawnie i deterministycznie, z zachowaniem
obowiązków informacyjnych (R), a efekt marżowy był policzalny i rozliczalny wobec producenta.

**2. Granice:** od zatwierdzonej definicji promocji do potwierdzonej aktywacji w POS/kanałach i
zaplanowanego wygaśnięcia. Następne odcinki value streamu: raportowanie skuteczności, rozliczenie
z producentem (rabat retro). NIE obejmuje naliczania przy sprzedaży (-> ORPR-SAL-01) ani obsługi
zwrotu towaru (-> ORPR-RTN-*), ale definiuje reguły cenowe zwrotu promocyjnego przekazywane do RTN
(patrz pole 11, zwroty).

**3. Właściciel:** Merchandising / Category Management. Definiuje struktura centralna (marketing,
category/product managerowie); polityka na poziomach centralnym, regionalnym, segmentu, lokalnym. [AUT-R 19.08, potwierdzone]

**4. Aktorzy:** category/product manager i marketing (centrala), manager regionalny, kierownik sklepu
(promocje lokalne, indywidualna przecena), sprzedawca (ręczny wybór promocji, przecena), compliance/
prawny, kontroling (raportowanie i rozliczenie). Producent jako strona kontraktu i inicjator akcji. [AUT-R 19.08, potwierdzone]

**5. Systemy:** centralny silnik promocyjny (nakładka na cennik), cennik wielopoziomowy albo marżownik,
POS, kanały omnichannel (digital), program lojalnościowy, silnik forecastowy, moduł rozliczeń
z producentem. [AUT-R 19.08, potwierdzone]

**6. Wyzwalacze:** plan/kalendarz promocyjny; akcja handlowa (gazetka - zestaw promocji w jednym oknie);
akcja producencka (ogólnopolska lub lokalna, z zaproszeniem retailera); kontrakt z producentem;
wczytanie kuponu; decyzja lokalna (konkurencyjność, wyprzedaż nadmiaru); uruchomienie ręczne. Okno:
okres, dzień tygodnia albo godziny. [AUT-R 19.08, potwierdzone]

**7. Wejścia (dokumenty):**
- obowiązkowe: definicja promocji (mechanika, poziom, forma korzyści, warunki), zakres asortymentu
  (produkt, wielokrotność, kategoria, producent), okno czasowe, zakres organizacyjny, cennik regularny
  albo marżownik, reguły promocji (pierwszeństwo, łączenie, **wykluczenia (exclusions)**, kolejność
  naliczania, minimalna marża) oraz **uzgodniona lista pozycji i kategorii nieobjętych promocją**;
  wykluczenia i ta lista są tu wymienione imiennie, bo konsumuje je warunek wejścia z pola 9 oraz
  flaga F18 (rabat koszykowy omijający wykluczenia pozycyjne)
  [PROP+ 19.08, naprawa po recenzji wydaniowej];
  **historia ceny regularnej i wyliczona z niej cena odniesienia** [-> ORPR-CAT-02], bo konsumuje je
  warunek wejścia z pola 9 (obowiązki informacyjne) oraz F30 (silnik czyta historię w momencie
  ogłaszania, nie bierze liczby z bieżącego cennika); **lista kategorii z ograniczeniem albo zakazem
  obniżki i z ceną regulowaną**, bo konsumuje ją warunek wejścia „dopuszczalność prawna kategorii
  potwierdzona" [PROP+ 19.08, naprawa po recenzji wydaniowej]; **reguła zaokrąglenia ceny
  promocyjnej**, bo konsumuje ją kontrola spójności paragonu z raportem (F7).
- opcjonalne: wskazania z forecastu; kontrakt producenta (rekompensata, premia od skuteczności, rabat
  retro odsprzedażowy z warunkami wolumenowymi; często obudowany usługami: wykup półki, miejsce
  w gazetce, premie w systemie personelu - patrz ostrzeżenie prawne w polu 12); definicja kuponu;
  powiązanie z programem lojalnościowym; budżet promo.

**8. Wyjścia:** dokumenty: opublikowana definicja promocji z regułami, konfiguracja w silniku/cenniku
rozdystrybuowana do POS i kanałów, raport skuteczności (podstawa raportowania i rozliczenia retro) |
zdarzenia: promocja-aktywowana, promocja-wygasła.

**9. Bramki decyzyjne:**
- warunki wejścia: mechanika jednoznaczna i rozstrzygalna przez kasę; przy kilku cennikach jednoznaczne,
  który wygrywa (poziom cennika); reguły pierwszeństwa, łączenia (combinability), wykluczeń (exclusions)
  i kolejności naliczania zdefiniowane; **margin floor** spełniony (twardy próg w silniku, nie w Excelu
  analityka) [AUT-R 19.08, potwierdzone]; dopuszczalność prawna kategorii potwierdzona
  [AUT-R 19.08, potwierdzone]: część kategorii ma ustawowe ograniczenia lub zakaz obniżek, a część ma
  cenę regulowaną albo urzędowo ustalaną; instancje branżowe wyłącznie w `profile/` i w overlay RM,
  nie w rdzeniu (P15). Pytania wykrywające: A53, A54, C43;
  obowiązki informacyjne o cenie i obniżce spełnione [R: PRICE-001..005]; równy dostęp do promocji po
  spełnieniu warunków, warunkowanie otwartym programem lojalnościowym dopuszczalne. **Oferty
  targetowane są dopuszczalne, ale muszą być wyraźnie oznaczone dla konsumenta** jako oferta
  skierowana do niego, a nie jako cena ogólnie obowiązująca [AUT-R 19.08, potwierdzone]. Reguła
  standardu brzmi więc: nie „równy dostęp albo nic", tylko **jawność adresowania**. Wymagane
  systemowo: silnik musi umieć oznaczyć ofertę jako targetowaną i przenieść to oznaczenie na nośnik
  ceny i do kanału. Umocowanie regulacyjne personalizacji 1:1 pozostaje niezweryfikowane w RM
  i jest zgłoszone jako luka, patrz pole 12; karta nie przesądza dopuszczalności prawnej.
- warunki wyjścia: konfiguracja potwierdzona we wszystkich objętych POS i kanałach PRZED startem okna;
  ustawiony tryb wyboru (optymalny zestaw / najwyższy priorytet / ręczny wybór sprzedawcy); wygaśnięcie
  zaplanowane; cena i marża wracają po wygaśnięciu do regularnej (nie „zawisa").
- kontrole: reguła pierwszeństwa i kolejności naliczania; dopuszczalność łączenia; margin floor; poziom
  cennika/marżownika; spójność ceny promo z podatkiem; spójność ceny na etykiecie i w POS [R: PRICE-005].

**10. Skutki (w tym odcinku) i sprzężenia międzydomenowe:**
- stock: NIE (konfiguracja ceny; wyjątek: gratis/multipak - obsługa kompletu -> L2) | pieniądze: NIE
  w konfiguracji (skutek przy sprzedaży, ORPR-SAL) | księgowość: NIE w tym odcinku.
- **Sprzężenie do asortymentu, jedyne w tym kierunku:** przymus asortymentowy z akcji reklamowej
  sieci **wymusza obecność pozycji w asortymencie lokalizacji**, więc ta karta stawia wymaganie
  ORPR-CAT-01, a nie odwrotnie. Bywa zapisem umownym: obowiązek posiadania na półce całego
  asortymentu objętego akcją. **Źródłem tego twierdzenia jest dyktando właściciela zapisane
  w ORPR-CAT-01** (tam nosi tag `[AUT-R 19.08]`), nie arkusz decyzyjny tej karty; dlatego lustro
  nie nosi tu tagu arkuszowego. Macierz: `standard/mapowania/modele-operacyjne.md`, wiersz
  `przymus asortymentowy z akcji reklamowej [CAT-03 -> CAT-01]`
  [PROP+ 20.08, naprawa po recenzji delty].
- **Sprzężenia do świadomości przy projektowaniu mechaniki** [AUT-R 19.08, potwierdzone; kierunek
  potwierdzony przez właściciela, ale **wiązanie z konkretnymi kartami domen FIN i podatków pozostaje
  do zrobienia**, bo tamte karty nie są jeszcze zredagowane]:
  naliczanie punktów lojalnościowych tworzy odroczone zobowiązanie albo rezerwę (skutek księgowy
  w innej domenie); **rabat od dostawcy pomniejsza koszt zakupu, czyli wchodzi w wycenę zapasu**
  [LIT: IAS 2 § 11: „Trade discounts, rebates and other similar items are deducted in determining the
  costs of purchase"], a **czy tak się dzieje u klienta, bywa parametrem konfiguracyjnym**
  [LIT: Oracle Retail Price Management, User Guide 16.0, „Promotions" -> „Deal Billing", pola
  `Include Deal Income in Stock Ledger`, `Include VAT in Deal Billing`]. Rabat retro warunkowany
  wolumenem jest osobnym przypadkiem i karta **nie rozstrzyga** jego ujęcia; kierunek IFRS 15
  (zmienne wynagrodzenie) jest tu wskazówką bez zweryfikowanego lokatora [do weryfikacji]. Wydanie
  gratisu ma skutek w VAT; promocja reklamowana bez pokrycia zapasem rodzi ryzyko „promocji
  niedostępnej".

**11. Warianty, mechaniki i wyjątki:**

*Katalog form korzyści, klas mechanik i osi sterujących w tej sekcji został potwierdzony przez
właściciela jako lista pokrycia 19.08.2026 [AUT-R 19.08, potwierdzone]. Stał tu wcześniej jeden tag
zbiorczy nad całą sekcją; usunięto go 19.08, bo uniemożliwiał decyzję per twierdzenie i był
dokładnie tym skrótem, przed którym broni rozdzielenie tagów.*

Formy korzyści: rabat, upust, gratis, kupon na kolejny zakup, punkty lojalnościowe, cashback,
gift-with-purchase (rdzeń nierabatowany), cena z kartą/member price (osobna klasa od rabatu).

Klasy mechanik (katalog pokrycia): obniżka %/kwotowa; wielokrotność (np. 30% na drugą sztukę);
buy-X-get-Y (inny produkt); bundle / mix-and-match; tiered/threshold (od N sztuk, od X zł, próg
darmowej dostawy); spend-and-get (wydaj 100, dostań voucher 20); markdown wyprzedażowy (time-decay)
- UWAGA na granicę: tu należy wyłącznie markdown CZASOWY, po którym cena wraca do regularnej; trwałe
obniżenie ceny regularnej (wycofanie pozycji, nowy poziom cenowy na stałe) to zdarzenie cenowe
ORPR-CAT-02. Kryterium granicy jest **jedno i wystarczające: czy po zakończeniu cena wraca do
poprzedniej**. Wraca to CAT-03, nie wraca to CAT-02. Wcześniejsze brzmienie uzasadniało tę granicę
dodatkowo rewaluacją zapasu; to uzasadnienie **wycofano 19.08 po recenzji**, bo skutek na zapasie
zależy od modelu wyceny zapasu u detalisty, a nie od typu zmiany ceny (ORPR-CAT-02 pole 10)
[PROP+ 19.08, recenzja v0.4];
price-match / gwarancja najniższej ceny; promocja na wagę/miarę; kupon (kod/klip/skan).

Osie sterujące (to zwykle ginie w karcie): combinability/stacking; exclusions (wykluczenia SKU/marek);
priority / kolejność aplikacji (% przed kwotą ≠ kwota przed %); eligibility (segment, kanał, sezon,
kategoria, konto - osobna oś, ARTS); margin floor; scheduling (okno, dzień, godziny); channel scope
(POS / e-com / app / marketplace / omni); limity ilościowe per transakcja/klient i „do wyczerpania
zapasów".

Wyzwalacz i poziom: automatyczny albo kupon; centralna / regionalna / segment / lokalna.
Tryb wyboru: optymalny zestaw dla konsumenta / jedna o najwyższym priorytecie / ręczny wybór sprzedawcy.

**Sprzedaż ze stratą jako taktyka handlowa (wabik)** należy TUTAJ, nie do CAT-02. W CAT-02 zejście
poniżej kosztu jest dopuszczalne wyłącznie dla towaru oznaczonego jako niepełnowartościowy; świadome
zejście poniżej kosztu na towarze pełnowartościowym jest mechaniką promocyjną i podlega margin floor
oraz bramce dopuszczalności z pola 9. [AUT-R 19.08, potwierdzone]

Przypadki szczególne: indywidualna przecena przez sprzedawcę/kierownika (np. towar uszkodzony), poza
silnikiem; rabaty pracownicze; oferty targetowane/segmentowe (regulacyjnie wrażliwe, patrz pole 12);
promocja z akcji producenckiej; kontrakt producenta z rabatem retro (warunki wolumenowe) i usługami
obudowującymi; gazetka (zestaw promocji w jednym oknie, z lead time druku - freeze konfiguracji po
druku); sieć bez cennika (marżownik).

**Zwroty przy cenie promocyjnej.** Reguła wyceny **nie jest definiowana tutaj**: obowiązuje reguła
z ORPR-CAT-02, czyli **zwrot zawsze po cenie transakcyjnej z dokumentu sprzedaży**, niezależnie od
tego, czy promocja jeszcze trwa i czy w międzyczasie zmieniła się cena regularna
[AUT-R 19.08, potwierdzone]. Nie ma wariantu „promo czy baza". CAT-03 linkuje, nie powtarza.

Tutaj rozstrzygamy wyłącznie to, czego CAT-02 nie obejmuje, bo dotyczy korzyści promocyjnej,
a nie ceny:
- **naliczone punkty lojalnościowe i wydane kupony przy zwrocie ANULUJEMY**
  [AUT-R 19.08, potwierdzone]. Korzyść przyznana pod warunkiem zakupu przestaje mieć podstawę, gdy
  zakup zostaje cofnięty. Wymaganie systemowe: silnik musi umieć wycofać naliczenie punktów i
  unieważnić wydany kupon, powiązane z dokumentem zwrotu, a nie tylko zwrócić pieniądze;
- **zwrot części zestawu albo mechaniki wielosztukowej** („3 za 2", bundle): pozostaje pytaniem
  otwartym do rozstrzygnięcia u klienta, bo zwrot jednej sztuki z trzech unieważnia warunek
  mechaniki dla pozostałych dwóch. Standard wymaga, żeby reguła była zapisana, nie żeby brzmiała
  konkretnie [PROP+ 19.08].

To najczęstszy cichy defekt UAT [AUT-R 19.08, potwierdzone]. Wykonanie w ORPR-RTN-*.

**12. Bezpieczniki prawne (R):** wiązania z regulatory-matrix v1.0.1 (legal_as_of 2026-08-14, confidence
verified), overlay retail_core:
- **PRICE-001** - najniższa cena z 30 dni przed obniżką [SRC-PRICE-INFO-2014, art. 4 ust. 2]
- **PRICE-002** - cena odniesienia dla towaru oferowanego <30 dni [art. 4 ust. 3]
- **PRICE-003** - cena odniesienia towaru szybko psującego się [art. 4 ust. 4]
- **PRICE-004** - widoczna cena i cena jednostkowa (etykiety, e-commerce) [art. 4 ust. 1 i 5; rozp. MRiT
  19.12.2022 § 3-5, 9-10]
- **PRICE-005** - najkorzystniejsza cena przy rozbieżności etykieta↔kasa [art. 5]

Źródła: SRC-PRICE-INFO-2014 (ustawa 9.05.2014 o informowaniu o cenach, Dz.U. 2023 poz. 168),
SRC-REG-PRICE-DISPLAY-2022 (rozporządzenie MRiT 19.12.2022, Dz.U. 2022 poz. 2776).

GAP-y do zgłoszenia maintainerowi RM (NIE asertować jako prawo w karcie):
- równy dostęp do promocji / warunkowanie lojalnością / personalizacja ceny 1:1 [do weryfikacji];
- **praktyki z dyrektywy o nieuczciwych praktykach rynkowych** (2005/29/WE, Załącznik I pkt 5, 6, 7):
  zapraszanie do zakupu bez racjonalnych podstaw do sądzenia, że towar będzie dostępny, oraz formuła
  o ograniczonej dostępności bez pokrycia. Overlay `retail_core` zna dziś wyłącznie PRICE-001..005;
  wiązanie do UCPD nie istnieje, a karta go używa w F28, więc **do czasu wiązania F28 stoi jako
  [do weryfikacji]**, nie jako prawo [PROP+ 19.08, naprawa po recenzji wydaniowej];
- **skutek podatkowy wydania nieodpłatnego** (F26) i **ujęcie punktów lojalnościowych** (F27):
  karta zbiera brzmienia i kieruje do doradcy klienta, nie asertuje [do weryfikacji];
- opłaty półkowe i usługi obudowujące kontrakt (pole 7) jako możliwe „inne niż marża opłaty za
  przyjęcie towaru do sprzedaży" - potencjalne ryzyko z UZNK / ustawy o przewadze kontraktowej
  [do weryfikacji; karta NIE przesądza, ale flaguje].

Ograniczenia branżowe (kategorie z ceną regulowaną lub zakazem promocji w danej branży) wchodzą
warstwą profilu ORPR (P15) i odpowiednim overlay w RM, nie rdzeniem.

**13. Powiązanie w górę i artefakty:** value stream „Promocja" (definicja -> POS -> pomiar efektu
[-> ORPR-CAT-04] -> rozliczenie warunków z dostawcą [-> ORPR-PRC-04]). Crosswalk: standard/mapowania/crosswalk-frameworki.md. Powiązane artefakty
współdzielone do zrobienia: macierz decyzyjna stackingu (pierwszeństwo × łączenie × kolejność), katalog
scenariuszy testowych UAT, glosariusz PL->EN (marżownik, gazetka, retro). KPI (z definicjami do
uzupełnienia): udział sprzedaży promocyjnej, marża po promocji (z retro czy bez - do zdefiniowania),
skuteczność akcji (podstawa premii/rabatu retro), % promocji aktywowanych bezbłędnie przed startem okna,
**udział promocji uruchomionych ścieżką awaryjną** (miara zapowiedziana w A23 i F20: jeśli nikt nie zna
tej liczby, wyprzedzenie jest deklaracją, nie kontrolą).

## 14. Bank pytań analityka

Każde pytanie rozstrzygalne, każde z uzasadnieniem, pytania złożone rozbite.

**Jak tego używać, czyli czego nie da się uciąć** [PROP+ 19.08]. Bank nie jest scenariuszem jednej
sesji. Priorytety:

| Priorytet | Pytania | Kiedy |
|---|---|---|
| **P0, bez tego nie ma projektu** | A1, A2, A3, A4 | blok wstępny, pierwsze 20 minut warsztatu |
| **P1, wyjście z pierwszej sesji** | A5, A6, A9, A13, A17, A22, A26, A30, A33, A39 | warsztat z biznesem, jedna sesja 2-3 h |
| **P2, do dobrania po pierwszej sesji** | pozostałe A | mail, druga sesja albo warsztat tematyczny |
| **P3, praca dokumentacyjna** | cały blok B | z zespołem utrzymania obecnego systemu |
| **P4, formalne zapytanie** | cały blok C | pisemnie do vendora, z wymogiem lokatora w dokumentacji |

**Czego tu nie ma, bo pyta o to inna karta.** Podłoże cenowe (ile poziomów cennika, co rozstrzyga
przy kilku naraz, matryca marżowa, historia ceny regularnej) należy do ORPR-CAT-02 i tam stoją
pytania A1-A3, A25, B13, C1 tamtej karty. Na warsztacie promocyjnym korzystamy z odpowiedzi już
zebranych, nie zadajemy ich drugi raz (P13).

### A. Do biznesu (na warsztat)

**Blok wstępny: cztery pytania, bez których reszta warsztatu jest zgadywaniem.**

A1. Jaki jest model relacji między siecią a lokalizacjami: sieć własna, franczyza twarda, franczyza
miękka, sieć partnerska? *(Wyznacza, KTO prowadzi politykę promocyjną. W modelu twardym centrala ma
cennik i silnik, a lokalizacja robi nakładki. W miękkim lokalizacja ma własną politykę, a centralna
promocja jest zaproszeniem, które sklep wykonuje u siebie. To są dwa różne modele uprawnień i dwie
różne architektury dystrybucji.)*

A2. Czy sprzedajecie w więcej niż jednym kanale, i czy promocje mają być w nich wspólne?
*(Nie każda sieć ma kanał cyfrowy, a część prowadzi go na osobnym silniku. Od odpowiedzi zależy,
czy w ogóle rozmawiamy o jednym silniku dla wszystkich kanałów, czy o synchronizacji dwóch.)*

A3. Czy macie forecast i czy planujecie nim opłacalność promocji? *(Zakładać należy, że większość
sieci forecastu nie ma. Pytanie zadane w tej kolejności chroni przed zbudowaniem wymagań na proces,
którego u klienta nie ma.)*

A4. Kto może uruchomić promocję i na jakim poziomie: centrala, region, segment, lokalizacja?
*(Poziom uruchomienia rozstrzyga model uprawnień i to, ile ścieżek zatwierdzania musi obsłużyć
system. Odpowiedź wynika z A1, ale trzeba ją potwierdzić wprost, bo modele mieszane są częste.)*

**Blok: mechanika i rozstrzyganie**

A5. Jakie formy korzyści musi obsłużyć system: rabat, upust, gratis, kupon na kolejny zakup, punkty
lojalnościowe, cashback, prezent do zakupu, cena z kartą? *(Lista pokrycia, po której sprawdza się,
czy nowy system umie to, co stary. Forma korzyści rozstrzyga też skutek podatkowy i księgowy, patrz
A35, A36 i A51.)*

A6. Jakie klasy mechanik są w grze: obniżka procentowa i kwotowa, wielokrotność, kup X dostaniesz Y,
zestaw i mix-and-match, progi ilościowe i kwotowe, wydaj i dostań, markdown czasowy, gwarancja
najniższej ceny, promocja na wagę, kupon? *(Każda klasa ma inną mechanikę rozliczenia zwrotu i inny
reżim obowiązku informacyjnego, patrz A46. Zawężenie listy na starcie oszczędza pół projektu.)*

A7. Gdy na jedną pozycję łapie się kilka promocji: naliczamy zestaw optymalny dla klienta, jedną
o najwyższym priorytecie, czy sprzedawca wybiera ręcznie? *(To jest decyzja handlowa, nie techniczna,
a systemy różnią się w niej fundamentalnie. Uwaga: „system wybierze najkorzystniejszy zestaw" bywa
obietnicą, której vendorzy w dokumentacji nie składają, patrz C4.)*

A8. Które promocje wolno łączyć, a które się wykluczają? *(Reguła łączenia bywa ustawiana na dwóch
piętrach naraz: na pojedynczej promocji i globalnie na systemie. Gdy oba piętra istnieją, wynik
zależy od tego, które wygrywa, a tego nie widać bez wykonania transakcji.)*

A9. W jakiej kolejności naliczane są promocje różnych typów, gdy łapią się na tę samą pozycję?
*(Ten sam „30 %" daje różny wynik przed i po rabacie kwotowym. W części silników kolejność klas
rabatu jest zaszyta w kodzie i konfiguracja jej nie zmienia, a „priorytet" steruje czym innym niż
kolejnością arytmetyczną.)*

A10. Czy istnieje u Was promocja oznaczona jako wyłączna, blokująca wszystkie inne na danej pozycji?
*(Dopytanie osobne: A60. Wyłączność ustawiona kiedyś „na wszelki wypadek" i nigdy niecofnięta wycina
późniejsze akcje. W części silników promocja wyłączna jest oceniana przed pozostałymi niezależnie
od priorytetu, więc niski priorytet jej nie ratuje.)*

A11. Od jakiej kwoty liczy się próg przy mechanikach progowych: przed rabatami, po rabatach, czy
z pominięciem pozycji nierabatowalnych? *(Trzy sensowne odpowiedzi, jeden wynik na paragonie.
Spór „miałem sto złotych, a próg nie zadziałał" bierze się dokładnie stąd.)*

A12. Czy pozycje wyłączone z promocji wliczają się do progu ilościowego albo kwotowego?
*(Osobne pytanie od A11 i osobny parametr w systemach, które to rozróżniają. Odpowiedź zmienia
wynik na koszykach mieszanych, czyli na większości.)*

A13. Czy rabat na cały paragon respektuje wykluczenia pozycji i kategorii, czy trzeba mu je zbudować
drugi raz osobno? *(Rabat koszykowy jest innym bytem niż pozycyjny i w części systemów wykluczenia
trzeba dla niego konfigurować powtórnie. Skutek: rabat dosięga pozycji, na które promocji być nie
powinno, i przechodzi przez bramkę dopuszczalności kategorii.)*

A14. Czy jakakolwiek korzyść dla klienta jest wyliczana poza głównym silnikiem promocyjnym:
lojalność, kupony, personalizacja, integracja zewnętrzna? *(Korzyść liczona poza silnikiem bywa
aplikowana przed wszystkim innym i nie podlega ani wykluczeniom, ani progowi marży. Wchodzi zwykle
w drugiej fali wdrożenia, już po odbiorze.)*

**Blok: marża i opłacalność**

A15. Czy istnieje twardy próg marży, który BLOKUJE naliczenie promocji, czy tylko raport pokazujący
przekroczenie po fakcie? *(Różnica jest zasadnicza: bramka odmawia w momencie sprzedaży, raport
informuje miesiąc później. Żądaj pokazania transakcji, w której system odmówił, a nie raportu.)*

A16. Na jakim poziomie liczony jest próg marży: pojedynczej pozycji, całego paragonu, czy obu?
*(Próg egzekwowany na pozycji nie widzi rabatu koszykowego ani progowego. Kumulacja rabat pozycyjny
plus koszykowy plus kupon schodzi pod koszt, choć każdy składnik osobno próg respektuje.)*

A17. Kto zatwierdza promocję i czy zatwierdzenie jest rozdzielone od jej wprowadzenia? *(W większości
sieci nie ma drugiej pary oczu i kontrolę pełni parametr systemowy. Jeśli nie ma ani rozdziału ról,
ani parametru, kontroli nie ma żadnej.)*

A18. Czy korzyść od dostawcy obniża Wam koszt własny sprzedaży, koryguje wycenę zapasu, czy jest
ujmowana jako przychód? *(W części systemów to jest parametr konfiguracyjny, a nie oczywistość.
Kierunek rachunkowy jest ustalony, ale konfiguracja bywa ustawiana przez wdrożeniowca bez pytania
księgowości, i wychodzi przy pierwszym zamknięciu okresu.)*

**Blok: czas, okno, dystrybucja**

A19. Jak zapisujecie okno promocji: sama data, czy data z godziną? *(Okno godzinowe wprowadza całą
klasę problemów granicznych, której okno dzienne nie ma. Jeśli odpowiedź brzmi „data", pomijamy
A20 i A21.)*

A20. Czy któraś lokalizacja pracuje przez północ? *(Okno kończące się o północy bywa obsługiwane
błędnie i skutkiem nie jest sekundowa luka, tylko brak promocji przez cały dzień. Wychodzi
pierwszego dnia akcji, na kasie, nie w testach.)*

A21. W jakiej strefie czasowej zapisywane jest okno i w jakiej interpretuje je kasa? *(Platformy
chmurowe trzymają okno w czasie uniwersalnym. Sieć jednostrefowa nie zauważy tego do zmiany czasu,
wielostrefowa zauważy pierwszego dnia.)*

A22. Jakie jest wymagane wyprzedzenie między zatwierdzeniem promocji a startem okna, i kto ma prawo
je ominąć? *(Wyprzedzenie to jedyna prewencja przed rozjazdem materiału reklamowego z kasą.
Ścieżka awaryjna zwykle istnieje i zwykle jest zabezpieczona wyłącznie uprawnieniem, nie
mechanizmem, więc erozja jest kwestią czasu.)*

A23. Ile promocji w ostatnim kwartale weszło ścieżką awaryjną? *(Jeśli nikt nie zna liczby, to
znaczy że nikt tego nie mierzy, a wtedy wyprzedzenie z A22 jest deklaracją, nie kontrolą. To jest
też gotowa miara do pola 13.)*

A24. Jak wyłączacie JEDNĄ pozycję z trwającej promocji, nie wyłączając całej akcji? Ile to trwa?
*(W części systemów wyjątku nie da się dodać do zatwierdzonej promocji bez cofnięcia jej do stanu
roboczego, co samo w sobie przerywa jej działanie na kasach.)*

A25. Co się dzieje na kasach w trakcie korekty parametru trwającej promocji? *(W części systemów
edycja wymaga wyłączenia promocji, a wyłączenie w centrali nie jest komunikatem „skasuj z kasy",
tylko brakiem komunikatu. Powstaje okno, w którym kasa ma starą regułę albo żadnej.)*

A26. Czy mechanika czasowa jest u Was budowana jako promocja, czy jako trwała przecena?
*(To jest granica CAT-02 i CAT-03. Zbudowana jako przecena, po zakończeniu okna nie wraca sama do
ceny regularnej i zostawia trwały ślad w ewidencji, a marża cicho wycieka.)*

**Blok: kupony i limity**

A27. Kupon ma numer oferty czy numer egzemplarza? *(Bez identyfikacji egzemplarza nie ma technicznej
podstawy do wymuszenia jednokrotnego użycia; jest tylko licznik po stronie silnika, który da się
obejść w innym sklepie tego samego dnia.)*

A28. Co się dzieje z limitem użyć kuponu przy anulowaniu transakcji albo zwrocie: licznik wraca?
*(W części systemów licznik nie cofa się nigdy. Klient traci kupon przy anulowaniu, a sieć nie
odzyskuje limitu, i obie strony mają rację, że to nie działa.)*

A29. Limit „raz na klienta": jak ma działać przy kasie, gdzie klient nie jest identyfikowany?
*(W części systemów limit na klienta w ogóle nie istnieje dla sprzedaży anonimowej, czyli dla
domyślnego trybu kasy stacjonarnej.)*

A30. Gdzie ustawia się datę końca akcji kuponowej: na promocji czy na kuponie?
*(Dopytanie osobne: A61. W części systemów włączenie kuponu przejmuje sterowanie datami z promocji, przez co dwa
zespoły ustawiają je niezależnie i kupon działa po wygaśnięciu akcji.)*

A31. Ile promocji miewacie aktywnych jednocześnie w szczycie kalendarza? *(Silniki mają twarde
limity liczby aktywnych promocji i liczby pozycji w jednej promocji. Przekroczenie objawia się
w szczycie sezonu, czyli w najgorszym możliwym momencie.)*

**Blok: zwroty, gratisy, zestawy**

A32. Jak rozkładacie rabat wielosztukowy na linie paragonu: proporcjonalnie na wszystkie, czy
w całości na najtańszą? *(Rabat skoncentrowany na najtańszej linii oznacza, że przy zwrocie dwóch
z trzech sztuk klient zatrzymuje darmową sztukę, a detalista notuje stratę. To jest udokumentowany
problem biznesowy, nie usterka.)*

A33. Co się dzieje przy zwrocie części zestawu albo części mechaniki wielosztukowej? *(Zwrot jednej
sztuki z trzech unieważnia warunek mechaniki dla pozostałych dwóch. Standard wymaga, żeby reguła
była zapisana, nie żeby brzmiała konkretnie.)*

A34. Czy paragon pokazuje rabat rozłożony na linie, czy skoncentrowany, i czy to jest ta sama
liczba, którą zobaczy zwrot? *(Jeśli prezentacja i podstawa zwrotu to dwie różne liczby, spór
z klientem jest kwestią czasu.)*

A35. Gratis jest u Was rabatem stu procent na linii, czy osobną pozycją wydania nieodpłatnego?
*(To nie jest kwestia estetyki paragonu. Wydanie nieodpłatne i obniżka ceny to dwa różne zdarzenia
o różnym skutku podatkowym, a rozróżnienie jest przedmiotem orzecznictwa.)*

A36. Czy system prowadzi ewidencję wydań nieodpłatnych i czy gratis zdejmuje zapas? Którym
dokumentem? *(Bez ewidencji nie ma materiału, na którym doradca podatkowy klienta mógłby oprzeć
ocenę wyłączeń dla drobnych wydań; karta prawa podatkowego nie asertuje, patrz F26 [do weryfikacji].
Osobno i niezależnie: bez dokumentu zapas i sprzedaż rozjeżdżają się o wolumen gratisów.)*

**Blok: zapas, nośnik, komunikat**

A37. Kto i kiedy sprawdza pokrycie zapasem przed publikacją materiału promocyjnego, i czy to jest
bramka blokująca publikację, czy raport informacyjny? *(Zapraszanie do zakupu bez racjonalnych
podstaw do sądzenia, że towar będzie dostępny, jest praktyką **nazwaną w źródłach prawa ochrony
konsumenta**, a nie tylko wpadką operacyjną; wiązanie nie jest jeszcze w regulatory-matrix, patrz
F28 i GAP w polu 12 [do weryfikacji].)*

A38. Co robicie, gdy towar promocyjny się skończy: zamiennik, odroczona realizacja, rekompensata?
*(Uznane sposoby wyjścia z tej sytuacji istnieją i są opisane, ale trzeba je mieć przygotowane
przed akcją, nie wymyślać przy ladzie.)*

A39. Czy komunikat „do wyczerpania zapasów" jest ustawiany świadomie na konkretnej promocji, czy
dopisywany domyślnie na wszystkim? *(Deklaracja ograniczonej dostępności użyta bez pokrycia jest
w tych samych źródłach **osobną nazwaną praktyką**, patrz F28 [do weryfikacji], więc formuła wklejana
odruchowo tworzy ryzyko zamiast je zdejmować.)*

A40. Czy zestaw promocyjny jest u Was regułą w silniku, czy osobną pozycją z własnym
identyfikatorem? *(Standard identyfikacji przewiduje, że produkt promocyjny bywa, że wymaga własnego
numeru na poziomie opakowania zbiorczego. Te dwie drogi mają zupełnie inne skutki w kartotece,
w zamówieniu i w przyjęciu towaru.)*

A41. Co robicie z niesprzedanym zapasem pozycji promocyjnej po zakończeniu akcji? *(Jeśli zestaw
jest osobną pozycją, po akcji zostaje w kartotece i w magazynie jako byt bez ceny regularnej.)*

**Blok: obowiązki informacyjne**

A42. Od jakiej ceny liczycie procent obniżki pokazywany klientowi? *(Podstawą jest cena odniesienia
wyliczona z historii, a nie cena z bieżącego cennika. To jest wprost wiązanie do ORPR-CAT-02:
silnik promocyjny musi widzieć historię ceny w momencie ogłaszania.)*

A43. Czy moduł promocyjny czyta historię ceny automatycznie, czy ktoś wkleja liczbę ręcznie?
*(Liczba wklejana ręcznie jest liczbą, której nikt nie przelicza po zmianie ceny regularnej
w międzyczasie.)*

A44. Na jakie nośniki i do jakich kanałów jedzie cena odniesienia razem z promocją: etykieta, ekran,
aplikacja, materiał drukowany, reklama zewnętrzna? *(Obowiązek dotyczy każdego miejsca prezentowania
obniżki, nie tylko półki. Podanie ceny odniesienia w jednym miejscu nie zwalnia z pozostałych.)*

A45. Czy odróżniacie obniżkę stopniową w jednej kampanii od dwóch osobnych kampanii po sobie?
Po czym? *(Od tego zależy podstawa komunikatu przy drugim i trzecim etapie przeceny, a rozróżnienie
musi być zapisane jako atrybut, bo z samej mechaniki nie wynika.)*

A46. Kto i w którym momencie decyduje, czy dana promocja wymaga podania ceny odniesienia?
*(Dwie promocje o identycznej mechanice mogą mieć różny obowiązek informacyjny, w zależności od tego,
co komunikują klientowi. Z samej reguły w silniku to nie wynika. Dopytanie osobne: A58.)*

A47. Który z Waszych kodów rabatowych jest naprawdę indywidualny, a który jest kodem publicznym
udającym indywidualny? *(Reżim informacyjny jest inny dla obu, a różnica nie leży w technice, tylko
w tym, czy kod jest realnie adresowany do jednej osoby.)*

A48. Czy jakakolwiek cena albo korzyść jest u Was ustalana automatycznie na podstawie profilu
klienta? *(Dopytanie osobne: A62. Kandydat na obowiązek ujawnienia personalizacji ceny jest osobną
osią od obowiązku podania ceny odniesienia. Oznaczenie musi być atrybutem promocji przenoszonym do
kanału, a nie tekstem wpisanym w kreację.)*

**Blok: rozliczenie z dostawcą**

A49. Jak rozliczacie promocje z producentem i skąd bierzecie wolumen do rozliczenia? *(Wolumen
liczony inaczej w systemie sprzedaży, a inaczej w rozliczeniu, jest najczęstszą przyczyną sporu
i utraty rekompensaty.)*

A50. Czy promocja bywa sprzedawana producentowi w pakiecie z usługami: obecność w materiale
reklamowym, miejsce ekspozycyjne, premie dla personelu?
*(Usługi obudowujące kontrakt bywają kwalifikowane jako opłaty inne niż marża za przyjęcie towaru
do sprzedaży, więc powiązanie ich z konkretną usługą i jej wykonaniem ma znaczenie dowodowe.
Dopytanie osobne: A59.)*

A51. Kto i z jakiego raportu wycenia zobowiązanie z tytułu nierozliczonych punktów lojalnościowych?
*(Punkty naliczone przy sprzedaży **bywają ujmowane jako zobowiązanie wobec klienta, a nie jako
koszt marketingu**; karta tego nie przesądza, patrz F27 [do weryfikacji]. Niezależnie od
rozstrzygnięcia księgowego wycena wymaga salda, wiekowania i wskaźnika faktycznego wykorzystania,
a system musi umieć je podać. To jest wymaganie systemowe i ono stoi w każdym wariancie.)*

A52. Jaki jest wymagany zakres i odbiorcy raportowania skuteczności, wewnętrznie i wobec producenta?
*(Raport skuteczności jest wyjściem tej karty i wejściem procesu pomiaru efektu, ORPR-CAT-04.
Zakres uzgodniony po fakcie zwykle okazuje się niepoliczalny z danych, które zbierano.)*

A53. Czy w Waszym asortymencie są kategorie, w których obniżka jest ograniczona albo zakazana, albo
w których cena jest regulowana lub urzędowo ustalana?
*(To jest pytanie wykrywające do F11 i jedyna droga do spełnienia warunku wejścia z pola 9
„dopuszczalność prawna kategorii potwierdzona". Bez odpowiedzi bramka jest niewykonalna, bo nikt nie
wie, czego dotyczy. Lista bywa branżowa i zmienna, więc odpowiedź „chyba nie mamy" jest odpowiedzią
do zweryfikowania u prawnika klienta, nie rozstrzygnięciem.)*

A54. Czy lista kategorii z ograniczeniem obniżki jest atrybutem w systemie, czy wiedzą osoby
ustawiającej promocję? *(Wykrywa F11 od drugiej strony: bramka, której nie da się wyegzekwować
maszynowo, jest procedurą, nie kontrolą.)*

A55. Jaka jest reguła zaokrąglenia przy naliczeniu promocji: zaokrąglamy na linii czy na sumie,
przed podatkiem czy po, i w którą stronę? *(To jest pytanie wykrywające do F7. ORPR-CAT-02 stawia
analogiczny wymóg dla ceny regularnej: reguła zdefiniowana PRZED wyliczeniem, nie po pierwszym
sporze.)*

A56. Czy istnieje uzgodniona lista pozycji, które nie podlegają promocji, i czy silnik ją respektuje
także przy rabacie na cały paragon? *(Wykrywa F18 od strony danych, nie mechaniki.)*

A57. Skąd bierzecie listę kategorii z ograniczeniem obniżki i kto ją aktualizuje? *(Dopytanie do A53.
Lista bez właściciela i bez daty przeglądu jest listą sprzed dwóch lat.)*

A58. Czy wymóg podania ceny odniesienia jest polem w systemie, czy wiedzą osoby ustawiającej
promocję? *(Dopytanie do A46. Wiedza w głowie nie przechodzi przez bramkę akceptacji i znika razem
z osobą.)*

A59. Czy system wiąże usługi sprzedane producentowi w pakiecie z promocją z konkretnym kontraktem
i z potwierdzeniem ich wykonania? *(Dopytanie do A50. Brak powiązania oznacza brak materiału
dowodowego przy sporze o charakter opłaty.)*

A60. Kto decyduje o oznaczeniu promocji jako wyłącznej i czy ktokolwiek przegląda wyłączności
ustawione w przeszłości? *(Dopytanie do A10. Decyzja bez przeglądu produkuje zaległość, która wycina
przyszłe akcje.)*

A61. Kto ma dostęp do daty na promocji, a kto do daty na kuponie? *(Dopytanie do A30. Dwa zespoły
z dostępem do dwóch pól, które sterują tym samym oknem, to gotowy rozjazd.)*

A62. Gdzie klient dowiaduje się, że cena została ustalona automatycznie na podstawie jego profilu?
*(Dopytanie do A48. Oznaczenie musi być atrybutem promocji przenoszonym do kanału, a nie tekstem
wpisanym w kreację.)*

### B. Do legacy (obserwowalne zachowanie obecnego systemu)

B1. Jak rozstrzyga się kolizja kilku promocji na jednej pozycji i czy da się prześledzić, dlaczego
kasa naliczyła akurat tę cenę? *(Bez śladu rozstrzygnięcia rekoncyliacja marży pokazuje różnicę,
której nie da się wyjaśnić, a reklamacja klienta kończy się słowem przeciw słowu.)*

B2. Czy kolejność naliczania promocji jest konfigurowalna, czy zaszyta w kodzie? *(Kolejność zaszyta
oznacza, że każda zmiana polityki handlowej jest zmianą wersji systemu.)*

B3. Czy reguła łączenia promocji jest ustawiana na promocji, czy globalnie na systemie? *(Jeśli na
obu piętrach naraz, trzeba wiedzieć, które wygrywa, i sprawdzić to na transakcji, nie w opisie.)*

B4. Czy flaga „zatrzymaj kolejne promocje" działa na pojedynczej pozycji, czy na całym koszyku?
*(Różnica wychodzi wyłącznie na teście z dwiema różnymi pozycjami objętymi dwiema różnymi
promocjami. Przy testach jednopozycyjnych nie wyjdzie nigdy.)*

B5. Ile promocji macie dziś oznaczonych jako wyłączne i kto je przegląda? *(Wyłączność ustawiona
kiedyś i nigdy niecofnięta jest cichym wygaszaczem późniejszych akcji.)*

B6. Jak dowiadujecie się, że promocja nie dojechała do kasy albo do kanału przed startem okna?
*(Odróżnia raport wysyłki od potwierdzenia odbioru, czyli „promocja obowiązuje" od „promocja
obowiązuje wszędzie".)*

B7. Czy start promocji jest blokowany przy braku kompletu potwierdzeń, czy tylko raportowany?
*(Rozstrzyga, czy niepełna dystrybucja jest incydentem widocznym, czy cichym.)*

B8. Czy moduł promocyjny widzi historię ceny regularnej w momencie ogłaszania obniżki? *(Jedyne
pytanie o historię ceny, które należy do tej karty; miejsce i granularność przechowywania pyta
ORPR-CAT-02.)*

B9. Co przelicza konflikty między promocjami: zmiana samej promocji, czy zmiana czegokolwiek, co
promocja czyta? *(Jeśli konflikt jest sprawdzany wyłącznie przy zmianie statusu, to zmiana ceny
regularnej po zatwierdzeniu promocji nie uruchomi ponownego sprawdzenia i nikt się o niej nie
dowie.)*

B10. Jak obsługiwany jest materiał reklamowy jako zestaw promocji uruchamiany i wygaszany łącznie?
*(Zestaw traktowany jako zbiór niezależnych promocji rozjeżdża się przy pierwszej korekcie jednej
z nich.)*

B11. Jaki jest lead time druku materiału i co się dzieje, gdy promocja zmieni się po druku?
*(Freeze konfiguracji po druku jest albo regułą, albo fikcją. Jeśli fikcją, klient trzyma w ręku
inną cenę niż ta w kasie.)*

B12. Jak realizowana jest indywidualna przecena poza silnikiem i jak jest audytowana? *(Ta ścieżka
istnieje w każdej sieci i zwykle nie ma właściciela w standardzie; trzeba wiedzieć, ile jej jest.)*

B13. Czym różnią się w regułach rabaty pracownicze? *(Zwykle mają własny reżim łączenia i własne
wykluczenia, a bywają zaszyte poza silnikiem promocyjnym.)*

B14. Jak liczycie rabat retro i skąd bierzecie wolumen? *(Weryfikuje A49 po stronie obecnego
systemu.)*

B15. Jak zachowuje się system przy zwrocie pozycji kupionej w promocji? *(Weryfikuje A32 i A33.
Interesuje nas, jaką kwotę widzi zwrot, a nie jaka jest polityka na papierze.)*

B16. Co się dzieje z naliczonymi punktami i wydanym kuponem przy zwrocie? *(Standard wymaga
anulowania. Pytanie brzmi, czy system to potrafi i czy potrafi to udokumentować.)*

B17. Czy system podaje saldo, wiekowanie i wskaźnik wykorzystania punktów lojalnościowych?
*(Bez tych trzech liczb nie da się wycenić zobowiązania ani rozpoznać przedawnienia.)*

B18. Jak system rozróżnia gratis od rabatu stu procent? *(Weryfikuje A35 na poziomie tego, co
faktycznie trafia na dokument sprzedaży i do ewidencji.)*

B19. Czy okno promocji zapisywane jest z godziną i w jakiej strefie? *(Weryfikuje A19 i A21.)*

B20. Co się dzieje z promocją godzinową w nocy zmiany czasu? *(Aktywacja odpali się podwójnie albo
wcale; dwa razy w roku i prawie nigdy w planie testów.)*

B21. Jak wyłączyć jedną pozycję z trwającej promocji i ile to trwa do kasy? *(Weryfikuje A24.)*

B22. Czy zdarzało się, że promocja nie weszła w życie, mimo że operator widział ją jako wprowadzoną?
*(Systemy z progiem tolerancji wyjątków zostawiają zdarzenie w statusie roboczym i nie wysyłają go
do kas.)*

B23. Ile promocji potraficie mieć aktywnych naraz i przy jakiej liczbie zaczynają się problemy?
*(Weryfikuje A31 na danych historycznych, nie na deklaracji.)*

B24. Czy kanał cyfrowy i kasa liczą promocję tym samym kodem, czy dwoma osobnymi implementacjami?
*(Dwie implementacje rozjeżdżają się nie na regułach, tylko na zaokrągleniach, kolejności i alokacji
rabatu na linie.)*

B25. Jak liczycie zamówienie złożone w jednym kanale, a odbierane w drugim, gdy między złożeniem
a odbiorem promocja wygasła? *(Reguła ceny z momentu zawarcia umowy jest w ORPR-CAT-02; tutaj
sprawdzamy, czy silnik promocyjny ją respektuje.)*

B26. Kto sprawdza, że procent obniżki na nośniku zgadza się z liczbą w systemie? *(Jeśli odpowiedź
brzmi „nikt", to jest gotowa czerwona flaga, a nie luka do zapełnienia deklaracją.)*

B27. Czy istnieje pole oznaczające, że promocja wymaga podania ceny odniesienia, i kto je wypełnia?
*(Weryfikuje A46. Brak pola oznacza, że obowiązek jest wiedzą w głowie jednej osoby.)*

### C. Do vendora

Przy każdym pytaniu wymagamy wskazania miejsca w dokumentacji i informacji, czy rzecz jest
konfigurowalna bez programisty. „Tak, obsługujemy" bez lokatora nie jest odpowiedzią.

C1. Na której warstwie cenowej operuje silnik promocyjny: na cenniku, na cenie wyliczonej, czy na
obu? *(O kierunek przepływu ceny między centralą a lokalizacją pyta ORPR-CAT-02, C1. Tutaj interesuje nas wyłącznie
punkt zaczepienia promocji.)*

C2. Jak system rozstrzyga pierwszeństwo, łączenie, wykluczenia i kolejność naliczania?
*(Cztery osie jednej mechaniki rozstrzygania; odpowiedź musi objąć każdą z nich osobno, bo w części
silników sterują nimi różne pola. O konfigurowalność pyta osobno C46.)*

C3. Pokażcie na dwóch promocjach, jednej kwotowej i jednej procentowej, obie łapiące się na tę samą
pozycję: którą liczycie pierwszą i czy da się tę kolejność zmienić? *(Prosimy o wynik na
transakcji, nie o opis możliwości.)*

C4. Czy potwierdzacie na piśmie, że silnik wybiera zestaw najkorzystniejszy dla klienta przy
dowolnej liczbie promocji, czy tylko w obrębie jednego priorytetu? *(Rozstrzyganie optimum przy
wielu promocjach jest problemem kombinatorycznym i część vendorów wprost pisze w dokumentacji, że
go nie rozwiązuje. Poproście o zdanie z dokumentacji, nie z prezentacji.)*

C5. Czy reguła łączenia jest ustawiana na promocji, globalnie na systemie, czy na obu piętrach
naraz? Które wygrywa? *(Weryfikuje B3 po stronie nowego systemu.)*

C6. Czy flaga zatrzymania kolejnych promocji działa na linii, czy na koszyku? Pokażcie test
z dwiema pozycjami objętymi dwiema różnymi promocjami. *(Weryfikuje B4. Bez testu dwupozycyjnego
odpowiedź jest nieweryfikowalna.)*

C7. Jak zachowuje się promocja oznaczona jako wyłączna wobec promocji o wyższym priorytecie?
*(W części silników wyłączność jest oceniana przed priorytetem i wygrywa niezależnie od niego.)*

C8. Od jakiej podstawy liczony jest próg i czy pozycje nierabatowalne wliczają się do niego?
Czy to jest parametr? *(Weryfikuje A11 i A12.)*

C9. Czy rabat transakcyjny respektuje wykluczenia zdefiniowane dla pozycji, czy wymaga własnych?
*(Weryfikuje A13.)*

C10. Czy da się wstrzyknąć korzyść z zewnątrz, poza silnikiem, i w którym momencie wchodzi do
rachunku? *(Weryfikuje A14; korzyść spoza silnika bywa aplikowana przed wszystkim innym.
Dopytanie osobne: C47.)*

C11. Pokażcie transakcję, w której silnik ODMÓWIŁ naliczenia, bo kumulacja zeszłaby pod próg marży.
*(Weryfikuje A15. Raport po fakcie nie jest odpowiedzią na to pytanie.)*

C12. Na jakim poziomie egzekwowany jest próg marży: linii, paragonu, obu? *(Weryfikuje A16.)*

C13. Czy system ma parametr rozstrzygający, czy korzyść od dostawcy wchodzi do wyceny zapasu?
*(Weryfikuje A18; w części systemów to jest jawny przełącznik, o którym nikt nie pyta przy
wdrożeniu.)*

C14. Czy okno promocji rozstrzygane jest wobec strefy czasowej i doby biznesowej lokalizacji?
*(Weryfikuje A21.)*

C15. Co się dzieje z aktywacją zaplanowaną na godzinę, która przy zmianie czasu występuje dwa razy
albo wcale? *(Weryfikuje B20.)*

C16. Jak system obsługuje okno kończące się o północy? *(Klasa problemu jest udokumentowana
publicznie i skutkiem bywa brak promocji przez cały dzień, a nie sekundowa luka.)*

C17. Czy wymusza minimalne wyprzedzenie zatwierdzenia wobec startu okna? Czy ma odrębną,
audytowaną ścieżkę awaryjną? *(Weryfikuje A22 i A23.)*

C18. Kiedy przeliczane są konflikty: przy zmianie promocji, czy przy zmianie danych, które promocja
czyta? *(Weryfikuje B9. Sprawdzanie wyłącznie przy zmianie statusu zostawia zatwierdzone promocje
w stanie nieaktualnym.)*

C19. Czy da się dodać wyjątek do trwającej, zatwierdzonej promocji bez cofania jej do stanu
roboczego? *(Weryfikuje A24 i B21.)*

C20. Co się dzieje na kasach podczas edycji trwającej promocji i czy wyłączenie promocji w centrali
jest komunikatem kasującym ją z kasy? *(Weryfikuje A25. Brak komunikatu nie jest komunikatem.)*

C21. Czy mechanika czasowa da się zbudować tak, żeby cena wracała sama po wygaśnięciu okna?
*(Weryfikuje A26 i granicę CAT-02 wobec CAT-03.)*

C22. Czy kupon może mieć identyfikator egzemplarza, nie tylko oferty? *(Weryfikuje A27; bez tego
jednokrotność użycia opiera się wyłącznie na liczniku.)*

C23. Czy licznik użyć kuponu cofa się przy anulowaniu i przy zwrocie? *(Weryfikuje A28.)*

C24. Jak działa limit „raz na klienta" przy sprzedaży bez identyfikacji klienta? *(Weryfikuje A29;
w części systemów taki limit po prostu nie działa na kasie stacjonarnej.)*

C25. Gdzie ustawia się okno akcji kuponowej i czy włączenie kuponu przejmuje sterowanie datami
z promocji? *(Weryfikuje A30.)*

C26. Ile promocji może być aktywnych jednocześnie i ile pozycji może objąć jedna promocja? Podajcie
liczby z dokumentacji. *(Weryfikuje A31. „Tyle, ile trzeba" nie jest liczbą.)*

C27. Jak nadawany jest priorytet i co robicie, gdy trzeba wstawić promocję między dwie istniejące?
*(W części silników przestrzeń priorytetów jest unikalna globalnie, więc wstawienie „pomiędzy" jest
operacją na całym katalogu promocji.)*

C28. Czy rabat wielosztukowy da się rozłożyć proporcjonalnie na wszystkie linie, czy zawsze siada
na najtańszej? Czy to jest parametr? *(Weryfikuje A32; od tego zależy strata przy zwrocie części
zestawu.)*

C29. Jak system modeluje wydanie nieodpłatne: jako rabat stu procent, czy jako odrębne zdarzenie?
*(Weryfikuje A35 i B18.)*

C30. Czy prowadzi ewidencję wydań nieodpłatnych i zdejmuje zapas przy gratisie? *(Weryfikuje A36.)*

C31. Czy potrafi zablokować publikację promocji przy niewystarczającym pokryciu zapasem?
*(Weryfikuje A37; bramka blokująca to co innego niż raport.)*

C32. Czy zestaw promocyjny może istnieć jako osobna pozycja z własnym identyfikatorem i czy system
obsługuje oba warianty? *(Weryfikuje A40.)*

C33. Czy natywnie liczy cenę odniesienia z historii ceny regularnej i podaje ją do komunikatu
promocyjnego? *(Weryfikuje A42 i A43.)* [R: PRICE-001..003]

C34. Do jakich nośników i kanałów system przenosi cenę odniesienia razem z promocją? *(Weryfikuje
A44; cena odniesienia jest atrybutem komunikatu, nie polem raportowym.)*

C35. Czy system odróżnia obniżkę ciągłą w jednej kampanii od ciągu osobnych kampanii? *(Weryfikuje
A45; od tego zależy podstawa komunikatu na drugim i trzecim etapie.)*

C36. Czy istnieje atrybut promocji oznaczający obowiązek podania ceny odniesienia, z bramką
akceptacji? *(Weryfikuje A46 i B27.)*

C37. Czy system potrafi oznaczyć ofertę jako personalizowaną automatycznie i przenieść to oznaczenie
na nośnik i do kanału? *(Weryfikuje A48.)*

C38. Czy promocję liczy jeden serwis dla wszystkich kanałów, czy każdy kanał ma własną
implementację? *(Weryfikuje B24. Jeden serwis liczący eliminuje całą klasę rozjazdów między
kanałami; karta nie twierdzi, że to wymóg rynkowy, tylko że alternatywa wymaga dowodu zgodności
wyników.)*

C39. Czy jest audytowalne potwierdzenie aktywacji per lokalizacja i kanał przed startem, z blokadą
startu bez kompletu potwierdzeń? *(Weryfikuje B6 i B7.)*

C40. Czy wiąże promocję z kontraktem producenta i liczy rabat retro według wolumenu? *(Weryfikuje
A49 i B14.)*

C41. Czy modeluje promocję jako regułę, modyfikator, kwalifikację i rozstrzyganie konfliktów, jako
osobne, wersjonowane i audytowalne obiekty? *(Pierwsze trzy rozdzielają uznane modele danych.
Czwarty, rozstrzyganie konfliktów, jest wymaganiem ORPR wykraczającym poza te modele. Zlanie
wszystkiego w jedno uniemożliwia odtworzenie po fakcie, dlaczego kasa naliczyła tę cenę.)*

C42. Czy pokazuje symulację wpływu promocji na marżę PRZED startem okna? *(Symulacja po starcie
jest raportem, przed startem jest bramką.)*

C43. Czy system pozwala oznaczyć kategorię jako wyłączoną z obniżek albo z ceną regulowaną i czy
blokuje utworzenie promocji na takiej kategorii? *(Weryfikuje A53 i A54. Odpowiedź „można ustawić
wykluczenie ręcznie" nie jest odpowiedzią twierdzącą: pytamy o blokadę, nie o możliwość.)*

C44. Gdzie konfiguruje się regułę zaokrąglenia dla ceny promocyjnej i czy jest ona ta sama, co dla
ceny regularnej? *(Weryfikuje A55. Dwie różne reguły w jednym systemie produkują rozjazd, którego
nikt nie umie odtworzyć.)*

C45. Jakie osie kwalifikacji (eligibility) obsługuje silnik: pozycja, klient, struktura towarowa,
sezon, kanał, lokalizacja, segment? *(Kwalifikacja jest w uznanych modelach danych osobną osią od
reguły i od modyfikatora, a bank pytań tej karty jej wcześniej nie pokrywał. Zawężona lista osi
kwalifikacji ogranicza politykę handlową bardziej niż brak którejkolwiek mechaniki.)*

C46. Które z reguł rozstrzygania z C2 są konfigurowalne bez programisty? *(Dopytanie do C2. Reguła
zaszyta w kodzie oznacza zmianę wersji systemu przy każdej zmianie polityki handlowej.)*

C47. Czy korzyść wstrzyknięta spoza silnika podlega wykluczeniom pozycyjnym i progowi marży?
*(Dopytanie do C10. Jeśli nie podlega, cały margin floor jest iluzją przy każdej promocji
lojalnościowej.)*

C48. Czy okno dostępności pozycji i okno kampanii promocyjnej to w systemie dwa osobne pola?
*(Standardy wymiany danych rozdzielają daty dostępności od dat kampanii. Zlanie ich w jedno powoduje,
że wycofanie pozycji kasuje historię kampanii albo odwrotnie.)*

### Czerwone flagi (wychodzą typowo dopiero w UAT lub po starcie)

Każda flaga ma przypisane pytanie, którym się ją wykrywa.

F1. **Niedeterministyczne rozstrzyganie kilku promocji.** Kasa nalicza „jakąś" cenę, a różnicę widać
dopiero w marży po fakcie. Pytania: A7, A9, B1, C2, C3. [AUT-R 19.08, potwierdzone]

F2. **Cena nie wraca po wygaśnięciu okna.** Promocja „na zawsze", cichy wyciek marży. Mechanizm
źródłowy: mechanika czasowa zbudowana jako trwała przecena zamiast jako promocja. Pytania: A26,
**B22** (promocja widziana jako wprowadzona, a niedziałająca albo niecofnięta), C21. B15 dotyczy
zwrotów i tej flagi nie wykrywa [PROP+ 19.08, naprawa po recenzji wydaniowej].
[AUT-R 19.08, potwierdzone]

F3. **Częściowa dystrybucja.** Promocja aktywna w części lokalizacji albo kanałów; klient widzi inną
cenę niż w materiale reklamowym, a raport pokazuje sukces. Pytania: A22, B6, B7, C39.
[AUT-R 19.08, potwierdzone]

F4. **Kumulacja bez progu marży schodzi poniżej kosztu.** Pytania: A15, A16, C11, C12.
[AUT-R 19.08, potwierdzone]

F5. **Rabat retro z niespójnego wolumenu.** Inny w systemie sprzedaży, inny w rozliczeniu: spór
i utrata rekompensaty. Pytania: A49, B14, C40. [AUT-R 19.08, potwierdzone]

F6. **Rozjazd nośnika ceny wobec kasy przy promocji.** Klient płaci więcej niż na etykiecie
[R: PRICE-005]. Pytania: A44, B26, C34. [AUT-R 19.08, potwierdzone]

F7. **Zaokrąglenia groszowe.** Procent, potem zaokrąglenie, potem rozjazd dokumentu sprzedaży
z raportem. Pytania: **A55** (reguła zaokrąglenia), **C44** (gdzie się ją konfiguruje), A34, B24,
C38. [AUT-R 19.08, potwierdzone]

F8. **Granica północy, strefa czasowa, zmiana czasu.** Promocja startuje albo gaśnie nie wtedy, co
zaplanowano. Osobno udokumentowana klasa problemu: okno kończące się o północy potrafi wyłączyć
promocję **na cały dzień**, a nie na sekundę. Pytania: A19, A20, A21, B19, B20, C14, C15, C16.
[AUT-R 19.08, potwierdzone]
[LIT: Microsoft Dynamics blog, „AX 2012 R2 for Retail - Using advanced discount periods with
discounts that have start and end times around 12am”, 05.01.2014; źródło dotyczy AX 2012 R2, więc
jest dowodem istnienia klasy problemu, nie aktualnego defektu D365]

F9. **Dane pozycji zmienione w trakcie okna.** Nowa albo wycofana pozycja w środku promocji zostaje
bez zdefiniowanego zachowania. Pytania: A24, B9, C18, C19. [AUT-R 19.08, potwierdzone]

F10. **Autonomia cenowa lokalizacji wobec promocji centralnej.** W modelu miękkim centrala nie
narzuca promocji, tylko zaprasza; założenie odwrotne kończy się sporem albo niewykonaniem akcji.
Pytania: A1, A4, C2. [AUT-R 19.08, potwierdzone]

F11. **Promocja na kategorii z ograniczeniem albo zakazem obniżek.** Wygląda jak zwykła obniżka,
a jest naruszeniem. Bramka dopuszczalności kategorii z pola 9. Pytania: **A53** (czy takie kategorie
w ogóle są w asortymencie), **A54** (czy lista jest atrybutem, czy wiedzą w czyjejś głowie),
**C43** (czy system blokuje), A46, C36. [AUT-R 19.08, potwierdzone]

F12. **Priorytet mylony z kolejnością arytmetyczną.** „Priority" w silnikach zwykle nie znaczy
„stosuj najpierw", tylko „wygrywa w rozstrzyganiu", a bywa, że kolejność klas rabatu jest zaszyta
w kodzie i konfiguracja jej nie zmienia. Analityk zapisuje w specyfikacji jedno, system robi drugie,
i nikt tego nie zderza aż do audytu marży. Pytania: A9, B2, C3.
[PROP+ 19.08, recenzja i research 19.08]
[LIT: Salesforce B2C Commerce, „Promotion Priority Rules”, help.salesforce.com id
`cc.b2c_promotion_priority_rules`: „If two promotions have a rank, the promotion with the lowest
rank is calculated first”]

F13. **Dwa piętra sterowania łączeniem promocji.** Ustawienie na pojedynczej promocji bywa
nadpisywane parametrem globalnym systemu, a w badanym silniku dwa dostępne modele globalne dają
przeciwne zachowanie
przy tej samej konfiguracji promocji. Wychodzi jako „dziwny wynik na jednym koszyku", którego nikt
nie wiąże z parametrem globalnym, albo po roku, przy zmianie tego parametru w ramach aktualizacji.
Pytania: A8, B3, C5. [PROP+ 19.08, research]

F14. **Obietnica najlepszej ceny dla klienta, której vendor nie składa.** Rozstrzygnięcie optimum
przy wielu promocjach jest problemem kombinatorycznym, a **część vendorów wprost pisze, że go nie
rozwiązuje**, tylko stosuje heurystykę priorytetów. Biznes słyszy „system wybierze najkorzystniejszy
zestaw" na prezentacji i wpisuje to do wymagań. Wychodzi przy reklamacji klienta, który policzył
ręcznie lepszy wariant. Pytania: A7, C4. [PROP+ 19.08, research]
[LIT: Salesforce B2C Commerce, „Promotion Priority Rules”: „B2C Commerce doesn't evaluate all
sequences of promotions”; Microsoft Learn, „Apply multiple retail discounts to a product”: tryb
`Best price` jest konkursem wewnątrz priorytetu, nie globalnym]

F15. **Flaga zatrzymania kolejnych promocji potrafi działać na koszyku zamiast na linii.** Rabat na
pozycji drugiej znika, bo pozycja pierwsza miała ustawione „nie licz nic więcej". Przy testach
jednopozycyjnych nie wyjdzie nigdy. **Podstawą jest udokumentowany, numerowany defekt jednego
produktu, naprawiony w późniejszej wersji**, więc flaga dowodzi, że taka implementacja bywa
spotykana, a nie że tak zachowuje się klasa silników. Pytania: A8, B4, C6. [PROP+ 19.08, research]
[LIT: Adobe Commerce, Quality Patches Tool, ACSD-49480; dotknięte wersje 2.4.4-2.4.5, naprawa
w 2.4.7]

F16. **Promocja wyłączna ustawiona kiedyś i nigdy niecofnięta.** W części silników wyłączność jest
oceniana przed priorytetem, więc stara promocja o niskim priorytecie wycina nową akcję. Wychodzi
pierwszego dnia akcji reklamowej. Pytania: A10, B5, C7. [PROP+ 19.08, research]
[LIT: Microsoft Learn, „Apply multiple retail discounts to a product”: „the system always evaluates
and applies Exclusive discounts before it evaluates Best price and Compounded discounts”; Salesforce
B2C Commerce, hierarchia Global Exclusive / Class Exclusive Product / Non-Exclusive Product]

F17. **Próg liczony od innej podstawy niż zakładał biznes.** Kwota przed rabatami, po rabatach,
albo z pominięciem pozycji nierabatowalnych: trzy sensowne odpowiedzi, jeden wynik na paragonie.
Objawia się jako spór z klientem, nie jako błąd systemu. Pytania: A11, A12, C8.
[PROP+ 19.08, research]

F18. **Rabat na cały paragon omija wykluczenia pozycyjne.** Rabat koszykowy jest osobną klasą bytu
i w części systemów wymaga własnych wykluczeń. Skutek jest poważniejszy niż marża: rabat dosięga
pozycji, na które promocji być nie powinno, i obchodzi bramkę dopuszczalności kategorii.
Pytania: A13, C9. [PROP+ 19.08, research]

F19. **Korzyść liczona poza silnikiem wchodzi poza kolejką.** Lojalność, kupony albo personalizacja
wstrzykiwane integracją bywają aplikowane przed wszystkim innym i nie podlegają ani wykluczeniom,
ani progowi marży. Wchodzi zwykle w drugiej fali wdrożenia, już po odbiorze, więc nie ma nawet kogo
zapytać. Pytania: A14, C10. [PROP+ 19.08, research]

F20. **Erozja wyprzedzenia.** Ścieżka awaryjna używana rutynowo, bo szybsza, kasuje jedyną prewencję
przed rozjazdem materiału reklamowego z kasą. Nie wychodzi jako awaria, tylko jako trend, mierzalny
dopiero gdy ktoś policzy udział aktywacji awaryjnych. Miara do pola 13. Pytania: A22, A23, C17.
[PROP+ 19.08, research]

F21. **Konflikt sprawdzany przy zmianie statusu, nie przy zmianie danych.** Promocja zatwierdzona
tydzień temu nie wie, że wczoraj zmieniła się cena regularna pozycji, którą obejmuje. Wychodzi
w szczycie kalendarza promocyjnego. Pytania: B9, C18. [PROP+ 19.08, research]

F22. **Kupon bez identyfikatora egzemplarza.** Numer identyfikuje ofertę, nie wydany egzemplarz,
więc jednokrotność użycia opiera się wyłącznie na liczniku silnika. Osobno: licznik bywa
niecofający się przy anulowaniu ani zwrocie, a limit „raz na klienta" w części implementacji nie ma
się do czego przyczepić przy sprzedaży bez identyfikacji klienta, czyli w domyślnym trybie kasy.
Drugi człon jest odczytem z API jednego produktu, nie pomiarem rynku. Pytania: A27, A28, A29, C22,
C23, C24. [PROP+ 19.08, research]
[LIT: GS1, Global Coupon Number (GCN), strona standardu klucza identyfikacyjnego; commercetools HTTP
API, „Discount Codes”, pola `maxApplications` i `maxApplicationsPerCustomer`]

F23. **Okno kuponu ustawiane gdzie indziej niż okno promocji.** Włączenie kuponu potrafi przejąć
sterowanie datami, przez co dwa zespoły ustawiają je niezależnie i kupon działa po wygaśnięciu
akcji. Pytania: A30, C25. [PROP+ 19.08, research]
[LIT: Microsoft Learn, „Retail discounts”, sekcja „Coupon code required”]

F24. **Limity silnika osiągnięte w szczycie kalendarza.** Liczba aktywnych promocji i liczba pozycji
w jednej promocji **bywają ograniczone twardym limitem** (w badanych źródłach: limity dzierżawy SaaS
oraz ostrzeżenie wydajnościowe), a przekroczenie objawia się w najgorszym możliwym momencie i jako
błąd zapisu, nie jako błędna cena. Karta **nie twierdzi, że limit ma każdy silnik**; twierdzi, że to
jest liczba do wyciągnięcia od vendora. Pytania: A31, B23, C26, C27. [PROP+ 19.08, research]
[LIT: commercetools, „Limits”; Microsoft Learn, „Retail discounts”, ostrzeżenie o wydajności]

F25. **Rabat wielosztukowy skoncentrowany na najtańszej linii.** Przy zwrocie sztuk pełnopłatnych
klient zatrzymuje darmową sztukę, a detalista notuje stratę. Wychodzi kilka tygodni po starcie
mechaniki, przez zwroty; w testach prawie nigdy, bo rzadko testuje się zwrot CZĘŚCI zestawu.
Pytania: A32, A33, A34, B15, C28. [PROP+ 19.08, research]
[LIT: Microsoft Learn / Dynamics 365 release notes, kwiecień 2019, „Distribute discount across lines”]

F26. **Gratis modelowany jako rabat stu procent.** Wydanie nieodpłatne i obniżka ceny to w ujęciu
projektowym dwa różne zdarzenia, a **karta nie asertuje prawa podatkowego**: zbiera brzmienia
i kieruje do doradcy podatkowego klienta. Konsekwencja systemowa, którą karta stawia we własnym
imieniu: bez odrębnego zdarzenia nie ma ewidencji, na której doradca mógłby cokolwiek oprzeć.
Pytania: A35, A36, B18, C29, C30. [PROP+ 19.08, research; do weryfikacji]
[LIT: TSUE C-48/97, sentencja i pkt 29-31, EUR-Lex; art. 7 ust. 2-4 ustawy o VAT. Odczyt art. 7
ust. 4 niepełny, drugi próg kwotowy nieodczytany]

F27. **Punkty lojalnościowe traktowane jako koszt marketingu.** Kierunek, który karta wskazuje do
sprawdzenia z księgowością klienta: punkty naliczone przy sprzedaży bywają ujmowane jako
zobowiązanie wobec klienta, a nie jako koszt marketingu; wycena wymaga wtedy salda, wiekowania
i wskaźnika wykorzystania. **Karta nie asertuje rozstrzygnięcia rachunkowego.** Konsekwencja
systemowa we własnym imieniu: jeśli system podaje wyłącznie saldo, nie ma z czego zrobić wyceny,
a brak wychodzi przy pierwszym zamknięciu rocznym.
Pytania: A51, B16, B17. [PROP+ 19.08, research; do weryfikacji]
[LIT: IFRS 15 B39-B43, numeracja paragrafów przez opracowanie wtórne (IFRS Community, „Customer
Loyalty Programmes"), nieodczytana z tekstu standardu]

F28. **Promocja reklamowana bez pokrycia zapasem.** Zapraszanie do zakupu bez racjonalnych podstaw
do sądzenia, że towar będzie dostępny, oraz formuła o ograniczonej dostępności użyta bez pokrycia,
figurują w źródłach jako **nazwane praktyki**. **Karta nie asertuje tego jako prawa wiążącego**:
regulatory-matrix w tej karcie zna wyłącznie PRICE-001..005 i wiązania z dyrektywą o nieuczciwych
praktykach w niej nie ma; wiązanie zgłoszone jako GAP w polu 12. Pytania: A37, A38, A39,
C31. [PROP+ 19.08, research; do weryfikacji]
[LIT: Dyrektywa 2005/29/WE, Załącznik I pkt 5, 6 i 7, tekst skonsolidowany EUR-Lex, wersja
28.05.2022; eCFR 16 CFR § 424.1-424.2]

F29. **Zestaw promocyjny bez rozstrzygnięcia, czy jest regułą czy pozycją.** Standard identyfikacji
przewiduje, że produkt promocyjny bywa, że wymaga własnego numeru na poziomie opakowania
zbiorczego. Objawia się jako problem magazynowy przy pierwszym przyjęciu, więc nikt nie łączy go
z promocją. Pytania: A40, A41, C32. [PROP+ 19.08, research]
[LIT: GS1 GTIN Management Standard, reguły 2.7 i 2.8, ref.gs1.org]

F30. **Procent obniżki liczony od ceny z cennika zamiast od ceny odniesienia.** Silnik promocyjny
musi czytać historię ceny w momencie ogłaszania, a nie brać liczby z bieżącego cennika ani od
analityka. To jest wprost wiązanie do ORPR-CAT-02. Nie wychodzi w testach, bo testy sprawdzają
naliczenie, nie treść komunikatu. Pytania: A42, A43, B8, C33.
[PROP+ 19.08, research; R: PRICE-001]
[LIT: UOKiK, komunikat o decyzjach DOZIK-9/2025 i DOZIK-10/2025; wytyczne Komisji Europejskiej
2021/C 526/02, sekcja 2.1]

F31. **Cena odniesienia podana w jednym miejscu, brakująca w innym.** Obowiązek dotyczy każdego
miejsca prezentowania obniżki, więc etykieta, ekran, aplikacja i materiał drukowany muszą dostać tę
samą liczbę z tego samego źródła. Wychodzi wcześniej jako spór o to, kto ma ją wpisać.
Pytania: A44, B26, C34. [PROP+ 19.08, research; R: PRICE-004]
[LIT: UOKiK, „Informacja o obniżce ceny. Wyjaśnienia Prezesa UOKiK", Warszawa 2023, s. 26;
Komisja Europejska 2021/C 526/02, sekcja 2.2]

F32. **Obniżka etapowa liczona od ceny sprzed pierwszego etapu.** Kampania ciągła i ciąg osobnych
kampanii mają różną podstawę komunikatu, a rozróżnienie musi być zapisane jako atrybut, bo z samej
mechaniki nie wynika. Pytania: A45, C35. [PROP+ 19.08, research; R: PRICE-001]
[LIT: UOKiK 2023, s. 18; Komisja Europejska 2021/C 526/02, sekcja 4.3]

F33. **Obowiązek informacyjny wywodzony z mechaniki, a nie z komunikatu.** Dwie promocje o
identycznej regule w silniku mogą mieć różny obowiązek, bo różnią się tym, co mówią klientowi.
To jest najmniej intuicyjna rzecz w całej warstwie i analityk sam na nią nie wpadnie. Wymaga pola
w systemie i bramki akceptacji, nie wiedzy w czyjejś głowie. Pytania: A46, A47, B27, C36.
[PROP+ 19.08, research]
[LIT: UOKiK 2023, s. 19; Komisja Europejska 2021/C 526/02, sekcja 3]

F34. **Personalizacja ceny bez ujawnienia.** Istnieje **kandydat na obowiązek** poinformowania
konsumenta, że cena została ustalona automatycznie na podstawie jego profilu, i jest to oś osobna od
obowiązku podania ceny odniesienia. **Karta nie przesądza, że taki obowiązek wiąże w Polsce**: wiązanie
nie jest jeszcze w regulatory-matrix i figuruje w polu 12 jako GAP. Niezależnie od rozstrzygnięcia
prawnego pozostaje wymaganie projektowe: jeśli klient ma być poinformowany, oznaczenie musi być
atrybutem promocji przenoszonym do kanału, nie tekstem w kreacji.
Pytania: A48, C37. [PROP+ 19.08, research; do weryfikacji]
[LIT: Parlament Europejski, studium „Personalised pricing", IPOL_STU(2022)734008, sekcja o obowiązkach
prawnych, cytująca dyrektywę o prawach konsumenta art. 6(1)(ea); odczyt ze studium, nie z tekstu
dyrektywy; numer przepisu polskiej ustawy wdrażającej nieustalony]

F35. **Dwa silniki, dwa wyniki.** Gdy kanał cyfrowy i kasa liczą promocję osobnymi implementacjami,
wyniki potrafią się rozjechać. **Mechanizm rozjazdu (zaokrąglenia, kolejność, alokacja rabatu na
linie) jest hipotezą wywiedzioną logicznie, nie pomiarem** [HIP]: nie znaleziono źródła, które by go
zmierzyło. Objaw, którego szukamy: różnica grosza w koszyku z odbiorem w lokalizacji.
Pytania: B24, B25, C38. [PROP+ 19.08, research]
[LIT: SAP, opis przez źródło wtórne (ERPQnA), pewność niska; dokumentacja pierwotna niedostępna]
