# [ORPR-CAT-01] Item-to-Sellable

> [!NOTE]
> **Szybka ścieżka:** zacznij od celu biznesowego, granic, właściciela, wejść, wyjść i bramek.
> Metadane, historia wersji, bank pytań i czerwone flagi dokumentują pochodzenie treści oraz
> wspierają późniejszy warsztat; nie trzeba ich czytać, aby zrozumieć podstawowy przebieg procesu.

Podtytuł roboczy (PL): od decyzji o wprowadzeniu pozycji do asortymentu, przez skompletowanie danych i dopuszczenie do sprzedaży, po wycofanie i zastąpienie następcą.

| | |
|---|---|
| ID | ORPR-CAT-01 (wg standard/mapa-procesow.md; freeze notacji: obowiązuje od v0.1.0) |
| Wersja karty | 0.7 |
| Status | **reviewed** (19.08.2026, wg wewnętrzna procedura redakcyjna: arkusz decyzyjny rozstrzygnięty w całości, 0 otwartych `[PROP]`, liczone wzorcem na klasę tagu, nie na jego pustą formę, patrz P20). Do `released` brakuje niezależnej recenzji wydaniowej wg KONSTYTUCJI sekcja 6, **wykonanej modelem innym niż główny autor** |
| Zmiany w 0.4 (19.08.2026) | naprawa po recenzji wydaniowej: rozstrzygnięte 6 otwartych `[PROP]` niewidocznych dla poprzedniego filtra; usunięta zduplikowana macierz obsady bramek (żyje w `standard/mapowania/modele-operacyjne.md`); CM domknięte jako implikacja jednostronna wobec M2 i M3; pole 12 uzupełnione o PRICE-001, PRICE-002 i PRICE-004; „siedem danych" poprawione na osiem (policzone); nazwa „klasyfikacja psuwalności" zastąpiona czytelnym „oznaczenie towaru jako szybko psującego się" |
| Zmiany w 0.5 (19.08.2026) | naprawa po recenzji wydaniowej FABLE (recenzent innym modelem niż autor, zasady governance projektu spełniona): „cztery z dziesięciu" -> **cztery z dziewięciu** przy dziewięciowierszowej tabeli pola 12 (poprzednia naprawa liczb wprowadziła nową błędną liczbę); pole 13 przestało zapowiadać artefakt, który już istnieje; **pole 7 deklaruje zakres sprzedawalności w trzech wymiarach**, konsumowany przez pole 9 i F22; F18 i pole 11 przestały asertować obowiązek prawny w momencie dopuszczenia, przeformułowane na wymaganie ORPR z jawnym `[do weryfikacji]`; bank policzony na **92 pytania** zamiast raportowanych 94 |
| Zmiany w 0.6 (20.08.2026) | naprawa po recenzji delty FABLE: wycofane twierdzenie, że ORPR-CAT-03 stawia tej karcie wymaganie (grep po CAT-03 dawał zero trafień) - atrybucja poprawiona na dyktando plus macierz, lustrzany zapis dopisany po stronie CAT-03; klasa `[do weryfikacji]` dopisana do legendy karty i do kanonicznej tabeli klas w `procedura redakcyjna`; kontrola „identyfikator nie niesie znaczenia" przepisana na zdanie przeparsowalne, z jawną adresacją wystawca kontra detalista; A1 przestało pytać listą nazw i odsyła do testu T1-T3; A32 i A21 rozbite na osobne fakty (nowe A41, A42); uporządkowana kolejność bloku B; bank 92 -> 94 pytania |
| Zmiany w 0.7 (20.08.2026) | naprawa po recenzji **pełnej** (tryb wg KONSTYTUCJI 6a: 5,9% zmienionych linii, próg przekroczony): pole 7 deklaruje **dane produktowe wymagane prawem** (konsumowane przez warunek wyjścia pola 9 i F18), **rynek docelowy** (F16, A30, C19) oraz **typ bytu** (F26, A37, C27); A41 i A42 przeniesione nad nagłówek bloku B, w którym omyłkowo wylądowały przy rozbijaniu pytań złożonych; klasa `[R: ...]` dopisana do legendy karty, choć karta używała jej 12 razy |
| Klasa treści | rdzeń retail-neutralny; warstwa branżowa w profile/ (P15) |
| Bezpieczniki R | regulatory-matrix v1.0.1, legal_as_of 2026-08-14 (patrz pole 12) |
| Crosswalk | standard/mapowania/crosswalk-frameworki.md (APQC / ARTS-NRF / GS1) |
| Clean-room | 2026-08-19: wiedza dziedzinowa, źródła publiczne i prawo powszechne; zero materiałów klientów i pracodawców |

Klasy twierdzeń wg wewnętrznej procedury redakcyjnej, krok 1: `[AUT-R]` wypowiedź właściciela z datą,
`[PROP]` propozycja redakcyjna do rozstrzygnięcia, `[PROP+ data]` propozycja przyjęta, `[LIT: ...]`
źródło publiczne z lokatorem, `[HIP]` hipoteza z mechanizmu, `[R: <ID>]` wiązanie z regulatory-matrix (struktura, nie opinia
prawna), `[do potwierdzenia]` niezweryfikowane u źródła, `[do weryfikacji]` kandydat do zgłoszenia
maintainerowi regulatory-matrix, **NIE asertowany jako prawo**.

Dyktanda właściciela: **19.08.2026 tura 1** (sześć odcinków zakresu) oraz **19.08.2026 tura 2**
(arkusz decyzyjny, 21 pytań plus blok zbiorczy; cztery odpowiedzi przyniosły korektę merytoryczną,
a nie samo zatwierdzenie: dwie blokady zamiast jednej, branżowa baza referencyjna jako klasa
systemu, kalibracja o skuteczności wykrywania duplikatów, kalibracja o zakresie wymiaru czasu).

## Miejsce karty w domenie CAT

| Zagadnienie | Właściciel |
|---|---|
| decyzja o wprowadzeniu pozycji do asortymentu | **CAT-01** |
| tożsamość pozycji: identyfikacja, nazwa, producent, deklaracje | **CAT-01** |
| dane do wyceny: jednostka sprzedaży, miary, klasyfikacja podatkowa | **CAT-01** |
| dopuszczenie do sprzedaży i zakres (lokalizacje, kanały) | **CAT-01** |
| cykl życia pozycji, wycofanie, następstwo | **CAT-01** |
| cena regularna, cennik, historia ceny | ORPR-CAT-02 |
| promocja | ORPR-CAT-03 |
| zapas, przyjęcie towaru, partie fizyczne | domena zapasu i zakupów |
| naliczenie w koszyku | ORPR-SAL-01 |

