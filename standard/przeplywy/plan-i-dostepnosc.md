# Przepływ / Plan i dostępność

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem.

Dwie twarze obszaru. **Plan** (prognoza, zapotrzebowanie, alokacja, uzupełnienie półki, braki) ma sześć
procesów, ale NIE ma protokołu kanonicznego w rejestrze styków, więc łańcuch planistyczny jest tu
ZAŁOŻENIEM z opisu bytów i kamieniołomu, do potwierdzenia polem 2 kart L1. **Dostępność** (rezerwacja
pod zobowiązanie klienta) opiera się na protokole kanonicznym 1 (SFC-SUP) i projekcji ATP, więc jest
rozstrzygnięta.

**1. Cel biznesowy:** Utrzymać właściwy towar we właściwym miejscu i czasie: od sygnału popytu, przez
prognozę, zapotrzebowanie netto i alokację przy ograniczeniach, po uzupełnienie półki, rezerwację
dostępności pod zobowiązanie klienta i rozwiązanie braku. Wynik: dostępność utrzymana, a zapotrzebowanie
netto przekazane do zakupu.

**2. Granice:**
- Start: pojawia się sygnał popytu (sprzedaż, prognoza, próg zapasu, zamówienie klienta) → uruchamia
  planowanie lub rezerwację.
- Koniec: (a) zapotrzebowanie netto przekazane do Zakupu; (b) dostępność zarezerwowana pod zobowiązanie
  klienta (commitment); (c) brak towaru rozwiązany (uzupełnienie, substytucja, transfer).
- NIE obejmuje: zakupu, przyjęcia i zapłaty dostawcy (→ Przepływ / Zakup do zapłaty); fizycznego
  przyjęcia, transferu, inwentaryzacji i wyceny zapasu (→ Proces przekrojowy / Zapas); sprzedaży i wydania towaru
  klientowi (→ Przepływ / Realizacja sprzedaży); dopuszczenia pozycji, ceny i promocji do sprzedaży
  (→ Przepływ / Oferta handlowa).
- Wejście z: Realizacja sprzedaży (sygnał popytu, zamówienie klienta pod rezerwację); Proces przekrojowy / Zapas
  (stan on-hand jako wejście prognozy i admisji). Handoff-out: Zakup do zapłaty (zapotrzebowanie netto
  → zamówienie; to jest start `PRC-01`).

**3. Właściciel:** Planowanie popytu i zapasu (demand and supply planning), ze współodpowiedzialnością
operacji lokalizacji na odcinku uzupełnienia półki i rozwiązania braku.

**4. Aktorzy:** planista popytu, planista zapasu / alokator, kupiec (odbiór zapotrzebowania), pracownik
lokalizacji (uzupełnienie półki, zgłoszenie i rozwiązanie braku), kierownik lokalizacji.

**5. Systemy (typy, vendor-neutral):** system prognozowania popytu, system planowania zapasu i uzupełnień
(replenishment), silnik alokacji, rejestr dostępności (availability ledger), system zadań w lokalizacji
(uzupełnienia, braki), ERP/WMS jako źródło stanu on-hand.

**6. Wyzwalacze:** sygnał popytu (sprzedaż, sezon, zapowiedź promocji z Oferty handlowej); cykl prognozy;
próg lub minimum zapasu; zamówienie klienta wymagające rezerwacji; wykryty brak na półce; ograniczenie
podaży (limit dostawcy, decyzja alokacyjna).

## Uczestnicy L0 (nazwy czytelne)
Plan podaży i dostępność · Stan magazynowy (on-hand) · Zamówienie klienta i rezerwacja · Lokalizacja ·
Zamówienie zakupowe (wyjście do Zakupu).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Dwa tory.

Tor planistyczny (ZAŁOŻENIE z opisu bytów i kamieniołomu, bez protokołu kanonicznego): sygnał popytu →
prognoza → zapotrzebowanie netto (dostępne = on-hand - zarezerwowane - zaalokowane + inbound; to jest
projekcja ATP, nie ścieżka zapisu) → przy ograniczeniach alokacja → dwa wyjścia: (a) zapotrzebowanie do
zakupu, ścieżką automatyczną lub ręczną, przekazane do Zakupu; (b) uzupełnienie półki w lokalizacji.
Brak na półce, sygnał kasjera o niedostępności i ręczna ocena kategorii/półki są w warstwie A pełnoprawnymi wyzwalaczami `DEM-01` (`ST-BRAK-WYKRYTY`, `ST-SYGNAL-KASJERA-NIEDOSTEPNOSC`, `ST-OCENA-MANUALNA-KATEGORII`), na równi z prognozą; nie są danymi pomocniczymi prognozy. Brak na półce uruchamia także rozwiązanie lokalne (`INV-06`) i wraca do zapotrzebowania,
nie oddaje pałeczki dalej.

