# Crosswalk ORPR ↔ uznane frameworki (APQC / ARTS-NRF / GS1)

Artefakt współdzielony standardu. Cel: dać każdej karcie procesu kotwice do uznanych
frameworków (dowód kompletności + wspólny język z vendorami), których pojedynczy analityk
nie nosi w głowie. Karty linkują tu, nie kopiują (P13).

## Jak używać
- Każdy proces ORPR dostaje wiersze mapowania na APQC, ARTS/NRF i GS1 tam, gdzie istnieją.
- Klasa pewności przy każdym mapowaniu: [P-wysoka] odczytane ze źródła, [P-średnia] prawdopodobne,
  [do potwierdzenia] wymaga dostępu do płatnego/oficjalnego wydania.
- Freeze: przed wydaniem publicznym każda kotwica [P-*] weryfikowana u źródła i podnoszona do
  [zweryfikowane] albo oznaczana jako GAP.

## Źródła frameworków
- APQC PCF Cross-Industry v7.4 (PDF oficjalny) — ID i nazwy elementów. [P-wysoka]
- APQC PCF Retail v6.1.1 — osobne wydanie, ID promocyjne w wersji retail [do potwierdzenia; paywall].
- ARTS / NRF (Association for Retail Technology Standards) — Operational Data Model + IXRetail
  Dictionary v2.1 — encje modelu danych. [P-wysoka]
- GS1 — Global Coupon Number (GCN), Digital Coupon Standard, GS1 DataBar Coupon, GDSN. [P-wysoka]

---

## ORPR-CAT-03 Promotion-to-POS (value stream „Promocja")

### APQC PCF (Cross-Industry v7.4)
| ORPR | APQC element | ID | Pewność |
|---|---|---|---|
| definicja i zarządzanie promocją | Develop and manage promotional activities | 20010 (3.3.4) | [P-wysoka] |
| publikacja/egzekucja w POS | Execute promotional activities | 10169 (3.3.4.5) | [P-wysoka] |
| raportowanie skuteczności (następnik) | Evaluate promotional performance metrics | 10170 (3.3.4.6) | [P-wysoka] |
| korekta polityki | Refine promotional activities | 10171 (3.3.4.7) | [P-wysoka] |
| cennik/marżownik jako podłoże | Define pricing strategy / guidelines for discounting | 10123 / 10124 (3.2.2) | [P-wysoka] |
| zarządzanie cennikiem | Develop and manage pricing | 20593 (3.3.3) | [P-wysoka] |
| kontrakt/rekompensata producenta | Define trade programs and funding options | 11521 (3.4.2.5) | [P-wysoka] |
| gazetka/kalendarz akcji | Develop promotional/category management calendars | 11522 (3.4.2.10) | [P-wysoka] |

### ARTS / NRF (Operational Data Model, IXRetail Dictionary v2.1)
| ORPR | Encja ARTS | Rola | Pewność |
|---|---|---|---|
| reguła promocji | PriceDerivationRule / ItemPriceDerivationRule | rdzeń reguły cenowo-promocyjnej | [P-wysoka] |
| forma korzyści / modyfikator | RetailPriceModifier | jak modyfikuje cenę | [P-wysoka] |
| promocja pakietowa / mix&match | MixAndMatchPriceDerivationRule | bundle, X+Y | [P-wysoka] |
| okno czasowe | TemporaryPriceChange / PermanentPriceChange | ograniczenie czasowe | [P-wysoka] |
| kwalifikacja (osobna oś!) | *PriceDerivationRuleEligibility (Item/Customer/MerchandiseStructure/Season) | kto/co się kwalifikuje | [P-wysoka] |
| lojalność | CustomerLoyaltyAccount / …Redemption | warunkowanie i realizacja | [P-wysoka] |
| rabat pracowniczy | EmployeeMembershipDiscountGroup | szczególny rodzaj | [P-wysoka] |
| kupon | CouponHandlingRule / ManufacturerCouponFamily | kupon detalisty vs producenta | [P-wysoka] |

Wniosek modelowy [P-wysoka **dla trzech pierwszych bytów**]: promocja to nie „krok procesu", lecz
reguła + modyfikator + kwalifikacja. To uzasadnia traktowanie ich jako osobnych, wersjonowanych,
audytowalnych obiektów (wymagane też przez PRICE-001: historia ceny odniesienia).

**Rozstrzyganie konfliktów jest wymaganiem ORPR, nie odczytem z ARTS** [PROP+ 19.08, naprawa po
recenzji wydaniowej]. Tabela powyżej nie zawiera encji konfliktu, bo w przeszukanym materiale takiej
encji ani obszaru nie znaleziono. Wcześniejsze brzmienie liczyło cztery byty i przypisywało wszystkie
modelowi danych; to była nadinterpretacja. Zgodne z ORPR-CAT-03, sekcja „Widok modelu danych".

### GS1
| ORPR | GS1 | Rola | Pewność |
|---|---|---|---|
| identyfikacja kuponu | Global Coupon Number (GCN) | **klucz OFERTY kuponowej, nie wydanego egzemplarza**; jednokrotność użycia nie wynika z numeru i musi ją zapewnić licznik silnika | [P-wysoka] |
| kupon cyfrowy / kod | Digital Coupon Standard / GS1 DataBar Coupon | mechanika kuponu | [P-wysoka] |
| synchronizacja danych oferty | GDSN | interoperacyjność | [P-wysoka] |

