# REJESTR STYKOW L0 ORPR v1.0 (zatwierdzony na Bramce A 24.08.2026)

Status: ZATWIERDZONY na Bramce A (24.08.2026, akt wlasciciela) razem z mapa L0 v0.5.1.
Artefakt pierwszej klasy metody "mapa najpierw": formalizuje styki miedzy bytami L0, ktore mapa v0.5
opisala tylko czesciowo (sekcje 2-3 v0.5 = "kluczowe" protokoly).

Podstawa: wewnętrzny materiał roboczy (wzorzec + kryterium + rejestr wlascicieli +
6 protokolow), `-v0.5.1-freeze-candidate.md` (delta AR/QUOTA/asercje), syntezy 3. i 4. ataku.
Decyzje wlasciciela 24.08 wbudowane: (a) AR = ROZSZERZ SFT (16 L0); (b) 9 stykow wyprowadzonych ->
przyjete jako [PROP+ 24.08]; (c) autor polityki limitu kredytowego AR = CXR.

## Legenda

Typ przeplywu:
- STAN - odczyt autorytatywnego stanu innego L0 (referencja / read-model)
- ZDARZ - zdarzenie domenowe emitowane przez pisarza, konsumowane idempotentnie (ack)
- KMD - komenda (orkiestrator -> uczestnik; z legiem kompensacji)
- AUT - odczyt autorytetu FAIL-CLOSED (regula-z-wersja / decyzja eligibility / limit)

Status i zrodlo (higiena twierdzen):
- [PROT] - rozstrzygniety protokol kanoniczny, v0.5 sekcja 3
- [OPIS] - wynika wprost z opisu pisarza L0, v0.5 sekcja 1
- [DELTA] - z v0.5.1 (AR, QUOTA-licznik, 5 asercji spec)
- [PROP+ 24.08] - styk WYPROWADZONY analitycznie z opisow (nie z dyktanda), PRZYJETY przez wlasciciela
  24.08 jako propozycja Claude. To nie jest [AUT-R] (nie slowa wlasciciela) - do zmiany na jego zadanie.
- [DLUG-L1] - mechanizm/detal jawnie odlozony do Etapu B (nie blokuje freeze)

---

## A. Rejestr wlascicieli stanow (16 L0, jeden wylaczny pisarz na stan)

Zrodlo: v0.5 sekcja 2, zaktualizowane delta v0.5.1 (QUOTA out z L0, AR homed w SFT).

| L0 | Wylaczny pisarz stanu | Typ bytu |
|---|---|---|
| MCO | offer scope + category plan (wykonywalna decyzja handlowa) | pisarz stanu |
| PIN | fakt/rekord produktu | L0-autorytet (system-of-record) |
| SRC | relacja z dostawca + kontrakt + warunki | pisarz stanu |
| PO | zamowienie zakupowe (requisition -> zamkniete) | pisarz stanu |
| OBLIG | 3-way match + zobowiazanie do zaplaty (terminal "zwolnione-do-zaplaty") + arbiter sporu match | pisarz stanu |
| SUP | supply plan + allocation policy + availability ledger + admission decision | pisarz stanu |
| LEX | on-hand + ruch fizyczny + fakt wariancji/straty | pisarz stanu (wylaczny on-hand) |
| SITE | lokalizacja: tozsamosc + licencja + jurysdykcja + cykl zycia | L0-autorytet (system-of-record) |
| STX | store execution: kolejka zadan lokalnych + atestacja wykonania | pisarz stanu |
| CXR | relacja + party identity + ksiega punktow (liczba) + kurs OPERACYJNY | pisarz stanu |
| SFC | zamowienie klienta + customer commitment + Transaction Eligibility Decision | pisarz stanu |
| SRV | sprawa zwrotu (+ orkiestrator sagi S3) | pisarz stanu + orkiestrator |
| SFT | settlement + gotowka klienta + chargeback + kwota-zwrocona-per-capture + naleznosc klienta AR (+ orkiestrator tendera S17) | pisarz stanu + orkiestrator |
| REBATE | retro accrual -> claimable -> claimed -> settled | pisarz stanu |
| FIN | ksiega + podatek + wycena zobowiazania lojalnosciowego (wlasna metoda) | pisarz stanu (pierscien) |
| RCA | polityka + wersjonowana regula + obowiazek + compliance case + remediacja (+ orkiestrator) | pisarz stanu + orkiestrator (pierscien) |

