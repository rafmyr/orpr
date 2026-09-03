# [ORPR-CAT-02] Price-to-POS
Podtytuł roboczy (PL): od ustalenia ceny regularnej do jej obowiązywania w kasach, kanałach i na nośniku ceny, aż do zastąpienia albo wygaśnięcia.

| | |
|---|---|
| ID | ORPR-CAT-02 (wg standard/mapa-procesow.md; freeze notacji: obowiązuje od v0.1.0) |
| Wersja karty | 1.0 |
| Status | **released** (20.08.2026, decyzja właściciela). Bramka domknięta: 0 otwartych `[PROP]`, `[AUT-R]` podpisane w sześciu turach dyktanda, niezależna recenzja wydaniowa wykonana **modelem FABLE, innym niż główny autor** (zasady governance projektu), werdykt **WYDAĆ**. Zapis recenzji: wewnętrzny materiał roboczy. `released` jest stanem wewnętrznym repo, nie publikacją publiczną (patrz `standard/SZABLON-KARTY.md`) |
| Zmiany w 0.7 (19.08.2026) | naprawa po recenzji wydaniowej: cofnięta regresja statusu (P19); bank policzony na 108 pytań zamiast deklarowanych 100; **trzeci dopuszczalny stan nośnika** (cena przyszła z jawną datą obowiązywania) i uspójniona z nim tabela stanów; wycofane twierdzenie o legalności sprzedaży w dwóch cenach naraz; pole 7 deklaruje przelicznik do opakowania zbiorczego i moment zaokrąglenia netto-brutto, które konsumuje pole 9; sekcja ARTS w crosswalku uspójniona z kartą |
| Zmiany w 0.8 (19.08.2026) | naprawa po recenzji wydaniowej FABLE: **tabela stanów uspójniona z polem 9 w sprawie nośnika zaległego** (rejestr plus zegar; poprzednia naprawa uspójniła tylko cenę przyszłą z datą); wiersz „wysłana" dostał ten sam warunek jawnej daty co wiersz „odebrana"; **pole 7 deklaruje minimalne wyprzedzenie i maksymalny czas nadrobienia**, konsumowane przez pole 9 oraz flagi F13 i F27; bank policzony na **108 pytań**, zgodnie z deklaracją v0.7 |
| Zmiany w 1.0 (20.08.2026) | wydanie. Zmian merytorycznych brak wobec v0.8; recenzja delty FABLE nie zgłosiła do tej karty żadnego blokera ani zarzutu ważnego poza dwoma odłożonymi do `rejestr tematów odłożonych` (tag zbiorczy nad sekcją osi 2, interpunkcja listy w polu 7) |
| Klasa treści | rdzeń retail-neutralny; warstwa branżowa w profile/ (P15) |
| Bezpieczniki R | regulatory-matrix v1.0.1, legal_as_of 2026-08-14 (patrz pole 12) |
| Crosswalk | standard/mapowania/crosswalk-frameworki.md (APQC / ARTS-NRF / GS1) |
| Clean-room | 2026-08-19: wiedza dziedzinowa, źródła publiczne i prawo powszechne; zero materiałów klientów i pracodawców |

### Klasy twierdzeń (obowiązują od v0.3)

| Tag | Znaczenie | Co z tym robi właściciel |
|---|---|---|
| `[AUT-R]` | ekspertyza właściciela, z datą dyktanda | podpisuje albo koryguje |
| `[PROP]` | propozycja redakcyjna z researchu albo recenzji, NIE wypowiedź właściciela | **przyjmuje albo odrzuca; to jedyne linie wymagające jego przejścia** |
| `[PROP+ data]` | propozycja **przyjęta** przez właściciela; pochodzenie redakcyjne zachowane, status rozstrzygnięty | nic, sprawa zamknięta |
| `[LIT: ...]` | źródło publiczne z lokatorem | weryfikuje recenzent, nie właściciel |
| `[R: <ID>]` | wiązanie z regulatory-matrix | struktura, nie opinia prawna |
| `[HIP]` | hipoteza z mechanizmu, bez badania potwierdzającego | nie asertujemy |
| `[do potwierdzenia]` | kandydat do weryfikacji u źródła | nie asertujemy |

Dyktanda właściciela w tej karcie: **19.08.2026 tura 1** (sześć osi), **19.08.2026 tura 2**
(weryfikacja punktowa), **19.08.2026 tury 3 i 4** (arkusz decyzyjny, 21 pozycji) oraz
**19.08.2026 tura 5** (rozstrzygnięcie o skutku zmiany ceny na wycenie zapasu, po recenzji v0.4)
oraz **19.08.2026 tura 6** (nośnik zaległy z limitem czasu; cena porcji jako funkcja ceny opakowania). Rozdzielenie dawnego, wspólnego tagu autorskiego na `[AUT-R]` i `[PROP]` wprowadzone po
stwierdzeniu, że w v0.2 jeden tag obejmował 55 twierdzeń, z czego wypowiedzią właściciela była
mniejszość (55 policzone niezależnie 19.08.2026 na commicie b1119fd).

## Terminologia

**Cena regularna** to cena detaliczna obowiązująca poza promocją. Termin główny standardu; funkcjonuje
w obrocie i w kontekście prawnym obniżek [LIT: słowniki branżowe i publicystyka prawna dot. obowiązku
podawania ceny poprzedniej]. Synonimy praktyczne, dopuszczalne na warsztacie, nie w standardzie:
**„cena 100 %"** [AUT-R 19.08]. Termin **„cena bazowa"** został z tej karty **wycofany**: był
zdefiniowany, a potem nieużyty ani razu, więc definiował pojęcie, którego w karcie nie ma
[PROP+ 19.08, recenzja v0.4].

**Matryca marżowa**: mechanizm wyliczania ceny przez doliczenie marży do ceny zakupu. Synonim
praktyczny: **„marżownik"** [AUT-R 19.08]. Standard używa „matrycy marżowej", bo popularności „marżownika"
nie potwierdzono w źródłach publicznych w żadną stronę [do potwierdzenia].

## Miejsce karty w domenie CAT

| Zagadnienie | Właściciel |
|---|---|
| cennik wielopoziomowy, matryca marżowa, kierunek przepływu ceny | **CAT-02** |
| historia ceny regularnej; wyliczenie ceny odniesienia | **CAT-02** |
| cena jednostkowa: wyliczenie i uwidocznienie | **CAT-02** |
| nośnik ceny (metka, etykieta półkowa, ekspozycja w kanale) i jego zgodność z kasą | **CAT-02** |
| trwałe obniżenie ceny regularnej | **CAT-02** |
| skutek zmiany ceny na wycenie zapasu (rewaluacja) | **zależny od modelu wyceny zapasu**, nie od tej karty; rozstrzygnięcie i wyjście w polu 10 |
| **korekta faktury zakupowej po przyjęciu towaru** | **ORPR-PRC / FIN, NIE ta karta** (patrz niżej) |
| miary opakowania, klasyfikacja podatkowa, perishability jako DANE pozycji | ORPR-CAT-01 |
| reguła promocyjna, modyfikator, kwalifikacja, markdown time-decay, sprzedaż ze stratą jako wabik | ORPR-CAT-03 |
| naliczenie ceny w koszyku, moment zamrożenia ceny w transakcji, rabat na pojedynczej transakcji | ORPR-SAL-01 |
| wycena zwrotu towaru | ORPR-RTN-*, reguła i dane z CAT-02 |

**Rozstrzygnięcie: „przecena".** Test: **czy po zakończeniu cena wraca do poprzedniej?**
Wraca to CAT-03 (mechanika czasowa). Nie wraca to CAT-02 (trwałe obniżenie ceny regularnej).

**Rozstrzygnięcie: sprzedaż poniżej kosztu.** W CAT-02 obniżenie poniżej kosztu jest dopuszczalne
**wyłącznie dla towaru niepełnowartościowego, oznaczonego znakiem w systemie**, i wymaga wyższego
poziomu uprawnień niż zwykła zmiana ceny [AUT-R 19.08]. Sprzedaż ze stratą jako świadoma taktyka
handlowa (wabik) nie jest zmianą ceny regularnej, tylko mechaniką promocyjną, więc należy do CAT-03
[PROP+ 19.08, przyjęte przez właściciela 19.08].

**Rozstrzygnięcie: korekta faktury.** Cena zakupu wchodzi do wyceny **wyłącznie raz, w momencie
przyjęcia towaru na stan**. Późniejsze korekty faktury nie przeliczają ceny półkowej i nie są
zdarzeniem cenowym [AUT-R 19.08]. Wychodzą z tej karty do domeny zakupów i finansów.

**Zakres potwierdzenia w źródłach, świadomie zawężony po recenzji v0.4** [PROP+ 19.08, recenzja v0.4].
Model danych ARTS rozdziela **Item Price Maintenance** od **Item Rewards Derivation** (cena wyliczana
regułą w transakcji); narracja 01300: „the starting price is taken from the ItemSellingPrices entity"
[LIT: ARTS Retail ODM 7.3, Logical Narrative, widoki 01300 i 01400]. To potwierdza granicę
**CAT-02 wobec SAL-01** (utrzymanie ceny kontra derywacja w transakcji) i **nic więcej**.

Granicy CAT-02 wobec CAT-03 ARTS **nie potwierdza**, a nawet stoi z nią w napięciu: widok 01300
obejmuje zmiany „permanentne albo czasowe", czyli wkłada markdown czasowy tam, gdzie ta karta go
nie chce (standard/mapowania/crosswalk-frameworki.md, sekcja ARTS). Granica CAT-02 wobec CAT-03
opiera się **wyłącznie** na teście „czy cena wraca", który jest rozstrzygnięciem tego standardu,
a nie cytatem ze źródła. Poprzednie brzmienie stawiało ARTS jako „potwierdzenie modelowe" pod
wszystkimi trzema rozstrzygnięciami naraz i było nadinterpretacją.

## Model pojęciowy

### Oś 1: model relacji sieć-lokalizacja wyznacza KIERUNEK przepływu ceny

To jest pierwsza zmienna, którą analityk musi ustalić. Bez niej cała reszta modelu jest zgadywana,
bo kierunek przepływu odwraca się między modelami [AUT-R 19.08]:

| Model relacji | Kto tworzy cennik | Rola drugiej strony |
|---|---|---|
| sieć własna, franczyza twarda | centrala | kierownik lokalizacji: co najwyżej korekta lokalna |
| franczyza miękka, sieć partnerska luźna | kierownik lokalizacji | centrala: **nakładka na wybrane pozycje** (np. objęte akcją reklamową) |

Lokalizacja **może, ale nie musi** mieć cennik lokalny; to nie jest przełącznik funkcjonalny, tylko
konsekwencja modelu własnościowego [AUT-R 19.08]. Spektrum jest ciągłe (od sieci własnej przez franczyzę
twardą i miękką po sieć partnerską), a nie dwupunktowe.
**Macierz obsady bramek dla wszystkich modeli: `standard/mapowania/modele-operacyjne.md`.**
Tam stoi test klasyfikacyjny (trzy pytania), pełna macierz bramka razy model dla trzech kart domeny
CAT oraz rejestr odcinków warunkowych. Ta karta nie powtarza macierzy [PROP+ 19.08, redakcja].


Konsekwencje projektowe [PROP+ 19.08]: w modelu odwróconym „cennik centralny" nie jest cennikiem, tylko
**listą pozycji z narzuconą ceną**, nakładaną na cennik lokalny. Reguła rozstrzygania konfliktu jest
wtedy inna niż w modelu centralnym: centrala wygrywa tylko na swojej liście, poza nią nie ma zdania.

### Oś 2: dwa reżimy wyznaczania ceny, nie dwa zapisy tej samej rzeczy

[AUT-R 19.08, obie tury]

| Reżim | Skąd cena | Kiedy się zmienia |
|---|---|---|
| **matryca marżowa** | marża doliczona do ceny zakupu; poziom marży zależny od ceny, kategorii, producenta | **przy dostawie** |
| **cennik dedykowany** | cena wpisana wprost; metod ustalenia wiele (badanie rynku, uzgodnienia z producentem, strategia kategorii) | **nie przelicza się wcale**, stoi do czasu decyzji człowieka |

Oba reżimy występują równolegle, per kategoria [AUT-R 19.08]. Wniosek redakcyjny [PROP+ 19.08]:
to rozróżnienie decyduje o zakresie wdrożenia, bo pierwszy reżim wymaga, by system cenę **liczył**,
a drugi tylko by ją **przechowywał**.

**Koszt jest zamrażany w momencie przyjęcia towaru na stan.** Analiza ceny zakupu następuje raz,
przy przyjęciu. Późniejsza korekta faktury nie uruchamia przeliczenia [AUT-R 19.08]. Skutek uboczny
do świadomości: po korekcie faktury koszt użyty do wyceny i koszt rzeczywisty rozjeżdżają się na
stałe, a marża raportowana jest liczona od kosztu zamrożonego [PROP+ 19.08].

Korzyści pozafakturowe zwykle **nie schodzą na cenę półkową**, tylko podnoszą marżę sieci albo
lokalizacji [AUT-R 19.08]. Praktyka ograniczania dostępu personelu lokalizacji do pełnych warunków
handlowych jest realna; wymaganie systemowe brzmi: **model uprawnień musi umieć pokazać cenę zakupu
bez pokazywania warunków handlowych** [AUT-R 19.08, tura 1].

### Oś 3: partia jako część klucza ceny

Najważniejsza zmiana wobec v0.2. Karta NIE może zakładać, że pozycja ma w danym momencie jedną cenę.