### Test kompletności (7 osi, na które frameworki zgodnie dzielą „manage promotions")
strategia/wytyczne cenowo-rabatowe · definicja i egzekucja mechaniki (rule + modifier) ·
kwalifikacja (eligibility) jako osobna oś · kupony · lojalność · kalendarz/trade · ewaluacja.
Jeśli karta procesu nie adresuje którejś osi — to jest luka do uzupełnienia.

---

## ORPR-CAT-02 Price-to-POS (value stream „Cena")

Weryfikacja 19.08.2026 na publicznie dostępnych wydaniach. Uwaga korygująca do sekcji CAT-03 wyżej:
element 10124 to **3.2.2.2**, czyli zadanie wewnątrz 10123, a nie samodzielny element 3.2.2. Znaczenie:
wytyczne cenowo-rabatowe siedzą w strategii marketingowej (3.2), nie w planie marketingowym (3.3).

### APQC PCF (Cross-Industry v7.4, dokument K014750)

Strategia i wytyczne, czyli wejście do CAT-02:

| ORPR | APQC element | ID | Hierarchia | Pewność |
|---|---|---|---|---|
| strategia cenowa | Define pricing strategy | 10123 | 3.2.2 | [P-wysoka] |
| analiza cenowa jako wejście | Conduct pricing analysis | 13169 | 3.2.2.1 | [P-wysoka] |
| wytyczne cenowo-rabatowe | Establish guidelines for applying pricing and discounting | 10124 | 3.2.2.2 | [P-wysoka] |
| cele cenowe (podstawa marży docelowej) | Establish pricing targets | 19999 | 3.2.2.3 | [P-wysoka] |
| zatwierdzenie polityki cenowej | Approve pricing strategies/policies and targets | 10125 | 3.2.2.4 | [P-wysoka] |

Rdzeń karty, hierarchia 3.3.3:

| ORPR | APQC element | ID | Hierarchia | Pewność |
|---|---|---|---|---|
| proces nadrzędny karty | Develop and manage pricing | 20593 | 3.3.3 | [P-wysoka] |
| wejście kosztowe i kanałowe | Understand resource requirements for each product/service and delivery channel/method | 20009 | 3.3.3.1 | [P-wysoka] |
| wyliczenie ceny regularnej | Determine pricing based on volume/unit forecast | 10163 | 3.3.3.3 | [P-wysoka] |
| **ustalenie ceny regularnej w cenniku** | Execute pricing plan | 10164 | 3.3.3.4 | [P-wysoka] |
| monitoring obowiązywania | Evaluate pricing performance | 10165 | 3.3.3.5 | [P-wysoka] |
| zastąpienie ceny | Refine pricing as needed | 10166 | 3.3.3.6 | [P-wysoka] |
| **granica: to CAT-03, nie CAT-02** | Implement promotional pricing programs | 11495 | 3.3.3.7 | [P-wysoka] |
| programy cenowe niepromocyjne | Implement other retail pricing programs | 11496 | 3.3.3.8 | [P-wysoka] |
| **rdzeń „Price-to-POS": dystrybucja i wejście w życie** | Communicate and implement price changes | 11497 | 3.3.3.9 | [P-wysoka] |
| bramka regulacyjna cyklu ceny | Achieve regulatory approval for pricing | 17684 | 3.3.3.10 | [P-wysoka] |

Elementy poza 3.3.3 istotne dla cyklu życia ceny:

| ORPR | APQC element | ID | Hierarchia | Pewność mapowania |
|---|---|---|---|---|
| dane pozycji pod cenę (-> CAT-01) | Manage product and service master data | 11740 | 2.1.4 | [P-wysoka] |
| miary opakowania do ceny jednostkowej | Manage specifications | 11744 | 2.1.4.4 | ID [P-wysoka], rola [P-średnia] |
| klasyfikacja do grupy podatkowej i poziomu cennika | Manage product/materiał classification | 11746 | 2.1.4.6 | ID [P-wysoka], rola [P-średnia] |
| uwidocznienie ceny w punkcie sprzedaży | Define point of sale (POS) communication strategy | 16855 | 3.2.5.7 | [P-wysoka] |
| model danych cennika | Define enterprise data models | 20772 | 8.4.2.2 | [P-wysoka] |
| właścicielstwo cennika, audytowalność zmiany | Establish data ownership and stewardship responsibilities | 20774 | 8.4.2.4 | [P-wysoka] |
| kanał replikacji cennika | Maintain business information feeds and repositories | 20781 | 8.4.4.2 | ID [P-wysoka], rola [P-średnia] |
| reżim wdrażania zmian (lead time) | Define IT change/release standards | 20829 | 8.6.1.4 | ID [P-wysoka], rola [P-średnia] |
| dystrybucja pliku cen do sieci | Distribute software components network-wide | 20855 | 8.6.4.7 | ID [P-wysoka], rola [P-średnia] |
| potwierdzenie odbioru przez POS | Verify change/release implementation success | 20856 | 8.6.4.8 | ID [P-wysoka], rola [P-średnia] |
| rollback błędnego cennika | Execute roll-back plan / Manage IT roll-back procedures | 20857 / 20839 | 8.6.4.9 / 8.6.2.7 | [P-wysoka] |
| wersjonowanie stawek podatku | Maintain tax master data | 10929 | 9.9.1.3 | [P-wysoka] |