Poza L0: QUOTA-licznik = dedykowana ksiega-licznik L1 pod RCA (wylaczny pisarz licznika; SFC NIE
inkrementuje). Regula limitu = tresc RCA; brama = SFC eligibility.

---

## B. Macierz stykow L0 <-> L0

### Grupa 1: Zakup do zaplaty (P2P)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-01 | SRC -> PO | STAN | warunki kontraktu (ceny/terminy) jako wejscie zamowienia | [OPIS] |
| STK-02 | SRC -> OBLIG | STAN | warunki kontraktu jako referencja 3-way match | [OPIS] |
| STK-03 | SRC -> REBATE | STAN | warunki retro (progi, stawki) | [OPIS] |
| STK-04 | PO -> LEX | ZDARZ | zapowiedz dostawy / oczekiwane przyjecie (inbound) | [PROT] |
| STK-05 | LEX -> OBLIG | ZDARZ | fakt przyjecia (receipt) = druga strona 3-way match | [PROT] |
| STK-06 | PO -> OBLIG | STAN | zamowienie = pierwsza strona 3-way match | [PROT] |
| STK-07 | OBLIG -> FIN | ZDARZ | "zwolnione-do-zaplaty" -> payable + accrual GR/IR z receipt | [PROT] |
| STK-08 | OBLIG -> SFT | STAN | zobowiazanie do zaplaty -> trigger wyplaty buy-side | [PROT] |
| STK-09 | SFT -> OBLIG | ZDARZ | PaidV1; OBLIG konsumuje i SAM sie zamyka (SFT nie mutuje) | [DELTA] |
| STK-10 | SFT -> FIN | ZDARZ | PaidV1; FIN konsumuje i SAM zamyka payable | [DELTA] |
| STK-11 | REBATE -> PO/OBLIG | STAN | actuals (zrealizowane wolumeny/wartosci) | [OPIS] |
| STK-12 | REBATE -> FIN | ZDARZ | accrual -> claimable -> settled (`ST-KORZYSC-ROZLICZONA`); skutek ksiegowy naleznosci. Poprzednia nazwa stanu `ST-RABAT-RETRO-ROZLICZONY` = przypadek retro. Draft `FIN-01` nie czyta tego stanu (rozjazd wobec warstwy A). | [PROP+ 24.08] |

### Grupa 2: Plan i dostepnosc (rezerwacja)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-13 | SFC -> SUP | KMD | zadanie rezerwacji (reserve-before-issue; POS walk-in tez) | [PROT] |
| STK-14 | SUP -> SFC | ZDARZ | wynik atomowego check-and-reserve na availability ledger -> commitment | [PROT] |
| STK-15 | SUP -> SITE | STAN | wiazanie wymiaru lokalizacji (site) w chwili admisji | [PROT] |
| STK-16 | SUP -> LEX | STAN | odczyt on-hand do decyzji admisji/alokacji | [PROP+ 24.08] |

