# Proces przekrojowy / Rozliczenia kasowe

Karta szkieletowa procesu przekrojowego (Etap B). Status: szkielet · Wersja 0.1 · Notacja: `standard/mapa-procesow.md`.
Clean-room: bez materiałów klientów/pracodawców (2026-08-24).

Zakres tej karty: pola 1-6 + uczestnicy L0 + protokół + procesy + wołania z przepływów + styki + dług L1.
Głębia (pola 7-14, bank pytań, bramki, warianty, ścieżki wyjątku) = Etap C, za popytem. UCZCIWIE: to
najsłabiej zakotwiczony obszar standardu. W rejestrze L0 NIE MA bytu „kasa" ani żadnego bytu „CSH";
nie ma też bytu „bank". Rozliczenia kasowe to WARSTWA OPERACYJNA domykająca dzień lub zmianę kasy nad bytem
settlement (gotówka klienta, rozliczenie form płatności) oraz nad księgą, z wpłatą do banku jako celem
zewnętrznym. Dlatego niemal cała treść operacyjna tej karty jest `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`;
realnie kotwiczy się wyłącznie w styku settlement gotówkowy klienta → księga (STK-30) i w wejściu
customer commitment → settlement (STK-25). Brak dedykowanego protokołu kanonicznego (protokoły 1-6 nie
dotyczą kasy). Karta jest z założenia cienka i heavy-ZAŁOŻENIE; nie dodano tu bytu ani protokołu, którego
rejestr nie potwierdza.

**1. Cel biznesowy:** Domknąć operacyjny dzień lub zmianę kasy i uzgodnić wpływy wobec sprzedaży: od
otwarcia kasy, przez uzgodnienie gotówki i rozliczenie form bezgotówkowych, po zamknięcie kasy, wpłatę
gotówki do banku i potwierdzenie rozliczenia. Wynik: kasa zamknięta i uzgodniona, gotówka wpłacona,
rozliczenie form bezgotówkowych potwierdzone, skutek księgowy przekazany do księgi.

**2. Granice:**
- Start: rezultat rozliczenia z Przepływu / Płatności (settlement gotówkowy klienta i rozliczenie form
  bezgotówkowych) trafia do warstwy operacyjnej kasy; kotwica: settlement gotówkowy klienta → księga
  (STK-30), z wejściem sprzedażowym customer commitment → settlement (STK-25). `[ZAŁOŻENIE z opisu bytów
  i kamieniołomu]`: sekwencja otwarcie kasy → uzgodnienie → zamknięcie nie ma bytu L0, więc jej początek
  jest warstwą operacyjną, nie stykiem rejestru.
- Koniec: kasa zamknięta i uzgodniona, gotówka wpłacona do banku, formy bezgotówkowe rozliczone przez
  schemat rozliczeniowy, skutek księgowy przekazany do Proces przekrojowy / Księga. `[ZAŁOŻENIE]`: sam
  moment wpłaty do banku nie ma bytu L0 (bank poza rejestrem).
- NIE obejmuje: orkiestracji tenderu, autoryzacji i przechwycenia form płatności ani samego rozliczenia
  klienta (→ Przepływ / Płatności, to jest wołający); księgowań poza skutkiem uzgodnienia kasy i wpłaty
  (→ Proces przekrojowy / Księga); anulowania sprzedaży i zwrotu środków (→ Przepływ / Zwrot); zapasu
  i gotówkowego obrotu magazynowego (→ Proces przekrojowy / Zapas).
- Wołana przez: Przepływ / Płatności (rezultat rozliczenia: settlement gotówkowy i bezgotówkowy → warstwa
  rozliczeń kasowych, zamknięcie kasy, wpłata). `[ZAŁOŻENIE]`: dokładny punkt wołania i to, czy wołanie
  jest per transakcja czy zbiorczo na koniec zmiany, do rozstrzygnięcia w kartach L1.
- Zwraca do wołającego: potwierdzenie wpłaty i rozliczenia (do banku) oraz skutek do Proces przekrojowy /
  Księga (settlement gotówkowy klienta → księga, STK-30). `[ZAŁOŻENIE]`: kanał zwrotu potwierdzenia
  bezgotówkowego (schemat rozliczeniowy → warstwa kasy) nie ma styku w rejestrze.

**3. Właściciel:** Finanse / operacje kasowe (uzgodnienie gotówki i rozliczeń, wpłata do banku), ze
współodpowiedzialnością settlementu na odcinku wpływu gotówkowego i bezgotówkowego oraz księgi na odcinku
skutku księgowego.

