# Manifest pokrycia L0 — pisarz stanu → proces na mapie albo decyzja wyłączenia

Status: **ZATWIERDZONY DYKTANDEM WŁAŚCICIELA 2026-08-30** (`1a`, `2a`, `3a`, `4a`, `5c`; werdykty
i warianty odrzucone w wewnętrznym rejestrze decyzji, wpis z 30.08). Przypisania nie są już `[PROP]`.
Pilnowany asercją wewnętrzny materiał roboczy.

Po co: audyt 25.08 złapał sierotę infra (STX) ręcznie, właściciel złapał sierotę biznesową
(SRC, oś category managementu) okiem. Ten manifest + asercja robią to mechanicznie: dla każdego
z 16 pisarzy stanu L0 (zamrożony `rejestr-stykow-L0.md`, sekcja A) musi istnieć albo proces na
mapie produkujący jego stan, albo decyzja wyłączenia w rejestr decyzji projektowych. Byt bez jednego i drugiego =
SIEROTA = błąd twardy.

Reguły dla asercji (jak czyta ten plik):
- Kolumna `Byt` = kod L0. Zbiór bytów TU musi = zbiór z rejestru sekcja A (kontrola K-L0-KOMPLET).
- Kolumna `Status` ∈ {POKRYTY, WYŁĄCZONY, ZAPLANOWANY, LUKA} (**`ZAPLANOWANY` dodany Wyjątkiem 9, 2026-08-30**).
- Kolumna `Dowód`: dla POKRYTY = stałe ID procesu obecne w **warstwie A spisu F2b** w backtickach
  (np. `PRC-01`); dla WYŁĄCZONY i **ZAPLANOWANY** = dosłowna fraza-kotwica obecna w rejestr decyzji projektowych;
  dla LUKA = `-`. **Źródło istnienia procesu zmienione z mapy nawigacyjnej na spis Wyjątkiem 9**
  (pomiar 2026-08-30: mapa stała przy 39 procesach, spis miał 67; pozycja długu `H16`).
- `ZAPLANOWANY` ≠ `WYŁĄCZONY`: wyłączony znaczy „świadomie nie opisujemy”, zaplanowany znaczy
  „mapa POWINNA to wytwarzać i nie wytwarza”. Oba wymagają kotwicy, więc żadnego nie da się
  wpisać bez decyzji właściciela.
- LUKA zawsze FAILuje. To celowe: sierota ma świecić na czerwono, dopóki właściciel nie podejmie
  decyzji (pokryć procesem-kandydatem albo wyłączyć jak STX).