| Model wyceny | Klucz ceny | Co widzi klient |
|---|---|---|
| jedna cena na pozycję | pozycja + zakres + kanał | jedna cena na półce |
| **cena per partia** | pozycja + **partia** + zakres + kanał | **ten sam produkt na półce w różnych cenach jednocześnie** |

W modelu partiowym towar jest **metkowany razem z ceną** przy przyjęciu, więc cena jest przypisana do
egzemplarza, nie do miejsca na półce [AUT-R 19.08]. Praca na partiach występuje tam, gdzie towar jest
identyfikowalny co do dostawy; wybór modelu jest polityką, nie techniką [AUT-R 19.08].

**Konsekwencja krytyczna** [PROP+ 19.08]: w modelu partiowym rozjazd między ceną na metce a ceną w kasie jest
**wbudowany, nie przypadkowy**, ponieważ kasa skanuje identyfikator pozycji, a nie partii. Czym system
rozstrzyga, którą cenę naliczyć, jest pytaniem otwartym i warunkiem spełnienia [R: PRICE-005]
(pytania B9, C13).

### Metody uspójnienia ceny przy dostawie (reżim jednocenowy)

Gdy nowa dostawa ma wyrównać cenę wszystkich sztuk na półce, sposób wyliczenia jest polityką sieci
i możliwością systemu. Spotykane [AUT-R 19.08]:
- uzgodniony poziom marży liczony od **uśrednionej** ceny zakupu;
- cena wyznaczana od **ostatniej** ceny zakupu;
- **second-best**: z ostatnich pięciu cen zakupu odrzucamy najwyższą, druga w kolejności jest
  podstawą wyliczenia;
- inne mechanizmy, zależne od systemu.

Systemy różnią się właśnie tutaj, więc jest to pytanie do vendora (C6), nie założenie karty.

### Oś 4: cennik wielopoziomowy i kanał

**Poziomy cennika** [AUT-R, potwierdzone 19.08 tura 2]: równolegle istnieje wiele cenników (sieć,
region, typ sklepu, lokalizacja, producent, kategoria). Poziom oznacza **odrębny cennik, który wygrywa
z cennikiem niższego poziomu**, a nie regułę filtrującą wewnątrz jednego cennika. Wniosek redakcyjny
[PROP+ 19.08]: model danych musi więc obsłużyć hierarchię cenników z deterministycznym
rozstrzyganiem, a nie zestaw warunków.

**Kanał** [AUT-R 19.08]: stanem domyślnym przy omnichannelu są **te same ceny i promocje we wszystkich
kanałach**; różnicowanie jest nadbudową, którą sieć włącza świadomie. Możliwe są promocje dedykowane
kanałowi. W modelu z odbiorem w lokalizacji **kanał zamówienia determinuje cenę** także dla wydania
w kanale tradycyjnym.