### Grupa 3: Sprzedaz i sprzedawalnosc (eligibility)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-17 | RCA -> MCO | ZDARZ | zmiana reguly-z-wersja -> outbox/ack (gwarancja dostawy) -> MCO przelicza projekcje | [PROT] |
| STK-18 | SFC -> RCA | AUT | werdykt sprzedawalnosci FAIL-CLOSED (odrzuca przeterminowany stempel wersji) | [PROT] |
| STK-19 | SFC -> Offer Eligibility (⊗, host MCO) | AUT | sprzedawalnosc = f(PIN x SITE x RCA x czas x MCO-scope) | [DELTA] |
| STK-20 | SFC -> QUOTA-licznik (L1/RCA) | AUT | odczyt licznika konsumpcji fail-closed | [DELTA] |
| STK-21 | zdarzenie wydania -> QUOTA-licznik | ZDARZ | licznik konsumuje wydanie (check-and-decrement); wylaczny pisarz licznika | [DELTA] |
| STK-22 | SFC -> LEX | KMD | rozchod ZLECA (issue); LEX wykonuje jako pisarz on-hand | [OPIS] |
| STK-23 | MCO -> SFC | STAN | offer scope / category plan jako wejscie sprzedawalnosci (przez projekcje) | [OPIS] |
| STK-24 | PIN -> SFC/eligibility | STAN | fakt produktu jako referencja | [OPIS] |

### Grupa 4: Klient, lojalnosc, tender

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-25 | SFC -> SFT | ZDARZ | customer commitment -> settlement/tender | [OPIS] |
| STK-26 | SFT -> CXR | KMD | tender S17: zadanie autoryzacji/blokady punktow (hold z TTL) | [PROT] |
| STK-27 | SFT -> CXR | KMD | leg kompensacji release-hold (idempotencja tender-id) | [PROT] |
| STK-28 | CXR (commit tendera) | STAN | CXR jedyny pisarz dekrementu liczby punktow (SFT nigdy nie pisze liczby) | [PROT] |
| STK-29 | CXR -> FIN | ZDARZ | zdarzenie zmiany kursu OPERACYJNEGO; FIN wlasna metoda wyceny (breakage, effective-dating); CXR nie steruje zobowiazaniem FIN | [PROT] |
| STK-30 | SFT -> FIN | ZDARZ | settlement gotowkowy klienta -> ksiega | [PROP+ 24.08] |

### Grupa 5: Zwrot (saga S3; SRV = orkiestrator)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-31 | SRV -> SFT | KMD | refund; straznik capture-id wspolny z chargeback (remaining-returnable; brak podwojnego refundu) | [PROT] |
| STK-32 | SRV -> LEX | KMD | przyjecie zwrotu fizycznego -> on-hand | [PROP+ 24.08] |
| STK-33 | SRV -> CXR | KMD | anulowanie punktow/kuponow przy zwrocie | [PROP+ 24.08] |
| STK-34 | SRV <-> FIN | ZDARZ | FIN nie-terminalny (podstan "prowizorycznie zamkniete"); trigger reopen przez SRV | [PROT] |
| STK-35 | SRV -> SFC | STAN | sprawa zwrotu odnosi sie do pierwotnego commitmentu/transakcji SFC | [PROP+ 24.08] |

### Grupa 6: Regulacja i remediacja (RCA = orkiestrator)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-36 | RCA -> wszystkie L0 | AUT | regula-z-wersja jako autorytet egzogeniczny konsumowany transakcyjnie (K4) | [OPIS] |
| STK-37 | RCA -> wlasciciele procesow | KMD | remediacja jako orkiestrowana sprawa; skutki wykonuja wlasciciele L0 (jak SRV) | [OPIS] |
| STK-38 | L0 -> RCA | ZDARZ | zdarzenia zgodnosci / findingi zasilajace compliance case | [PROP+ 24.08] |

### Grupa 7: Naleznosc klienta (AR; v0.5.1, SFT rozszerzony)

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-39 | SFT (AR) - wewn. | WEWN | naleznosc-otwarta -> rozliczona (aging, harmonogram rat) | [DELTA] |
| STK-40 | SFC -> limit kredytowy (polityka, autor CXR) | AUT | limit czytany przez SFC eligibility; AUTOR polityki limitu = CXR (relacja z klientem), decyzja 24.08 | [DELTA] + [PROP+ 24.08] |
| STK-41 | SFT (AR) -> FIN | ZDARZ | naleznosc klienta -> ksiega (accrual, aging) | [PROP+ 24.08] |