**4. Aktorzy:** operator punktu sprzedaży (otwarcie i zamknięcie kasy, przeliczenie gotówki), kierownik
zmiany (zatwierdzenie uzgodnienia), specjalista ds. rozliczeń (settlement, formy bezgotówkowe), specjalista
ds. wpłat i banku, kontroler / finanse.

**5. Systemy (typy, vendor-neutral):** moduł rozliczeń kasowych (szuflada, zmiana, uzgodnienie), rejestr
rozliczeń (settlement ledger) na odcinku wpływu, przełącznik i schemat rozliczeniowy dla form bezgotówkowych
(vendor-neutral), moduł wpłat gotówkowych do banku (treasury / cash management), księga główna
(skutek uzgodnienia). `[ZAŁOŻENIE]`: podział na system kasowy, settlement i treasury jest opisem
warstwy operacyjnej, nie granicą bytów L0.

**6. Wyzwalacze:** otwarcie kasy lub zmiany; przybycie rezultatu rozliczenia z Płatności (gotówka klienta,
forma bezgotówkowa); zamknięcie kasy lub zmiany; różnica przy uzgodnieniu (nadwyżka lub niedobór);
przygotowanie wpłaty do banku; potwierdzenie rozliczenia przez schemat rozliczeniowy; termin okresowego
uzgodnienia. `[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: większość tych wyzwalaczy nie ma zdarzenia w
rejestrze styków (brak bytu kasy).

## Uczestnicy L0 (nazwy czytelne)
Settlement i gotówka klienta (odcinek wpływu) · Księga (skutek uzgodnienia).
UWAGA (uczciwość): „Kasa" NIE jest bytem L0 (brak w rejestrze; nie ma pisarza stanu kasy). „Bank" również
NIE jest bytem L0 (cel zewnętrzny wpłaty, poza 16 bytami). Rozliczenia kasowe to warstwa operacyjna nad
settlementem i księgą, bez własnego pisarza stanu.
(kody bytów w modelu technicznym `standard/mapowania/rejestr-stykow-L0.md`; nie w warstwie czytelnika)

## Protokół / przepływ
`[ZAŁOŻENIE z opisu bytów i kamieniołomu]` DOMINUJE w całej tej sekcji: brak protokołu kanonicznego dla
kasy (protokoły 1-6 dotyczą rezerwacji, zwrotu, tenderu, sprzedawalności, wyceny lojalnościowej i P2P,
żaden nie obejmuje domknięcia kasy), brak bytu kasy, brak bytu banku.

Realnie kotwiczy się TYLKO: settlement gotówkowy klienta → księga (STK-30, `[PROP+ 24.08]`) oraz wejście
sprzedażowe customer commitment → settlement (STK-25). To są styki settlement↔księga i sprzedaż↔settlement,
NIE styki kasy. Rozliczenie form bezgotówkowych (forma płatności → rozliczenie przez schemat rozliczeniowy)
oraz wpłata gotówki do banku są warstwą operacyjną bez bytu L0 i bez styku w rejestrze.

Sekwencja operacyjna (`[ZAŁOŻENIE]`): otwarcie kasy z saldem początkowym → przyjmowanie wpływów w trakcie
zmiany (gotówka klienta i formy bezgotówkowe pochodzą z rezultatu rozliczenia Płatności) → zamknięcie
kasy z przeliczeniem gotówki i uzgodnieniem wobec zarejestrowanej sprzedaży (różnica: nadwyżka lub
niedobór) → wpłata gotówki do banku → rozliczenie form bezgotówkowych przez schemat rozliczeniowy →
skutek księgowy do księgi. Uzgodnienie gotówki kotwiczy się w wpływie settlementu (STK-30); reszta łańcucha
jest do walidacji kartami L1.

## Procesy w obszarze (dług L1 → Etap C)
- 01 Od otwarcia do zamknięcia kasy · `CSH-01`
- 02 Od gotówki do wpłaty · `CSH-02`
- 03 Od przechwyconych płatności kartą do uzgodnienia wpływów dnia · `CSH-03`
- 04 Od rozliczenia do banku · `CSH-04`

## Wołania z przepływów (kto woła ten proces przekrojowy)
- Przepływ / Płatności: po zamknięciu rozliczenia klienta rezultat (settlement gotówkowy oraz forma
  bezgotówkowa) wchodzi do warstwy rozliczeń kasowych; ten proces przekrojowy uzgadnia gotówkę,
  domyka kasę, przygotowuje wpłatę i rozlicza formy bezgotówkowe. Kotwica wołania: settlement
  gotówkowy klienta → księga (STK-30) i wejście customer commitment → settlement (STK-25).
- Zwraca do wołającego lub dalej: potwierdzenie wpłaty i rozliczenia (do banku) do Przepływu / Płatności
  oraz skutek księgowy do Proces przekrojowy / Księga.

`[ZAŁOŻENIE z opisu bytów i kamieniołomu]`: pozostałe potencjalne wołania (np. zbiorcze domknięcie dnia
niezależne od pojedynczej płatności) nie mają styku w rejestrze i wymagają potwierdzenia polem 2 kart L1.

## Diagram (ILUSTRACYJNY, do potwierdzenia polem 2 kart L1)
Reguła: plain łańcuch proces→proces, bez bytów i bramek (rejestr decyzji projektowych). Węzeł = nazwa procesu w
formie „Od X do Y" (bez strzałki w nazwie); strzałka tylko na krawędzi = przekazanie. Semantyka linii:
`─▶` ciągła = przekazanie potwierdzone polem 2 karty; `⇢` przerywana = założenie do walidacji (brak karty
L1 z polem 2 lub brak styku L0); bez rombów, bez swimlane. `NN` to numer porządkowy, nie krok sekwencji.
Wołanie z Przepływu / Płatności rysujemy jako wejście; wpłata do banku i skutek do księgi jako wyjścia.
Cała sekwencja kasy jest przerywana (brak bytu kasy w L0), więc niemal wszystkie krawędzie to założenia.
```
[woła: Przepływ / Płatności · rezultat rozliczenia (gotówka i forma bezgotówkowa)] ⇢ 01 Od otwarcia do zamknięcia kasy
                                                                                      01 ⇢ 02 Od gotówki do wpłaty ⇢ 04 Od rozliczenia do banku
                                                                                      01 ⇢ 03 Od przechwyconych płatności kartą do uzgodnienia wpływów dnia ⇢ [tor niezależny: terminal-POS]