**Zakres organizacyjny** [PROP+ 19.08, rekomendacja modelowa, nie opis stanu]: standard rekomenduje wiązanie
ceny i nośnika ceny z grupą jednostek biznesowych, bo w tym zapisie błąd zakresu daje się wykryć
[LIT: ARTS ODM 7.3, `BusinessUnitGroup`, `BusinessUnitGroupItem`; reguła „ItemLabel is related to
BusinessUnitGroupItem rather than Item"]. Obserwacja rynkowa bez badania potwierdzającego [HIP]: wiele
systemów wiąże cenę wprost z lokalizacją i działa to poprawnie, więc analityk nie powinien uznać
modelu klienta za błędny wyłącznie na tej podstawie.

## Cykl życia ceny regularnej

ustalenie (przy dostawie albo decyzją) -> zatwierdzenie -> dystrybucja do POS i kanałów ->
potwierdzenie odbioru -> wejście w życie -> uwidocznienie na nośniku -> obowiązywanie -> zastąpienie
albo wygaśnięcie -> historia.

### Stany rekordu ceny

Łańcuch wyżej to kroki, a analityk i vendor potrzebują **stanów**: tego, co w danym momencie wolno,
co robi kasa i co widzi klient. Tabela zbiera rozstrzygnięcia rozsypane po polach 9, 10 i 11 w jedno
miejsce, bo to jest artefakt, który realnie rysuje się na tablicy podczas warsztatu
[PROP+ 19.08, recenzja v0.4; treść wywiedziona z rozstrzygnięć już obecnych w tej karcie].

| Stan | Czy kasa nalicza | Czy nośnik pokazuje | Czy da się cofnąć | Jak się z niego wychodzi |
|---|---|---|---|---|
| **projektowana** | nie | nie | tak, bez skutku operacyjnego | zatwierdzenie albo odrzucenie |
| **zatwierdzona** | nie | nie | tak, ale zatwierdzenie zostaje w śladzie audytowym | wysyłka do POS i kanałów |
| **wysłana** | nie | nie, chyba że zlecenie metkowania ruszyło wcześniej; wtedy obowiązuje ten sam warunek co w stanie „odebrana": nośnik wyprzedzający wolno wystawić **wyłącznie z jawną datą obowiązywania** | tak, wycofaniem cennika przed momentem wejścia w życie | potwierdzenie odbioru przez objęte kasy i kanały |
| **odebrana, przed momentem wejścia w życie** | nie; kasa zna ją jako cennik przyszły | zależy od harmonogramu nośników; rozjazd w tym oknie jest oczekiwany i mierzony minimalnym wyprzedzeniem. Nośnik **wolno** wyprzedzić, ale tylko z jawną datą obowiązywania na tym samym nośniku; nośnik pokazujący cenę przyszłą bez daty jest rozbieżnością wg [R: PRICE-005], nie zapowiedzią | tak | nadejście momentu wejścia w życie |
| **wysłana, odbiór niekompletny w momencie wejścia w życie** | **rozstrzygnięcie obowiązkowe, nigdy cisza.** Kasy, które odebrały, naliczają nową cenę; kasy, które nie odebrały, naliczają starą, więc ta sama sieć sprzedaje w dwóch cenach naraz. Standard wymaga jednej z dwóch reakcji: blokada startu dla całego zakresu albo start z jawnym zdarzeniem `dystrybucja-niepełna-przed-momentem-wejścia`. Standard **nie przesądza której**, ale wymaga, żeby była wybrana świadomie i zapisana | część nośników nową, część starą | tak, ale przy wariancie ze startem część transakcji jest już po nowej cenie | uzupełnienie odbioru albo decyzja o wycofaniu |
| **obowiązująca** | tak | ma pokazywać. Nośnik, który jeszcze nie pokazuje, jest stanem dopuszczalnym **tylko wtedy, gdy jest zapisany na liście czekających na wymianę i mieści się w maksymalnym czasie nadrobienia** (pole 9). Rozbieżność nieodnotowana albo po przekroczeniu zegara jest incydentem [R: PRICE-005] | tylko przez wycofanie, ze skutkiem na transakcje już zrealizowane | zastąpienie, wygaśnięcie albo wycofanie |
| **obowiązująca w trybie awaryjnym** | tak, kasa nalicza z ostatniego znanego cennika dla danej daty; przy cennikach przyszłych nalicza zaplanowaną, przy ich braku przegapia zmianę | bez zmian, nośnik nie wie o trybie awaryjnym | nie z poziomu centrali, bo łączności nie ma | powrót łączności i zastosowanie zaległych zmian w kolejności momentu wejścia w życie |
| **zastąpiona** | nie, nalicza cenę następną | nie | nie | wpis w historii ceny |
| **wygasła** | nie; jeśli nie ma ceny następnej, pozycja zostaje bez ceny i uruchamia procedurę z pola 11 | nie | nie | wpis w historii ceny |
| **wycofana (rollback)** | nie | wymaga cofnięcia nośnika, co jest osobnym zleceniem i osobnym czasem | z definicji jest cofnięciem | wpis w historii ceny plus rozstrzygnięcie, co z dokumentami sprzedaży wystawionymi po błędnej cenie |

Trzy uwagi do tabeli:

1. **Tryb awaryjny nie jest osobnym etapem, tylko przecina stany.** Kasa odcięta od sieci może być
   jednocześnie „obowiązująca w trybie awaryjnym" dla jednej pozycji i nieświadoma zmiany dla innej.
2. **W modelu partiowym stan dotyczy rekordu ceny, nie pozycji.** Ta sama pozycja może mieć
   jednocześnie kilka rekordów w różnych stanach, po jednym na partię.
3. Stan „wysłana, odbiór niekompletny" jest jedynym, w którym sieć sprzedaje w dwóch cenach naraz
   **bez decyzji handlowej**, czyli nie dlatego, że ktoś tak chciał, tylko dlatego, że dystrybucja
   się nie domknęła. Karta **nie twierdzi, że taki stan jest zgodny z prawem**: [R: PRICE-005] daje
   konsumentowi prawo do ceny najkorzystniejszej wszędzie tam, gdzie cena uwidoczniona rozjeżdża
   się z ceną przy zapłacie, więc stan jest co najwyżej **tolerowany operacyjnie i kosztowny**
   [PROP+ 19.08, naprawa po recenzji wydaniowej]. Pytania wykrywające: B1, B2, B3, C12, C13;
   flagi F1 i F19.

**1. Cel biznesowy:** ustalić dla każdej pozycji sprzedażowej cenę regularną obowiązującą
w zadeklarowanym zakresie organizacyjnym, kanałowym i czasowym, dowieźć ją do wszystkich kas
i kanałów przed momentem wejścia w życie, uwidocznić ją zgodnie z obowiązkami informacyjnymi (R)
i utrzymać jej odtwarzalną historię jako podstawę marży, wyceny zwrotów i ceny odniesienia przy
obniżce.

**2. Granice:** od zdarzenia cenowego po zatwierdzeniu, do potwierdzonego obowiązywania we wszystkich
objętych kasach, kanałach i na nośnikach ceny, oraz do zapisu w historii.

NIE obejmuje: danych pozycji, w tym miar opakowania, klasyfikacji podatkowej i oznaczenia
towaru jako szybko psującego się (-> CAT-01); **korekty faktury zakupowej po przyjęciu towaru** (-> PRC / FIN, bo nie
przelicza ceny); promocji i sprzedaży ze stratą jako taktyki (-> CAT-03); naliczenia ceny w koszyku
oraz rabatu na pojedynczej transakcji (-> SAL-01); wykonania zwrotu (-> RTN); **wydania towaru bez
opłaty** (patrz niżej).

**Rozstrzygnięcie: wydanie bez opłaty nie jest sprzedażą.** Nie istnieje sprzedaż po cenie zero;
pozycja musi mieć co najmniej najmniejszą jednostkę monetarną, żeby dało się ją ująć na dokumencie
sprzedaży [AUT-R 19.08]. Gratis można wydać i zarejestrować, ale to jest odrębne zdarzenie bez ceny,
więc CAT-02 nie ma tu nic do powiedzenia poza jednym: **cennik nie może wyprodukować pozycji
o cenie zero**. Obsługa rozkłada się na trzy miejsca: mechanika promocyjna, która do wydania
prowadzi, należy do CAT-03; rejestracja wydania towaru do domeny zapasu; skutek podatkowy do
domeny finansów. Karta nie przypisuje tego do konkretnych identyfikatorów procesów, bo tamte karty
nie są jeszcze zredagowane.

Przekazuje dalej: cenę regularną i historię ceny do CAT-03 (cena odniesienia); cenę obowiązującą do
SAL-01; regułę wyceny zwrotu do RTN; wartość rewaluacji do domeny zapasu i finansów **wyłącznie
przy wycenie zapasu w cenach detalicznych**. Przy wycenie w cenach zakupu netto, która jest modelem
dominującym operacyjnie, to wyjście w ogóle nie powstaje (patrz pole 10).

**3. Właściciel:** zależny od modelu relacji sieć-lokalizacja (oś 1). W modelu centralnym:
Merchandising / Category Management. W modelu odwróconym: kierownik lokalizacji, z centralą jako
właścicielem nakładki na wybrane pozycje. [AUT-R 19.08]

**4. Aktorzy:** category/product manager i dział cen; kontroling (nadzór nad marżą); manager
regionalny; **właściciel albo kierownik lokalizacji** (cennik lokalny albo korekta lokalna, zależnie
od osi 1); kierownik kategorii (ograniczony wpływ, jeśli model to przewiduje); operator przyjęcia
towaru (moment zamrożenia kosztu); operator utrzymania danych; personel lokalizacji (metkowanie
i nośniki ceny). [AUT-R 19.08]

**5. Systemy:** system zarządzania cenami, cennik wielopoziomowy albo matryca marżowa, system danych
podstawowych pozycji, moduł przyjęcia towaru (źródło kosztu i momentu wyceny), mechanizm replikacji
cen, serwer lokalny lokalizacji albo bezpośrednio końcówki POS, POS, kanały cyfrowe, system nośników
ceny (metkowanie, druk etykiet, etykiety elektroniczne), rejestr stawek podatku, rejestr historii
ceny. [AUT-R 19.08]

**6. Wyzwalacze:**
- **dostawa i przyjęcie towaru na stan** (reżim matrycy marżowej; główny wyzwalacz, nie zmiana
  kosztu jako taka) [AUT-R 19.08];
- decyzja cenowa: centrali albo kierownika lokalizacji, zależnie od osi 1 [AUT-R 19.08];
- kalendarz zmian cen; wejście nowej pozycji do sprzedaży (-> CAT-01); zmiana klasyfikacji podatkowej
  pozycji; zastąpienie pozycji pozycją następcą; zmiana zakresu organizacyjnego albo kanałowego;
  oznaczenie towaru jako niepełnowartościowego; zdarzenie awaryjne; uruchomienie systemu i migracja
  cen (cutover). [PROP+ 19.08]

**7. Wejścia (dokumenty):**

- **obowiązkowe:**
  - pozycja z kompletem danych do wyceny [-> CAT-01]: identyfikacja, jednostka sprzedaży
    i **przelicznik do opakowania zbiorczego**, miara opakowania i miara porównawcza do ceny
    jednostkowej, klasyfikacja podatkowa. Przelicznik jest tu wymieniony imiennie, bo konsumuje go
    kontrola ceny porcji w polu 9; CAT-01 deklaruje go imiennie jako daną wytwarzaną
    [PROP+ 19.08, naprawa po recenzji wydaniowej];
  - **data pierwszego oferowania pozycji** i **oznaczenie towaru jako szybko psującego się** [-> CAT-01];
    bez nich nie da się wyliczyć ceny odniesienia [R: PRICE-002, PRICE-003];
  - **model relacji sieć-lokalizacja** (oś 1), bo wyznacza, kto jest źródłem cennika;
  - **model wyceny: jedna cena na pozycję czy cena per partia** (oś 3), bo wyznacza klucz rekordu;
  - definicja cennika i jego poziomu w hierarchii;
  - zakres obowiązywania: organizacyjny i kanałowy;
  - moment wejścia w życie: data i godzina, ze wskazaniem strefy albo doby biznesowej;
  - deklaracja, czy źródłem prawdy jest kwota netto czy brutto, **oraz moment zaokrąglenia przy
    przeliczeniu netto na brutto: na pozycji czy na dokumencie sprzedaży**. Obie dane konsumuje
    kontrola w polu 9; bez drugiej z nich kontrola nie ma czego sprawdzać
    [PROP+ 19.08, naprawa po recenzji wydaniowej];
  - podstawa ceny: w reżimie matrycy marżowej cena zakupu z przyjęcia i parametry matrycy wraz
    z **metodą uspójnienia**; w reżimie cennika dedykowanego cena wpisana wprost z zapisaną metodą;
  - **relacja następstwa pozycji** (pozycja zastępowana i pozycja następca) [-> CAT-01], gdy
    zdarzenie cenowe dotyczy pozycji zastępowanej. Bez niej nie da się przenieść historii ceny,
    a okno ceny odniesienia zeruje się przy każdej zmianie identyfikatora [R: PRICE-001]. CAT-01
    deklaruje tę daną imiennie jako konsumowaną przez CAT-02 [PROP+ 19.08, recenzja v0.4];
  - **oznaczenie towaru jako niepełnowartościowego**, gdy zdarzenie cenowe schodzi poniżej kosztu.
    Uwaga na właścicielstwo: flaga **nie powstaje ani w tej karcie, ani w CAT-01**, która jawnie
    wskazuje domenę zapasu jako miejsce jej powstania. Domena zapasu nie ma jeszcze karty, więc
    bramka wejścia CAT-02 stoi dziś na danej bez właściciela w standardzie; luka zarejestrowana
    w wewnętrznym rejestrze tematów odłożonych [PROP+ 19.08, recenzja v0.4].
  - **minimalne wyprzedzenie** zdarzenia cenowego wobec czasu potrzebnego na metkowanie albo
    aktualizację nośników, wyrażone liczbą, nie zwyczajem. Konsumuje je warunek wejścia z pola 9
    i flaga F13; bez zadeklarowanej wartości kontrola nie ma czego porównać
    [PROP+ 19.08, naprawa po recenzji wydaniowej];
  - **maksymalny czas nadrobienia** dla listy nośników czekających na wymianę. Konsumuje go warunek
    wyjścia z pola 9 i flaga F27; to jest ten „zegar", bez którego rejestr zaległości staje się
    stałym tłem [PROP+ 19.08, naprawa po recenzji wydaniowej].
- **obowiązkowe przy cutoverze:** historia ceny przeniesiona z systemu poprzedniego (przeniesienie
  jest wykonalne [AUT-R 19.08]), albo jawna decyzja o starcie bez historii wraz z jej konsekwencją.
- **opcjonalne:** reguły zaokrąglania i końcówek cenowych; cena sugerowana producenta (jako dana,
  NIE jako cennik); dane o cenach rynkowych; strategia kategorii; harmonogram metkowania albo
  propagacji nośników; limit uprawnień cenowych dla poziomu lokalnego; **obowiązkowa opłata doliczana
  do ceny, nieujęta w cenie regularnej** (klasa; instancje w profilu, P15) [PROP+ 19.08]; waluta i reguły
  zaokrągleń per waluta.

**8. Wyjścia:** dokumenty: zatwierdzone zdarzenie cenowe z zakresem organizacyjnym, kanałowym
i momentem wejścia w życie; cennik obowiązujący w lokalizacji i kanale; **cena jednostkowa**;
**cena odniesienia** wyliczona z historii na potrzeby CAT-03; zlecenie metkowania albo aktualizacji
nośnika ceny; **reguła wyceny zwrotu** do RTN; wpis w historii ceny per pozycja, zakres, kanał
i (w modelu partiowym) partia | zdarzenia: cena-zatwierdzona, cennik-wysłany,
cennik-odebrany-przez-lokalizację, cena-weszła-w-życie, cena-zastąpiona, nośnik-zaktualizowany,
dystrybucja-niepełna-przed-momentem-wejścia, **rozbieżność-ceny-zarejestrowana** (nośnik albo metka
kontra kasa, z dowodem uwidocznionej oferty) [PROP+ 19.08, recenzja v0.4; R: PRICE-005].

**9. Bramki decyzyjne:**

- **warunki wejścia:**
  - komplet danych pozycji do wyceny, w tym miara do ceny jednostkowej, data pierwszego oferowania
    i oznaczenie towaru jako szybko psującego się; brak któregokolwiek BLOKUJE zdarzenie cenowe [R: PRICE-002, PRICE-003];
  - jednoznaczny zakres organizacyjny i kanałowy oraz poziom cennika w hierarchii;
  - jednoznaczny moment wejścia w życie, rozstrzygalny wobec strefy czasowej i doby biznesowej;
  - zadeklarowane źródło prawdy: netto albo brutto;
  - w reżimie matrycy marżowej: koszt pobrany z **przyjęcia towaru**, wraz z zapisaną metodą
    uspójnienia; reguła zaokrąglenia zdefiniowana PRZED wyliczeniem [LIT: Oracle Retail Merchandising
    Foundation Cloud 22.1, „Pricing Pre-Requisites": strefa cenowa z regułami zaokrągleń musi istnieć
    przed założeniem pozycji];
  - uprawnienie adekwatne do osi 1: w modelu centralnym uprawnienie centrali, w odwróconym
    uprawnienie lokalizacji; **cennik lokalny w sieci zarządzanej kategoriami przechodzi przez
    akceptację centrali**, bo lokalizacja nie zna strategii kategorii i mogłaby ją zaburzyć
    [AUT-R 19.08];
  - **obniżenie poniżej kosztu wyłącznie przy oznaczeniu towaru jako niepełnowartościowego**,
    z wyższym poziomem uprawnień [AUT-R 19.08]. Flaga niepełnowartościowości jest warunkiem, nie
    samo uprawnienie;
  - minimalne wyprzedzenie wobec czasu potrzebnego na metkowanie albo aktualizację nośników
    zachowane, albo jawnie użyta ścieżka awaryjna z odrębnym uprawnieniem [PROP+ 19.08].
- **warunki wyjścia:**
  - odbiór cennika **potwierdzony** przez każdą objętą kasę i kanał przed momentem wejścia w życie.
    Warunek jest wykonalny tylko wtedy, gdy okno dystrybucji mieści się w oknie operacyjnym, więc
    musi być policzony z realnych wolumenów, nie założony. Brak kompletu potwierdzeń ma zdefiniowaną
    reakcję: blokada startu albo jawne zdarzenie, nigdy cisza [PROP+ 19.08];
  - cena obowiązująca rozstrzygalna deterministycznie przy kilku poziomach cennika i kanałach naraz;
    **w modelu partiowym dodatkowo rozstrzygalna przy skanowaniu**, mimo że kasa czyta identyfikator
    pozycji, a nie partii [PROP+ 19.08];
  - cena jednostkowa wyliczona z właściwej miary i uwidoczniona, albo pozycja jawnie sklasyfikowana
    jako wyłączona z obowiązku [R: PRICE-004];
  - nośnik ceny (cenówka, metka, etykieta elektroniczna, publikacja w kanale) jest w jednym
    z trzech dopuszczalnych stanów:
    1. pokazuje cenę obowiązującą;
    2. pokazuje cenę przyszłą **wraz z datą, od której ta cena obowiązuje**, podaną na tym samym
       nośniku i czytelną dla konsumenta [AUT-R 19.08, rozstrzygnięcie właściciela]. Bez daty
       nośnik wyprzedzający jest rozbieżnością, nie zapowiedzią, i uruchamia [R: PRICE-005];
    3. jest zapisany na liście nośników czekających na wymianę, z momentem, od kiedy czeka.

    **Czwarta możliwość, czyli cisza, nie istnieje.** Nośnik, który został w tyle
    i nikt o tym nie wie, jest tym samym co brak kontroli [AUT-R 19.08, tura 6];
  - dla listy nośników czekających na wymianę zdefiniowany jest **maksymalny czas nadrobienia**.
    Jego przekroczenie jest incydentem, nie normalnym stanem pracy [AUT-R 19.08, tura 6].
    Uzasadnienie właściciela: przy dużej sieci nie da się wymienić wszystkich nośników w tej samej
    minucie, więc wymóg „wszystko wymienione, inaczej cena nie wchodzi" jest niewykonalny i zostanie
    obejściem wyłączony. Rejestr bez limitu czasu też nie działa, bo zaległość staje się stałym tłem
    i nikt jej nie goni. Działa dopiero rejestr **plus** zegar;
  - wpis historii ceny zamknięty z momentem, zakresem i kanałem [R: PRICE-001..003].
- **kontrole:**
  - poziom cennika i kanał rozstrzygają jednoznacznie; w modelu odwróconym nakładka centralna wygrywa
    **wyłącznie na pozycjach nią objętych**, poza nimi nie nadpisuje cennika lokalnego [PROP+ 19.08];
  - **cena zero jest niedopuszczalna jako cena sprzedaży**; dolnym ograniczeniem jest najmniejsza
    jednostka monetarna waluty, bo pozycja o cenie zerowej nie da się ująć na dokumencie sprzedaży
    [AUT-R 19.08]. Nie ma tu wariantu „zero zamierzone": wydanie bez opłaty nie jest sprzedażą
    i wychodzi z tego procesu (patrz pole 2);
  - cena nie jest ujemna [LIT: Oracle Retail Price Management, reguła niewyłączalna „future retail
    cannot be negative"]; cena pusta na pozycji dopuszczonej do sprzedaży blokuje sprzedaż albo
    uruchamia zapisaną procedurę zastępczą;
  - **koszt zamrożony przy przyjęciu**: korekta faktury po przyjęciu nie modyfikuje ceny półkowej
    ani podstawy marży historycznej [AUT-R 19.08];
  - jedno zdarzenie cenowe na pozycję, zakres i dzień; duplikat blokowany albo jawnie rozstrzygany
    [LIT: Oracle RPM, „Duplicate Price Change"];
  - zaległe zmiany stosowane w kolejności momentu wejścia w życie, nie odbioru [PROP+ 19.08];
  - spójność jednostki miary między ceną a opakowaniem (mianownik ceny porównawczej liczony od
    zawartości opakowania sprzedażowego, nie od sztuki w środku; ryzyko opisane we flagach F8);
  - **cena porcji wydzielonej z opakowania zbiorczego wynika z ceny tego opakowania**, a nie jest
    ustalana osobno: jeżeli sprzedajesz litr z bańki piętnastolitrowej, cena litra to jedna piętnasta
    ceny bańki, przy zapisanej regule zaokrąglenia. Zasada ogólna: **pozycja ma jedną cenę, która
    może być dzielona; nie ma drugiej, niezależnej ceny dla porcji** [AUT-R 19.08, tura 6];
  - stawka podatku wersjonowana niezależnie od ceny, z uzgodnionym momentem obowiązywania; zmiana
    klasyfikacji podatkowej pozycji jest zdarzeniem cenowym [R: FISC-020];
  - **przeniesienie historii ceny na pozycję następcę** przy zastąpieniu pozycji; brak przeniesienia
    zeruje okno ceny odniesienia i otwiera ścieżkę obejścia obowiązku przez wymianę identyfikatora
    [PROP+ 19.08; R: PRICE-001];
  - zgodność ceny na nośniku albo metce z ceną w kasie, mierzona, nie zakładana [R: PRICE-005];
  - **przypadek rozbieżności jest rejestrowany jako zdarzenie z dowodem uwidocznionej oferty**, a nie
    tylko rozstrzygany na korzyść konsumenta przy kasie. Bez rejestru KPI dokładności cenowej da się
    policzyć wyłącznie z próby audytowej, a reklamacja klienta pozostaje jedynym mechanizmem
    wykrywania [PROP+ 19.08, recenzja v0.4; R: PRICE-005];
  - **arytmetyka netto kontra brutto jest zdefiniowana i jednokierunkowa**: zadeklarowane źródło
    prawdy, moment zaokrąglenia (na pozycji czy na dokumencie) i sposób postępowania z groszem
    różnicy między dokumentem sprzedaży a raportem. To jest inna kontrola niż zaokrąglenie wyniku
    narzutu: tam chodzi o wyliczenie ceny, tu o konwersję podatkową tej samej ceny. Kontrola musi
    przetrwać zmianę stawki podatku, która jest zdarzeniem cenowym [PROP+ 19.08, recenzja v0.4;
    R: FISC-020];
  - ślad audytowy zmiany: kto, kiedy, na jakiej podstawie [LIT: ARTS ODM 7.3, `Operator`, `Worker`,
    `PartyRoleAssignment`, „for audit and control purposes"].

**Uwaga o źródle autorytetu kontroli** [PROP+ 19.08, recenzja v0.4]. Trzy kontrole wyżej (zakaz ceny
ujemnej, blokada duplikatu na dzień, zachowanie ceny awaryjnej w polu 11) mają dziś jedyne oparcie
w dokumentacji jednego produktu. Same kontrole są sensowne i standard je utrzymuje, ale dopóki nie
znajdzie się dla nich drugie, niezależne źródło albo potwierdzenie u adoptera, należy je czytać jako
**praktykę udokumentowaną w jednej implementacji**, a nie jako regułę rynku. To jest ryzyko opisania
konkretnego produktu zamiast retailu.

**Kontrola parametryczna zamiast drugiej pary oczu** [AUT-R 19.08]. W zdecydowanej większości sieci
zatwierdzanie ceny **nie ma** rozdziału ról; kontrolę pełni system, pilnując parametru (np. progu
marży). Rozdział ról występuje w konkretnym wzorcu: sieć zarządzana na poziomie kategorii, w której
kierownik zgłasza cennik lokalny, a zatwierdza go centrala. Karta wymaga więc **kontroli
parametrycznej jako minimum**, a rozdziału ról jako wariantu przypisanego do tego wzorca; nie stawia
rozdziału ról jako wymagania powszechnego. (W v0.2 było odwrotnie i było to nadużycie.)

**10. Skutki i sprzężenia międzydomenowe:**
- **stock: ZALEŻY OD MODELU WYCENY ZAPASU.** Skutek zmiany ceny sprzedaży na zapasie nie jest
  własnością procesu cenowego, tylko konsekwencją tego, w jakich cenach detalista wycenia zapas
  [AUT-R 19.08, tura 5]:
  - **wycena w cenach zakupu netto**: zmiana ceny sprzedaży NIE rusza wyceny zapasu ani księgowości.
    To jest model dominujący operacyjnie i domyślne założenie tej karty [AUT-R 19.08, tura 5];
  - **wycena w cenach detalicznych**: zmiana ceny wywołuje rewaluację zapasu i księgowanie różnicy
    [LIT: ARTS ODM 7.3, widok 01300, `StockLedgerAccount`].

  Karta **nie rozstrzyga**, który model jest właściwy, i nie nazywa drugiego wyjątkiem. Wymaga
  ustalenia modelu na wejściu (pytanie A24), bo od odpowiedzi zależy, czy zdarzenie cenowe jest
  jednocześnie zdarzeniem księgowym, a więc czy ten proces ma w ogóle wyjście do finansów.
  Rozstrzygnięcie 19.08 po recenzji v0.4: poprzednie brzmienie („wariant rzadki", „wyjątek")
  przypisywało procesowi cenowemu skutek, który należy do polityki rachunkowości detalisty
  [PROP+ 19.08, recenzja v0.4].
- **pieniądze: NIE.** Przepływ środków powstaje przy sprzedaży (-> SAL) i przy rozliczeniu zakupu
  (-> PRC).
- **księgowość: ZALEŻY**, tym samym rozstrzygnięciem co zapas. Przy wycenie zapasu w cenach zakupu
  netto zdarzenie cenowe nie jest zdarzeniem księgowym; przy wycenie w cenach detalicznych jest.
- sprzężenie z podatkiem: cena i stawka podatku to dwa niezależnie wersjonowane strumienie
  [R: FISC-020; LIT: ARTS ODM 7.3 rozdziela schemat Price od Transaction Tax].
- sprzężenie z promocją: cena regularna jest wejściem CAT-03; historia jest jedynym źródłem ceny
  odniesienia [R: PRICE-001..003].
- sprzężenie ze zwrotami: historia ceny jest jedynym źródłem wyceny zwrotu towaru kupionego przed
  zmianą ceny.
- sprzężenie z zakupami: przyjęcie towaru jest momentem wejścia kosztu do wyceny; korekta faktury
  po przyjęciu zostaje po stronie PRC/FIN i tworzy trwały rozjazd między kosztem wyceny a kosztem
  rzeczywistym.

**11. Warianty i wyjątki kluczowe:**

**Dystrybucja i tryb awaryjny** [AUT-R 19.08]. Cenniki wysyłane z centrali na końcówki POS albo na
serwer lokalny lokalizacji i tam zapisywane; każda zmiana wywołuje synchronizację. Przy zaniku
łączności kasa pracuje na cenniku lokalnym w trybie awaryjnym, na ostatnim znanym cenniku dla danej
daty. **Kasa powinna otrzymywać także cenniki przyszłe**, z datą wejścia w życie do przodu, nie tylko
bieżący [AUT-R 19.08]; inaczej lokalizacja odcięta od sieci przegapi zaplanowaną zmianę i wróci
online już po jej terminie. Silnik promocyjny działa analogicznie, ale część mechanik wymaga trybu
online (limit sztuk na poziomie sieci, synchronizacja z programem lojalnościowym); szczegół w CAT-03.

**Moment obowiązywania** [AUT-R 19.08]. Spotykane dwa modele: cena od dnia oraz cena od dnia i godziny;
w praktyce częściej ten drugi. Prawo lokalizacji do opóźnienia albo odrzucenia cennika wynika z osi 1:
w sieci własnej zwykle nie występuje, w modelu franczyzowym i partnerskim jest realne i kontraktowe.
Moment musi być rozstrzygalny wobec doby biznesowej lokalizacji, nie tylko kalendarzowej [LIT: ARTS
ODM 7.3: „all transactional entities are tied to a business day"].

**Nośnik ceny** [AUT-R 19.08]. Możliwe równolegle: metkowanie egzemplarza przy przyjęciu, etykieta półkowa
drukowana, etykieta elektroniczna. W modelu partiowym metkowanie egzemplarza jest tym, co niesie cenę.
Karta nie przesądza technologii, ale wymaga potwierdzenia, że nośnik pokazuje cenę obowiązującą.
Wzorzec porównawczy spoza PL, **orientacyjny, NIE prawo obowiązujące w jurysdykcji tej karty**:
w amerykańskim modelowym przepisie metrologicznym procedura weryfikacji sprawdza cenę „on a shelf,
item, or otherwise advertised" wobec bazy POS, czyli nie różnicuje wymagania ze względu na technologię
nośnika [LIT: NIST Handbook 130, Section V, wyd. 2023, DOI 10.6028/NIST.HB.130-2023]. Obowiązki
wiążące w tej karcie wynikają z [R: PRICE-004, PRICE-005], nie z HB130 [PROP+ 19.08, recenzja v0.4].

**Cena uwidoczniona poza lokalizacją** [PROP+ 19.08]. Ekspozycja ceny regularnej w kanale cyfrowym,
w reklamie i w materiale drukowanym niepromocyjnym podlega temu samemu obowiązkowi co etykieta
[R: PRICE-005]. Lista nośników musi obejmować wszystkie miejsca publikacji ceny. Materiał promocyjny
należy do CAT-03.

**Uprawnienia lokalne** [AUT-R 19.08]. Systemy mają zwykle drabinkę uprawnień, bez standardu
rynkowego. Uwaga na granicę: drabinka po stronie lokalizacji (kasjer ma bezpieczny poziom rabatu,
wyższe rabatowanie wymaga zatwierdzenia kierownika) dotyczy **rabatu na pojedynczej transakcji**,
czyli SAL-01, a nie zmiany cennika. CAT-02 odpowiada wyłącznie za uprawnienie do zmiany ceny
obowiązującej dla wszystkich klientów do odwołania. Rozdzielenie tych dwóch rzeczy jest pierwszą
rzeczą do ustalenia na warsztacie (pytania A9 i A10).

**Zdarzenie awaryjne** [PROP+ 19.08]. Cena wchodząca z pominięciem minimalnego wyprzedzenia. Osobna,
audytowana ścieżka z odrębnym uprawnieniem, bo omija czas potrzebny na nośniki. Ryzyko do sprawdzenia
w konkretnym produkcie: w co najmniej jednej udokumentowanej implementacji cena awaryjna nadpisuje
wcześniej odebraną według kolejności odbioru, nie momentu wejścia w życie; ten sam produkt ma osobny
mechanizm kontroli konfliktów, więc zachowanie zależy od konfiguracji [LIT: Oracle Retail Price
Management, „Price Change Overview" i Operations Guide 16.0, rozdz. Conflict Checking].

**Cutover i migracja historii** [AUT-R 19.08]. Przeniesienie historii cen z systemu poprzedniego jest
wykonalne i zwykle się je robi. Start z pustą historią jest więc **decyzją albo zaniedbaniem
projektowym, nie barierą techniczną**, a jego konsekwencją jest brak możliwości zgodnego z prawem
ogłoszenia obniżki przez pełne okno ustawowe [R: PRICE-001]. Osobny, poprawny przypadek: **nowa
lokalizacja zaczyna historię od pierwszego dnia** [AUT-R 19.08], co wiąże się z ceną odniesienia dla towaru
oferowanego krócej niż okno ustawowe [R: PRICE-002].

**Pozycja zastępowana i zmiana identyfikatora** [PROP+ 19.08]. Przy zmianie opakowania albo zastąpieniu
pozycji następcą trzeba rozstrzygnąć, czy historia ceny przechodzi. Brak przeniesienia daje utratę
możliwości ogłoszenia obniżki oraz otwartą ścieżkę obejścia okna przez wymianę identyfikatora.

**Zmiana zakresu organizacyjnego lub kanałowego pozycji albo lokalizacji** [PROP+ 19.08, recenzja v0.4].
Karta ma to jako wyzwalacz i ma flagę na **błędny** zakres (F12), ale zmiana zakresu jest osobnym
przypadkiem: lokalizacja przechodzi z jednego regionu do drugiego, otwiera się nowa lokalizacja,
lokalizacja zmienia typ, grupa jednostek zostaje przedefiniowana. Trzy rzeczy wymagają
rozstrzygnięcia i żadna nie ma odpowiedzi domyślnej: czy ceny są **dziedziczone** z nowego zakresu
czy **przeliczane**; czy historia ceny idzie **za lokalizacją** czy **za zakresem**; co z cenami
przyszłymi już wysłanymi na starym zakresie. Przy cennikach wielopoziomowych (oś 4) ten moment
dotyka jednocześnie hierarchii, historii i replikacji, więc jest jednym z częstszych miejsc,
w których wdrożenie się wywraca. Kontrola: zmiana zakresu jest zdarzeniem cenowym dla każdej pozycji
objętej różnicą między starym a nowym cennikiem, nie operacją na słowniku.

**Obowiązkowe doliczenia do ceny** [PROP+ 19.08]. Jeśli w danym reżimie do ceny dolicza się obowiązkową
opłatę, decyzja, czy jest ona częścią ceny regularnej, czy pozycją doliczaną przy sprzedaży, zmienia
jednocześnie cenę na nośniku, cenę jednostkową, podstawę marży i cenę odniesienia. Klasa należy do
rdzenia, instancje do profilu (P15).

**Dokumenty otwarte w czasie** [AUT-R 19.08]. Zamówienie klienta, rezerwacja, przedpłata, wydanie
późniejsze niż zamówienie: obowiązuje **cena z momentu zawarcia umowy sprzedaży albo rezerwacji**,
nie z momentu wydania. Uzasadnienie jest po stronie klienta, nie systemu: ma dostać cenę, na którą
się zgodził, składając zamówienie. Reguła tutaj, wykonanie w SAL-01.

**Wycena zwrotu po zmianie ceny regularnej** [AUT-R 19.08]. Zwrot wyceniany **zawsze po cenie
transakcyjnej z dokumentu sprzedaży** (paragon albo faktura), niezależnie od tego, jaka cena
obowiązuje w momencie zwrotu. Nie ma wariantu „niższa z dwóch" ani „cena aktualna". Reguła
definiowana tutaj, bo tutaj jest historia; wykonanie w RTN.

**Cena regularna a cena sugerowana producenta.** Standard wymiany B2B oznacza cenę sugerowaną
osobnym kodem: `RETAIL_PRICE` w GS1 GDSN Price Synchronisation to „the retail (to consumer) price as
suggested by the manufacturer" [LIT: GS1 BMS Price Synchronisation, BMS Release 3.1.0]. Błędem jest
podpięcie **tego kodu** jako własnej ceny regularnej. Sam **kanał wymiany danych** GDSN (nie mylić z kanałem sprzedaży,
który w tej karcie jest osią klucza ceny) pozostaje poprawnym źródłem innych typów cen, w tym
zakupowych [PROP+ 19.08, recenzja v0.4].

**Pozycja bez ceny na sprzedaży.** Wymaga zapisanej procedury ustalenia ceny; to jest wymaganie tej
karty, nie cytat. Wzorzec porównawczy, **orientacyjny, NIE prawo obowiązujące w jurysdykcji tej
karty**: w amerykańskim modelowym przepisie metrologicznym pozycja spoza bazy nie jest błędem sama
w sobie, ale staje się nim, gdy cena zastosowana okaże się niespójna z pisemną albo zadeklarowaną
polityką [LIT: NIST HB130, Section V, `Not-on-File Item`]. Przeniesienie tego wzorca do specyfikacji
jako obowiązku prawnego byłoby błędem [PROP+ 19.08, recenzja v0.4].

**Sprzedaż na wagę, miarę i w porcjach wydzielonych** [LIT: ARTS ODM 7.3, `BulkItem`,
`UnitOfMeasureConversion`]. Inny tor liczenia i inny mianownik ceny porównawczej. Reguła standardu:
**cena porcji jest funkcją ceny opakowania, z którego porcję wydzielono**, a nie osobną pozycją
cennika. Litr wydany z bańki piętnastolitrowej kosztuje jedną piętnastą ceny bańki, przy zapisanej
regule zaokrąglenia [AUT-R 19.08, tura 6]. Konsekwencja: zmiana ceny opakowania zbiorczego jest
jednocześnie zmianą ceny porcji i nie wymaga osobnego zdarzenia cenowego. Konsekwencja druga:
suma cen porcji po zaokrągleniu bywa różna od ceny opakowania i ta różnica musi być świadoma,
a nie odkryta przy inwentaryzacji [PROP+ 19.08, recenzja v0.4].

**Wycofanie błędnego cennika** [PROP+ 19.08]. Rollback jest częścią procesu: zdefiniowany stan docelowy,
zakres, moment oraz odpowiedź, co z transakcjami zrealizowanymi po błędnej cenie.

**12. Bezpieczniki prawne (R):** regulatory-matrix v1.0.1, legal_as_of 2026-08-14, overlay retail_core:

| ID | Norma | Pewność w RM | Rola w tej karcie |
|---|---|---|---|
| PRICE-004 | widoczna cena i wymagana cena jednostkowa | verified | warunek wyjścia: uwidocznienie |
| PRICE-005 | przy rozbieżności ceny uwidocznionej i przy zapłacie konsument ma prawo do ceny najkorzystniejszej | verified | kontrola nośnik kontra kasa; **w modelu partiowym ryzyko strukturalne, patrz F3** |
| PRICE-001 | najniższa cena z 30 dni przed obniżką | verified | historia i wyliczenie odniesienia tutaj, komunikat w CAT-03 |
| PRICE-002 | cena odniesienia dla towaru oferowanego krócej niż 30 dni | verified | wymusza datę pierwszego oferowania; dotyczy też nowej lokalizacji |
| PRICE-003 | cena odniesienia towaru szybko psującego się | verified | wymusza oznaczenie takiego towaru w kartotece (dana z CAT-01) |
| FISC-020 | stawka podatku z wersjonowanej klasyfikacji obowiązującej w chwili sprzedaży | qualified | wymóg wersjonowania i uzgodnienia momentów wobec cennika |

**RTL-CONS-001 NIE jest wiązany do tej karty.** Obowiązek udostępnienia całkowitej ceny przed
zatwierdzeniem sprzedaży realizuje SAL-01; CAT-02 dostarcza mu daną. Zapisane jawnie, żeby przy
redakcji SAL-01 nie powstało podwójne wiązanie (P13).

**Cena odniesienia przy wielu cenach jednocześnie.** W modelu partiowym ta sama pozycja bywa
sprzedawana w kilku cenach naraz. Do wyliczenia ceny odniesienia bierze się wtedy **cenę najniższą**
[AUT-R 19.08]. Kalibracja po recenzji v0.4 [PROP+ 19.08, recenzja v0.4]: reguła właściciela
**mieści się w literalnym brzmieniu wymagania**, które mówi o najniższej cenie *stosowanej* w oknie,
a nie o jednej cenie w danym momencie. Jeżeli w oknie stosowano równolegle kilka cen, minimum bierze
się z całego zbioru. Poprzednie brzmienie opisywało tę regułę jako niepokrytą przez wymaganie i tym
samym niepotrzebnie ją osłabiało. Luka, która realnie istnieje, jest węższa, patrz GAP-y niżej.

Twardy wniosek z PRICE-001..003: **cena odniesienia jest funkcją historii ceny regularnej.** Bez
ciągłej historii per zakres i kanał (a w modelu partiowym także per partia) CAT-03 nie ma z czego
policzyć komunikatu; RM blokuje wtedy publikację obniżki [R: PRICE-001, TEST-PRICE-001-NEG].

**Kontekst porównawczy spoza PL, orientacyjny, NIE prawo obowiązujące.** [LIT: NIST Handbook 130,
Section V, wyd. 2023] Kryterium dokładności cenowej 98 %, liczone dla nadpłat i niedopłat. Dwa
zastrzeżenia: próg jest nierozłączny od metodyki próby, więc bez niej jest liczbą produkowalną
z dowolnego pomiaru; a to, czy zaokrąglenie w dół (`intentional undercharge`) jest liczone do
wskaźnika czy z niego wyłączone, wymaga sprawdzenia w wydaniu [do potwierdzenia].

**GAP-y do zgłoszenia maintainerowi regulatory-matrix** (NIE asertować jako prawo):
- **czy cena przypisana do pojedynczej partii jest „ceną stosowaną" w rozumieniu PRICE-001.**
  Wymaganie mówi o najniższej cenie stosowanej w oknie, ale nie rozstrzyga, czy cena obowiązująca
  dla kilku sztuk z jednej dostawy, przy jednoczesnej sprzedaży tej samej pozycji po innej cenie
  z innej dostawy, jest „stosowana" w tym sensie. Od tego zależy, czy w modelu partiowym cena
  odniesienia liczona jest z całego zbioru cen, czy tylko z ceny dominującej. To jest
  najkonkretniejszy GAP tej karty [do potwierdzenia; zarejestrowany w wewnętrznym rejestrze tematów odłożonych];
- brak wymagania o **minimalnym wyprzedzeniu zmiany ceny** wobec aktualizacji nośnika; PRICE-005
  działa jako skutek, nie prewencja [do potwierdzenia];
- brak odrębnego wymagania dla **nośników elektronicznych** (propagacja, potwierdzenie wyświetlenia)
  [do potwierdzenia];
- brak wymagania o **retencji historii ceny** jako danych, mimo że PRICE-001..003 jej wymagają
  operacyjnie [do potwierdzenia];
- brak pokrycia **sprzedaży poniżej kosztu** jako zagadnienia prawa konkurencji; ta karta wymaga
  tylko flagi niepełnowartościowości i uprawnienia, nie przesądza dopuszczalności [do potwierdzenia;
  pokrywa się z GAP-em G4 z CAT-03].

**GAP procesowy standardu:** rabat na pojedynczej transakcji przy kasie (drabinka kasjer, kierownik)
nie ma dziś właściciela. CAT-03 wypycha go jako „poza silnikiem", CAT-02 jako niebędący zdarzeniem
cennikowym, SAL-01 nie jest zredagowana. W rejestrze tematów odłożonych, warunek podjęcia: redakcja SAL-01.

Ograniczenia branżowe (kategorie z ceną regulowaną, urzędowo ustalaną albo objęte zakazem obniżek)
wchodzą warstwą profilu (P15) i overlay w RM, nie rdzeniem.

**13. Powiązanie w górę i artefakty:** value stream „Cena" (ustalenie -> dystrybucja -> obowiązywanie
-> historia), podłoże dla value streamu „Promocja" (CAT-03). Crosswalk: standard/mapowania/
crosswalk-frameworki.md. Artefakty do zrobienia: katalog scenariuszy UAT dla dystrybucji ceny;
glosariusz PL do EN (cena regularna, matryca marżowa, cennik wielopoziomowy, nośnik ceny, zdarzenie
cenowe, metkowanie).

KPI kandydujące (licznik i mianownik raportowane osobno, nie sam procent, P2):
- **dokładność cenowa**: pozycje, w których cena na nośniku zgadza się z ceną w kasie, wobec pozycji
  w próbie, przy zadeklarowanej metodyce doboru próby;
- **terminowość dystrybucji**: lokalizacje i kanały z potwierdzonym odbiorem przed momentem wejścia
  w życie, wobec objętych;
- **czas propagacji**: mediana i 95. percentyl od zatwierdzenia do aktualizacji nośnika;
- **udział zdarzeń awaryjnych** w ogóle zdarzeń cenowych;
- **odchylenie marży zrealizowanej od docelowej** po zaokrągleniach, per kategoria;
- **pokrycie historii ceny**: pozycje z ciągłą historią za wymagane okno, wobec pozycji aktywnych.

## 14. Bank pytań analityka

Każde pytanie rozstrzygalne, każde z uzasadnieniem, pytania złożone rozbite.

**Jak tego używać, czyli czego nie da się uciąć** [PROP+ 19.08, recenzja v0.4]. Bank ma 108 pytań
i nie jest scenariuszem jednej sesji. Priorytety:

| Priorytet | Pytania | Kiedy |
|---|---|---|
| **P0, bez tego nie ma projektu** | A1, A2, A3, A4 | blok wstępny, pierwsze 20 minut warsztatu |
| **P1, wyjście z pierwszej sesji** | A5, A7, A9, A10, A13, A14, A17, A20, A22, A24, A25, A27, A29, A31, A32 | warsztat z biznesem, jedna sesja 2-3 h |
| **P2, do dobrania po pierwszej sesji** | pozostałe A | mail, druga sesja albo warsztat tematyczny |
| **P3, praca dokumentacyjna** | cały blok B | z zespołem utrzymania obecnego systemu, nie na warsztacie z biznesem |
| **P4, formalne zapytanie** | cały blok C | pisemnie do vendora, z wymogiem lokatora w dokumentacji |

Reguła cięcia: **pytanie P0 albo P1 bez odpowiedzi jest ryzykiem do zarejestrowania, nie tematem do
pominięcia.** Odpowiedź „nie wiemy" też jest odpowiedzią i trzeba ją zapisać z datą.

### A. Do biznesu (na warsztat)

**Blok wstępny: cztery pytania, bez których reszta warsztatu jest zgadywaniem.**

A1. Jaki jest model relacji między siecią a lokalizacjami: sieć własna, franczyza twarda, franczyza
miękka, sieć partnerska? *(Wyznacza KIERUNEK przepływu ceny. W jednym modelu cennik idzie z centrali
do sklepu, w drugim odwrotnie: sklep tworzy cennik, a centrala nakłada tylko wybrane pozycje. Model
danych jest inny w obie strony.)*

A2. Czy jedna pozycja może mieć w tym samym momencie kilka różnych cen, zależnie od dostawy?
*(Rozstrzyga klucz rekordu ceny: pozycja plus zakres, czy pozycja plus PARTIA plus zakres. Zmiana
tej odpowiedzi po starcie projektu to przebudowa modelu, nie konfiguracja.)*

A3. Czy cena regularna powstaje z matrycy marżowej, z cennika dedykowanego, czy jedno i drugie
zależnie od kategorii? *(Matryca reaguje na dostawy, cennik dedykowany nie przelicza się wcale.
Rozstrzyga, czy system musi cenę liczyć, czy tylko przechowywać.)*

A4. Czy cena regularna może różnić się między kanałami? *(Domyślnie przy omnichannelu ceny są
wspólne, a różnicowanie jest świadomą nadbudową. Odpowiedź „nie" upraszcza model radykalnie.)*

**Blok: wyliczanie ceny**

A5. Gdy przychodzi nowa dostawa po innej cenie zakupu: cena starych sztuk zostaje, czy wszystko na
półce jest wyrównywane do jednej ceny? *(To jest praktyczna forma pytania A2, zadana językiem
operacji, nie modelu.)*

A6. Jeśli wyrównujecie: od czego liczycie? Marża od uśrednionej ceny zakupu, od ostatniej ceny
zakupu, czy metodą odrzucającą skrajne (np. z ostatnich pięciu odrzucamy najwyższą i bierzemy drugą)?
*(Systemy różnią się dokładnie tutaj i nie każdy obsłuży każdą metodę.)*

A7. Narzut liczycie od kosztu czy od ceny detalicznej? *(Ten sam „30 %" daje dwie różne ceny: przy
koszcie 10 wychodzi 13,00 albo 14,29 (przeliczone niezależnie 19.08.2026: 10 x 1,30 = 13,00;
10 / 0,70 = 14,2857 -> 14,29). Błędu nie widać na jednej pozycji, tylko na rozkładzie marży
w kategorii.)* Typowe odpowiedzi: „od zakupu", „marża na cenie", „nie wiem, tak liczy system"
(najczęstsza, weryfikacja przez B11).

A8. Jakie są reguły zaokrąglania wyniku wyliczenia ceny? Czy stosujecie końcówki cenowe? *(Reguła zdefiniowana po założeniu
pozycji wymaga masowej rewaluacji, nie dopisania parametru; zaokrąglenie w dół obniża rzeczywistą
marżę wobec docelowej, najmocniej na pozycjach niskocenowych.)*

**Blok: uprawnienia. Uwaga, dwie różne rzeczy.**

A9. Czy lokalizacja ma własny cennik, czy tylko wykonuje cennik centrali? *(Cennik lokalny to cena
obowiązująca dla wszystkich klientów do odwołania. Odpowiedź wynika z A1, ale trzeba ją potwierdzić
wprost, bo modele mieszane są częste.)*

A10. Osobno: kto i do jakiej wysokości może udzielić rabatu na pojedynczej transakcji przy kasie?
*(To NIE jest zmiana cennika i w standardzie należy do innego procesu. Mieszanie tych dwóch rzeczy
na warsztacie kończy się specyfikacją, w której kasjer ma prawo zmieniać cennik.)*

A11. Czy cennik lokalny wymaga akceptacji centrali? *(W sieciach zarządzanych na poziomie kategorii
tak, bo lokalizacja nie zna strategii kategorii i mogłaby ją zaburzyć. To jedyny rozpowszechniony
wzorzec rozdziału ról w cenach.)*

A12. Czego pilnuje system przy zmianie ceny: progu marży, progu odchylenia od ceny centralnej, czegoś
innego? *(W większości sieci nie ma drugiej pary oczu i to parametr jest jedyną kontrolą. Jeśli nie
ma ani rozdziału ról, ani parametru, kontroli nie ma żadnej.)*

A13. Kto może obniżyć cenę poniżej kosztu? Pod jakim warunkiem wolno to zrobić? *(Typowo wolno to wyłącznie na
towarze oznaczonym jako niepełnowartościowy, przy wyższym uprawnieniu. Jeśli u klienta wolno bez
oznaczenia, to jest dziura w kontroli marży.)*

**Blok: czas, dystrybucja, nośnik**

A14. Cena wchodzi w życie od dnia czy od dnia i godziny? *(Determinuje, czy w ogóle mamy problem
granicy doby.)*

A15. Przy wielu strefach czasowych: czyja to godzina, centrali czy lokalizacji? *(„Od 00:00" bez
wskazania strefy jest nierozstrzygalne.)*

A16. O której zamyka się u Was dzień sprzedażowy? Czy pokrywa się z dobą kalendarzową? *(Przy
lokalizacjach pracujących przez północ cena aktywowana na dobę kalendarzową wchodzi w środek
poprzedniego dnia sprzedażowego i rozjeżdża raporty.)*

A17. Czy lokalizacja może opóźnić albo odrzucić przysłany cennik? *(W sieci własnej zwykle nie;
w modelu franczyzowym i partnerskim autonomia cenowa bywa kontraktowa i system musi ją obsłużyć
albo jawnie wykluczyć.)*

A18. Jakie jest wymagane minimalne wyprzedzenie zmiany ceny wobec możliwości zametkowania towaru albo
zaktualizowania nośników? *(To jedyna prewencja przed rozjazdem nośnik kontra kasa; wszystko inne jest
reakcją po fakcie.)*

A19. Kto ma prawo ominąć to wyprzedzenie? Jak jest to audytowane? *(Ścieżka awaryjna używana
rutynowo kasuje prewencję z A18, a bez pomiaru nikt tego nie zauważy.)*

A20. Czym niesiecie cenę do klienta: metką na egzemplarzu, etykietą półkową, etykietą elektroniczną,
kilkoma naraz? *(W modelu partiowym cenę niesie metka na egzemplarzu i to zmienia całą logikę
weryfikacji.)*

A21. Gdzie jeszcze publikujecie cenę regularną poza półką: strona, aplikacja, materiał drukowany?
*(Obowiązek najkorzystniejszej ceny dotyczy każdej prawidłowo uwidocznionej ceny, nie tylko etykiety.)*

**Blok: dane, historia, granice**

A22. Skąd bierzecie miarę do liczenia ceny jednostkowej? *(Zawartość netto, masa brutto i miara
opakowania zbiorczego to trzy różne liczby; pomyłka daje błąd o rząd wielkości.)*

A23. Czy macie pozycje, dla których cena porównawcza liczy się z innej miary niż zawartość netto?
*(Dotyczy m.in. koncentratów i produktów mierzonych powierzchnią albo długością; standard wymiany
danych ma na to osobny atrybut.)*

A24. Jak wyceniacie zapas: w cenach zakupu netto czy w cenach detalicznych? *(Tylko druga odpowiedź
robi ze zmiany ceny zdarzenie księgowe wymagające rewaluacji zapasu, czyli daje temu procesowi
wyjście do finansów. Operacyjnie dominuje pierwsza, ale to jest odpowiedź do potwierdzenia
u klienta, nie założenie do przyjęcia.)*

A25. Jak długo trzymacie historię ceny? Z jaką granularnością zakresu i kanału? *(Bez ciągłej historii za wymagane
okno nie da się policzyć ceny odniesienia i system musi zablokować ogłoszenie obniżki.)*

A26. Przy wielu cenach tej samej pozycji naraz: która idzie do wyliczenia ceny odniesienia?
*(Praktyka wskazuje najniższą, ale wymaganie regulacyjne tego wprost nie rozstrzyga; odpowiedź
klienta trzeba zapisać jako świadomą decyzję, nie założenie systemu.)*

A27. Czy przy migracji z obecnego systemu przenosicie samą cenę, czy także historię cen?
*(Przeniesienie historii jest wykonalne; jeśli go nie zrobicie, przez pełne okno ustawowe nie
ogłosicie legalnie żadnej obniżki na pozycjach bez pokrycia.)*

A28. Czy przy zastąpieniu pozycji następcą historia ceny ma przechodzić? *(Brak przeniesienia zeruje
okno przy każdej zmianie opakowania i tworzy ścieżkę obejścia obowiązku przez wymianę identyfikatora.)*

A29. Co się dzieje z ceną półkową, gdy po przyjęciu towaru przyjdzie korekta faktury? *(Typowo nic:
koszt jest zamrożony przy przyjęciu. Trzeba to potwierdzić, bo od tego zależy, czy korekta faktury
jest w zakresie tego procesu, czy poza nim.)*

A30. Czy do ceny doliczacie obowiązkowe opłaty? Jeśli tak, czy są one częścią ceny regularnej? *(Zmienia
jednocześnie cenę na nośniku, cenę jednostkową, podstawę marży i cenę odniesienia.)*

A31. Przy zamówieniu z późniejszym wydaniem: obowiązuje cena z momentu zamówienia czy wydania?
*(Bez reguły każda zmiana ceny w międzyczasie kończy się sporem z klientem.)*

A32. Po jakiej cenie przyjmujecie zwrot towaru kupionego przed zmianą ceny regularnej? *(Jedyne
źródło tej odpowiedzi to historia ceny, czyli ten proces; bez reguły decyduje kasjer.)*

A33. Kto utrzymuje definicje zakresów organizacyjnych cennika? *(Zakres jest słownikiem, który
zmienia skutek każdego zdarzenia cenowego, a bywa utrzymywany przez kogoś innego niż dział cen.)*

A34. Jak mierzycie dziś zgodność ceny na nośniku z ceną w kasie: jak często, na jakiej próbie, gdzie
trafia wynik? *(Jeśli nikt nie mierzy, wskaźnik trzeba zbudować od zera razem z metodyką próby,
a to osobny zakres prac.)*

A35. W ilu walutach działacie? Czy reguły zaokrągleń są takie same w każdej? *(Waluta jest dodatkową
osią cennika i osobnym zestawem reguł.)*

**Blok: uzupełnienia po recenzji v0.4** [PROP+ 19.08, recenzja v0.4]

A36. Jak wykrywacie, że zmiana ceny poszła na złą grupę lokalizacji? *(Błąd zakresu nie wygląda na
błąd: obie ceny działają, tylko w złych miejscach, więc ani test terminowości, ani reklamacja klienta
go nie złapią. Jeśli odpowiedź brzmi „nie wykrywamy", to jest to ryzyko do zarejestrowania.)*

A37. W którym momencie zaokrąglacie przy przeliczeniu netto na brutto: na pozycji czy na dokumencie
sprzedaży? *(To jest inna sprawa niż zaokrąglenie wyniku narzutu z A8. Tu chodzi o konwersję
podatkową tej samej ceny; grosz różnicy między dokumentem sprzedaży a raportem bierze się właśnie
stąd i wychodzi przy pierwszej rekoncyliacji, a nie w UAT.)*

A38. Co dzieje się z cenami, gdy lokalizacja zmienia region, typ albo grupę cenową: są dziedziczone
z nowego zakresu czy przeliczane? *(Przy cennikach wielopoziomowych ten moment dotyka jednocześnie
hierarchii, historii i replikacji. Osobno trzeba ustalić, czy historia ceny idzie za lokalizacją,
czy zostaje przy zakresie, bo od tego zależy, czy po przeniesieniu da się policzyć cenę
odniesienia.)*

A39. Jak szybko zmiana ceny jest widoczna na stronie, w aplikacji i u pośredników sprzedaży?
*(Obowiązek uwidocznienia dotyczy każdego miejsca publikacji ceny, nie tylko półki. Nieświeży cache
albo opóźniony feed pokazuje starą cenę większej liczbie klientów naraz niż etykieta z martwą
baterią, a wygląda na działający.)*

A40. Czy rejestrujecie przypadki rozbieżności ceny między nośnikiem a kasą jako zdarzenia, czy
rozstrzygacie je tylko przy kasie? *(Bez rejestru wskaźnik dokładności cenowej da się policzyć
wyłącznie z próby audytowej, a reklamacja klienta zostaje jedynym mechanizmem wykrywania.)*

A41. Ile czasu ma lokalizacja na wymianę cenówek i metek po wejściu ceny w życie, i co się dzieje
po przekroczeniu tego czasu? *(Standard dopuszcza, żeby cena weszła w kasie przed wymianą nośników,
ale wyłącznie pod dwoma warunkami: system wie, które nośniki czekają, i istnieje maksymalny czas
nadrobienia. Rejestr bez zegara zamienia zaległość w stałe tło, którego nikt nie goni.)*

A42. Czy sprzedajecie porcje wydzielone z większego opakowania, i czy cena porcji wynika z ceny
tego opakowania? *(Reguła standardu: pozycja ma jedną cenę, która może być dzielona, a nie dwie
niezależne ceny. Litr z bańki piętnastolitrowej to jedna piętnasta ceny bańki. Jeśli u klienta cena
porcji jest wpisywana ręcznie, to zmiana ceny opakowania jej nie ruszy i rozjazd narasta po cichu.)*

### B. Do legacy (obserwowalne zachowanie obecnego systemu)

B1. Skąd wiecie, że cennik dojechał do wszystkich kas i kanałów? *(Odróżnia raport wysyłki od
potwierdzenia odbioru, czyli „cena obowiązuje" od „cena obowiązuje wszędzie".)*

B2. Czy start ceny jest blokowany przy braku kompletu potwierdzeń, czy tylko raportowany?
*(Rozstrzyga, czy niepełna dystrybucja jest incydentem widocznym, czy cichym.)*

B3. Ile trwa propagacja pełnego cennika, a ile samej delty, przy Waszej liczbie lokalizacji
i końcówek? *(Bez tej liczby warunek „potwierdzenie przed startem" jest życzeniem: przechodzi UAT na
kilkunastu sklepach i przewraca się przy pełnej skali.)*

B4. Czy kasa dostaje tylko cennik bieżący, czy także cenniki przyszłe z datą wejścia do przodu?
*(Jeśli tylko bieżący, lokalizacja odcięta od sieci przegapi zaplanowaną zmianę i wróci online już
po terminie.)*

B5. Po jakim czasie kasa przechodzi w tryb awaryjny i na jakim cenniku wtedy pracuje? *(Determinuje,
jak stara cena może zostać naliczona i przez jak długo.)*

B6. Kiedy kasa próbuje wrócić online? *(W części implementacji próba następuje wyłącznie na początku
transakcji, więc kasa bez ruchu potrafi zostać offline dowolnie długo.)* [LIT: dokumentacja publiczna
Microsoft Dynamics 365 Commerce, „Offline point of sale (POS) functionality"]

B7. Zaległe zmiany po powrocie łączności aplikują się w kolejności odbioru czy momentu wejścia
w życie? *(Kolejność odbioru oznacza, że lokalizacja może wylądować na cenie już wycofanej.)*

B8. Czy da się dla pojedynczej transakcji odtworzyć, z jakiej wersji cennika pochodzi zastosowana
cena? *(Bez tego rekoncyliacja marży pokazuje różnicę, której nie da się wyjaśnić.)*

B9. Gdy na półce leży ten sam produkt w dwóch cenach z dwóch dostaw: czym kasa rozstrzyga, którą cenę
naliczyć? *(Kasa skanuje identyfikator pozycji, nie partii. Odpowiedź decyduje, czy obowiązek ceny
najkorzystniejszej da się w tym modelu w ogóle spełnić.)*

B10. Co system robi, gdy cena na metce jest niższa niż cena wyliczona przy kasie? *(Weryfikuje
zachowanie wobec obowiązku ceny najkorzystniejszej; „kasjer poprawia ręcznie" to też odpowiedź
i trzeba ją zapisać.)*

B11. Jak w systemie ustawiony jest typ narzutu: od kosztu czy od ceny detalicznej? *(Weryfikacja
odpowiedzi z A7; to pytanie o konfigurację, nie o deklarację.)*

B12. Co się dzieje z ceną półkową po korekcie faktury zakupowej? *(Weryfikuje A29. Jeśli system
przelicza, to macie inny model niż zakładany i trzeba przeprojektować granicę z zakupami.)*

B13. Gdzie system trzyma historię ceny? Z jaką granularnością zakresu i przez ile czasu? *(To
inwentaryzacja tego, co da się przenieść przy migracji, patrz A27.)*

B14. Jak system zachowuje się przy zmianie stawki podatku od zadanej daty: przelicza brutto, netto,
czy nic? *(Ujawnia, co jest faktycznym źródłem prawdy w cenniku, niezależnie od deklaracji.)*

B15. Czy zmiana klasyfikacji podatkowej pozycji przechodzi tę samą ścieżkę zatwierdzania co zmiana
ceny? *(Jeśli nie, istnieje ścieżka zmiany ceny brutto omijająca całą kontrolę cenową.)*

B16. Jak wykrywacie, że nośnik pokazuje cenę inną niż kasa? Po jakim czasie od zmiany to widać? *(Odróżnia
detekcję systemową od reklamacji klienta jako mechanizmu wykrywania.)*

B17. Czy system nośników elektronicznych wymaga potwierdzenia wyświetlenia per etykieta? Czy
monitoruje zasilanie etykiet? *(Etykieta e-ink zachowuje ostatnią treść po utracie zasilania, więc wygląda na sprawną,
pokazując starą cenę.)*

B18. Jak utrzymujecie przypisanie nośnika do pozycji? Co się z tym przypisaniem dzieje po zmianie ekspozycji?
*(Cennik i kasa mogą być poprawne, a błędna jest mapa nośnik do pozycji; żaden test cennika tego nie
wykryje.)*

B19. Czy system blokuje cenę zero, ujemną i pustą na pozycji dopuszczonej do sprzedaży? *(Pozycji
o cenie zerowej nie da się ująć na dokumencie sprzedaży, więc cennik, który ją dopuszcza, produkuje
pozycje niesprzedawalne, a defekt wychodzi dopiero na sklepie.)*

B20. Jak rejestrujecie wydanie towaru bez opłaty, na przykład gratis albo próbkę? *(Jeśli odpowiedź
brzmi „sprzedaż za grosz" albo „sprzedaż za zero", to wydanie jest modelowane jako sprzedaż i trzeba
sprawdzić, co z tego wynika dla dokumentu sprzedaży i dla podatku.)*

B21. Jaka jest procedura, gdy pozycja jest w sprzedaży, a nie ma ceny? Czy jest zapisana?
*(W metrologii prawnej pozycja spoza bazy nie jest błędem sama w sobie, ale staje się nim, gdy cena
zastosowana okaże się niespójna z zadeklarowaną polityką.)*

B22. Jak wygląda wycofanie błędnego cennika? Co z dokumentami sprzedaży wystawionymi w międzyczasie?
*(Rollback bez odpowiedzi na drugą część zostawia rozjazd między systemem a dokumentami sprzedaży.)*

B23. Czy do cennika trafiają ceny z synchronizacji danych od dostawców, a jeśli tak, to które typy?
*(Cena sugerowana przez producenta podpięta jako regularna oznacza oddanie polityki cenowej
dostawcy.)*

B24. Czy zdarzało się, że zmiana ceny nie weszła w życie, mimo że operator widział ją jako
wprowadzoną? *(Systemy z progiem tolerancji wyjątków zostawiają takie zdarzenie w statusie roboczym
i nie wysyłają go do kas.)*

B25. (graniczne, docelowy właściciel: ORPR-SAL-01) W którym momencie cena jest zamrażana
w transakcji: przy zarejestrowaniu pozycji czy przy podsumowaniu? *(Zamrożenie przy rejestracji daje
różne ceny w jednym paragonie przy aktywacji w trakcie; przy podsumowaniu daje cenę inną niż
wyświetlana przy skanowaniu.)*

B26. Jak długo strona, aplikacja i feed do pośredników mogą pokazywać starą cenę po zmianie
w cenniku? Czy ktoś to mierzy? *(Weryfikuje A39 po stronie obecnego systemu. Cache i CDN mają własne
okno ważności, niezależne od replikacji do kas.)* [PROP+ 19.08, recenzja v0.4; R: PRICE-005]

B27. Czy system zapisuje przypadek rozbieżności ceny jako zdarzenie z dowodem uwidocznionej oferty,
czy tylko rozstrzyga go przy kasie? *(Weryfikuje A40. Rozstrzygnięcie bez zapisu nie zostawia danych
do wskaźnika ani do analizy przyczyny.)* [PROP+ 19.08, recenzja v0.4]

### C. Do vendora

Przy każdym pytaniu wymagamy wskazania miejsca w dokumentacji i informacji, czy rzecz jest
konfigurowalna bez programisty. „Tak, obsługujemy" bez lokatora nie jest odpowiedzią.

C1. Czy system obsługuje oba kierunki przepływu ceny: cennik centralny nakładany na lokalizacje ORAZ
cennik lokalny z centralną nakładką na wybrane pozycje? *(Drugi kierunek jest rzadziej wspierany
natywnie, a bez niego sieci franczyzowe i partnerskie są nieobsługiwalne.)*

C2. Czy w modelu odwróconym nakładka centralna nadpisuje wyłącznie pozycje nią objęte, zostawiając
resztę cennika lokalnego nietkniętą? *(Nadpisanie całego cennika zamiast listy pozycji kasuje
autonomię lokalizacji przy każdej akcji centralnej.)*

C3. Czy system obsługuje cenę per partia, czy tylko jedną cenę na pozycję? *(Weryfikuje A2. Jeśli
tylko jedną, a klient pracuje na partiach, to jest luka funkcjonalna, nie kwestia konfiguracji.)*

C4. Jeśli tak: jak rozstrzyga, którą cenę naliczyć przy skanowaniu identyfikatora pozycji?
*(Weryfikuje B9 po stronie nowego systemu; od tego zależy zgodność z obowiązkiem ceny
najkorzystniejszej.)*

C5. Ile poziomów cennika obsługuje? Jak rozstrzyga, który wygrywa? *(Reguła zaszyta w kodzie oznacza,
że każda zmiana polityki cenowej jest zmianą wersji systemu.)*

C6. Które metody uspójnienia ceny przy dostawie obsługuje: marża od średniej, od ostatniego zakupu,
metody odrzucające skrajne? *(Weryfikuje A6; systemy różnią się dokładnie tutaj.)*

C7. Czy zamraża koszt w momencie przyjęcia? Czy korekta faktury po przyjęciu może wywołać
przeliczenie ceny? *(Weryfikuje A29 i B12; niezamierzone przeliczenie zmienia ceny na półce bez
zdarzenia cenowego.)*

C8. Czy cena może różnić się per kanał? Czy kanał jest wymiarem cennika, czy osobnym cennikiem?
*(Determinuje, czy omnichannel jest konfiguracją, czy duplikacją danych.)*

C9. Czy przy odbiorze w lokalizacji obowiązuje cena kanału zamówienia? *(Weryfikuje A31 i typową
regułę click and collect.)*

C10. Czy replikacja jest idempotentna i uporządkowana po momencie wejścia w życie, a nie po momencie
odbioru? *(Jedyne zabezpieczenie przed wylądowaniem na cenie wycofanej po dłuższej awarii łącza.)*

C11. Czy wysyła do kas cenniki przyszłe, czy tylko bieżący? *(Weryfikuje B4.)*

C12. Czy wymaga potwierdzenia odbioru per kasa i kanał? Czy potrafi zablokować wejście ceny w życie
przy braku kompletu potwierdzeń? *(Rozstrzyga, czy niepełna dystrybucja jest błędem, czy informacją.)*

C13. Jaki jest zmierzony czas propagacji przy skali z B3? *(Prosimy o liczbę z wdrożenia
porównywalnej skali, nie o deklarację możliwości.)*

C14. Czy moment obowiązywania jest rozstrzygany wobec strefy czasowej i doby biznesowej lokalizacji?
*(Bez tego „od 00:00" jest nierozstrzygalne w sieci wielostrefowej.)*

C15. Co się dzieje z zadaniem aktywacji zaplanowanym na godzinę, która przy zmianie czasu występuje
dwa razy albo wcale? *(Aktywacja odpali się podwójnie albo wcale; dwa razy w roku i prawie nigdy
w planie testów.)*

C16. Czy wymusza minimalne wyprzedzenie? Czy ma odrębną, audytowaną ścieżkę awaryjną? *(Weryfikuje A18
i A19.)*

C17. Czy cena awaryjna nadpisuje wcześniejszą według kolejności odbioru, czy momentu wejścia w życie?
*(W udokumentowanej implementacji decyduje kolejność odbioru, przy jednoczesnym istnieniu osobnego
mechanizmu kontroli konfliktów, więc zachowanie zależy od konfiguracji.)* [LIT: Oracle Retail Price
Management, „Price Change Overview" oraz Operations Guide 16.0, rozdz. Conflict Checking]

C18. Które konflikty wykrywa PRZED zatwierdzeniem: duplikat na ten sam dzień, cena ujemna,
niezgodność jednostki miary, cena porcji niewynikająca z ceny opakowania zbiorczego? *(Kontrola po zatwierdzeniu
jest raportem, przed zatwierdzeniem jest bramką.)*

C19. Które z tych reguł da się wyłączyć konfiguracją? *(Reguła wyłączalna zostanie wyłączona przy
pierwszym pilnym wdrożeniu; warto wiedzieć która.)*

C20. Co robi, gdy udział pozycji z konfliktem przekroczy próg tolerancji? Co wtedy widzi operator?
*(W części implementacji zdarzenie zostaje w statusie roboczym i nigdy nie trafia do kas.)*

C21. Czy utrzymuje historię ceny w rozdzielczości wymaganej do wyliczenia ceny odniesienia? Czy
wystawia ją do modułu promocji? *(Bez tego moduł promocji nie ma z czego policzyć komunikatu o obniżce.)*
[R: PRICE-001..003]

C22. Przy wielu cenach naraz: którą bierze do ceny odniesienia? Czy da się to skonfigurować?
*(Wymaganie regulacyjne tego wprost nie rozstrzyga, więc zachowanie systemu musi być jawne
i świadomie wybrane.)*

C23. Czy potrafi zaimportować historię cen z systemu poprzedniego? W jakiej granularności zakresu?
*(Weryfikuje wykonalność A27; import per lokalizacja do modelu per grupa jednostek wymaga jawnej
reguły mapowania.)*

C24. Czy przenosi historię ceny na pozycję następcę? *(Weryfikuje A28.)*

C25. Czy liczy cenę jednostkową? Czy rozróżnia zawartość netto od miary porównawczej? *(Brak rozróżnienia
oznacza błędną cenę jednostkową na koncentratach.)*

C26. Czy obsługuje pozycje wyłączone z obowiązku ceny jednostkowej? Czy zapisuje tę klasyfikację?
*(Bez tego albo wymusza cenę jednostkową tam, gdzie nie trzeba, albo jej nie pilnuje tam, gdzie
trzeba.)* [R: PRICE-004]

C27. Czy stawka podatku jest wersjonowana niezależnie od ceny i wyznaczana z wersji obowiązującej
w chwili sprzedaży, ze wskazaniem źródła? *(Dwa niezależne strumienie replikacji trzeba uzgodnić co
do granicy doby.)* [R: FISC-020]

C28. Czy pozwala oznaczyć towar jako niepełnowartościowy i uzależnić od tej flagi prawo zejścia
poniżej kosztu? *(Weryfikuje A13; bez flagi obniżka poniżej kosztu przechodzi jak każda inna.)*

C29. Czego pilnuje przy zatwierdzeniu ceny: progu marży, odchylenia od ceny centralnej, czy niczego?
*(Weryfikuje A12; w większości sieci to jedyna kontrola, jaka istnieje.)*

C30. Czy rozróżnia rolę wprowadzającego i zatwierdzającego cennik lokalny, z konfigurowalnym progiem?
*(Weryfikuje A11.)*

C31. Czy ma ścieżkę wycofania błędnego cennika z określonym stanem docelowym, zakresem i momentem?
*(Rollback improwizowany na produkcji jest gorszy niż błędna cena.)*

C32. Czy raportuje mierzalną zgodność ceny na nośniku z ceną w kasie, czy tylko wysyła dane do
nośników? *(Odróżnia system, który wie, co jest na półce, od systemu, który wie, co wysłał.)*

C33. Czy modeluje cenę regularną jako obiekt odrębny i wersjonowany wobec reguł promocyjnych?
*(Uznane modele danych rozdzielają utrzymanie ceny od derywacji w transakcji; zlanie ich uniemożliwia
odtworzenie ceny regularnej po fakcie.)* [LIT: ARTS ODM 7.3, `ItemSellingPrices`, widoki 01300/01400]

C34. Czy cennik może wyprodukować pozycję o cenie zero? Jeśli tak, czy system blokuje ją na etapie
zatwierdzania, czy dopiero przy sprzedaży? *(Blokada dopiero przy sprzedaży oznacza, że błąd
wychodzi na sklepie, przy kliencie, a nie u operatora cennika.)*

C35. Jak system modeluje wydanie towaru bez opłaty: jako sprzedaż z ceną minimalną, czy jako odrębne
zdarzenie wydania bez ceny? *(Pierwsze zaśmieca historię ceny i podstawę marży wartościami, które nie
są ceną; drugie wymaga osobnego typu dokumentu.)*

C36. Czy publikacja ceny do kanałów cyfrowych jest potwierdzana, czy system tylko wypycha feed?
Jakie opóźnienie deklaruje osobno dla karty produktu, strony kategorii i pośrednika? *(Ta sama
różnica co między „wysłano" a „obowiązuje" w kasach, tylko w kanale cyfrowym nikt jej zwykle nie
mierzy.)* [PROP+ 19.08, recenzja v0.4; R: PRICE-005]

C37. Czy moment zaokrąglenia przy przeliczeniu netto na brutto jest konfigurowalny: na pozycji czy
na dokumencie? Jak system postępuje z groszem różnicy między dokumentem sprzedaży a raportem?
*(Weryfikuje A37. Zachowanie zaszyte w kodzie oznacza, że rekoncyliacja marży będzie miała stały,
niewyjaśnialny błąd.)* [PROP+ 19.08, recenzja v0.4; R: FISC-020]

C38. Czy system utrzymuje listę nośników czekających na wymianę, z momentem rozpoczęcia oczekiwania,
i czy potrafi zaalarmować po przekroczeniu zadanego czasu nadrobienia? *(Weryfikuje A41. Bez zegara
lista zaległości jest rejestrem, nie kontrolą.)* [AUT-R 19.08, tura 6]

C39. Czy cena porcji wydzielonej z opakowania zbiorczego jest wyliczana z ceny tego opakowania, czy
wpisywana jako osobna pozycja cennika? *(Weryfikuje A42. Osobna pozycja oznacza, że zmiana ceny
opakowania nie zmienia ceny porcji i rozjazd narasta bez żadnego zdarzenia.)* [AUT-R 19.08, tura 6]

### Czerwone flagi (wychodzą typowo dopiero w UAT lub po starcie)

Każda flaga ma przypisane pytanie, którym się ją wykrywa.

F1. **„Wysłano" mylone z „obowiązuje".** System raportuje wysyłkę cennika, nie potwierdzenie odbioru
per kasa i kanał. Cena formalnie obowiązuje, faktycznie nie wszędzie. Pytania: B1, B2, C12. [PROP+ 19.08]

F2. **Kolejność odbioru wygrywa z momentem obowiązywania.** Po powrocie łączności zaległe zmiany
aplikują się w kolejności przyjścia i lokalizacja ląduje na cenie już wycofanej. Pytania: B7, C10,
C17. [LIT: Oracle Retail Price Management, „Price Change Overview" oraz Operations Guide 16.0,
rozdz. Conflict Checking; zachowanie zależne od konfiguracji]

F3. **Rozjazd nośnik kontra kasa, w modelu partiowym WBUDOWANY.** W modelu jednocenowym rozjazd jest
kwestią opóźnienia. W modelu partiowym jest strukturalny: metka niesie cenę egzemplarza, a kasa
skanuje identyfikator pozycji, więc dwa egzemplarze tego samego produktu mają na półce legalnie różne
ceny, a kasa musi którąś wybrać. Każdy wybór inny niż najkorzystniejszy dla konsumenta jest
naruszeniem [R: PRICE-005]. Skala rozjazdu w modelu jednocenowym też nie jest teoretyczna:
w publicznym badaniu terenowym 2023 błędna cena przy kasie wystąpiła w 3,7 % pozycji w sieciach
krajowych i około 10 % w sklepach mniejszych, przy czym 70-71 % błędów było na niekorzyść konsumenta
(wartości przepisane z publikacji, nie wyniki działania; zgodność z notatką źródłową sprawdzona
19.08.2026)
[LIT: Scottish Trading Standards / SCOTSS 2023, około 9 000 pozycji przy kasie]. Asymetria kierunku
jest zgodna z hipotezą „baza aktualizuje się przed nośnikiem", ale sama danych nie rozstrzyga: ten
sam rozkład wychodzi, gdy w okresie było więcej podwyżek niż obniżek [HIP]. Pytania: A2, A20, B9,
B10, B16, C4, C32.

F4. **Granica doby, strefa czasowa i zmiana czasu.** Aktywacja zaplanowana na godzinę, która przy
zmianie czasu występuje dwa razy albo wcale. Osobno: cena aktywowana na dobę kalendarzową
w lokalizacji pracującej przez północ wchodzi w środek poprzedniego dnia sprzedażowego. Pytania: A14,
A15, A16, C14, C15. [HIP na skali, mechanizm dobrze umocowany]

F5. **Transakcja przez granicę zmiany ceny.** Pozycje zarejestrowane przed i po aktywacji dostają
różne ceny w jednym dokumencie; przy zamówieniach i dokumentach zawieszonych okno rośnie z sekund do
dni. Pytania: A31, B25. Wykonanie należy do SAL-01.
[LIT: ARTS ODM 7.3; lokator do uzupełnienia, do potwierdzenia]

F6. **Reguła zaokrąglenia zdefiniowana po fakcie.** Pozycje dostają surową cenę z narzutu; naprawa
wymaga masowej rewaluacji. Wychodzi przy audycie marży, 1-3 miesiące po starcie. Pytania: A8.
[LIT: Oracle Retail, „Pricing Pre-Requisites"]

F7. **Narzut liczony od złej podstawy.** Pomylenie narzutu od kosztu z narzutem od ceny detalicznej;
błąd niewidoczny na pojedynczej pozycji, widoczny na rozkładzie marży w kategorii. Pytania: A7, B11.
[wynika z arytmetyki pokazanej w A7; nie jest twierdzeniem wymagającym źródła zewnętrznego]

F8. **Cena jednostkowa z błędnej miary.** Masa brutto zamiast zawartości netto, opakowanie zbiorcze
zamiast jednostki sprzedaży, brak konwersji jednostek, brak miary porównawczej dla koncentratów.
W badaniu 2023 błędna albo brakująca cena jednostkowa wystąpiła w 6,5 % pozycji w sieciach krajowych
i 8,6 % w mniejszych; uwaga metodyczna: wskaźnik łączy błąd z brakiem i liczony jest na innej
populacji niż wskaźnik z F3, więc obu nie należy zestawiać wprost. Wychodzi w kontroli, nie w UAT.
Pytania: A22, A23, C25, C26. [LIT: SCOTSS 2023; GS1 GDSN]

F9. **Cicha zmiana przez stawkę podatku.** Zmiana stawki albo przeklasyfikowanie pozycji do innej
grupy podatkowej jest zdarzeniem cenowym, choć nie wygląda jak zmiana ceny, więc omija ścieżkę
zatwierdzania. Pytania: B14, B15, C27. [R: FISC-020; LIT: ARTS ODM 7.3]

F10. **Nośnik elektroniczny z martwą baterią.** Etykieta e-ink zachowuje ostatnią treść po utracie
zasilania, więc wygląda na sprawną, pokazując starą cenę. Detekcja wymaga monitoringu i potwierdzeń
wyświetlenia. Pytania: A20, B17, C32. [HIP: mechanizm z technologii, brak publicznego
badania ilościowego]

F11. **Nośnik przypisany do złego produktu.** Po zmianie ekspozycji albo wymianie etykiety; cennik
i kasa poprawne, błędna mapa nośnik do pozycji. Pytania: B18. [LIT: patenty US 6,256,615 i US 5,382,779
(numery w formacie patentów udzielonych, nie zgłoszeń); istnienie patentów dowodzi, że problem był
wart rozwiązania, nie jego rozpowszechnienia]

F12. **Błąd zakresu, nie czasu.** Cena zmieniona dla złej grupy jednostek albo złego kanału: część
sieci ma nową cenę, część starą, i nikt nie zgłasza, bo obie „działają". Pytania: A4, A33, A36, A38, C5, C8.
[LIT: ARTS ODM 7.3, `BusinessUnitGroup`, `BusinessUnitGroupItem`]

F13. **Erozja lead time.** Ścieżka awaryjna używana rutynowo, bo szybsza, co kasuje jedyną prewencję
przed F3. Miara ostrzegawcza w polu 13. Pytania: A18, A19, C16. [PROP+ 19.08]

F14. **Cena sugerowana producenta podpięta jako regularna.** Dane B2B niosą cenę sugerowaną pod
osobnym kodem; podpięcie jej pod cennik oddaje politykę cenową dostawcy. Pytania: B23. [LIT: GS1 GDSN,
kod `RETAIL_PRICE`]

F15. **Zdarzenie cenowe, które po cichu nie weszło.** Przy przekroczeniu progu tolerancji wyjątków
zostaje w statusie roboczym, a operator widzi je jako wprowadzone. Pytania: B24, C20.
[LIT: Oracle Retail Price Management; lokator do uzupełnienia, do potwierdzenia]

F16. **Start z pustą historią cen.** Po uruchomieniu systemu nie da się zgodnie z prawem ogłosić
obniżki przez pełne okno ustawowe. Uwaga kalibracyjna: przeniesienie historii jest wykonalne
i zwykle się je robi [AUT-R 19.08], więc to jest **zaniedbanie projektowe, nie bariera techniczna**.
Pytania: A25, A27, C23. [R: PRICE-001]

F17. **Historia gubiona przy zmianie identyfikatora pozycji.** Zmiana opakowania zeruje okno ceny
odniesienia dla towaru, który fizycznie się nie zmienił, i tworzy ścieżkę obejścia obowiązku.
Pytania: A28, C24. [PROP+ 19.08; R: PRICE-001]

F18. **Brak jakiejkolwiek kontroli przy zmianie ceny.** Nie chodzi o brak rozdziału ról, bo tego
w większości sieci nie ma i to jest normalne. Chodzi o sytuację, w której nie ma ANI rozdziału ról,
ANI parametru pilnowanego przez system. Wtedy kontroli nie ma żadnej. Pytania: A11, A12, C29, C30.
Podstawa faktograficzna: w większości sieci drugiej pary oczu nie ma, a kontrolę pełni parametr pilnowany przez system [AUT-R 19.08].
Sformułowanie flagi: [PROP+ 19.08]

F19. **Warunek „potwierdzenie przed startem" niewykonalny przy pełnej skali.** Przechodzi UAT na
kilkunastu lokalizacjach i przewraca się przy pełnym wdrożeniu, bo okno propagacji nie mieści się
w oknie operacyjnym. Pytania: B3, C13. [PROP+ 19.08]

F20. **Cennik przepuszcza cenę zero jako cenę sprzedaży.** Pozycja o cenie zerowej nie da się ująć
na dokumencie sprzedaży, więc cennik, który ją dopuszcza, produkuje pozycje niesprzedawalne. Defekt
wychodzi dopiero przy pierwszej próbie sprzedaży takiej pozycji, czyli na sklepie, nie w cenniku.
Osobno i częściej: **wydanie bez opłaty modelowane jako sprzedaż za zero** zamiast jako odrębne
zdarzenie wydania. Pytania: pierwszy człon B19, C34; drugi człon B20, C35. [AUT-R 19.08]

F21. **Kierunek przepływu ceny wzięty z założenia.** Analityk zakłada model centralny, bo taki widział
ostatnio, a klient ma model odwrócony (cennik lokalny z nakładką centralną). Wychodzi dopiero przy
projektowaniu uprawnień albo przy pierwszej akcji centralnej, która skasuje ceny lokalne. Pytania:
A1, A9, C1, C2. Podstawa faktograficzna: kierunek przepływu ceny odwraca się między modelami operacyjnymi [AUT-R 19.08].
Sformułowanie flagi: [PROP+ 19.08]

F22. **Korekta faktury przeliczająca cenę półkową.** Koszt ma być zamrożony przy przyjęciu. Jeśli
system przelicza po korekcie, ceny na półce zmieniają się bez zdarzenia cenowego i bez wiedzy
handlu. Pytania: A29, B12, C7. Podstawa faktograficzna: koszt jest zamrażany w momencie przyjęcia towaru na stan [AUT-R 19.08].
Sformułowanie flagi: [PROP+ 19.08]

F23. **Marża liczona od kosztu, który już nie obowiązuje.** Odwrotna strona F22 i konsekwencja
poprawnego zamrożenia: po korekcie faktury koszt wyceny i koszt rzeczywisty rozjeżdżają się trwale,
a raport marży pokazuje wartość liczoną od zamrożonego. To nie jest błąd systemu, tylko właściwość,
o której trzeba wiedzieć przy czytaniu raportów. Pytania: A29, B12. [PROP+ 19.08]

F24. **Metoda uspójnienia ceny nieuzgodniona z możliwościami systemu.** Klient liczy marżę metodą
odrzucającą skrajne ceny zakupu, a system umie tylko od ostatniej dostawy. Wychodzi przy pierwszym
imporcie danych historycznych albo przy pierwszym porównaniu marży z legacy. Pytania: A6, C6.
Podstawa faktograficzna: katalog metod uspójnienia ceny przy dostawie [AUT-R 19.08].
Sformułowanie flagi: [PROP+ 19.08]

F25. **Nieświeża cena w kanale cyfrowym.** Strona, aplikacja albo feed do pośrednika pokazuje cenę
sprzed zmiany, bo cache, CDN i harmonogram feedu mają własne okna ważności, niezależne od replikacji
do kas. Mechanizm jest ten sam co przy etykiecie z martwą baterią: nośnik wygląda na sprawny
i pokazuje starą cenę, tylko liczba klientów widzących błąd jest o rzędy wielkości większa.
Karta wymaga, żeby lista nośników obejmowała wszystkie miejsca publikacji ceny, a cała dotychczasowa
maszyneria detekcyjna dotyczyła wyłącznie półki. Pytania: A21, A39, B26, C36.
[PROP+ 19.08, recenzja v0.4; R: PRICE-005]

F26. **Grosz na konwersji netto na brutto.** Cena trzymana w jednej reprezentacji, pokazywana
w drugiej; zaokrąglenie raz na pozycji, raz na dokumencie. Rozjazd jest o jeden grosz i dlatego
nie wychodzi w UAT, tylko przy pierwszej rekoncyliacji dokumentów sprzedaży z raportem, i wtedy
wygląda na błąd raportu. Odrębne od F6, które dotyczy zaokrąglenia wyniku narzutu. Wywala się
najmocniej przy zmianie stawki podatku, która jest zdarzeniem cenowym. Pytania: A37, B14, C37.
[PROP+ 19.08, recenzja v0.4; R: FISC-020]

F27. **Lista zaległych nośników bez zegara.** Sieć rejestruje, które cenówki czekają na wymianę,
i uznaje sprawę za załatwioną. Bez maksymalnego czasu nadrobienia zaległość staje się stałym tłem:
zawsze jakaś liczba nośników czeka, nikt nie wie, czy to trzy godziny czy trzy tygodnie, i nic nie
świeci na czerwono. Rejestr bez zegara jest dowodem, że wiedzieliśmy, a nie kontrolą. Pytania: A18,
A41, C38. Podstawa faktograficzna: rejestr plus zegar, nie sam rejestr [AUT-R 19.08, tura 6].
Sformułowanie flagi: [PROP+ 19.08, recenzja v0.4]

F28. **Cena porcji odklejona od ceny opakowania.** Porcja wydzielona z opakowania zbiorczego dostaje
własną pozycję cennika zamiast być liczona z ceny opakowania. Zmiana ceny opakowania jej nie rusza,
więc rozjazd narasta po cichu i wychodzi dopiero przy inwentaryzacji albo przy porównaniu marży.
Pytania: A42, C39. Podstawa faktograficzna: pozycja ma jedną cenę, która może być dzielona; nie ma
drugiej, niezależnej ceny dla porcji [AUT-R 19.08, tura 6].
Sformułowanie flagi: [PROP+ 19.08, recenzja v0.4]