### Grupa 8: Tozsamosc i wykonanie lokalne

| ID | Styk | Typ | Co plynie | Status |
|---|---|---|---|---|
| STK-42 | SITE -> STX | STAN | lokalizacja (tozsamosc/licencja/jurysdykcja) -> kolejka zadan lokalnych | [OPIS] |
| STK-43 | STX -> Operating Readiness (⊗) | ZDARZ | atestacja wykonania zasila projekcje readiness | [OPIS] |
| STK-44 | PIN <-> SITE | STAN | sprzedawalnosc jako para (pozycja, site) - referencja krzyzowa w eligibility | [PROP+ 24.08] |

---

## C. Protokoly kanoniczne (6 rozstrzygnietych; v0.5 sekcja 3, pelne brzmienie)

1. **Rezerwacja (SFC-SUP):** SFC zada -> SUP wykonuje ATOMOWY check-and-reserve na AVAILABILITY LEDGER
   (nie na projekcji ATP; serializacja / compare-and-set) -> commitment (SFC). POS walk-in TEZ przez
   admisje SUP (reserve-before-issue). reserved z wymiarem lokalizacji (site wiazany w chwili admisji
   przez SUP). Inwariant egzekwowany na sciezce ZAPISU. Styki: STK-13, STK-14, STK-15.

2. **S3 zwrot:** SRV = ORKIESTRATOR (detekcja awarii/timeout per krok, jedyna wladza komend
   kompensujacych; uczestnicy nie kompensuja sami). Idempotencja i straznik pieniadza na CAPTURE-ID
   wspolny z torem chargeback (SFT kwota-zwrocona-per-capture; refund i chargeback rezerwuja wobec
   remaining-returnable; brak podwojnego refundu). Skutki nieodwracalne = pivot/forward-recovery, nie
   rollback. FIN nie-terminalny: sprawa nie osiaga stanu ostatecznego dopoki FIN nie uzgodni (podstan
   "prowizorycznie zamkniete"); FIN ma trigger reopen przez SRV. Styki: STK-31, STK-32, STK-33, STK-34, STK-35.

3. **Tender (S17):** SFT = orkiestrator; CXR autoryzuje/BLOKUJE punkty (hold z TTL) -> SFT capture ->
   commit/kompensacja (komenda SFT->CXR release-hold, idempotencja tender-id); CXR jedyny pisarz
   dekrementu liczby (SFT nigdy nie pisze liczby). Styki: STK-26, STK-27, STK-28.

4. **Sprzedawalnosc:** RCA(regula-z-wersja) zmiana -> outbox/ack -> MCO przelicza Offer Eligibility
   Projection (⊗). SFC czyta werdykt FAIL-CLOSED (odrzuca przy przeterminowanym stemplu wersji).
   QUOTA sprawdzana write-through fail-closed. Resolver = ⊗ Technology. Styki: STK-17, STK-18, STK-19, STK-20, STK-21.

5. **Loyalty wycena:** CXR kurs OPERACYJNY (co dostaje klient) != FIN zalozenia WYCENY (breakage, kurs
   wyceny). CXR emituje zdarzenie zmiany kursu operacyjnego; FIN wlasna metoda decyduje o skutku
   ksiegowym (effective-dating). CXR NIE steruje zobowiazaniem FIN. Styk: STK-29.

6. **P2P:** PO(zamowienie) -> LEX(przyjecie, fakt) -> OBLIG(3-way match, arbiter sporu,
   zwolnione-do-zaplaty) -> FIN(payable, accrual GR/IR z receipt) -> SFT(wyplata, "oplacone", zdarzenie
   PaidV1 zamyka OBLIG i FIN). REBATE czyta warunki SRC + actuals PO/OBLIG. Styki: STK-01..STK-12.

---

## D. Dlug L1 stykow (jawnie odlozony do Etapu B; NIE blokuje freeze)