Tor dostępności (protokół kanoniczny 1, rejestr sekcja C.1): zamówienie klienta żąda rezerwacji → plan
podaży wykonuje ATOMOWY check-and-reserve na availability ledger (nie na projekcji ATP; serializacja /
compare-and-set) → commitment po stronie zamówienia klienta, z wiązaniem wymiaru lokalizacji w chwili
admisji. Sprzedaż z półki (walk-in) też przechodzi przez admisję planu podaży (reserve-before-issue).
Plan podaży czyta on-hand do decyzji admisji i alokacji. Inwariant egzekwowany na ścieżce ZAPISU
(availability ledger), nie na projekcji.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od popytu do zapotrzebowania netto · `DEM-01`
- 02 Od zapotrzebowania do zakupu (ścieżka ręczna) · `DEM-02`
- 03 Od sygnału popytu do prognozy · `DEM-03`
- 04 Od ograniczeń do alokacji · `DEM-04`
- 05 Od uzupełnienia do półki · `INV-05`
- 06 Od braku towaru do rozwiązania · `INV-06`

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok
sekwencji. Rezerwacja (protokół 1) to protokół byt↔byt, więc NIE wchodzi na diagram proces→proces
(opis w sekcji „Protokół / przepływ"). Handoff-out do Zakupu jest ciągły (potwierdzony
polem 2: karta P2P deklaruje „Wejście z: Plan i dostępność", a ta karta deklaruje ten handoff-out);
krawędź wejścia z Realizacji/Zapas przerywana (źródło nie deklaruje handoffu do Planu, to sygnał lub
odczyt, nie potwierdzone przekazanie); krawędzie wewnętrzne przerywane (karty L1 jeszcze nie istnieją).
06 poza główną sekwencją.
```
[z: Realizacja sprzedaży · Proces przekrojowy / Zapas] ⇢ 03 Od sygnału popytu do prognozy
                                               03 ⇢ 01 Od popytu do zapotrzebowania netto
                                               01 ⇢ 04 Od ograniczeń do alokacji
04 ⇢ 02 Od zapotrzebowania do zakupu (ścieżka ręczna) ─▶ [handoff: Zakup do zapłaty / 01]
01 ⇢ 02   założenie: ścieżka automatyczna zapotrzebowania też zasila zakup
04 ⇢ 05 Od uzupełnienia do półki   ·   [wynik: dostępność na półce]
06 Od braku towaru do rozwiązania   ·   wejście: sygnał braku (OOS); pętla ⇢ 01 / 05 (nie handoff)
```

## Styki L0↔L0 (rejestr sekcja B grupa 2: STK-13..16)
Rezerwacja: zamówienie klienta zleca rezerwację planowi podaży (STK-13, komenda, reserve-before-issue,
POS walk-in też); plan podaży zwraca wynik atomowego check-and-reserve na availability ledger jako
commitment (STK-14); plan podaży wiąże wymiar lokalizacji w chwili admisji (STK-15); plan podaży czyta
on-hand do decyzji admisji i alokacji (STK-16, `[PROP+ 24.08]`). Projekcja ATP (rejestr sekcja E) =
on-hand - zarezerwowane - zaalokowane + inbound. Pełne brzmienie, typy i protokół 1:
`standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Cały tor planistyczny bez protokołu kanonicznego (prognoza → zapotrzebowanie → alokacja → półka → braki):
łańcuch założony z opisu bytów i kamieniołomu, do potwierdzenia polem 2 kart L1. Styk zapotrzebowanie →
zamówienie (planowanie → Zakup) NIE jest skatalogowany w rejestrze L0 (grupa 1 zaczyna od istniejącego
zamówienia zakupowego); to handoff procesowy do `PRC-01`, do formalizacji. Poziom izolacji locka
rezerwacji (rejestr sekcja D poz. 3, STK-13/14: serializacja / compare-and-set). Projekcja ATP: host
i spójność (ATP to projekcja, rezerwacja idzie na availability ledger, nie na ATP). Krawędzie topologii
sieci i cross-site routing alokacji (rejestr sekcja D poz. 8). In-transit do klienta (rejestr sekcja D poz. 7);
inbound-podaż do dostępności bez odrębnej pozycji w rejestrze (do formalizacji). Kryterium wyboru ścieżki automatycznej vs ręcznej zapotrzebowania
(`DEM-01` vs `DEM-02`). Substytucja i transfer jako rozwiązanie braku (`INV-06`): granica wobec
Proces przekrojowy / Zapas (transfer = `INV-02`), wołanie procesu przekrojowego odłożone (rejestr decyzji projektowych).
