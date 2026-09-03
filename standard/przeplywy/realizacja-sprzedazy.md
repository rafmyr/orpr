# Przepływ / Realizacja sprzedaży

Karta szkieletowa mega-procesu (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + styki + dług L1. Głębia (pola 7-14,
bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem. Karta SAL-01 jest już wydana
(v1.0), a SAL-03 zrecenzowana; ta karta OBSZARU nie duplikuje ich treści L1, tylko szkicuje granice.

Dwie twarze obszaru. **Sprzedaż** (koszyk, finalizacja, dokument fiskalny, wydanie towaru) ma trzy
procesy, ale NIE ma protokołu kanonicznego dla łańcucha proces→proces: styki rozchodu i tenderu są
w rejestrze na poziomie `[OPIS]`, więc łańcuch jest tu ZAŁOŻENIEM z opisu bytów i kamieniołomu, do
potwierdzenia polem 2 kart L1. **Dopuszczenie do sprzedaży** (sprzedawalność jako warunek koszyka)
opiera się na protokole kanonicznym 4 (RCA-MCO-SFC, projekcja Offer Eligibility, FAIL-CLOSED), więc
mechanizm jest rozstrzygnięty, ale należy głównie do „Oferta handlowa" i tu jest KONSUMOWANY.

**1. Cel biznesowy:** Doprowadzić przedstawiony koszyk do sfinalizowanej sprzedaży, a jej skutek
zapasowy do domknięcia: od sprawdzenia dopuszczenia pozycji do sprzedaży, przez akceptację kwoty
i pełne pokrycie rozliczeniem, po wynik fiskalny lub potwierdzone zwolnienie, a dla pozycji
zapasowych po wydanie towaru (rozchód) albo jawne anulowanie.

**2. Granice:**
- Start: klient przedstawia koszyk do finalizacji (kasa obsługowa lub samoobsługowa, klient obecny),
  a pozycje mają ustalone dopuszczenie do sprzedaży.
- Koniec: (a) sprzedaż sfinalizowana z pełnym pokryciem kwoty i wynikiem fiskalnym albo potwierdzonym
  zwolnieniem; (b) dla pozycji zapasowych każda sprzedana ilość doprowadzona do stanu wydana albo
  anulowana (rozchód on-hand lub zwolnienie zobowiązania zapasu).
- NIE obejmuje: dopuszczenia pozycji, ceny i promocji do sprzedaży (→ Przepływ / Oferta handlowa;
  konsumowane tu jako warunek koszyka); rezerwacji dostępności i planowania (→ Przepływ / Plan
  i dostępność); rozliczenia płatności, autoryzacji, przechwycenia i tenderu (→ Przepływ / Płatności);
  zwrotu, anulowania po wydaniu i zwrotu środków (→ Przepływ / Zwrot); fizycznego stanu, transferu,
  inwentaryzacji i wyceny zapasu poza faktem rozchodu (→ Proces przekrojowy / Zapas); dekretacji, kosztu własnego
  i rozrachunków (→ Proces przekrojowy / Księga); rozliczeń kasowych (→ Proces przekrojowy / Rozliczenia kasowe); sprzedaży
  na odległość (checkout cyfrowy, klient nieobecny), która podlega odrębnej obsłudze.
- Wejście z: Oferta handlowa (dopuszczenie do sprzedaży, cena, promocja jako warunek koszyka;
  sprzedawalność wchodzi protokołem byt↔byt, nie handoffem proces→proces). Handoff-out: Płatności
  (customer commitment → tender/settlement, STK-25); Proces przekrojowy / Zapas (rozchód on-hand przy wydaniu,
  STK-22; wołanie procesu przekrojowego odłożone, jak w Planie); Proces przekrojowy / Księga (zdarzenie źródłowe
  sprzedaży oraz rozchód do wyceny, poza tą kartą).

**3. Właściciel:** Sales Operations (finalizacja sprzedaży), ze współodpowiedzialnością Order
Fulfillment / Realizacji zamówień na odcinku wydania towaru.

**4. Aktorzy:** klient albo uprawniony odbierający, operator sprzedaży, rola zatwierdzająca wyjątek
handlowy, właściciel wyjątku po rozliczeniu, pracownik lokalizacji (przygotowanie i wydanie),
kierownik lokalizacji, wykonawca fiskalizacji, wykonawca rozliczenia (Płatności), przewoźnik.

**5. Systemy (typy, vendor-neutral):** system prowadzenia transakcji sprzedaży (kasa obsługowa
i samoobsługowa), silnik kalkulacji ceny i korzyści, moduł fiskalizacji, moduł rozliczenia płatności
i tenderu, autorytet dopuszczenia do sprzedaży (reguła-z-wersją) z projekcją Offer Eligibility, rejestr
zamówienia klienta i commitmentu, zarządzanie realizacją zamówień, ewidencja i dostępność zapasu
(on-hand), system zadań w lokalizacji, obsługa wysyłki. Karta nie przesądza podziału tych zdolności
między aplikacje ani dostawców.

**6. Wyzwalacze:** przedstawienie koszyka do finalizacji; wznowienie prawidłowo zawieszonej transakcji;
udokumentowanie sprzedaży pozycji zapasowej (uruchamia wydanie); zdarzenia realizacji (zakończenie
przesunięcia, częściowe wydanie, upływ terminu, anulowanie); zmiana reguły dopuszczenia (przelicza
sprzedawalność).

## Uczestnicy L0 (nazwy czytelne)
Zamówienie klienta i finalizacja sprzedaży · Fakt produktu · Lokalizacja · Reguła regulacyjna z wersją ·
Plan oferty i kategorii · Dopuszczenie do sprzedaży (projekcja ⊗ Offer Eligibility, nie byt L0) · Stan
magazynowy i rozchód (on-hand) · Rozliczenie i tender (wyjście do Płatności) · Licznik konsumpcji / limit
(księga-licznik L1 pod regułą regulacyjną, nie byt L0).
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
Dwa tory.

Tor sprzedaży (ZAŁOŻENIE z opisu bytów i kamieniołomu, bez protokołu kanonicznego dla łańcucha
proces→proces): koszyk przedstawiony → kontrola dopuszczenia pozycji i kwoty należnej → akceptacja
klienta zamraża kwotę należną → pokrycie rozliczeniem (Płatności wykonuje rozliczenia, finalizacja
sprawdza pełne pokrycie względem kwoty należnej) → zdarzenie sprzedaż-sfinalizowana kończy SAL-01. Z tego
stanu SAL-02 (dokument fiskalny) i SAL-03 (skutek zapasowy) startują równolegle, nie jako dalsze kroki tej
samej sekwencji. Dla pozycji zapasowych: udokumentowanie sprzedaży zobowiązuje zapas w lokalizacji
(zmniejsza dostępność, może uruchomić uzupełnienie), a potwierdzone wydanie klientowi lub przekazanie
przewoźnikowi daje rozchód on-hand; anulowanie przed wydaniem zwalnia zobowiązanie i wytwarza zdarzenie
kompensujące. **Korekta 2026-09-03** (rozstrzygnięcie właściciela, decyzja 1 w
wewnętrzny materiał roboczy; recenzja Sola, delta `e58a313`,
finding B1): fiskalizacja nie jest bramką blokującą wewnątrz finalizacji; SAL-02 jest osobnym procesem L1,
równoległym do SAL-03. Poprzednie brzmienie tworzyło cykl z tym samym rozstrzygnięciem.

Tor dopuszczenia do sprzedaży (protokół kanoniczny 4, rejestr sekcja C.4): reguła regulacyjna z wersją
zmienia się → outbox/ack (gwarancja dostawy) → plan oferty przelicza projekcję Offer Eligibility (⊗,
host: plan oferty) = f(fakt produktu × lokalizacja × reguła × czas × zakres oferty) → zamówienie klienta
czyta werdykt sprzedawalności FAIL-CLOSED (odrzuca przeterminowany stempel wersji). Licznik konsumpcji
(QUOTA) sprawdzany write-through fail-closed, a zdarzenie wydania konsumuje licznik (check-and-decrement).
Rozchód: zamówienie klienta ZLECA issue stanowi magazynowemu (komenda), który wykonuje go jako wyłączny
pisarz on-hand (STK-22). Dopuszczenie należy głównie do Oferty handlowej; tu jest KONSUMOWANE jako
warunek przy koszyku. Inwariant sprzedawalności egzekwowany na ścieżce CZYTANIA fail-closed; projekcja
wykrywa po fakcie, nie egzekwuje.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od koszyka do sprzedaży · `SAL-01`
- 02 Od sprzedaży do dokumentu fiskalnego · `SAL-02`
- 03 Od sprzedaży do wydania towaru · `SAL-03`

## Diagram przepływu (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu
w formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii
(rejestr decyzji projektowych): `─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie
do walidacji (brak karty L1 z polem 2); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok
sekwencji. Dopuszczenie do sprzedaży (protokół 4, sprzedawalność) to protokół byt↔byt, więc NIE wchodzi
na diagram proces→proces (opis w sekcji „Protokół / przepływ"). Krawędzie 01→03 oraz 01→Płatności są
ciągłe (potwierdzone polem 2 wydanej karty SAL-01: przekazanie skutku zapasowego do SAL-03 i rozliczenie
przez Płatności); krawędź 03→Proces przekrojowy / Zapas potwierdzona polem 2 zrecenzowanej SAL-03 (wołanie wspólnej
zdolności odłożone). Krawędź wejścia z Oferty handlowej oraz 01→02 przerywane (dopuszczenie idzie
protokołem byt↔byt; karta SAL-02 istnieje w statusie draft, a linia ciągła czeka na jej podniesienie do
`reviewed` polem 2. **Korekta 2026-09-03**, recenzja Sola, delta `e58a313`, finding B1: granica 01/02 jest
rozstrzygnięta decyzją 1, SAL-02 równolegle do SAL-03; poprzednie brzmienie mówiło błędnie, że granica nie
jest rozstrzygnięta i że karta SAL-02 nie istnieje).
```
[z: Oferta handlowa · cena/promocja do koszyka] ⇢ 01 Od koszyka do sprzedaży
        01 ⇢ 02 Od sprzedaży do dokumentu fiskalnego   ·   proces równoległy do 03, nie bramka w 01; karta SAL-02 w statusie draft
        01 ─▶ 03 Od sprzedaży do wydania towaru         ·   pozycje zapasowe (pole 2 SAL-01)
        01 ─▶ [handoff: Płatności · customer commitment → tender/settlement]
        03 ─▶ [handoff: Proces przekrojowy / Zapas · rozchód on-hand; wołanie procesu przekrojowego odłożone]
Dopuszczenie do sprzedaży (protokół 4, sprzedawalność)  ·  protokół byt↔byt, poza diagramem proces→proces
```

## Styki L0↔L0 (rejestr sekcja B grupa 3: STK-17..24, plus STK-25 z grupy 4)
Dopuszczenie: zmiana reguły-z-wersją przelicza projekcję (STK-17); werdykt sprzedawalności FAIL-CLOSED,
odrzuca przeterminowany stempel wersji (STK-18); sprzedawalność = f(produkt × lokalizacja × reguła
× czas × zakres oferty) (STK-19); odczyt licznika konsumpcji fail-closed (STK-20); wydanie konsumuje
licznik, check-and-decrement (STK-21); zakres oferty i plan kategorii jako wejście przez projekcję
(STK-23); fakt produktu jako referencja (STK-24). Rozchód: zamówienie klienta ZLECA issue stanowi
magazynowemu, który wykonuje go jako pisarz on-hand (STK-22, komenda). Handoff do Płatności: customer
commitment → settlement/tender (STK-25). Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
Cały łańcuch proces→proces sprzedaży bez protokołu kanonicznego (koszyk → sprzedaż → dokument fiskalny
→ wydanie): założony z opisu bytów i kamieniołomu, do potwierdzenia polem 2 kart L1. Granica
finalizacja/dokument fiskalny (SAL-01/SAL-02): **rozstrzygnięta 2026-09-03** (decyzja 1 w
wewnętrzny materiał roboczy, wariant a): SAL-02 osobny proces,
równoległy do SAL-03, nie bramka blokująca wewnątrz finalizacji ani podproces L2. Formalne potwierdzenie
polem 2 czeka na podniesienie karty SAL-02 do statusu `reviewed`.
Kompletność fail-closed resolvera sprzedawalności (STK-18/19/20, rejestr sekcja D poz. 4) oraz outbox/ack
dostawy zmiany reguły (STK-17, rejestr D poz. 5). Rozchód jako komenda do stanu magazynowego (STK-22):
klucz idempotencji i in-transit do klienta (rejestr D poz. 7); wołanie procesu przekrojowego Proces przekrojowy / Zapas
odłożone (rejestr decyzji projektowych, jak w Planie). Handoff do Płatności (STK-25) i semantyka tenderu S17
(protokół 3): granica wołanie kontra handoff, do formalizacji polem 2/9 kart L1. Strona fiskalna oraz
sprzedaż na odległość (checkout cyfrowy) poza SAL-01: odrębna obsługa (rejestr tematów odłożonych w SAL-01). Wydania
częściowe, jednostka realizacji, zmiana źródła oraz realizacja partnerska kontra przesunięcie INV-02:
granica wobec Proces przekrojowy / Zapas (SAL-03).