**Luka strukturalna PCF, istotna dla ORPR** [P-wysoka co do braku elementu, P-średnia co do
interpretacji]: PCF Cross-Industry v7.4 nie ma osobnego elementu dla replikacji cennika do kas,
publikacji ceny na nośniku ani wygaśnięcia ceny. Cały ten odcinek jest zwinięty w 11497. To jest
uzasadnienie istnienia CAT-02 jako karty dekomponującej 11497, a nie powtarzającej PCF.

APQC PCF Retail (wydanie branżowe, ostatnie publicznie ogłoszone 7.2.1) prawdopodobnie rozwija cykl
ceny detalicznej bogaciej. Identyfikatory retail-specific: **[do potwierdzenia]**, nie zgadujemy ID.

### ARTS / NRF (Retail Operational Data Model 7.3, Logical Narrative, depozytorium OMG)

**Co źródło potwierdza, a czego nie** [P-wysoka co do treści cytatu, rozstrzygnięcie granicy jest
własne]. Widok **01300 Item Price Maintenance** opisuje nadpisanie ceny („overwrites the previous
price with a new"), zmiany statyczne, permanentne albo czasowe, powodujące rewaluację zapasu. Widok
**01400 Item Rewards Derivation** opisuje ceny wyliczane regułą w transakcji. Narracja 01300:
„the starting price is taken from the **ItemSellingPrices** entity".

- **Granica CAT-02 wobec SAL-01** (utrzymanie ceny kontra derywacja w transakcji): źródło ją
  potwierdza wprost.
- **Granica CAT-02 wobec CAT-03**: źródło jej **nie potwierdza** i stoi z nią w napięciu, bo 01300
  obejmuje zmiany „permanentne albo czasowe", czyli wkłada markdown czasowy po stronie utrzymania
  ceny, a ORPR kładzie go po stronie CAT-03. Granica opiera się **wyłącznie** na teście „czy cena
  wraca", który jest rozstrzygnięciem tego standardu, nie cytatem [PROP+ 19.08, naprawa po recenzji
  wydaniowej; spójne z ORPR-CAT-02 sekcja „Zakres potwierdzenia w źródłach"].

| ORPR | Encja ARTS | Rola | Pewność |
|---|---|---|---|
| **cena regularna** | `ItemSellingPrices` | kanoniczny nośnik ceny regularnej, referencjonowany z `Item` | [P-wysoka] |
| pozycja | `Item`, `StockItem` | pozycja i jej jednostki miary | [P-wysoka] |
| pozycja luzem | `BulkItem` | inny tor wyceny, per jednostka miary | [P-wysoka] |
| **zakres obowiązywania** | `BusinessUnitGroup`, `BusinessUnitGroupItem` | cena wiązana do grupy jednostek, nie do lokalizacji | [P-wysoka] |
| zdarzenie cenowe | `DataMaintenanceEvent`, `ItemMaintenanceEvent` | zdarzenie utrzymania ceny dla grupy jednostek | [P-wysoka] |
| ślad audytowy zmiany | `Operator`, `Worker`, `WorkerOperatorAssignment`, `PartyRoleAssignment` | kto wprowadził zmianę, „for audit and control purposes" | [P-wysoka] |
| rewaluacja zapasu | `StockLedgerAccount` | konto różnicy przy markdown | [P-wysoka] |
| nośnik ceny | `ItemLabel` i podtypy: `ItemTicket`, `ItemShelfLabel`, `ItemElectronicLabel` | metka, etykieta półkowa, etykieta elektroniczna | [P-wysoka] |
| miary do ceny jednostkowej | `UnitOfMeasure`, `UnitOfMeasureCode`, `UnitOfMeasureConversion` | jednostki i konwersje; kod wiązany z elementem UCC 355 | [P-wysoka] |
| podatek sprzężony z ceną | `TaxRateRule`, `TaxGroupRule` | stawki i przypisanie reguł do grup pozycji | [P-wysoka] |
| temporalność | `Calendar`, `CalendarPeriod`, `TimeGroup`, **business day** | „all transactional entities are tied to a business day" | [P-wysoka] |
| pre-load ceny do urządzenia | `DevicePrice` (widok 20020) | wzorzec wgrania cen przed transakcją; **uwaga: widok branżowy**, nie dowód dla ogółu retailu | [P-wysoka] na encji, [P-niska] na uogólnieniu |
| granica: derywacja | `RewardDerivationRule` i rodzina `*RewardDerivationRuleEligibility` | warstwa reguł promocyjnych, **CAT-03** | [P-wysoka] |

Uwaga nazewnicza [P-wysoka]: w ODM 7.3 nie potwierdzono encji o nazwie `ItemPrice`. Kanoniczna nazwa
to `ItemSellingPrices`. Encja `PriceDerivationRule` istnieje jako pojęcie odziedziczone, ale w linii
7.x warstwa derywacji została przemianowana na rodzinę `Reward*`. Nazwy `TaxRate` i `TaxGroup` bez
sufiksu `Rule`: [do potwierdzenia]. Atrybuty temporalne (`effectiveDate` i podobne) na
`ItemSellingPrices`: [do potwierdzenia], narracja logiczna nie schodzi na poziom atrybutów.

**Reguła modelowa istotna dla karty** [P-wysoka]: `ItemLabel is related to BusinessUnitGroupItem
rather than Item`, czyli nośnik ceny jest wiązany na tym samym poziomie co cena. Stąd wniosek karty,
że rozjazd cena kontra nośnik bywa błędem zakresu, nie tylko czasu.

### ARTS XML / IXRetail (katalog schematów OMG) - warstwa komunikatów

| Schemat | Rola w CAT-02 | Pewność |
|---|---|---|
| **Price** | cennik centralny do systemów cenowych, „so pricing can be changed centrally" | [P-wysoka] |
| **Price Service Interface** | wykonanie cen i promocji w kanałach (omni) | [P-wysoka] |
| **Item Maintenance** | **replikacja danych pozycji i cen do systemów sklepowych, w tym POS** | [P-wysoka] |
| **Location Services** | ekspozycja pozycji i ceny w aplikacjach i kanałach | [P-wysoka] |
| **Transaction Tax** | osobny strumień reguł podatkowych; **rozdzielenie od schematu Price jest źródłową przyczyną rozjazdu cena kontra stawka** | [P-wysoka] |
| **POSLog 6.0** | dowód, jaka cena faktycznie zadziałała; materiał do pomiaru dokładności cenowej | [P-wysoka] |
| **Product Content Management** | most do GDSN | [P-wysoka] |

Wersje i struktura elementów tych schematów poza POSLog 6.0: [do potwierdzenia].

### GS1

| ORPR | GS1 | Rola | Pewność |
|---|---|---|---|
| klucz pozycji | GTIN | pozycja, do której wiąże się cena | [P-wysoka] |
| zakres organizacyjny | GLN | identyfikacja jednostki biznesowej | [P-średnia] |
| klasyfikacja | GPC | wejście do grupy podatkowej i poziomu cennika | [P-średnia] |
| synchronizacja cen B2B | GDSN Price Synchronisation, BMS 3.1.0: `PriceSynchronisationDocument`, `ItemPriceType`, `priceTypeCode` | katalog cenowy dostawca do detalisty | [P-wysoka] |
| wersjonowanie temporalne | `SegmentEffectiveStartDateInformation` / `...EndDate...`, z `effectiveStartDateContextCode` | wzorzec: data ZAWSZE z kodem kontekstu, nigdy goła data | [P-wysoka] |
| progi ilościowe | `BracketQualifier`, `bracketTierMinimum`, `bracketTierMaximum` | price bracket istnieje w standardzie | [P-wysoka] |
| **mianownik ceny jednostkowej** | `TradeItemMeasurements.netContent`, `priceComparisonMeasurement`, `isBasePriceDeclarationRelevant` | GS1 świadomie rozdziela zawartość netto od miary porównawczej | [P-wysoka] |
| nośnik danych na etykiecie | GS1 Digital Link (URI Syntax, resolver) | punkt zaczepienia dla ceny w kanale cyfrowym z kodu 2D | [P-wysoka] na standardzie |

**Ostrzeżenie crosswalkowe, krytyczne dla CAT-02** [P-wysoka]: GDSN Price Synchronisation jest
standardem B2B dostawca do detalisty, a kod `RETAIL_PRICE` jest w nim zdefiniowany jako „the retail
(to consumer) price **as suggested by the manufacturer**". **GS1 GDSN nie standaryzuje własnej ceny
bazowej detalisty.** Mapowanie musi to jawnie odciąć, inaczej implementator podepnie GDSN pod złe
miejsce w procesie i odda politykę cenową dostawcy. Sam kanał pozostaje poprawnym źródłem innych
typów cen, w tym cen zakupowych do matrycy marżowej.

Czego GS1 NIE standaryzuje w tym procesie [P-średnia, wniosek]: momentu wejścia ceny w życie
w lokalizacji, replikacji cennika do kasy, cyklu życia etykiety półkowej i elektronicznej. Te warstwy
pokrywa ARTS/IXRetail.

### Metrologia prawna jako źródło miary (poza trzema frameworkami)

| ORPR | Źródło | Rola | Pewność |
|---|---|---|---|
| pomiar dokładności cenowej | NIST Handbook 130, Section V „Examination Procedure for Price Verification", wyd. 2023, DOI 10.6028/NIST.HB.130-2023 | kryterium 98 %, plany próby dwustopniowe, definicje `Pricing Integrity`, `Not-on-File Item`, `Overcharge`, `Undercharge` | [P-wysoka] |
| obowiązek ceny i ceny jednostkowej w UE | Dyrektywa 98/6/WE | podstawa krajowych reżimów uwidaczniania cen | [P-wysoka] na przedmiocie, treść artykułowa [do potwierdzenia] |

Zastrzeżenie: kryterium 98 % jest nierozłączne od metodyki próby, z której pochodzi. Przeniesione
do KPI bez tej metodyki jest liczbą, którą da się wyprodukować z dowolnej próby.

### Luka crosswalku: wycena per partia

Praktyka pokazuje model, w którym jedna pozycja ma jednocześnie kilka cen, zależnych od dostawy,
a cena jest metkowana na egzemplarzu przy przyjęciu towaru. W przejrzanych źródłach **nie znalazłem
kotwicy dla tego modelu**:
- APQC PCF v7.4: brak elementu wiążącego cenę z partią; 11497 („Communicate and implement price
  changes") milczy o granularności [P-wysoka co do braku];
- ARTS ODM 7.3: `ItemSellingPrices` jest referencjonowana z `Item`, a `ItemLabel` z
  `BusinessUnitGroupItem`; nie potwierdziłem encji wiążącej cenę z partią ani z egzemplarzem
  **[do potwierdzenia]** - wymaga dostępu do wydania fizycznego modelu, narracja logiczna nie
  schodzi na ten poziom;
- GS1: standaryzuje identyfikację partii (atrybuty serializacji i lot), ale nie wiąże jej z ceną
  detaliczną **[do potwierdzenia]**.

Wniosek roboczy [P-średnia]: albo modele referencyjne zakładają milcząco jedną cenę na pozycję,
albo kotwica istnieje w warstwie, do której nie dotarliśmy. To jest realna luka do zamknięcia przed
wydaniem, bo od niej zależy klucz rekordu ceny w CAT-02 i wykonalność obowiązku ceny
najkorzystniejszej. Nie zgadujemy encji.

### Test kompletności CAT-02 (osie, na które źródła zgodnie dzielą cykl ceny)
podstawa ceny (koszt i narzut albo cena wpisana) · zakres organizacyjny i kanałowy · temporalność
(moment wejścia w życie wobec doby biznesowej i strefy) · kontrola przy zatwierdzeniu (parametr albo rozdział ról) ·
kierunek przepływu ceny (centrala do lokalizacji albo odwrotnie) · granularność ceny (pozycja albo
pozycja plus partia) · moment zamrożenia kosztu · replikacja i potwierdzenie odbioru · uwidocznienie
na nośniku · cena jednostkowa i jej mianownik ·
sprzężenie ze stawką podatku · historia ceny i cena odniesienia · wycofanie i rollback ·
**stany rekordu ceny wraz ze skutkiem każdego stanu na naliczanie i na nośnik** (dodane 19.08.2026
po recenzji CAT-02 v0.4; źródła opisują przejścia, ale żadne nie podaje tabeli stanów, więc jest to
oś wymagana przez standard, a nie przejęta z frameworku).
Karta nieadresująca którejś osi ma lukę do uzupełnienia.

---

## ORPR-CAT-01 Item-to-Sellable (value stream „Asortyment")

Weryfikacja 19.08.2026. Ustalenie nadrzędne: **żaden z trzech frameworków nie pokrywa tej domeny
w całości**, i to jest wynik, nie wymówka. APQC daje dane podstawowe bez dopuszczenia do sprzedaży,
ARTS daje strukturę pozycji bez stanów i temporalności, GS1 daje tożsamość bez procesu.

### APQC PCF (Cross-Industry v7.4)

| ORPR | APQC element | ID | Hierarchia | Pewność |
|---|---|---|---|---|
| dane podstawowe pozycji, proces nadrzędny | Manage product and service master data | 11740 | 2.1.4 | [P-wysoka] |
| specyfikacje: miary opakowania i miara porównawcza | Manage specifications | 11744 | 2.1.4.4 | ID [P-wysoka], rola [P-średnia] |
| klasyfikacja, w tym do grupy podatkowej | Manage product/materiał classification | 11746 | 2.1.4.6 | ID [P-wysoka], rola [P-średnia] |
| dane śledzenia pozycji | Manage traceability data | 11749 | 2.1.4.9 | [P-wysoka] |
| uprawnienia do danych pozycji | Review and approve data access requests | 11750 | 2.1.4.10 | [P-wysoka] |
| wprowadzenie pozycji do oferty | Introduce new products/services | 10077 | 2.1.2.2 | [P-wysoka] |
| wycofanie pozycji z oferty | Retire outdated products/services | 10078 | 2.1.2.3 | [P-wysoka] |
| cykl życia pozycji, proces nadrzędny | Manage product and service life cycle | 10067 | 2.1.2 | [P-wysoka] |
| planowanie modyfikacji oferty | Plan for product/service offering modifications | 10076 | 2.1.1.6 | [P-wysoka] |
| wymagania regulacyjne pozycji | Manage patents, copyrights, and regulatory requirements | 19985 | 2.1.3 | [P-wysoka] |
| utrzymanie danych podatkowych | Maintain tax master data | 10929 | 9.9.1.3 | [P-wysoka] |
| utrzymanie danych podstawowych w dystrybucji | Maintain master data | 10252 | 4.1.5.1 | [P-wysoka] |

Elementy 11741, 11742, 11743, 11745 i 11748 (listy materiałowe, marszruty, rysunki, specyfikacje
procesowe) są dla CAT-01 nierelewantne: hierarchia 2.1.4 ma rodowód produkcyjny [P-wysoka].

**Luki strukturalne PCF Cross-Industry dla tej karty** [P-wysoka co do braku elementu, P-średnia co
do interpretacji]:
- brak elementu dla **dopuszczenia pozycji do sprzedaży w zakresie lokalizacji i kanałów**;
- brak jednostki sprzedaży i przelicznika opakowań jako przedmiotu procesu;
- terminy asortymentowe („assortment", „planogram", „merchandising") nie występują w dokumencie
  [PROP+ 19.08: ustalenie z wyszukiwania pełnotekstowego wykonanego 19.08.2026, nie cytat ze źródła;
  rozstrzygnięte razem z tym samym twierdzeniem w ORPR-CAT-01].
Rozwinięcie detaliczne może istnieć w wydaniu branżowym frameworku [do potwierdzenia].

### ARTS / NRF (Retail Operational Data Model 7.3)

| ORPR | Encja ARTS | Rola | Pewność |
|---|---|---|---|
| pozycja asortymentowa | `Item` | *„the irreducible retail stock keeping unit for every product and service that a retailer sells"* | [P-wysoka] |
| pozycja magazynowa | `StockItem` | dobra materialne; nosi dwie różne role jednostki miary | [P-wysoka] |
| pozycja sprzedawana luzem | `BulkItem` | inny tor wyceny, per jednostka miary | [P-wysoka] |
| pozycja usługowa | `ServiceItem` | byt niebędący towarem w tej samej kartotece | [P-wysoka] |
| **zakres sprzedawalności** | `BusinessUnitGroupItem` | nadpisania per lokalizacja lub grupa; sprzedawalność jest właściwością pary, nie pozycji | [P-wysoka] |
| tożsamość przy kasie | `POSIdentity` | unikalna wyłącznie w kontekście grupy jednostek; jedna pozycja może mieć ich wiele | [P-wysoka] |
| relacja pozycja-dostawca | `ItemSupplierItem` | obsługuje też dwa SKU detalisty na jedną pozycję dostawcy | [P-wysoka] |
| jednostki miary i przeliczniki | `UnitOfMeasure`, `UnitOfMeasureConversion`, `SupplierReceivingUnitConversionRule` | konwersje wielopoziomowe; logika po stronie systemu detalisty | [P-wysoka] |
| dane konsumenckie pozycji | `StockItemConsumerProductLabel` | skład i właściwości deklarowane konsumentowi; wiązane ze `StockItem`, nie z grupą jednostek | [P-wysoka] |
| zdarzenie zmiany danych pozycji | `DataMaintenanceEvent`, `ItemMaintenanceEvent` | ślad audytowy zmiany | [P-wysoka] |
| ograniczenia sprzedaży w kasie | `ItemSellingRule`, `ItemSalesProhibitionPeriodRule` | wiek, licencja, okres zakazu; **nie** kompletność danych | [P-wysoka] |
| sprzedaż pozycji spoza kartoteki | `POSDepartment` | domyślna reguła sprzedaży i domyślna grupa podatkowa dla pozycji „not on file" | [P-wysoka] |
| śledzenie partii i serii | `ItemTraceableUnit` | równoległy zestaw kluczy obcych obok relacji na poziomie pozycji | [P-wysoka] |

**Czego w modelu NIE ma** [P-wysoka co do braku w publicznej narracji]: encji ani atrybutu statusu
pozycji, flagi wycofania, dat obowiązywania sprzedawalności. Model deklaruje to sam: *„Entities
related to the creation and management of item and price maintenance ... are not fully developed
beyond the DataMaintenanceEvent of this release."* Atrybuty mogą istnieć w pakiecie modelu, do
którego nie mamy dostępu [do potwierdzenia]. **Warstwę stanów i temporalności CAT-01 definiuje sam.**

Ostrzeżenie wydajnościowe ze źródła, istotne dla projektowania zakresu: pełny iloczyn 25 000 pozycji
przez 1100 lokalizacji daje **27,5 miliona** wierszy, więc materializacja par musi być ograniczana
[P-wysoka; liczba przeliczona niezależnie 19.08.2026, P5].

### GS1

| ORPR | GS1 | Rola | Pewność |
|---|---|---|---|
| tożsamość pozycji | GTIN | klucz pozycji; *„A trade item SHALL be assigned a GTIN before there is an offer made for sale"* | [P-wysoka] |
| **kiedy powstaje nowa pozycja** | GTIN Management Standard 1.1, sekcja 2, reguły 2.1 do 2.10 | dziesięć reguł wymuszających nowy identyfikator | [P-wysoka] |
| zawartość netto | reguła 2.3 | **brak progu**: każda zmiana wymusza nowy identyfikator | [P-wysoka] |
| wymiary i masa brutto | reguła 2.4 | próg 20 %, z klauzulą antyobejściową | [P-wysoka] |
| receptura i funkcjonalność | reguła 2.2 | **test koniunkcyjny**: deklaracja prawna ORAZ oczekiwanie rozróżnienia | [P-wysoka] |
| zakaz ponownego użycia | GenSpecs R26.0, 4.2.5 | *„An allocated GTIN SHALL NOT be reallocated to another trade item"*, od 1.01.2019 | [P-wysoka] |
| reguły zdeprecjonowane | GenSpecs R26.0, 4.16.1 | karencja 48 miesięcy, w części sektorów krótsza, w regulowanych brak reuse; **istotne dla danych zastanych** | [P-wysoka] |
| zestaw danych tożsamościowych | GenSpecs 4.2.2.2, trade item declarations | marka, typ i odmiana, zawartość netto, przy grupowaniu liczba jednostek | [P-wysoka] |
| **granica pozycja kontra oferta** | GenSpecs 2.1.15, offer declarations | cena, dostępność, warunki sprzedaży, **stan egzemplarza**; to jest teren CAT-02 i SAL-01 | [P-wysoka] |
| następstwo pozycji | atrybuty referencji do identyfikatora referowanego (typ relacji: zamiennik, zastąpienie, zastąpienie tymczasowe, odpowiednik) | relacja opcjonalna, więc detalista musi ją utrzymywać sam | [P-wysoka] |
| wariant bez zmiany identyfikatora | GenSpecs 4.2.2.3: Consumer Product Variant, identyfikator wariantu wewnętrznego | jedyny standardowy detektor cichej podmiany | [P-wysoka] |
| identyfikator wewnętrzny | GenSpecs 4.2.3.2 | dopuszczalny tylko dla pozycji bez GTIN i tylko we własnej sieci | [P-wysoka] |
| klasyfikacja towarowa | GPC | wspólny język kategorii z partnerami | [P-średnia] |
| miary do ceny jednostkowej | GDSN: zawartość netto, miara porównawcza, flaga obowiązku ceny porównawczej | dług CAT-02 realizowany danymi pozycji | [P-wysoka] |
| wycofanie jako sekwencja | Trade Item Implementation Guide, sekcja wycofania | trzy niezależne daty: koniec produkcji, koniec zamawiania, usunięcie z katalogu | [P-wysoka] |
| rynek docelowy | klucz synchronizacji GTIN plus lokalizacja plus rynek docelowy | ta sama rzecz, różne dane i obowiązki per rynek | [P-wysoka] |

**Ostrzeżenie crosswalkowe, krytyczne dla CAT-01** [PROP+ 19.08, rozstrzygnięte w ORPR-CAT-01;
status uspójniony 20.08 po recenzji delty]: reguły identyfikacji wiążą **wystawcę
identyfikatora**, nie detalistę. Dla detalisty są sygnałem, a nie regułą własną. Karta, która
przepisze je jako reguły detalisty, nie odpowie na najczęstszy realny przypadek: dostawca zmienił
produkt i nie zmienił numeru.

### Luka crosswalku: obiekt partii

CAT-02 dopuszcza partię jako część klucza ceny, a CAT-01 wypycha partie fizyczne do domeny zapasu,
która nie ma karty. **Obiekt partii nie ma dziś właściciela w całym standardzie**, mimo że pojawia
się w trzech miejscach: klucz ceny (CAT-02), granulacja blokady bezpieczeństwa (CAT-01) i śledzenie
(`ItemTraceableUnit` w ARTS). Do zamknięcia przy redakcji domeny zapasu. **To nie jest otwarta
propozycja redakcyjna, tylko zarejestrowany dług**: wewnętrzny rejestr tematów odłożonych, wpis „Obiekt PARTII bez
właściciela w całym standardzie" [PROP+ 20.08, naprawa po recenzji delty].

### Test kompletności CAT-01 (osie, na które źródła zgodnie dzielą cykl pozycji)
impuls i decyzja o wprowadzeniu · tożsamość i reguła jej zmiany · zestaw danych minimalny ·
kompletność zależna od klasy produktu i rynku · dopuszczenie do sprzedaży (automat plus decydent) ·
zakres: lokalizacje, kanały, czas · stany pozycji i ich skutki · zasilanie z zewnątrz i rozstrzyganie
konfliktu · duplikaty · wycofanie handlowe kontra bezpieczeństwa · następstwo · migracja kartoteki.
Karta nieadresująca którejś osi ma lukę do uzupełnienia.

---

## ORPR-CAT-04 Commercial-Action-to-Effect (pomiar efektu akcji handlowej)

Dodane 22.08.2026 przy integracji karty. Pełna propozycja z lokatorami i uzasadnieniem pewności: wewnętrzny materiał roboczy.

Uwaga wersyjna APQC: identyfikatory poniżej (10170, 10171, 10172, 10165, 10063) zweryfikowano 22.08.2026 na publicznych stronach APQC dla Cross-Industry v8.0; ten plik deklaruje globalnie v7.4. Numery są zgodne między wydaniami, ale reconciliacja wersji całego crosswalku (zostać przy v7.4 z weryfikacją w K014750 albo jawnie podnieść całość do v8.0) to otwarta decyzja właściciela, nierozstrzygana przy dopisaniu CAT-04. Nie mieszać wydań po cichu.

### APQC PCF (Cross-Industry, elementy jak niżej)
| ORPR | APQC element | ID | Pewność |
|---|---|---|---|
| ocena wyniku zakończonej promocji | Evaluate promotional performance metrics | 10170 (3.3.4.6) | [P-wysoka] |
| poprawa oceny i mechaniki na podstawie wyników | Refine promotional performance metrics | 10171 (3.3.4.7) | [P-wysoka element, P-średnia mapowanie] |
| powrót wiedzy do przyszłych działań (pętla uczenia) | Incorporate learning into future promotions | 10172 (3.3.4.8) | [P-wysoka] |
| ocena trwałej zmiany ceny regularnej | Evaluate pricing performance | 10165 (3.3.3.5) | [P-wysoka] |
| ocena zmiany asortymentowej | Evaluate performance of existing products against market opportunities | 10063 (2.1.1.1) | [P-wysoka element, P-średnia mapowanie] |
| jedno działanie: promocja plus cena plus asortyment plus korzyść producenta | brak pojedynczego elementu | GAP | APQC rozdziela te obszary; ORPR łączy je wspólną logiką celu, wykonania i uczenia |

Najmocniejsze kotwice: 10170 (promocja), 10165 (cena), 10172 (pętla uczenia); 10063 daje częściowe oparcie dla asortymentu. Brak jednego elementu APQC dla całego, wieloklasowego zakresu CAT-04.

### ARTS / NRF (Operational Data Model 7.3)
ARTS jest tu źródłem struktur danych, nie wzorcem procesu uczenia po działaniu.
| Potrzeba CAT-04 | Kotwica ARTS | Rola | Pewność |
|---|---|---|---|
| wynik sprzedaży: co, kiedy, gdzie, za ile | ODM 7.3 Retail Transaction Theme | dane wejściowe do wyniku działania i produktu | [P-wysoka] |
| jakie rabaty i modyfikacje ceny zastosowano | RetailTransactionLineItem, DiscountLineItem, price modification rules | dane do weryfikacji wykonania mechaniki | [P-wysoka dla struktur transakcyjnych] |
| monitoring i wyjątki operacyjne, warstwa analityczna | Operational Reporting, Data Warehouse Model | wsparcie oceny wykonania i analizy | [P-wysoka rola, P-średnia model CAT-04] |
| cel sieci vs producenta, poziomy analizy, wynik „przyczyna nierozstrzygnięta", wiedza przy mechanice | brak obiektu lub procesu w sprawdzonym materiale | GAP | nie wyprowadzać z modelu transakcji |

Wniosek: ARTS zasila CAT-04 dowodem transakcyjnym i raportowym; nie potwierdza wspólnej logiki celu, trzech poziomów analizy ani procesu zachowania wiedzy.

### GS1 (GDSN Trade Item Implementation Guideline, Release 37)
| Potrzeba CAT-04 | Kotwica GS1 | Rola | Pewność |
|---|---|---|---|
| identyfikacja produktu w działaniu | GTIN | klucz łączący plan, wykonanie i wynik | [P-wysoka] |
| powiązanie jednostki promocyjnej ze standardową | Promotional Item Information Module, nonPromotionalTradeItem | wejście do analizy substytucji lub współistnienia | [P-wysoka w zakresie modułu] |
| rodzaj oferty i okno czasowe | promotionTypeCode, startAvailabilityDateTime, endAvailabilityDateTime | dane odtwarzające definicję oferty | [P-wysoka] |
| wynik, cel sieci, marża, korzyść producenta, wiedza po działaniu | brak odpowiednika | GAP | nie przypisywać GS1 funkcji pomiaru skuteczności |

Wniosek: GS1 łączy właściwy produkt, jego wariant promocyjny i ramy czasowe; nie dostarcza procesu oceny celu ani pętli uczenia. Nie każda promocja tworzy promocyjną jednostkę handlową objętą tym modułem.

### Luki wspólne CAT-04 (rozszerzenia ORPR z dyktanda, nie treść frameworków)
Brak w sprawdzonych źródłach wspólnego odpowiednika dla: jednej oceny obejmującej promocje, ceny i asortyment; rozdzielenia celu sieci od celu producenta; trzech proporcjonalnych poziomów analizy (w tym minimalnej dla „planktonu"); dopuszczenia wyniku „przyczyna nierozstrzygnięta"; zapisu wiedzy przy mechanice zamiast rekomendacji powtórzenia akcji; potwierdzenia warunku korzyści jako wyjścia do PRC-04; mocniejszej przesłanki analizy dla marki własnej bez automatycznego obowiązku.

---

## Do zrobienia (kolejne procesy)
Wiersz dla karty rozliczenia retro (ORPR-PRC-04), przy jej redakcji. Raportowanie skuteczności akcji = ORPR-CAT-04, sekcja wyżej, dodana 22.08.2026.

## Dług techniczny tego pliku
Sekcja CAT-03 (wyżej) używa em-dashy, co łamie bramkę done z wewnętrzną procedurą redakcyjną. Do wyczyszczenia
przy najbliższej edycji tego pliku; nie czyszczone przy dopisaniu CAT-02, żeby nie mieszać zmiany
redakcyjnej z merytoryczną w jednym commicie.