Zrodlo: v0.5.1 sekcja "Dlug L1" + 4. atak.

1. Inwentarz komend kompensacji per orkiestrator (SRV / SFT / RCA)
2. Klucz idempotencji (capture-id + operation-id)
3. Poziom izolacji locka rezerwacji (STK-13/14)
4. Kompletnosc fail-closed resolvera (STK-18/19/20)
5. Outbox/ack dostawy (STK-17)
6. Reconciliation released-unpaid (P2P: STK-07/08/09/10)
7. In-transit do klienta (LEX)
8. Krawedzie topologii sieci (SUP)
9. Party podatkowa B2B (CXR referuje, FIN konsumuje)
10. Cross-site routing zadan (STX)
(Pozycja "autor polityki limitu kredytowego AR" ROZSTRZYGNIETA 24.08: autor = CXR. Do dlugu wchodzi
tylko MECHANIZM: jak SFC czyta limit CXR fail-closed, STK-40.)

---

## E. Projekcje ⊗ (czytaja stany L0, NIE pisza; wykrywaja po fakcie, nie egzekwuja)

- **ATP** = LEX on-hand - SFC reserved - SUP allocated + inbound. Jedna odpowiedz na "ile dostepne".
- **Offer Eligibility** (host MCO) = PIN x SITE x RCA x czas x MCO-scope.
- **Operating Readiness** = LEX x SFT x SITE x ... (host do ustalenia w Etapie B).
- Pozostale ⊗: PRF (pomiar), Regulatory Bindings (aplikacja/referencja reguly), Technology &
  Integration (resolver sprzedawalnosci), Data Governance, AI Governance, decision-right (D),
  channel (K).

Zasada wzorca: projekcja = total-funkcja nad stanami L0, ⊗ NAWET jesli hostowana przez L0. Egzekucja
inwariantu = rola pisarza na sciezce zapisu, nie projekcji.

---

## F. Podsumowanie (liczby przeliczone skryptem 24.08, nie przepisane; P17)

- Stykow L0 <-> L0 skatalogowanych: **44** (STK-01..STK-44), numeracja ciagla, 0 luk, 0 duplikatow.
- Rozklad statusu (STK-40 nosi 2 tagi):
  - [PROT] rozstrzygniety protokol: **16**
  - [OPIS] wprost z opisu L0: **12**
  - [PROP+ 24.08] wyprowadzony i przyjety przez wlasciciela: **10** (STK-12, 16, 30, 32, 33, 35, 38, 41, 44 + STK-40)
  - [DELTA] z v0.5.1: **7**
  - [DLUG-L1] w tabeli B: **0** (mechanizmy w sekcji D)
- Pokrycie L0: **wszystkie 16 L0 wystepuja** jako zrodlo lub cel min. jednego styku. Sierot: 0.
  (SFC 11, SFT 10, OBLIG 7, FIN 7, RCA 6, LEX 5, CXR 5, SRV 5, PO 4, SUP 4, MCO 3, SRC 3, SITE 3,
  REBATE 3, PIN 2, STX 2 - wystapienia w kolumnie Styk.)
- Kontrola metody: tokenizer L0 sprawdzony na znanym przypadku (lapie "SRC -> PO", nie lapie "PO"
  w "OBLIG -> FIN").
- Dlug L1: 10 mechanizmow z v0.5.1 obecne w sekcji D. 6 protokolow kanonicznych z v0.5 sekcja 3
  obecne w sekcji C.

Decyzje wlasciciela 24.08 (Bramka A) wbudowane:
1. **10 stykow [PROP+ 24.08]** - przyjete jako propozycje Claude (nie [AUT-R]); do zmiany na zadanie.
2. **STK-40:** autor polityki limitu kredytowego AR = CXR.
3. **Lokalizacja:** `standard/mapowania/` (produkt).

Otwarte (nie blokuje; Etap B): mechanizm STK-40 (jak SFC czyta limit CXR fail-closed) + dlug L1 sekcji D.