**Granica karty jest zgodna z podziałem stosowanym w standardach wymiany danych**
[LIT: GS1 General Specifications R26.0, sekcja 2.1.15]. Standard rozdziela **trade item declarations** (deklaracje o produkcie: marka, typ, zawartość netto,
wymiary) od **offer declarations** (*„the set of all information declared (or agreed to) by the
seller about the trade item (inclusive of price, availability, terms of sale, claims, **condition of
the item**, shipping information, returns information)"*). Pierwsze to CAT-01, drugie to CAT-02
i SAL-01. To jest podział atrybutów w komunikacie między partnerami, a nie podział procesów
wewnętrznych detalisty, więc **zgodność jest argumentem za granicą ORPR, nie jej dowodem** [PROP+ 19.08].

**Wyłączenie: stan egzemplarza** [PROP+ 19.08]. Oznaczenie towaru jako niepełnowartościowego, którego CAT-02
używa jako warunku zejścia poniżej kosztu, **nie jest daną pozycji i nie powstaje tutaj**. Dotyczy
konkretnej sztuki albo partii, nie kartoteki, i w podziale stosowanym w standardach wymiany danych
należy do deklaracji oferty, nie do deklaracji pozycji. Miejscem jego powstania jest domena zapasu.
CAT-01 wytwarza natomiast osiem danych, których CAT-02 żąda wprost (patrz pole 8: osiem wierszy
tabeli wymienia CAT-02 jako konsumenta).

## Oś wstępna: model operacyjny sieci

Pierwsza zmienna do ustalenia, przed wszystkim innym. Że kierunek decyzji odwraca się między
modelami, jest wypowiedzią właściciela [AUT-R 19.08]; że ta sama oś pojawiła się wcześniej w CAT-02
przy kierunku przepływu ceny, jest obserwacją redakcyjną [PROP+ 19.08].

**Macierz obsady bramek dla wszystkich modeli stoi w `standard/mapowania/modele-operacyjne.md`.**
Tam jest test klasyfikacyjny (trzy pytania), pełna macierz bramka razy model dla trzech kart domeny
CAT oraz rejestr odcinków warunkowych. Treść macierzy pochodzi z dyktanda właściciela z 19.08.2026
[AUT-R 19.08]. **Ta karta macierzy nie powtarza** [PROP+ 19.08, redakcja]; wiersze jej dotyczące to
`wprowadzenie pozycji do asortymentu`, `założenie pozycji lokalnej` i `wycofanie pozycji z oferty`.

Przymus asortymentowy bywa zapisem umownym: obowiązek posiadania na półce całego asortymentu objętego
akcją reklamową sieci [AUT-R 19.08]. To jest jedyne miejsce, w którym wymaganie płynie **od promocji
do asortymentu**, a nie odwrotnie. Źródłem jest dyktando właściciela i wiersz macierzy
`przymus asortymentowy z akcji reklamowej [CAT-03 -> CAT-01]` w `standard/mapowania/modele-operacyjne.md`;
lustrzany zapis stoi w ORPR-CAT-03 pole 10 [PROP+ 20.08, naprawa po recenzji delty].

**Druga oś, warunkowa: zarządzanie kategorią (CM).** Występuje wyłącznie przy dwóch najtwardszych
modelach (M2 i M3); implikacja działa w jedną stronę, czyli CM oznacza M2 albo M3, ale M2 albo M3
nie oznacza CM. Falsyfikator tej reguły stoi w `standard/mapowania/modele-operacyjne.md`. Nie jest kolejnym stopniem na tej samej skali, tylko odrębnym wymiarem, który **dokłada
odcinki procesu, których bez niego nie ma** (patrz pole 11, odcinki warunkowe). [AUT-R 19.08]

## Model pojęciowy

### Tożsamość pozycji: kiedy powstaje nowa, a kiedy poprawiamy starą

To jest najbardziej niedoceniane pytanie w całej domenie CAT, bo od niego zależy ciągłość historii
ceny (CAT-02, flaga F17) i wiarygodność każdej analizy sprzedaży.

**Kogo wiąże standard, a kogo nie.** To rozróżnienie jest warunkiem poprawnego użycia całej tej
sekcji [PROP+ 19.08]. Reguły identyfikacji adresują **wystawcę identyfikatora** (właściciela marki) i mówią
mu, kiedy musi nadać nowy numer. Detalisty nie wiążą. Dla detalisty są **sygnałem**: nowy numer od
dostawcy oznacza, że przyszedł inny produkt. Detalista potrzebuje więc dwóch reguł, nie jednej:
- reguły odczytu sygnału: nowy identyfikator to nowa kartoteka;
- **własnej reguły na rozbieżność**: co zrobić, gdy dostawca zmienił produkt, a numeru nie zmienił
  (patrz flaga F3), albo zmienił numer bez zmiany produktu.
Karta, która przepisze reguły wystawcy jako reguły detalisty, zostawia ten drugi przypadek bez
odpowiedzi, a to jest właśnie przypadek, który występuje u klienta.

Standard identyfikacji daje na to twardą odpowiedź i jest ona **surowsza, niż zakłada praktyka**
[LIT: GS1 GTIN Management Standard, Release 1.1, ratyfikowany wrzesień 2023, sekcja 2, reguły 2.1
do 2.10]. Dziesięć reguł wymuszających nowy identyfikator: nowy produkt; zmiana deklarowanej receptury lub
funkcjonalności; **zmiana deklarowanej zawartości netto**; zmiana wymiaru lub masy brutto; dodanie
albo usunięcie znaku certyfikacji; zmiana marki podstawowej; produkt czasowy lub promocyjny;
liczba sztuk w opakowaniu zbiorczym; predefiniowany zestaw; nadruk ceny na opakowaniu.

**Dwa progi, które mylą się w praktyce** [LIT: jw., reguły 2.3 i 2.4]:
- **zawartość netto: brak progu.** Cytat: *„Any change (increase or decrease) to the legally-required
  declared net content that is printed on the pack, requires assignment of a new GTIN."* Zmiana
  gramatury o kilka gramów wymusza nowy identyfikator.
- **wymiary i masa brutto: próg 20 %**, z klauzulą antyobejściową: kumulowanie zmian poniżej progu,
  żeby uniknąć przekroczenia, jest w standardzie wskazane jako niedopuszczalna praktyka.

Powszechne przekonanie jest odwrotne: że próg procentowy dotyczy zawartości. Nie dotyczy.

**Furtka na cichą podmianę.** Reguła dotycząca receptury ma test **dwuczłonowy i koniunkcyjny**:
zmiana musi dotykać informacji wymaganej prawem na opakowaniu **oraz** właściciel marki musi
oczekiwać, że odbiorca ją rozróżni [LIT: jw., reguła 2.2]. Zmiana receptury, która nie dotyka
deklaracji prawnych, nie wymusza nowego identyfikatora. Standard przewiduje na to osobne oznaczenia
wariantu [LIT: GS1 General Specifications R26.0, 4.2.2.3: Consumer Product Variant oraz identyfikator
wariantu wewnętrznego]. Detalista, który tych oznaczeń nie czyta, **nie zauważy podmiany zawartości
przy niezmienionym identyfikatorze**.

### Ponowne użycie identyfikatora

Zasada obowiązująca: **identyfikator raz przypisany nie może zostać przypisany innej pozycji**
[LIT: GS1 GenSpecs R26.0, 4.2.5, obowiązuje od 1 stycznia 2019]. Wyjątki wąskie: identyfikator nigdy
nieopublikowany na zewnątrz, identyfikator publikowany wyłącznie jako roboczy (karencja 12 miesięcy
i zgoda partnerów), oraz powrót pozycji na rynek bez zmian wymuszających nowy numer.

Reguły zdeprecjonowane, **nadal istotne dla danych zastanych w systemie klienta** [LIT: jw., 4.16.1]:
karencja minimum 48 miesięcy, w części sektorów krótsza, a w sektorach regulowanych brak ponownego
użycia w ogóle (wartości per sektor pod wskazanym lokatorem; rdzeń ich nie powtarza, P15). Standard uzasadnia to wprost troską o dane historyczne partnerów, wykorzystywane do
analiz i serwisu długo po tym, jak pozycja zniknęła z obrotu.

To jest niezależne, źródłowe potwierdzenie praktyki właściciela: **przy wycofaniu pozycji identyfikator
zachowujemy ze względów analitycznych** [AUT-R 19.08].

### Następstwo pozycji

Standard nie zna statusu „następca" na poziomie identyfikatora. Relacja jest wyrażana atrybutami
wymiany danych: kod typu relacji do identyfikatora referowanego, z wartościami obejmującymi zamiennik,
zastąpienie, zastąpienie tymczasowe i odpowiednik [LIT: GS1 Attribute Business Definitions Standard,
Release 1.0, atrybuty referenced trade item type code oraz referenced trade item]. Osobno, przy
modyfikacji wymuszającej nowy numer: *„a linkage between the new GTIN and the original GTIN SHALL be
maintained and provided to downstream trading partners if requested"* [LIT: GenSpecs R26.0, 2.1.15].

**Wniosek dla karty** [PROP+ 19.08]: te atrybuty są opcjonalne i zależne od publikującego, więc detalista nie
może na nich polegać. Łańcuch następstwa pozycji musi być utrzymywany **po stronie detalisty**, jako
obiekt pierwszej klasy, a nie odczytywany z danych dostawcy.

### Sprzedawalność nie jest właściwością pozycji

Uznany model danych rozstrzyga to jednoznacznie: pozycja niesie wartości domyślne przedsiębiorstwa,
a nadpisania lokalne siedzą na powiązaniu pozycji z grupą jednostek biznesowych [LIT: ARTS Retail
Operational Data Model 7.3, Logical 01020: *„the enterprise default values for an item's attributes
are stored in `Item` while the entity `BusinessUnitGroupItem` stores per-store, (or per-group of
stores) localizations of those attribute values"*].

Czyli **sprzedawalność jest właściwością pary (pozycja, zakres organizacyjny)**, nie samej pozycji
[PROP+ 19.08]. Zgadza się to z praktyką: część asortymentu
obowiązuje wszystkich, reszta wchodzi nakładkami regionalnymi, a niektóre pozycje istnieją wyłącznie
w kanale cyfrowym albo wyłącznie stacjonarnie [AUT-R 19.08].

Standard ostrzega przy tym przed iloczynem kartezjańskim i podaje rachunek: 25 000 pozycji razy
1100 lokalizacji to **27,5 miliona** wierszy, więc zakres nadpisań musi być kontrolowany
[LIT: jw.; liczba przeliczona niezależnie 19.08.2026, P5].

### Czego modele referencyjne tu NIE mają

Dwa ustalenia negatywne, ważne, bo tłumaczą, dlaczego ta karta musi być pisana, a nie przepisana:

1. **Framework procesowy cross-industry daje kotwice dla danych pozycji, ale nie dla dopuszczenia
   jej do sprzedaży.** Hierarchia zarządzania danymi podstawowymi produktu ma rodowód produkcyjny
   (listy materiałowe, marszruty, rysunki, specyfikacje procesowe); nośne dla tej karty są w niej
   elementy specyfikacji, klasyfikacji, śledzenia i dostępu do danych [LIT: APQC PCF Cross-Industry
   v7.4, 2.1.4 i podelementy; mapowanie w standard/mapowania/crosswalk-frameworki.md]. Nie ma
   natomiast osobnego elementu dla **dopuszczenia pozycji do sprzedaży w zakresie lokalizacji
   i kanałów** ani dla zarządzania asortymentem. Karta dekomponuje więc element danych podstawowych,
   a nie powtarza framework. Wydanie detaliczne frameworku może to rozwijać [do potwierdzenia].
   Twierdzenie o nieobecności terminów asortymentowych opiera się na wyszukiwaniu pełnotekstowym
   wykonanym przez autora karty 19.08.2026, nie na cytacie ze źródła [PROP+ 19.08].
2. **Model danych sam deklaruje niedorozwój.** Cytat: *„Entities related to the creation and
   management of item and price maintenance ... are not fully developed beyond the DataMaintenanceEvent
   of this release."* Nie potwierdzono w publicznej narracji ani encji statusu pozycji, ani dat
   obowiązywania, ani flagi wycofania [LIT: ARTS ODM 7.3, Logical 01300; przeszukanie 190 tematów
   narracji]. Atrybuty mogą istnieć w pakiecie modelu, do którego nie mamy dostępu
   [do potwierdzenia].

Model danych daje więc kartę CAT-01 solidne kotwice dla samej pozycji i jej struktury (pozycja,
pozycja magazynowa, pozycja luzem, powiązanie pozycji z grupą jednostek, konwersje jednostek miary),
ale **nie daje wzorca dla stanów i temporalności pozycji**. Tę warstwę karta definiuje sama
(pole 8, tabela stanów) i jest to świadome uzupełnienie luki, nie powtórzenie modelu. [PROP+ 19.08]

## Cykl życia pozycji

impuls -> decyzja o wprowadzeniu -> nadanie tożsamości -> skompletowanie danych -> dopuszczenie do
sprzedaży w zadeklarowanym zakresie -> obowiązywanie i zmiany -> wstrzymanie albo wycofanie ->
zastąpienie następcą -> zachowanie identyfikatora i historii.

**1. Cel biznesowy:** doprowadzić pozycję asortymentową do stanu, w którym jest jednoznacznie
zidentyfikowana, ma komplet danych wymaganych do wyceny, uwidocznienia i sprzedaży, i jest dopuszczona
do sprzedaży w jawnie określonym zakresie lokalizacji i kanałów, a następnie utrzymać jej tożsamość
i ciągłość przez cały cykl życia, aż po wycofanie i zastąpienie następcą.

**2. Granice:** od impulsu do wprowadzenia pozycji do potwierdzonego dopuszczenia do sprzedaży
w zadeklarowanym zakresie; dalej przez zmiany danych, wstrzymanie i wycofanie, do zapisania relacji
następstwa.

NIE obejmuje: ustalenia ceny, cennika i historii ceny (-> CAT-02); promocji (-> CAT-03); planowania
zapotrzebowania i zamawiania (-> domena popytu i zakupów); przyjęcia towaru, partii fizycznych i stanu
egzemplarza, w tym **oznaczenia towaru niepełnowartościowego** (-> domena zapasu); naliczenia ceny
w koszyku (-> SAL-01); zarządzania półką i planogramem (-> poza zakresem obecnego pilota, brak karty).

Przekazuje dalej: tożsamość i dane pozycji do CAT-02 (wycena), CAT-03 (kwalifikacja do promocji),
domeny popytu (planowanie), SAL-01 (sprzedaż); zakres sprzedawalności do wszystkich powyższych;
relację następstwa do CAT-02 (ciągłość historii ceny).

**3. Właściciel:** zależny od modelu operacyjnego (oś wstępna). W modelu centralnym: zakupy,
marketing albo category management. W modelu rozproszonym: kierownik albo właściciel lokalizacji.
[AUT-R 19.08]

**4. Aktorzy:**
- właściciel albo kierownik lokalizacji [AUT-R 19.08]
- kierownik działu w lokalizacji, odpowiadający za wydzieloną część asortymentu [AUT-R 19.08]
- zakupy [AUT-R 19.08]
- marketing [AUT-R 19.08]
- category manager, wyłącznie przy zarządzaniu kategorią [AUT-R 19.08]
- **przedstawiciel producenta jako inicjator spoza organizacji** [AUT-R 19.08]
- operator danych podstawowych [PROP+ 19.08]
- dostawca jako źródło danych [PROP+ 19.08]
- compliance, przy kategoriach z wymaganiami informacyjnymi [PROP+ 19.08]

**5. Systemy:**
- system danych podstawowych pozycji [PROP+ 19.08]
- system zarządzania asortymentem [PROP+ 19.08]
- system informacji produktowej przy sprzedaży wielokanałowej: opisy, zdjęcia, parametry
  logistyczne [AUT-R 19.08]
- kanał wymiany danych z dostawcami [PROP+ 19.08]
- POS i kanały cyfrowe jako odbiorcy danych pozycji [PROP+ 19.08]
- rejestr klasyfikacji podatkowych [PROP+ 19.08]
- rejestr identyfikatorów i relacji następstwa [PROP+ 19.08]
- **branżowa baza referencyjna danych produktowych**, wspólna dla całego rynku danej branży, o ile
  w tej branży istnieje [AUT-R 19.08, tura 2]. To nie jest wariant „kanału wymiany danych
  z dostawcami": tam każdy dostawca przysyła swoje, tu jedno źródło opisuje cały rynek. Zmienia
  model zasilania kartoteki, bo pozycja nie jest zakładana od zera per detalista, tylko zaciągana
  z bazy, która zna produkt, zanim detalista go zobaczy. Klasa należy do rdzenia, instancje
  branżowe do profilu (P15).

**6. Wyzwalacze:**
- **oferta przedstawiciela producenta**, w praktyce najczęstszy wyzwalacz w modelu rozproszonym,
  często w postaci akcji wiązanej: rabat na produkt flagowy pod warunkiem przyjęcia nowości
  [AUT-R 19.08];
- zapotrzebowanie zgłoszone przez klienta lokalizacji [AUT-R 19.08];
- reklama zauważona przez klienta albo przez personel [AUT-R 19.08];
- decyzja handlowa centrali: sugestia albo **obowiązek umowny** posiadania asortymentu objętego
  akcją reklamową sieci [AUT-R 19.08];
- decyzja category managementu w ramach planu kategorii, tylko przy CM [PROP+ 19.08];
- wejście pozycji zastępującej wycofywaną [PROP+ 19.08];
- zmiana wymuszająca nową tożsamość pozycji wg reguł identyfikacji [LIT: GS1 GTIN Management
  Standard 1.1, sekcja 2];
- zmiana zakresu sprzedawalności: nowa lokalizacja, nowy kanał, nowe okno czasowe [PROP+ 19.08];
- **migracja kartoteki przy uruchomieniu nowego systemu (cutover)** [PROP+ 19.08];
- **wycofanie ze względów bezpieczeństwa, zainicjowane przez producenta albo organ nadzoru** [PROP+ 19.08].

**7. Wejścia (dokumenty):**

- **obowiązkowe, zestaw minimalny** [AUT-R 19.08]: nazwa; producent; stawka podatku; identyfikator
  pozycji (kod kreskowy). Poniżej tego zestawu pozycja nie istnieje jako byt handlowy.
- **obowiązkowe, jeśli sprzedaż odbywa się także w kanale zdalnym:** kwalifikacja pozycji do
  wyjątku od prawa odstąpienia od umowy. To jest atrybut pozycji, rozstrzygany tutaj i stosowany
  przy obsłudze zwrotu; jego brak oznacza, że przy każdym zwrocie decyzję podejmuje człowiek bez
  podstawy w danych [PROP+ 19.08; R: RTL-DIST-004].
- **obowiązkowe dodatkowo, jeśli pozycja ma być wyceniana i uwidoczniona** [-> dług CAT-02]:
  jednostka sprzedaży i przelicznik do opakowania zbiorczego; miara opakowania oraz **osobno miara
  porównawcza** do ceny jednostkowej; klasyfikacja podatkowa wersjonowana w czasie; **data pierwszego
  oferowania pozycji**; **oznaczenie towaru jako szybko psującego się**.
- **typowe, zależnie od organizacji** [AUT-R 19.08]: dostawca; jednostka miary; typ i rozmiar, gdy asortyment
  ma oś wariantu; kategoria sklepowa, rzadziej kategoria kategoryjna; podmiot odpowiedzialny
  za produkt.
- **przy sprzedaży wielokanałowej** [AUT-R 19.08]: integracja z systemem informacji produktowej,
  z której przychodzą opisy, zdjęcia i parametry logistyczne.
- **opcjonalne:** dane z kanału synchronizacji z dostawcami; klasyfikacja towarowa wspólna z partnerami;
  oznaczenie wariantu przy zmianie nieskutkującej nowym identyfikatorem [LIT: GS1 GenSpecs 4.2.2.3];
  relacja następstwa wobec pozycji zastępowanej.
- **obowiązkowe przy dopuszczeniu do sprzedaży: jawnie zadeklarowany zakres sprzedawalności
  w trzech wymiarach** - lokalizacje, kanały oraz okno czasowe (data początku i, jeśli dotyczy, data
  końca; okno bezterminowe jest poprawną wartością, nie brakiem danych). Wymieniony tu imiennie, bo
  konsumuje go warunek wejścia z pola 9 i flaga F22; bez deklaracji w wejściach bramka stoi na danej,
  której nikt nie zebrał [PROP+ 19.08, naprawa po recenzji wydaniowej].
- **obowiązkowe dla kategorii z wymaganiami informacyjnymi: dane produktowe wymagane prawem**
  (skład, ostrzeżenia, pochodzenie, w zakresie właściwym dla kategorii). Wymienione tu imiennie, bo
  konsumuje je warunek wyjścia z pola 9 („dane wymagane prawem dla danej kategorii kompletne albo
  pozycja jawnie zablokowana") oraz flaga F18. Instancje kategorii i konkretny zakres danych wchodzą
  warstwą profilu (P15) [PROP+ 20.08, naprawa po recenzji pełnej].
- **obowiązkowe przy sprzedaży na więcej niż jeden rynek: rynek docelowy** jako wymiar danych pozycji.
  Konsumuje go flaga F16 (obowiązek informacyjny jest funkcją klasy produktu **i rynku docelowego**)
  oraz pytania A30 i C19 [PROP+ 20.08, naprawa po recenzji pełnej].
- **obowiązkowe, jeśli kartoteka niesie byty inne niż towar: typ bytu** (towar, opłata, kaucja, karta
  podarunkowa, usługa). Konsumuje go flaga F26 oraz pytania A37 i C27; od typu bytu zależy, które
  bramki tej karty w ogóle się stosują [PROP+ 20.08, naprawa po recenzji pełnej].
- **branżowe:** klasyfikacje i reguły specyficzne dla kategorii regulowanych wchodzą warstwą profilu
  (P15), nie rdzeniem.

**8. Wyjścia:**

**Dokumenty:** kartoteka pozycji; decyzja o dopuszczeniu do sprzedaży z zakresem organizacyjnym,
kanałowym i **czasowym**; zapis relacji następstwa; zapis wycofania z zachowanym identyfikatorem.

**Dane wytwarzane tu, konsumowane przez inne procesy** (lista jawna, żeby domknięcie między kartami
dało się sprawdzić mechanicznie, a nie na słowo):

| Dana | Konsument |
|---|---|
| identyfikacja pozycji | CAT-02, CAT-03, SAL-01, popyt |
| jednostka sprzedaży i przelicznik do opakowania zbiorczego | CAT-02, popyt, zapas |
| miara opakowania | CAT-02 |
| **miara porównawcza do ceny jednostkowej** | CAT-02 [R: PRICE-004] |
| klasyfikacja podatkowa, wersjonowana w czasie | CAT-02, SAL-01 [R: FISC-020] |
| **data pierwszego oferowania pozycji** | CAT-02 [R: PRICE-002] |
| **oznaczenie towaru jako szybko psującego się** | CAT-02 [R: PRICE-003] |
| kwalifikacja pozycji do wyjątku od prawa odstąpienia | RTN [R: RTL-DIST-004] |
| dane opisowe wymagane prawem dla kategorii | SAL-01, kanał cyfrowy [R: RTL-CONS-001, RTL-DIST-001, RTL-CONS-003] |
| stan pozycji i zakres sprzedawalności | wszystkie procesy sprzedażowe i planistyczne |
| relacja następstwa | CAT-02 (ciągłość historii ceny) |

**Zdarzenia:** pozycja-utworzona, pozycja-dopuszczona-do-sprzedaży, zakres-sprzedawalności-zmieniony,
dane-pozycji-zmienione, stan-pozycji-zmieniony, pozycja-wycofana, następstwo-zapisane,
pozycja-zablokowana-ze-względów-bezpieczeństwa.

### Stany pozycji

Karta cyklu życia bez listy stanów jest niekompletna, bo analityk nie ma czego narysować, a vendor
nie ma czego zaimplementować. Minimalny zestaw, każdy stan rozstrzyga jednoznacznie cztery rzeczy
[PROP+ 19.08]:

| Stan | Zamawianie | Sprzedaż | Widoczna w kanale | Jak się z niego wychodzi |
|---|---|---|---|---|
| projektowana | nie | nie | nie | skompletowanie danych i decyzja |
| dopuszczona | tak | tak | tak | wstrzymanie, wycofanie, blokada |
| wstrzymana czasowo | nie | tak albo nie, do rozstrzygnięcia | zależnie od powodu | wznowienie albo wycofanie |
| wycofywana | nie | tak, do wyczerpania zapasu | zwykle nie | wyczerpanie zapasu |
| wycofana | nie | nie | nie | powrót do oferty (ten sam identyfikator) |
| zablokowana ze względów bezpieczeństwa | nie | **nie, twardo i natychmiast** | nie | zwolnienie blokady przez uprawnionego |

Dwie uwagi:
- **blokada zamawiania i blokada sprzedaży muszą istnieć jako dwie osobne blokady** [AUT-R 19.08,
  tura 2]. Typowy przypadek biznesowy, który tego wymaga: **wycofujemy produkt z asortymentu
  i jednocześnie chcemy go wyprzedać.** Zamawianie stoi, sprzedaż idzie dalej do wyczerpania zapasu.
  Stan, który miesza jedno z drugim w jedną flagę „aktywna albo nieaktywna", nie obsłuży ani
  wyprzedaży resztek, ani wycofania ze względów bezpieczeństwa, gdzie potrzebna jest odwrotność:
  sprzedaż stoi natychmiast, niezależnie od zapasu;
- **wycofanie po stronie dostawcy nie jest jednym zdarzeniem.** Standardy wymiany danych rozdzielają
  koniec produkcji, koniec przyjmowania zamówień i zniknięcie z katalogu jako trzy niezależne daty
  [LIT: GS1 Trade Item Implementation Guide, sekcja wycofania pozycji]. Mapowanie ich na jeden stan
  gwarantuje rozjazd z katalogiem dostawcy.

**9. Bramki decyzyjne:**

Bramka dopuszczenia do sprzedaży ma **dwa niezależne człony** i to jest ustalenie kluczowe dla tej
karty [AUT-R 19.08]:

| Człon | Czym jest | Czego pilnuje |
|---|---|---|
| **bramka logiczna systemu** | automat, nie człowiek | kompletności danych; nie przepuści pozycji bez stawki podatku |
| **decydent** | człowiek, obsada wg modelu operacyjnego | zasadności handlowej: czy ta pozycja ma tu być |

Systemy, które mają tylko pierwszy człon, dopuszczają do sprzedaży wszystko, co ma wypełnione pola.
Systemy, które mają tylko drugi, dopuszczają pozycje z dziurami w danych. Karta wymaga obu. [PROP+ 19.08]

- **warunki wejścia:**
  - zestaw minimalny wypełniony: nazwa, producent, stawka podatku, identyfikator [AUT-R 19.08];
  - **identyfikator nadany przed wystawieniem oferty.** Reguła źródłowa jest kategoryczna: *„A trade
    item SHALL be assigned a GTIN before there is an offer made for sale of the trade item"*
    [LIT: GS1 GenSpecs R26.0, 4.2.2];
  - jeśli pozycja ma być wyceniana: komplet danych z długu CAT-02 (miary, klasyfikacja podatkowa,
    data pierwszego oferowania, oznaczenie towaru jako szybko psującego się); brak któregokolwiek BLOKUJE dopuszczenie,
    a nie tylko oznacza [PROP+ 19.08; R: PRICE-002, PRICE-003, PRICE-004];
  - jawnie zadeklarowany zakres **w trzech wymiarach**: lokalizacje, kanały oraz **okno czasowe**
    (data początku sprzedawalności i, jeśli dotyczy, data końca). Bez wymiaru czasu nie da się
    obsłużyć sezonowości, uruchomienia kanału od dnia X ani planowanego wycofania [PROP+ 19.08].
    **Okno bezterminowe jest poprawną wartością, nie brakiem danych**: są kategorie sprzedawalne bez
    ograniczenia czasowego z natury, na przykład usługa, i systemy zwykle wydzielają je osobną
    kategorią [AUT-R 19.08, tura 2];
  - uprawnienie decydenta adekwatne do modelu operacyjnego (oś wstępna) [AUT-R 19.08];
  - przy pozycji zastępującej: zapisana relacja następstwa wobec pozycji wycofywanej [PROP+ 19.08].
- **warunki wyjścia:**
  - pozycja rozdystrybuowana i potwierdzona w każdej objętej kasie i kanale przed momentem, od którego
    ma być sprzedawalna; „wysłano" nie jest równe „obowiązuje" [PROP+ 19.08; analogicznie do CAT-02];
  - stan sprzedawalności rozstrzygalny jednoznacznie dla pary pozycja i zakres;
  - dane wymagane prawem dla danej kategorii kompletne albo pozycja jawnie zablokowana [PROP+ 19.08].
- **kontrole:**
  - **jedna pozycja to jedna rzecz.** Kartoteka nie może reprezentować kilku różnych produktów
    naraz. Praktyka „jedna karta na wiele produktów" (pozycja rodzajowa bez producenta i bez
    identyfikatora) występuje w organizacjach o niskiej dojrzałości i rozwala jednocześnie: wycenę,
    historię ceny, analizę sprzedaży i rozliczenie z dostawcą [AUT-R 19.08];
  - **wykrywanie duplikatów** przed utworzeniem pozycji, po identyfikatorze i po zestawie deklaracji
    tożsamościowych [PROP+ 19.08]. **Kalibracja właściciela: wymaganie jest słuszne, ale nie zna
    systemu, który realizowałby je skutecznie** [AUT-R 19.08, tura 2]. Wniosek dla analityka: to nie
    jest pozycja do odhaczenia w tabeli funkcjonalności vendora. Ciężar dowodu leży po stronie
    vendora i wymaga **demonstracji na danych klienta**, nie deklaracji „tak, obsługujemy";
  - **zmiana wymuszająca nową tożsamość** rozpoznana i obsłużona jako nowa pozycja z relacją
    następstwa, a nie jako edycja istniejącej [LIT: GS1 GTIN Management Standard 1.1, sekcja 2];
  - **zakaz ponownego użycia identyfikatora** dla innej pozycji [LIT: GS1 GenSpecs R26.0, 4.2.5];
  - **identyfikator nie koduje informacji o produkcie w swojej strukturze.** Chodzi o praktykę
    „numer sam mówi, co to za towar": zaszycie w cyfrach kategorii, gramatury albo wariantu.
    Standard tego odradza, bo **produkt zmienia się częściej niż wolno zmienić numer**, więc
    zaszyta informacja szybko przestaje być prawdziwa, a nikt jej nie prostuje
    [LIT: GS1 GenSpecs R26.0, 4.2.1]. **Reguła adresuje wystawcę identyfikatora**; dla detalisty
    jest kontrolą przy nadawaniu numerów własnych i sygnałem ostrzegawczym przy odczycie cudzych
    [PROP+ 20.08, naprawa po recenzji delty];
  - numer wewnętrzny dopuszczalny wyłącznie dla pozycji bez identyfikatora zewnętrznego i wyłącznie
    do użytku we własnej sieci [LIT: jw., 4.2.3.2];
  - przy zasilaniu z zewnątrz: jawna reguła, które źródło wygrywa przy konflikcie danych własnych
    i dostawcy [PROP+ 19.08];
  - ślad audytowy zmiany danych pozycji: kto, kiedy, co [LIT: ARTS ODM 7.3, `DataMaintenanceEvent`,
    `ItemMaintenanceEvent`, deklarowane „for audit and control purposes"].

**10. Skutki i sprzężenia międzydomenowe:**
- **stock: NIE.** Utworzenie ani dopuszczenie pozycji nie tworzy zapasu. Zapas powstaje przy przyjęciu
  towaru (domena zakupów i zapasu).
- **pieniądze: NIE.**
- **księgowość: NIE.**
- sprzężenie z wyceną: bez kompletu danych CAT-01 karta CAT-02 nie może wyliczyć ceny jednostkowej
  ani ceny odniesienia [R: PRICE-002, PRICE-003, PRICE-004].
- sprzężenie z podatkiem: klasyfikacja podatkowa jest daną pozycji, ale **wersjonowaną w czasie**,
  a jej zmiana jest zdarzeniem cenowym po stronie CAT-02 [R: FISC-020].
- sprzężenie z promocją: przymus asortymentowy z akcji reklamowej sieci wymusza obecność pozycji
  w asortymencie lokalizacji [AUT-R 19.08]; to jedyny kierunek, w którym domena promocji stawia
  wymaganie tej karcie. Lustrzany zapis: ORPR-CAT-03 pole 10 [PROP+ 20.08, naprawa po recenzji delty].
- sprzężenie z ciągłością historii: relacja następstwa pozycji jest jedynym mostem, po którym historia
  ceny przechodzi na pozycję zastępującą [PROP+ 19.08; R: PRICE-001].
- sprzężenie z planowaniem: status asortymentowy pozycji dla lokalizacji blokuje albo dopuszcza
  planowanie zapotrzebowania (domena popytu) [PROP+ 19.08].

**11. Warianty i wyjątki kluczowe:**

**Odcinek warunkowy: zarządzanie cyklem życia pozycji.** Obecny wyłącznie przy zarządzaniu kategorią.
Bez CM zarządzania cyklem życia praktycznie nie ma: pozycja wypada z oferty, bo przestaje się
sprzedawać. Typowe przyczyny wypadnięcia bez decyzji: zmiana kolekcji, zakończenie produkcji przez
wytwórcę, kanibalizacja przez inną pozycję. Przy CM pozycja przechodzi przez kolejne bramki, które
rozstrzygają, czy zostaje w ofercie, czy wypada. [AUT-R 19.08]

Karta opisuje pełny przebieg z bramkami, także tam, gdzie u konkretnego klienta ich nie ma. Odcinek
oznaczony jako warunkowy nie jest wymaganiem wobec klienta bez zarządzania kategorią.

**Odcinek warunkowy: SKU lokalne.** Prawo lokalizacji do założenia własnej pozycji na potrzeby lokalne
istnieje w części modeli, a przy zarządzaniu kategorią zwykle zamienia się w obowiązek zgłoszenia do
centrali, która może odmówić. [AUT-R 19.08]

**Zasilanie danych z zewnątrz.** Dane pozycji mogą przychodzić z kanału synchronizacji z dostawcami
albo z systemu informacji produktowej. Karta wymaga, by reguła rozstrzygania konfliktu między danymi
własnymi a zewnętrznymi była zapisana, a nie domyślna [PROP+ 19.08]. Sama treść reguły jest decyzją
klienta; pytania warsztatowe: A11, B14, C20.

**Zmiana bez zmiany identyfikatora.** Producent może zmienić recepturę tak, że reguły identyfikacji
nie wymuszają nowego numeru. Standard przewiduje wtedy oznaczenie wariantu, ale jest ono opcjonalne
[LIT: GS1 GenSpecs R26.0, 4.2.2.3]. Detalista, który go nie czyta, sprzedaje inny produkt pod tym
samym identyfikatorem i nie ma o tym wiedzy.

**Pozycja rodzajowa.** Kartoteka reprezentująca kategorię zamiast konkretnego produktu, bez producenta
i bez identyfikatora zewnętrznego. Występuje w organizacjach o niskiej dojrzałości danych. Karta
uznaje to za anty-wzorzec, nie za wariant. [AUT-R 19.08]

**Wycofanie pozycji.** Identyfikator zachowujemy ze względów analitycznych [AUT-R 19.08]; potwierdza
to standard identyfikacji, który zakazuje ponownego użycia i uzasadnia to danymi historycznymi
partnerów [LIT: GS1 GenSpecs R26.0, 4.2.5 i 4.16.1]. Zachowanie wobec sprzedaży i zamawiania
rozstrzyga tabela stanów w polu 8: wycofanie handlowe przechodzi przez stan wycofywana, w którym
zamawianie jest zablokowane, a sprzedaż resztek dozwolona. Pytania warsztatowe: A25, A26, B12.

**Powrót pozycji na rynek.** Pozycja wycofana i wprowadzona ponownie bez zmian wymuszających nowy
numer może użyć oryginalnego identyfikatora [LIT: jw., 4.2.5]. Wymaga to jednak, żeby stara kartoteka
nie została usunięta, tylko oznaczona.

**Kategorie z wymaganiami informacyjnymi.** Dla części kategorii dane produktowe wymagane prawem
(skład, ostrzeżenia, pochodzenie) warunkują zgodne z prawem **oferowanie** pozycji. Standard stawia
z tego **własne wymaganie projektowe**: ich brak ma blokować dopuszczenie, a nie tylko ostrzegać.
Karta **nie przesądza**, czy prawo wiąże już w momencie dopuszczenia, czy dopiero w momencie
sprzedaży; ta różnica jest zgłoszona w polu 12 jako GAP do regulatory-matrix [do weryfikacji]. Instancje kategorii i konkretne wymagania wchodzą warstwą
profilu i overlay w regulatory-matrix, nie rdzeniem (P15). [PROP+ 19.08]

**Wycofanie ze względów bezpieczeństwa.** To jest inny proces niż wycofanie handlowe i mylenie ich
jest kosztowne [PROP+ 19.08]. Różnice, wszystkie istotne dla systemu:

| | wycofanie handlowe | wycofanie bezpieczeństwa |
|---|---|---|
| kto inicjuje | organizacja, wg własnych kryteriów | producent albo organ nadzoru, z zewnątrz |
| tempo | rozłożone, z wyprzedażą resztek | **natychmiastowe** |
| zakres | zwykle wybrane lokalizacje albo kanały | **wszystkie naraz, bez wyjątków** |
| sprzedaż resztek | dozwolona i pożądana | **zabroniona, blokada twarda w kasie** |
| zależność od zapasu | wycofanie postępuje za zapasem | **niezależne od zapasu** |
| ślad | zwykły ślad zmiany danych | kto i kiedy zablokował, kto zwolnił blokadę |

Karta wymaga, żeby blokada bezpieczeństwa była **osobnym stanem**, a nie odmianą wycofania
handlowego, i żeby dało się ją wyegzekwować w kasie niezależnie od stanu zapasu i od blokady
zamawiania. Zakres wycofania bywa węższy niż pozycja (dotyczy konkretnych partii albo serii);
rozstrzygnięcie, na jakim poziomie granulacji działa blokada, należy do klienta i jest pytaniem
warsztatowym, nie założeniem karty. [PROP+ 19.08]

**Migracja kartoteki przy uruchomieniu systemu (cutover).** Karta ma za odbiorcę analityka
u detalisty wdrażającego nowy system, więc ładunek migracyjny jest normalnym wejściem procesu,
nie incydentem [PROP+ 19.08]. Do rozstrzygnięcia przed migracją, a nie po niej:
- pozycje bez identyfikatora zewnętrznego: co z nimi;
- **duplikaty do scalenia** i decyzja, która historia sprzedaży przechodzi na pozycję scaloną;
- kody wewnętrzne systemu poprzedniego wobec identyfikatorów docelowych;
- pozycje nieaktywne od lat: przenosimy czy odcinamy, i z jaką datą graniczną;
- pozycje wycofane, ale z zapasem w lokalizacjach;
- **data graniczna wiarygodności historii per identyfikator**, jeśli w danych zastanych występuje
  ponowne użycie identyfikatora sprzed 2019 (patrz flaga F4).

Kryterium odbioru migracji musi być ustalone **przed** startem i musi być liczbowe, nie opisowe:
udział pozycji z kompletem danych wymaganych do wyceny, liczba wykrytych duplikatów, liczba pozycji
bez identyfikatora. Bez tego migracja kończy się wtedy, gdy skończy się czas, a nie wtedy, gdy dane
są dobre. [PROP+ 19.08]

**12. Bezpieczniki prawne (R):** regulatory-matrix v1.0.1, legal_as_of 2026-08-14, overlay retail_core:

| ID | Norma | Pewność w RM | Rola w tej karcie |
|---|---|---|---|
| PRICE-001 | najniższa cena z 30 dni przed obniżką | verified | **relacja następstwa pozycji** jest tu warunkiem wejścia; bez niej pozycja zastępująca zeruje okno historii i nie da się ogłosić obniżki (flaga F5) |
| PRICE-002 | cena odniesienia dla towaru oferowanego krócej niż 30 dni | verified | **data pierwszego oferowania jest daną pozycji**, wytwarzaną tutaj, konsumowaną w CAT-02 |
| PRICE-003 | cena odniesienia towaru szybko psującego się | verified | **oznaczenie takiego towaru jest daną pozycji**, wytwarzaną tutaj, konsumowaną w CAT-02 |
| PRICE-004 | widoczna cena i wymagana cena jednostkowa | verified | **miara porównawcza do ceny jednostkowej jest daną pozycji**; bez niej CAT-02 nie policzy ceny jednostkowej |
| FISC-020 | stawka podatku z wersjonowanej klasyfikacji obowiązującej w chwili sprzedaży | qualified | **klasyfikacja podatkowa jest daną pozycji**; wersjonowanie w czasie jest wymogiem tej karty |
| RTL-CONS-001 | udostępnienie informacji o świadczeniu przed zatwierdzeniem sprzedaży w sklepie | qualified | dane opisowe pozycji zasilają obowiązek realizowany w SAL-01 |
| RTL-DIST-001 | informacje przed zawarciem umowy na odległość | qualified | dane opisowe pozycji zasilają obowiązek realizowany w kanale cyfrowym |
| RTL-DIST-004 | wyjątki od prawa odstąpienia | qualified | **kwalifikacja pozycji do wyjątku jest atrybutem pozycji**, rozstrzyganym tutaj, stosowanym w RTN |
| RTL-CONS-003 | ocena zgodności towaru z umową | verified | opis pozycji jest materialem dowodowym przy ocenie zgodności |

Uwaga: **cztery z dziewięciu** wiązań w tabeli powyżej mają w RM `confidence: qualified`, nie
`verified` (policzone z tabeli, nie przepisane). Karta używa ich jako
wiązań, nie jako pewników prawnych.

**Wniosek projektowy** [PROP+ 19.08]: dane opisowe pozycji nie są dodatkiem. Są materialem, na którym
opierają się trzy różne obowiązki: informacja przed sprzedażą, informacja przed umową na odległość
i ocena zgodności towaru z umową. Kartoteka pozycji jest tu **źródłem dowodu**, nie tylko źródłem
danych do wyszukiwania.

GAP-y do zgłoszenia maintainerowi regulatory-matrix (NIE asertować jako prawo):
- brak w RM wymagania dotyczącego **jednoznaczności identyfikacji pozycji** i zakazu reprezentowania
  wielu produktów jedną kartoteką, mimo że obowiązki informacyjne tego wymagają pośrednio
  [do potwierdzenia];
- brak wymagania o **kompletności danych produktowych jako warunku dopuszczenia do sprzedaży**;
  RM opisuje obowiązki w momencie sprzedaży, nie w momencie wprowadzenia pozycji [do potwierdzenia];
- brak pokrycia **odpowiedzialności za dane pochodzące od dostawcy** przy rozjeździe z danymi
  własnymi detalisty [do potwierdzenia].

Ograniczenia branżowe (kategorie z obowiązkowymi klasyfikacjami, dodatkowymi danymi produktowymi
albo reglamentacją) wchodzą warstwą profilu (P15) i overlay w RM, nie rdzeniem.

**13. Powiązanie w górę i artefakty:** value stream „Asortyment" (impuls -> decyzja -> tożsamość ->
dopuszczenie -> cykl życia), fundament pod value streamy „Cena" (CAT-02) i „Promocja" (CAT-03).
Crosswalk: standard/mapowania/crosswalk-frameworki.md.
Artefakt współdzielony **`standard/mapowania/modele-operacyjne.md` istnieje** (macierz obsady bramek
wg modelu operacyjnego; wchłonął oś wstępną tej karty i oś 1 z CAT-02) i ta karta z niego korzysta
zamiast powtarzać. Artefakty do zrobienia: glosariusz PL do EN.

KPI kandydujące (licznik i mianownik osobno, nie sam procent, P2) [PROP+ 19.08]:
- **kompletność danych**: pozycje dopuszczone do sprzedaży z kompletem danych wymaganych do wyceny,
  wobec pozycji dopuszczonych ogółem;
- **czystość kartoteki**: pozycje bez podejrzenia duplikatu, wobec pozycji aktywnych;
- **pokrycie następstwa**: pozycje wycofane z zapisaną relacją następstwa, wobec pozycji wycofanych
  ogółem;
- **czas od impulsu do sprzedawalności**, mediana i 95. percentyl, per model operacyjny;
- **udział pozycji rodzajowych** w asortymencie; miara dojrzałości danych, powinna dążyć do zera.

## 14. Bank pytań analityka

### A. Do biznesu (na warsztat)

**Blok wstępny: bez tego reszta warsztatu jest zgadywaniem**

A1. Jaki jest model relacji między siecią a lokalizacjami? *(Wyznacza kierunek decyzji
o asortymencie: w jednym modelu decyduje kierownik sklepu, w drugim centrala, i to są dwa różne
procesy obsadowo, nie jeden. **Nazwa, której klient używa u siebie, nie jest odpowiedzią.** To samo
słowo „franczyza" oznacza w dwóch sieciach dwa różne układy decyzyjne. Klasyfikuj **wynikiem testu
T1-T3** z `standard/mapowania/modele-operacyjne.md`, nie deklaracją; nazwy klas M0-M3 są tam
etykietami wyniku, nie pytaniem [PROP+ 20.08, naprawa po recenzji delty].)*

A2. Czy działa u Was zarządzanie kategorią, z planem kategorii i rolą menedżera kategorii? *(Bez tego
zarządzania cyklem życia pozycji praktycznie nie ma: produkt wypada, bo przestaje się sprzedawać.
Z tym pojawiają się bramki, których inaczej nikt nie stawia.)*

A3. Czy lokalizacja ma prawo założyć własną pozycję na potrzeby lokalne? Jeśli tak, czy wymaga to
zgody centrali? *(Rozstrzyga, czy kartoteka jest jedna dla całej sieci, czy istnieją równoległe
przestrzenie identyfikatorów, które kiedyś trzeba będzie pogodzić.)*

A4. Czy istnieje asortyment, który lokalizacja **musi** mieć, na przykład objęty akcją reklamową
sieci? *(To jedyny kierunek, w którym proces promocyjny narzuca coś procesowi asortymentowemu.
Jeśli obowiązek jest umowny, system musi go umieć wyegzekwować albo przynajmniej pokazać.)*

**Blok: skąd bierze się pozycja**

A5. Kto najczęściej inicjuje wprowadzenie nowej pozycji: przedstawiciel producenta, klient, personel,
centrala? *(Najczęstszym inicjatorem bywa przedstawiciel producenta, co znaczy, że wejście do procesu
jest poza organizacją i poza jej kontrolą.)*

A6. Czy zdarzają się oferty wiązane, w których warunkiem rabatu na produkt znany jest przyjęcie
nowości? *(To zmienia decyzję asortymentową w decyzję cenową i wprowadza do asortymentu pozycje,
których nikt nie oceniał na własnych kryteriach.)*

A7. Kto zatwierdza wprowadzenie pozycji i czy może odmówić? *(Odpowiedź wynika z A1, ale trzeba ją
potwierdzić wprost, bo modele mieszane są częste.)*

**Blok: dane pozycji**

A8. Jaki jest absolutny zestaw minimalny, bez którego pozycja nie może powstać? *(Typowo: nazwa,
producent, stawka podatku, kod kreskowy. Wszystko powyżej jest warstwą, wszystko poniżej jest awarią.)*

A9. Które pola blokują dopuszczenie do sprzedaży, a które tylko ostrzegają? *(Bez tego rozróżnienia
system albo blokuje wszystko i praca staje, albo nie blokuje nic i pozycje wchodzą z dziurami.)*

A10. Skąd biorą się dane opisowe: wpisuje je człowiek, przychodzą od dostawcy, czy z osobnego systemu
informacji produktowej? *(Determinuje, czy budujemy formularz, czy integrację, i kto odpowiada za
jakość.)*

A11. Gdy dane własne i dane od dostawcy się różnią, które wygrywają? *(Brak tej reguły oznacza, że
przy każdej aktualizacji od dostawcy ktoś traci swoje poprawki i nikt nie wie kiedy.)*

A12. Czy w Waszym asortymencie występuje oś wariantu, czyli rozmiar, kolor, wersja albo pojemność?
*(Asortyment wariantowy mnoży liczbę pozycji przez liczbę wariantów. Decyduje, czy potrzebny jest
poziom danych ponad pozycją, czy każdy wariant jest osobną pozycją.)*

A13. Czy prowadzicie kategorię sklepową, kategorię kategoryjną, czy obie? *(To dwie różne hierarchie
do dwóch różnych celów: układ sklepu kontra zarządzanie kategorią. Mylenie ich psuje raportowanie.)*

**Blok: tożsamość pozycji, najbardziej niedoceniany**

A14. Producent zmienia gramatykę opakowania z 500 g na 480 g. Zakładacie nową pozycję czy poprawiacie
istniejącą? *(Standard identyfikacji mówi jednoznacznie: każda zmiana deklarowanej zawartości netto
wymaga nowego identyfikatora, bez progu. Jeśli poprawiacie istniejącą, historia ceny i sprzedaży
łączy dwa różne produkty.)*

A15. A gdy zmienia się receptura albo producent, przy tej samej gramaturze? *(Tu standard daje test
dwuczłonowy i sporo swobody, więc odpowiedź musi być Wasza, nie standardu.)*

A16. Czy przy wycofaniu pozycji zwalniacie identyfikator do ponownego użycia? *(Ponowne użycie jest
dziś zakazane przez standard identyfikacji, ale w danych sprzed 2019 może występować jako zgodne
z ówczesnymi regułami. To znaczy, że historia pod jednym
identyfikatorem może obejmować dwa różne produkty.)*

A17. Czy zapisujecie, która pozycja zastąpiła którą? *(To jedyny most, po którym historia ceny
przechodzi na następcę. Bez niego każda zmiana opakowania zeruje okno ceny odniesienia.)*

A18. Czy zdarzają się u Was kartoteki reprezentujące kategorię zamiast konkretnego produktu, bez
producenta i bez kodu? *(Taka pozycja rozwala jednocześnie wycenę, historię ceny, analizę sprzedaży
i rozliczenie z dostawcą. Warto wiedzieć, ile ich jest, zanim ktoś obieca migrację jeden do jednego.)*

**Blok: dopuszczenie i zakres**

A19. Co dokładnie przełącza pozycję w stan sprzedawalna: automat w systemie, decyzja człowieka, czy
oba? *(Typowo oba, i to są dwa różne mechanizmy: automat pilnuje danych, człowiek pilnuje zasadności.
System z jednym członem zawodzi w przewidywalny sposób.)*

A20. Czy pozycja jest sprzedawalna wszędzie, czy per lokalizacja? *(Sprzedawalność jest właściwością
pary pozycja i zakres, nie samej pozycji. Jeśli klient myśli inaczej, model danych będzie za wąski.)*

A21. Czy macie asortyment wspólny plus nakładki regionalne? *(Dopytanie osobne: A42.)*

A22. Czy istnieją pozycje sprzedawane wyłącznie w jednym kanale? *(Kanał jest wtedy trzecim wymiarem
sprzedawalności, obok pozycji i lokalizacji.)*

**Blok: cykl życia**

A23. Jak pozycja przestaje być w ofercie: decyzją czy przez zanik sprzedaży? *(Bez zarządzania
kategorią zwykle przez zanik, co znaczy, że w systemie nie ma zdarzenia, tylko brak zdarzeń.)*

A24. Jakie są typowe przyczyny wypadnięcia pozycji z oferty? *(Zmiana kolekcji, koniec produkcji,
kanibalizacja przez inną pozycję. Każda z nich ma inny moment i inny skutek dla zapasu.)*

A25. Czy pozycja wycofana blokuje sprzedaż twardo, czy tylko zamawianie? *(Jeśli tylko zamawianie, to
resztki na półce dalej się sprzedają i trzeba wiedzieć, po jakiej cenie i przez jak długo.)*

A26. Co się dzieje z zapasem pozostałym w lokalizacjach po wycofaniu? *(Odpowiedź „wyprzedajemy"
oznacza, że wycofanie jest procesem rozłożonym w czasie, a nie zdarzeniem.)*

A27. Czy zdarza się, że pozycja wraca do oferty po wycofaniu? *(Powrót pod oryginalnym identyfikatorem
jest dopuszczalny, ale wymaga, żeby stara kartoteka nie została skasowana, tylko oznaczona.)*

A28. Kto sprząta duplikaty, gdy ta sama rzecz zostanie założona dwa razy, i po czym je rozpoznajecie?
*(Duplikat rozszczepia zapas, historię i marżę. Jeśli nikt nie sprząta, liczby w raportach są sumą
dwóch niezależnych ścieżek dla jednej rzeczy.)*

A29. Czy sprzedajecie towary niemarkowe, dostarczane przez różnych producentów jako to samo?
*(Standard identyfikacji jawnie przerzuca ten problem na detalistę: to samo z półki, różne
identyfikatory od różnych dostawców.)*

A30. Czy działacie na więcej niż jednym rynku krajowym? *(Ta sama rzecz fizyczna ma wtedy różne
zestawy danych i różne obowiązki informacyjne per rynek, a klucz danych rozszerza się o rynek
docelowy.)*

**Blok: stany, czas i sytuacje wyjątkowe**

A31. Wypiszmy razem stany, w jakich może być pozycja, i przy każdym rozstrzygnijmy dwie rzeczy: czy
wolno zamawiać i czy wolno sprzedawać. *(To jest jedyny sposób, żeby odpowiedzi na pytania o cykl
życia zeszły się w jedną całość. Bez tej tabeli każda odpowiedź jest osobną notatką.)*

A32. Czy są u Was kategorie, w których sprzedawalność jest bezterminowa z natury, na przykład usługi?
*(Okno bezterminowe jest poprawną wartością, nie brakiem danych; systemy zwykle wydzielają takie
kategorie osobno. Dopytanie osobne: A41.)*

A33. Kto może zablokować sprzedaż pozycji natychmiast, we wszystkich lokalizacjach naraz? *(To jest
inny mechanizm niż wycofanie handlowe: musi działać niezależnie od zapasu i od blokady zamawiania.
Jeśli nikt nie umie tego zrobić w minuty, macie lukę.)*

A34. Na jakim poziomie działa taka blokada: cała pozycja, czy konkretna partia albo seria?
*(Wycofanie bezpieczeństwa zwykle dotyczy części, nie całości. Blokada działająca tylko na całej
pozycji zatrzymuje sprzedaż towaru, który jest w porządku.)*

A35. Ile pozycji ma dziś kartoteka w obecnym systemie i ile z nich zamierzacie przenieść? *(Pierwsze
pytanie, które zada dział IT. Różnica między tymi liczbami to zakres projektu migracyjnego, o którym
nikt zwykle nie rozmawia na starcie.)*

A36. Jakie jest kryterium odbioru migracji kartoteki, wyrażone liczbą? *(Bez liczby migracja kończy
się wtedy, gdy skończy się czas, a nie wtedy, gdy dane są dobre.)*

A37. Czy w kartotece są byty, które nie są towarem: kaucja, opłata, karta podarunkowa, usługa?
*(Integrator kasy zapyta o to w pierwszej godzinie. Jeśli przechodzą tę samą bramkę dopuszczenia,
trzeba wiedzieć, które pola ich nie dotyczą.)*

A38. Czy sprzedajecie towar o zmiennej masie, ważony przy kasie albo w dziale? *(Kod z wbudowaną
wagą albo ceną rozbija jednocześnie skanowanie, cenę jednostkową i inwentaryzację, i wymaga innego
toru wyceny.)*

A39. Które dane produktowe są u Was wymagane prawem, a które są opisem handlowym, i kto to
rozstrzyga? *(Jeśli nikt nie rozdziela tych dwóch zbiorów, dane wymagane prawem są utrzymywane
z takim samym priorytetem co zdjęcie produktu, czyli żadnym.)*

A40. Czy w Waszej branży istnieje wspólna baza referencyjna danych produktowych, opisująca cały
rynek, i czy z niej korzystacie? *(Zmienia model zasilania kartoteki: pozycja nie jest zakładana od
zera, tylko zaciągana ze źródła, które zna produkt zanim Wy go zobaczycie. Wpływa na zakres
integracji, na regułę rozstrzygania konfliktu danych oraz na to, ile pracy zostaje po Waszej
stronie przy zakładaniu pozycji. Instancje branżowe zapisujemy w profilu, nie w rdzeniu standardu.)*
A41. Czy pozycja ma datę, od której wolno ją sprzedawać, i datę, do której? *(Dopytanie do A32,
osobny fakt: tam pytamy o istnienie kategorii bezterminowych, tu o zdolność systemu do prowadzenia
okna czasowego. Bez wymiaru czasu nie obsłużycie sezonowości ani planowanego uruchomienia kanału.
„Włączymy ręcznie" jest odpowiedzią, ale trzeba wiedzieć, że taka jest.)*

A42. Kto zarządza nakładkami regionalnymi? *(Dopytanie do A21. Nakładka bez właściciela to nakładka,
która nigdy nie jest aktualizowana.)*

### B. Do legacy (obserwowalne zachowanie obecnego systemu)

B1. Czy da się sprzedać rzecz, której nie ma w kartotece? *(Uznany model danych retailowych ARTS
przewiduje taką ścieżkę wprost, z podatkiem z wartości domyślnej działu. Jeśli u Was to działa, macie
kanał, którym towar wychodzi ze sklepu poza wszelką kontrolą danych.)*

B2. Jaką stawkę podatku dostaje taka sprzedaż? *(Wartość domyślna działu wychodzi dopiero przy
uzgodnieniu podatku na koniec okresu, kiedy nikt już nie pamięta, co to było.)*

B3. Które pola system twardo blokuje przy zakładaniu pozycji, a które przepuszcza puste? *(Weryfikacja
odpowiedzi z A9; to pytanie o konfigurację, nie o deklarację.)*

B4. Czy system wykrywa duplikat przy zakładaniu pozycji? Po czym: po kodzie, po nazwie, po zestawie
cech? *(Wykrywanie po samym kodzie nie łapie przypadku, w którym ta sama rzecz dostała dwa różne
kody.)*

B5. Ile macie dziś pozycji aktywnych, a ile z nich było sprzedanych w ostatnich dwunastu miesiącach?
*(Różnica to zwykle mieszanka pozycji martwych i duplikatów, i od razu pokazuje skalę pracy przy
migracji.)*

B6. Czy jedna pozycja może mieć w systemie więcej niż jeden kod kreskowy? *(To bywa poprawne, ale
tworzy drugi wektor duplikacji: dwa kody na jedną pozycję kontra dwie pozycje na jedną rzecz.)*

B7. Gdzie system trzyma jednostkę sprzedaży, a gdzie miarę wielkości opakowania? *(To dwie różne
role tej samej danej i pomylenie ich daje błędną cenę jednostkową.)*

B8. Jak wygląda przelicznik z opakowania zbiorczego na jednostkę sprzedaży i ile poziomów obsługuje?
*(Każdy dodatkowy poziom to kolejne miejsce, w którym można pomnożyć zamiast podzielić. Błąd wychodzi
przy pierwszym zamówieniu albo przy pierwszej inwentaryzacji.)*

B9. Czy zmiana klasyfikacji podatkowej pozycji jest wersjonowana w czasie, czy nadpisuje poprzednią?
*(Nadpisanie oznacza, że nie da się odtworzyć, jaką stawkę zastosowano do sprzedaży sprzed zmiany.)*

B10. Czy w danych historycznych zdarzało się ponowne użycie kodu dla innego produktu? *(Do 2019 było
to legalne. Jeśli występuje, trzeba ustalić datę graniczną wiarygodności historii per identyfikator,
zamiast zakładać ciągłość.)*

B11. Jak system rozpoznaje, że dostawca zmienił produkt bez zmiany kodu? *(Standard przewiduje na to
osobne oznaczenia wariantu, ale są opcjonalne. Jeśli ich nie czytacie, cicha podmiana zawartości jest
niewykrywalna.)*

B12. Czy pozycja wycofana daje się jeszcze zamówić? A sprzedać? *(To dwie osobne blokady i systemy
często mają tylko jedną.)*

B13. Ile różnych dat opisuje wycofanie: koniec produkcji, koniec zamawiania, zniknięcie z katalogu?
*(Standardy wymiany danych rozdzielają trzy niezależne zdarzenia w czasie. System mapujący je na jedną
flagę gwarantuje sobie rozjazd z dostawcą.)*

B14. Jak wygląda dziś import danych od dostawców: jaki kanał, jak często, co nadpisuje? *(Weryfikacja
A10 i A11 po stronie faktów.)*

B15. Czy istnieje ślad, kto i kiedy zmienił dane pozycji? *(Bez tego przy sporze o cenę albo o skład
nie da się ustalić, od kiedy dane wyglądają tak, jak wyglądają.)*

B16. Czy pozycja może być aktywna centralnie i nieaktywna w lokalizacji, albo odwrotnie? *(Pierwszy
kierunek daje głośną odmowę sprzedaży. Drugi daje sprzedaż bez pokrycia w danych centralnych, czyli
błąd cichy, ujawniający się dopiero w rozliczeniu.)*

B17. Ile pozycji wycofanych w ostatnim roku ma zapisanego następcę? *(Liczba, nie deklaracja.
Pokazuje, czy relacja następstwa jest praktyką, czy polem, które istnieje i stoi puste.)*

B18. Ile pozycji w kartotece ma komplet danych wymaganych do wyceny? *(To jest wyjściowy pomiar
przed migracją i jednocześnie kryterium jej odbioru.)*

B19. Czy pozycja ma w systemie datę początku i końca sprzedawalności, czy tylko flagę aktywna?
*(Sama flaga oznacza, że sezonowość i planowane uruchomienia obsługuje człowiek w kalendarzu.)*

B20. Jak dziś zatrzymalibyście sprzedaż jednej partii towaru we wszystkich sklepach w ciągu godziny?
*(Pytanie o zdolność, nie o funkcję. Odpowiedź „obdzwonilibyśmy sklepy" też jest odpowiedzią
i trzeba ją zapisać.)*

B21. Ile znaków ma nazwa pozycji na paragonie i czy różni się od nazwy pełnej? *(Kasa obcina nazwę
do kilkunastu znaków; klient nie rozpoznaje pozycji na paragonie i reklamuje zakup. Kosztuje tydzień
w UAT, a na warsztacie to pięć minut.)*

B22. Czy system w ogóle wie, które pola są wymagane prawem dla danej kategorii? *(Odpowiedź „nie"
oznacza, że kompletność regulacyjna jest pilnowana przez człowieka i przy pierwszej kontroli okaże
się, jak skutecznie.)*

### C. Do vendora

Przy każdym pytaniu wymagamy wskazania miejsca w dokumentacji i informacji, czy rzecz jest
konfigurowalna bez programisty.

C1. Czy system obsługuje oba kierunki decyzji asortymentowej: centrala narzuca lokalizacjom ORAZ
lokalizacja zgłasza do centrali z możliwością odmowy? *(Drugi kierunek bywa niewspierany natywnie,
a bez niego modele franczyzowe są nieobsługiwalne.)*

C2. Czy pozwala lokalizacji założyć własną pozycję i czy da się to ograniczyć uprawnieniem?
*(Weryfikuje A3.)*

C3. Czy sprzedawalność jest atrybutem pozycji, czy pary pozycja i zakres organizacyjny? *(Jeśli
atrybutem pozycji, to model jest za wąski dla sieci wielolokalizacyjnej i rozszerzenie go później
jest przebudową.)*

C4. Czy obsługuje asortyment wspólny z nakładkami regionalnymi i kanałowymi? *(Weryfikuje A21 i A22.)*

C5. Jak system radzi sobie z materializacją par pozycja i lokalizacja przy naszej skali? *(Pełny
iloczyn pozycji przez lokalizacje jest w praktyce nie do utrzymania, więc każdy system stosuje jakieś
ograniczenie, a każde ograniczenie tworzy strefę rozjazdu.)*

C6. Które pola system wymusza przed dopuszczeniem pozycji do sprzedaży i czy lista jest
konfigurowalna? *(Weryfikuje A9 i B3.)*

C7. Czy da się uzależnić wymagane pola od klasyfikacji produktu i od rynku? *(Obowiązek informacyjny
jest funkcją klasy produktu i jurysdykcji, nie stałej listy pól. System ze stałą listą albo blokuje
za dużo, albo za mało.)*

C8. Czy system pozwala sprzedać pozycję spoza kartoteki? Czy da się to wyłączyć? *(Weryfikuje B1;
odpowiedź „tak, i nie da się wyłączyć" to znaleziona luka kontrolna.)*

C9. Czy wykrywa duplikaty? Po jakich kryteriach? *(Weryfikuje B4. Żądaj demonstracji na próbce
danych klienta, nie deklaracji: żaden znany właścicielowi standardu system nie robi tego skutecznie,
więc odpowiedź „tak, obsługujemy" bez pokazu jest bezwartościowa.)*

C10. Czy obsługuje relację następstwa między pozycją wycofywaną a zastępującą, i czy przenosi po niej
historię? *(Weryfikuje A17; to jest most dla ciągłości ceny odniesienia.)*

C11. Czy blokuje ponowne użycie identyfikatora dla innej pozycji? *(Zakaz obowiązuje od 2019, ale
system może o tym nie wiedzieć.)*

C12. Czy potrafi przechwycić oznaczenie wariantu produktu przy niezmienionym identyfikatorze?
*(To jedyny standardowy detektor cichej podmiany zawartości.)*

C13. Czy klasyfikacja podatkowa jest wersjonowana w czasie? *(Weryfikuje B9.)* [R: FISC-020]

C14. Czy wycofanie pozycji jest jednym stanem, czy zestawem niezależnych dat? *(Weryfikuje B13;
jedna flaga oznacza gwarantowany rozjazd z katalogiem dostawcy.)*

C15. Czy pozwala odróżnić blokadę zamawiania od blokady sprzedaży? *(Weryfikuje B12.)*

C16. Czy obsługuje powrót pozycji do oferty pod oryginalnym identyfikatorem? *(Wymaga, żeby stara
kartoteka była oznaczana, a nie kasowana.)*

C17. Ile poziomów opakowań i przeliczników obsługuje, i gdzie leży logika konwersji? *(Modele danych
dostarczają strukturę i wprost zrzekają się odpowiedzialności za poprawność konwersji, więc leży ona
po stronie systemu.)*

C18. Czy rozróżnia jednostkę do liczenia sztuk od miary wielkości opakowania od miary do planowania
półki? *(To trzy różne role i systemy potrafią je zlewać.)*

C19. Czy obsługuje rynek docelowy jako wymiar danych pozycji? *(Weryfikuje A30; bez tego wielorynkowość
robi się przez duplikowanie pozycji.)*

C20. Jak integruje się ze źródłami zewnętrznymi danych produktowych i jaka jest reguła rozstrzygania
konfliktu? *(Weryfikuje A11.)*

C21. Czy prowadzi ślad zmian danych pozycji z identyfikacją osoby? *(Weryfikuje B15.)*

C22. Czy przewiduje bramki cyklu życia pozycji, czy tylko stan aktywna i nieaktywna? *(Bramki mają
sens tylko przy zarządzaniu kategorią, ale ich brak zamyka drogę do niego na przyszłość.)*

C23. Czy stan pozycji jest osobnym obiektem z rozstrzygnięciem dla zamawiania i dla sprzedaży
osobno? *(Jedna flaga aktywna kontra nieaktywna nie obsłuży ani wyprzedaży resztek, ani blokady
bezpieczeństwa.)*

C24. Czy sprzedawalność ma wymiar czasowy: datę od i datę do? *(Weryfikuje A32 i B19.)*

C25. Czy system ma funkcję natychmiastowej blokady sprzedaży, działającą niezależnie od zapasu
i od blokady zamawiania, i na jakim poziomie granulacji? *(Weryfikuje A33 i A34; to jest jedyne
pytanie z tej karty, w którym odpowiedź „nie" jest dyskwalifikująca.)*

C26. Jakie narzędzia migracyjne dostajemy: import, wykrywanie duplikatów, scalanie pozycji
z przeniesieniem historii, raport kompletności? *(Weryfikuje wykonalność A35 i A36.)*

C27. Czy obsługuje byty niebędące towarem: opłatę, kaucję, kartę podarunkową, usługę? Czy przechodzą
tę samą bramkę dopuszczenia? *(Weryfikuje A37.)*

C28. Czy obsługuje towar o zmiennej masie i kod z wbudowaną wagą albo ceną? *(Weryfikuje A38.)*

C29. Czy pozwala odróżnić nazwę na paragonie od nazwy pełnej i od nazwy w kanale cyfrowym?
*(Weryfikuje B21.)*

C30. Czy system potrafi zasilać kartotekę z branżowej bazy referencyjnej, jeśli taka w branży
istnieje, i jak rozstrzyga konflikt między danymi z tej bazy a danymi własnymi detalisty?
*(Weryfikuje A40. Bez tego integracja z bazą branżową jest projektem po stronie klienta,
a nie funkcją produktu.)* [PROP+ 19.08]
### Czerwone flagi (wychodzą typowo dopiero w UAT lub po starcie)

Każda flaga ma przypisane pytanie, którym się ją wykrywa.

F1. **Sprzedaż pozycji spoza kartoteki.** Uznany model danych **jawnie przewiduje** ścieżkę sprzedaży
rzeczy, której w kartotece nie ma, z podatkiem z wartości domyślnej działu. To nie jest luka
implementacji, to jest przewidziana funkcja. Skutek: towar wychodzi ze sklepu poza kontrolą danych,
a rozjazd wychodzi dopiero przy uzgodnieniu podatku na koniec okresu. Pytania: B1, B2, C8.
[LIT: ARTS ODM 7.3, Logical 01020 i 02310, encja `POSDepartment` z domyślną grupą podatkową]

F2. **Zmiana gramatury zrobiona jako edycja pozycji.** Standard identyfikacji nie zna tu progu: każda
zmiana deklarowanej zawartości netto wymaga nowego identyfikatora. Poprawienie istniejącej kartoteki
zlepia dwa różne produkty w jeden szereg czasowy ceny i sprzedaży. Wychodzi w analizie, nigdy w UAT.
Pytania: A14, A17, C10. [LIT: GS1 GTIN Management Standard 1.1, reguła 2.3]

F3. **Cicha podmiana zawartości.** Zmiana receptury, jakości surowca albo kraju produkcji nie musi
wymuszać nowego identyfikatora, jeśli nie dotyka informacji wymaganej prawem na opakowaniu. Standard
przewiduje na to oznaczenia wariantu, ale są opcjonalne. Detalista, który ich nie czyta, sprzedaje
inny produkt pod tym samym numerem i nie ma o tym wiedzy. Pytania: A15, B11, C12.
[LIT: GS1 GTIN Management Standard 1.1, reguła 2.2 jako koniunkcja; GenSpecs R26.0, 4.2.2.3]

F4. **Historia pod jednym identyfikatorem obejmuje dwa różne produkty.** Ponowne użycie identyfikatora
było dopuszczalne wg standardu do końca 2018 roku, z karencją 48 miesięcy, a w niektórych sektorach
krótszą. Dane zastane mogą to zawierać. Sprzedaż działa poprawnie, więc nic tego nie sygnalizuje; wychodzi w analityce
i przy reklamacji po latach. Pytania: A16, B10, C11. [LIT: GS1 GenSpecs R26.0, 4.2.5 i 4.16.1]

F5. **Brak relacji następstwa.** Pozycja zastępująca zaczyna historię od zera. Przy zmianie opakowania
oznacza to utratę okna ceny odniesienia, a przy odpowiednio częstych zmianach opakowań stałą
niemożność ogłoszenia obniżki. Pytania: A17, B17, C10. [PROP+ 19.08; R: PRICE-001]

F6. **Duplikat pozycji.** Ta sama rzecz założona dwa razy pod różnymi identyfikatorami. Rozszczepia
jednocześnie zapas, historię sprzedaży, historię ceny i marżę, bo koszty siedzą na obu kartotekach
niezależnie. Model danych tego nie blokuje, a dla towarów niemarkowych wprost przerzuca problem na
detalistę. Wychodzi przy inwentaryzacji i przy analizie kategorii, w UAT praktycznie nigdy.
Pytania: A28, A29, B4, B5, C9. [LIT: ARTS ODM 7.3, Logical 01500, `ItemSupplierItem`; GS1 GenSpecs
4.2.3.2]

F7. **Pozycja rodzajowa.** Kartoteka reprezentująca kategorię zamiast konkretnego produktu, bez
producenta i bez kodu. Rozwala wycenę, historię, analizę i rozliczenie naraz. Ujawnia się przy
pierwszej próbie migracji jeden do jednego albo przy pierwszym rozliczeniu z dostawcą.
Pytania: A18. [AUT-R 19.08]

F8. **Sprzedawalność zamodelowana jako atrybut pozycji.** Model jest wtedy za wąski dla sieci
wielolokalizacyjnej, a rozszerzenie go po starcie jest przebudową, nie konfiguracją. Pytania: A20,
C3. [LIT: ARTS ODM 7.3, Logical 01020: wartości domyślne przedsiębiorstwa na `Item`, nadpisania na
`BusinessUnitGroupItem`]

F9. **Sprzedawalna w lokalizacji, nieaktywna centralnie.** Kierunek odwrotny do intuicyjnego i dlatego
groźniejszy: sprzedaż działa, więc nikt nie zgłasza, a rozjazd ujawnia się dopiero w rozliczeniu.
Kierunek intuicyjny (aktywna centralnie, brak w lokalizacji) daje głośną odmowę sprzedaży i naprawia
się sam. Pytania: A20, B16, C3. [HIP na asymetrii; architektura P-wysoka]

F10. **Wycofanie zamodelowane jako jedna flaga.** Standardy wymiany danych rozdzielają trzy niezależne
zdarzenia w czasie: koniec produkcji, koniec zamawiania, zniknięcie z katalogu. System z jedną flagą
gwarantuje sobie rozjazd z katalogiem dostawcy, a przy wznowieniu produkcji po ustawieniu daty
wycofania nie ma czym tego obsłużyć. Pytania: A25, B13, C14.
[LIT: GS1 Trade Item Implementation Guide, sekcja wycofania pozycji]

F11. **Pozycja wycofana, która nadal się sprzedaje.** Blokada zamawiania i blokada sprzedaży to dwie
różne rzeczy, a systemy często mają tylko jedną. Resztki schodzą z półki po nieokreślonej cenie.
Pytania: A25, A26, B12, C15. [PROP+ 19.08]

F12. **Skasowana kartoteka pozycji, która wraca do oferty.** Powrót pod oryginalnym identyfikatorem
jest dopuszczalny, ale wymaga, żeby stara kartoteka była oznaczona, a nie usunięta. Skasowanie
zamyka tę drogę i wymusza nowy numer, czyli nową historię. Pytania: A27, C16.
[LIT: GS1 GenSpecs R26.0, 4.2.5]

F13. **Błędny przelicznik opakowania zbiorczego.** Wychodzi przy pierwszym zamówieniu, jako zamówienie
na złą krotność, albo przy pierwszej inwentaryzacji, jako rozjazd zapasu proporcjonalny do
przelicznika. Nie wychodzi w UAT, jeśli UAT nie obejmuje pełnego cyklu od zamówienia po
inwentaryzację. Pytania: B8, C17. [LIT: ARTS ODM 7.3, Logical 01500 i 01501; model dostarcza
strukturę i wprost zrzeka się odpowiedzialności za poprawność konwersji]

F14. **Zlanie trzech ról jednostki miary.** Jednostka do liczenia sztuk, miara wielkości opakowania
i miara do planowania półki to trzy różne rzeczy niesione przez ten sam typ danych. Pomylenie ich
daje błędną cenę jednostkową albo błędny plan półki. Pytania: B7, C18.
[LIT: ARTS ODM 7.3, Logical 01501]

F15. **Rozjazd danych własnych i dostawcy.** Bez jawnej reguły rozstrzygania konfliktu każda
aktualizacja od dostawcy kasuje czyjeś poprawki, a nikt nie wie kiedy ani które. Pytania: A11, B14,
C20. [PROP+ 19.08]

F16. **Kompletność danych jako stała lista pól.** Obowiązek informacyjny jest funkcją klasy produktu
i rynku docelowego, nie stałej listy. System ze stałą listą blokuje za dużo w jednych kategoriach
i za mało w innych. Pytania: A30, B22, C7, C19. [HIP; oparte na fakcie, że standardy wymiany danych sterują
zestawem atrybutów przez kontekst produktowy i rynek docelowy]

F17. **Klasyfikacja podatkowa nadpisana zamiast wersjonowanej.** Po zmianie stawki nie da się
odtworzyć, jaką zastosowano do sprzedaży sprzed zmiany. To jest jednocześnie problem CAT-01 (dana)
i CAT-02 (zdarzenie cenowe). Pytania: B9, C13. [R: FISC-020]

F18. **Dane wymagane prawem traktowane jako opis marketingowy.** Skład, ostrzeżenia i pochodzenie są
materialem, na którym opierają się obowiązki informacyjne i ocena zgodności towaru z umową.
**Wymaganie ORPR:** brak tych danych ma blokować dopuszczenie pozycji do sprzedaży, a nie tylko
ostrzegać. **Karta nie przesądza, że jest to obowiązek prawny w momencie wprowadzenia pozycji**:
wiązania `[R:]` poniżej dotyczą obowiązków w momencie sprzedaży, a rozciągnięcie ich na moment
dopuszczenia jest rozstrzygnięciem tego standardu, zgłoszonym w polu 12 jako GAP do RM
[do weryfikacji]. Wychodzi przy kontroli, z sankcją, albo nie wychodzi wcale.
Pytania: A9, A39, B22, C7. [R: RTL-CONS-001, RTL-DIST-001, RTL-CONS-003]

F19. **Zakres regulacyjny danych pozycji, który rośnie.** Wymagania dotyczące identyfikacji i danych
produktowych są rozszerzane aktami wykonawczymi per grupa produktowa. Karta traktuje to
architektonicznie: kartoteka musi umieć przyjąć nowe zestawy atrybutów sterowane klasyfikacją, a nie
mieć je wpisane na stałe. Kierunek i tempo rozszerzania wymagań: [do potwierdzenia], brak wiązania
w regulatory-matrix, zgłoszone jako GAP. Pytania: A39, C7. [PROP+ 19.08]

F20. **Wejście do procesu jest poza organizacją.** Najczęstszym inicjatorem bywa przedstawiciel
producenta, często z ofertą wiązaną. Oznacza to, że o kształcie asortymentu współdecyduje strona,
która nie ma interesu w jego spójności. Bez własnych kryteriów oceny nowej pozycji organizacja
przyjmuje cudze. Pytania: A5, A6, A7. [AUT-R 19.08]

F21. **Brak modelu stanów pozycji.** System zna tylko aktywna i nieaktywna, więc nie obsłuży ani
wyprzedaży resztek po wycofaniu, ani natychmiastowej blokady bezpieczeństwa, ani sezonowości.
Wychodzi przy pierwszym wycofaniu z zapasem na półce. Pytania: A31, B19, C23. [PROP+ 19.08]

F22. **Brak zdolności do prowadzenia okna czasowego sprzedawalności.** Sezonowość i planowane
uruchomienia obsługuje wtedy człowiek w kalendarzu, więc pozycja wchodzi do sprzedaży wtedy, gdy
ktoś sobie przypomni. **Kalibracja właściciela: wymiar czasu nie dotyczy wszystkich pozycji**
[AUT-R 19.08, tura 2]. Są kategorie sprzedawalne bezterminowo z natury, na przykład usługa,
i systemy zwykle wydzielają je osobną kategorią. Defektem jest więc brak **zdolności** systemu do
prowadzenia okna tam, gdzie jest potrzebne, a nie brak daty przy każdej pozycji. Analityk, który
zażąda daty od i do dla wszystkiego, dostanie sztuczne daty wpisane byle jak.
Pytania: A32, B19, C24. Sformułowanie flagi: [PROP+ 19.08]

F23. **Brak zdolności natychmiastowej blokady sprzedaży.** Wycofanie ze względów bezpieczeństwa
wymaga zatrzymania sprzedaży we wszystkich lokalizacjach naraz, niezależnie od zapasu i od blokady
zamawiania. Jeśli jedyną metodą jest obdzwonienie sklepów, to nie jest funkcja systemu, tylko
procedura ratunkowa. Pytania: A33, A34, B20, C25. [PROP+ 19.08]

F24. **Migracja bez kryterium odbioru.** Kartoteka przechodzi do nowego systemu razem z duplikatami,
pozycjami bez identyfikatora i niewiarygodną historią, bo nikt nie ustalił liczby, przy której
migracja jest zaliczona. Wychodzi po starcie, gdy pierwszy raport nie zgadza się z niczym.
Pytania: A35, A36, B18, C26. [PROP+ 19.08]

F25. **Nazwa pozycji obcięta na paragonie.** Klient nie rozpoznaje zakupu i reklamuje go. Kosztuje
tydzień w UAT, a rozstrzyga się w pięć minut na warsztacie. Pytania: B21, C29. [PROP+ 19.08]

F26. **Byty niebędące towarem w tej samej kartotece.** Opłata, kaucja, karta podarunkowa i usługa
przechodzą tę samą bramkę dopuszczenia co towar, więc albo blokuje je brak pól, które ich nie
dotyczą, albo przepuszcza brak pól, które ich dotyczą. Pytania: A37, C27. [PROP+ 19.08]