| Byt | Status | Dowód | Nota (co produkuje / dlaczego taki status) |
|---|---|---|---|
| MCO | POKRYTY | `AST-02` | offer scope + category plan; `AST-02` wytwarza `ST-STRATEGIA-KATEGORII-ZATWIERDZONA` (warstwa A) i jest pisarzem rejestru `PLAN-KATEGORII`. Proces pozostaje zakresowy: występuje, gdy organizacja stosuje formalne zarządzanie kategorią. **Pozycja zamknięta decyzją właściciela rangi wydania 2026-09-03** (integracja `AST-02`); wcześniejsze DYKTANDO [AUT-R 2026-08-30] wariant `c` i pomiar z 67 wyników warstwy A są historyczne |
| PIN | POKRYTY | `AST-01` | fakt/rekord produktu; **DYKTANDO [AUT-R 2026-08-30]:** `AST-01` wytwarza `ST-DANE-PRODUKTU` (warstwa A) i jest pisarzem rejestru `DANE-PRODUKTU`. Sugestia z 25.08, żeby wyłączyć jak `STX`, **odrzucona**: powstała, gdy mapa nie miała nic produkującego dane produktu |
| SRC | POKRYTY | `SUP-01` | relacja z dostawcą + kontrakt + warunki; **DYKTANDO [AUT-R 2026-08-30]:** `SUP-01` wytwarza `ST-WARUNKI-HANDLOWE` i jest pisarzem rejestru `WARUNKOW-HANDLOWYCH`; `dowod` wiersza sam wskazuje sierotę `SRC`. **Pokryta jest główna treść bytu, nie cała** — kontrakt produkuje `LEG-01`, samej relacji nie produkuje nikt; wariant z notą o tym odrzucony w rejestr decyzji projektowych |
| PO | POKRYTY | `PRC-01` | zamówienie zakupowe; Od zapotrzebowania do zamówienia produkuje PO |
| OBLIG | POKRYTY | `PRC-03` | 3-way match + zobowiązanie do zapłaty; Od faktury do zobowiązania |
| SUP | POKRYTY | `DEM-04` | supply plan + allocation + availability + admission; Od ograniczeń do alokacji (wsparcie: DEM-01) |
| LEX | POKRYTY | `INV-01` | on-hand + ruch fizyczny; Od przyjęcia do dostępności (wariancja: INV-03/04) |
| SITE | POKRYTY | `LOC-02` | lokalizacja: tożsamość + licencja + jurysdykcja; **DYKTANDO [AUT-R 2026-08-30]:** `LOC-02` wytwarza `ST-ZMIANA-LOKALIZACJI-DOMKNIETA` i jest **pisarzem** rejestru `PORTFEL-LOKALIZACJI` (potwierdzone przy `H3`). `LOC-01` odrzucony: produkuje zamiar (`ST-DECYZJA-LOKALIZACYJNA`) i jest czytelnikiem rejestru, nie pisarzem |
| STX | WYLACZONY | `Byt L0 STX pozostaje ZAMROŻONY` | store execution: warstwa wykonania/infra, świadomie poza mapą procesów (decyzja 25.08) |
| CXR | POKRYTY | `CRM-01` | relacja + party identity + księga punktów; **DYKTANDO [AUT-R 2026-08-30]:** `CRM-01` wytwarza `ST-RELACJA-Z-KLIENTEM-ZIDENTYFIKOWANA` i `ST-KSIEGA-LOJALNOSCIOWA-AKTUALNA`. Nota z 25.08 o CRM poza zakresem v0.x jest nieaktualna. **`C6` ROZSTRZYGNIĘTE I WYKONANE [AUT-R 2026-08-30, wariant `a`]:** księga lojalnościowa ma wiersz w `# REJESTRY` spisu z pisarzem `CRM-01`. Pytanie o POPRZEDNI stan księgi dostało odpowiedź: to odczyt własnego rejestru między przebiegami, nie osobne wejście — wzorzec `STANDARDOW` przy `BRD-01` (`A2` = b). Zdanie „`C6` zostaje otwarte” stało tu do 31.08 i było nieaktualne o dobę; zdjęte po findingu `F5` recenzji Sola |
| SFC | POKRYTY | `SAL-01` | zamówienie klienta + customer commitment + Transaction Eligibility; Od koszyka do sprzedaży |
| SRV | POKRYTY | `RTN-02` | sprawa zwrotu (+ orkiestrator); Od sprzedaży do zwrotu |
| SFT | POKRYTY | `PAY-01` | settlement + gotówka + AR; Od kwoty do formy płatności (AR = kandydat D8, nota; łańcuch PAY-01..03) |
| REBATE | POKRYTY | `PRC-04` | accrual → settled (`ST-KORZYSC-ROZLICZONA`; poprzednia nazwa `ST-RABAT-RETRO-ROZLICZONY` = przypadek retro); Od warunków handlowych do rozliczenia korzyści pozafakturowych |
| FIN | POKRYTY | `FIN-01` | księga + podatek; Od sprzedaży do księgi (specjalizacje FIN-02/03) |
| RCA | POKRYTY | `CTL-02` | polityka + reguła + compliance case + remediacja; Od wyjątku do rozwiązania (audyt: CTL-03) |

## Odczyt stanu zweryfikowany 2026-09-01

Pokrycie L0: **16 bytów, 0 sierot (`LUKA`), 0 ostrzeżeń miękkich**. Pozostaje **jeden byt
`ZAPLANOWANY`: brak** — `MCO` zamknięty 2026-09-03 integracją `AST-02` (decyzja właściciela
rangi wydania). Mapa nawigacyjna i warstwa A spisu F2b obejmują po **74 procesy**; różnice
identyfikatorów procesów w obu kierunkach są puste.

**Przebieg historyczny.** Zapis z 25.08 mówił o pięciu sierotach (`MCO`, `PIN`, `SRC`, `SITE`,
`CXR`) przy ówczesnej mapie około 39-procesowej. Pomiar z 30.08 użył wersji spisu F2b z 67
procesami; **cztery z pięciu miały już producenta**, sprawdzonego odczytem kolumny
`stan_wyjsciowy` i sekcji `# REJESTRY`. Piąty (`MCO`) producenta nie miał i pozostaje wynikiem
**negatywnym testu prospektywnego**, nie jego brakiem: pytanie brzmiało „czy mapa POWINNA mieć
producenta tego stanu" i przy `MCO` odpowiedź brzmi „tak, a nie ma".

**Bilans przejścia: cztery pozytywne, jeden negatywny.** Tego wymagała pozycja długu `H10` —
kontrola dodatnia **i** ujemna. Przejście na samych pozytywnych byłoby powtórzeniem wady metody
`G2`, którą recenzja nazwała findingiem `F2`.

**Czego ten manifest nie rozstrzyga** (te same granice, co asercja): czy przypisanie proces↔byt
jest merytorycznie trafne i czy proces produkuje CAŁY stan bytu, czy tylko główną jego treść.
Przy `SRC` jest to jawnie tylko główna treść. Rozstrzygnięcie należy do właściciela i recenzenta.

**Zgodność z mapą nawigacyjną.** Pomiar 2026-09-01: `standard/mapa-procesow.md` i warstwa A
spisu F2b mają po **70 procesów**, a różnice identyfikatorów w obu kierunkach są puste. Asercja
nie raportuje ostrzeżeń miękkich. Historyczny rozjazd zamknęła pozycja długu `H16`.