[woła: PAY-03 · kwota netto ST-ROZLICZENIE-PLATNOSCI-ZAMKNIETE] ⇢ 04 Od rozliczenia do banku ⇢ [wynik: uzgodnienie bankowe]
[skutek uzgodnienia: settlement gotówkowy → księga (STK-30)] ⇢ [do: Proces przekrojowy / Księga]
```

## Styki L0↔L0 (rejestr: STK powiązane, głównie settlement)
Jedyne realne kotwice w rejestrze (grupa 4, settlement/tender/gotówka):
- STK-30: settlement gotówkowy klienta → księga (`[PROP+ 24.08]`). To jest styk settlement↔księga, na
  którym opiera się uzgodnienie wpływu gotówkowego kasy.
- STK-25: customer commitment → settlement/tender (`[OPIS]`, wejście z Realizacji sprzedaży przez
  Płatności). Kontekst wejścia wpływu, nie styk kasy.

BRAK styku dla: otwarcia i zamknięcia kasy, przeliczenia gotówki, wpłaty do banku, rozliczenia form
bezgotówkowych przez schemat rozliczeniowy. Te elementy są warstwą operacyjną bez bytu L0
(`[ZAŁOŻENIE z opisu bytów i kamieniołomu]`). Pełne brzmienie i typy: `standard/mapowania/rejestr-stykow-L0.md`.

## Dług L1 (do Etapu C)
- NA CZELE: brak bytu L0 „kasa" do rozstrzygnięcia. Pytanie otwarte: czy rozliczenia kasowe potrzebują
  osobnego bytu lub rejestru (pisarza stanu kasy i zmiany), czy pozostają warstwą operacyjną nad
  settlementem i księgą. Analogiczne pytanie o „bank" jako cel wpłaty (byt vs punkt zewnętrzny).
- Kotwiczenie uzgodnienia gotówki: potwierdzenie, że uzgodnienie wpływu opiera się wyłącznie o STK-30,
  i domknięcie różnicy (nadwyżka lub niedobór) jako skutku księgowego.
- Rozliczenie form bezgotówkowych przez schemat rozliczeniowy: brak styku L0; do rozstrzygnięcia, czy
  potwierdzenie rozliczenia wraca do settlementu, do warstwy kasy, czy wprost do księgi.
- Wpłata gotówki do banku: klucz idempotencji zdarzenia wpłaty (brak podwójnej wpłaty i podwójnego
  zamknięcia zmiany), reconciliation „zamknięte w kasie, jeszcze niewpłacone lub nierozliczone".
- Kryterium podziału CSH-01 vs CSH-02 vs CSH-03 vs CSH-04 i potwierdzenie ich łańcucha oraz punktu
  wołania z Przepływu / Płatności polem 2 kart L1 (obecnie założenie z opisu bytów i kamieniołomu).
