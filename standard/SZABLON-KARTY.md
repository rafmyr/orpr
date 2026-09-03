# Szablon karty procesu L1 (z bankiem pytań analityka)

UWAGA (25.08.2026, decyzja właściciela): ten szablon obowiązuje WYŁĄCZNIE dla kart
POGŁĘBIONYCH (L2), tworzonych za popytem adoptera. Domyślną jednostką standardu jest karta
STANDARD wg `standard/SZABLON-KARTY-STANDARD.md` (rejestr decyzji projektowych, eksperyment minimalnej
wystarczalności). Jedno źródło prawdy formatu (P13): nowe karty NIE powstają wg tego pliku.

Zatwierdzony: rafalmyrta, 2026-08-18 (rejestr decyzji projektowych). Zasada: 1 proces = 1 plik (karta + pytania
razem). Pola 1-12 i 14 wymagane; pole 13 opcjonalne do fazy 1. Failure modes i kompensacje NIE
wchodzą do L1 (żyją w L2 przy scenariuszach). Klasy źródeł inline przy każdym twierdzeniu
nieoczywistym: `[LIT: pozycja, wersja, lokator]` albo `[AUT: R. Myrta — uzasadnienie z praktyki]`.

---

## SZABLON (kopiuj poniższą strukturę)

```markdown
# [ORPR-XXX-NN] Nazwa procesu

| | |
|---|---|
| ID | ORPR-XXX-NN |
| Wersja karty | 0.1 |
| Status | draft / reviewed / released |

**Znaczenie statusów** [AUT-R 19.08, rozstrzygnięcie właściciela]:

| Status | Co znaczy | Czym się przechodzi dalej |
|---|---|---|
| `draft` | karta w robocie, otwarte `[PROP]` dopuszczalne | arkusz decyzyjny rozstrzygnięty w całości, 0 otwartych `[PROP]` (wewnętrzna procedura redakcyjna) |
| `reviewed` | karta domknięta redakcyjnie, właściciel rozstrzygnął wszystkie twierdzenia | niezależna recenzja wydaniowa wg KONSTYTUCJI sekcja 6, recenzent **innym modelem niż główny autor** |
| `released` | **stan wewnętrzny repo**, nie publikacja publiczna. Karta jest gotowa do użycia w projekcie i nie zmienia się bez nowej wersji | publikacja publiczna repo jest **osobną decyzją właściciela**, z osobną listą warunków (m.in. domknięcie wpisów `rejestr tematów odłożonych` oznaczonych „przed wydaniem publicznym") |

Wniosek praktyczny: otwarte wpisy `rejestr tematów odłożonych` z adnotacją „obowiązkowo przed wydaniem publicznym"
**nie blokują** przejścia na `released`. Blokują publikację repo.

**1. Cel biznesowy:** (1-2 zdania, język biznesu, nie modelu)

**2. Granice:** od czego się zaczyna; na czym kończy; czego NIE obejmuje; komu oddaje pałeczkę
(ID procesów następnych).

**3. Właściciel:** (rola biznesowa)
**4. Aktorzy:** (role, nie stanowiska konkretnej firmy)
**5. Systemy:** (typy komponentów, vendor-neutral)
**6. Wyzwalacze:** (harmonogram / zdarzenie / próg / ręczne uruchomienie)

**7. Wejścia (dokumenty):**
- obowiązkowe: ...
- opcjonalne: ...

**8. Wyjścia:** dokumenty: ... | zdarzenia: ...

**9. Bramki decyzyjne:**
- warunki wejścia: ...
- warunki wyjścia: ...
- kontrole (reguły): ...

**10. Skutki:** stock: TAK/NIE (zdanie) | pieniądze: TAK/NIE (zdanie) | księgowość: TAK/NIE (zdanie)

**11. Warianty i wyjątki kluczowe:** (3-5 najważniejszych; → L2, jeśli głębia istnieje)

**12. Bezpieczniki prawne (PL):** [RM: <ref>, wersja, as_of <data>] albo „R: pending"

**13. Powiązanie w górę (opcjonalne do fazy 1):** value stream: ... | typowe KPI: ...

## 14. Bank pytań analityka

### A. Do biznesu (na warsztat)
A1. Pytanie? *(Dlaczego ważne: 1 zdanie.)* (typowe warianty odpowiedzi, jeśli znane)

### B. Do legacy (obserwowalne zachowanie obecnego systemu, nie kod)
B1. „Co się dzieje, gdy...?"

### C. Do vendora (czy i gdzie nowy system to obsługuje)
C1. Pytanie o funkcję + o miejsce w dokumentacji + o konfigurowalność.

### 🚩 Czerwone flagi (braki wychodzące typowo dopiero w UAT / po starcie)
F1. ...
```

Zasady jakości pytań: każde rozstrzygalne (tak/nie/liczba/procedura); każde z „dlaczego ważne";
wyjątki > happy path; pytania z praktyki autorskiej z tagiem [AUT].

---

## PRZYKŁAD WYPEŁNIONY (wzorzec jakości)

# [ORPR-DEM-01] Od popytu do zapotrzebowania netto

| | |
|---|---|
| ID | ORPR-DEM-01 (wg standard/mapa-procesow.md; freeze notacji: obowiązuje od v0.1.0) |
| Wersja karty | 0.1 |
| Status | draft |

**1. Cel biznesowy:** przełożyć prognozę (albo jawną metodę alternatywną) na wyjaśnione,
wersjonowane zapotrzebowanie netto per artykuł, lokalizacja i okres.

**2. Granice:** od zatwierdzonej prognozy / wniosku sklepu do zatwierdzonego zapotrzebowania
opublikowanego do alokacji. NIE wybiera źródeł pokrycia (→ proces alokacji). Zero skutków
stockowych i finansowych.

**3. Właściciel:** Supply Chain
**4. Aktorzy:** planista, kupiec
**5. Systemy:** POS centralny, ERP-zapasy, ERP-zakupy, silnik replenishment
**6. Wyzwalacze:** harmonogram; próg zapasu; zatwierdzona wersja prognozy; promocja; uprawnione
uruchomienie ręczne

**7. Wejścia:** obowiązkowe: stan zapasu (pozycja magazynowa), polityka replenishmentu, status
asortymentowy pozycji dla lokalizacji; opcjonalne: prognoza, wniosek sklepu, definicja promocji.

**8. Wyjścia:** dokumenty: zapotrzebowanie netto, propozycja zamówienia | zdarzenia:
zapotrzebowanie-wyliczone.

**9. Bramki decyzyjne:**
- wejścia: jedna aktywna authority planowania; prognoza rozłożona do poziomu
  artykuł-lokalizacja-okres; brak statusu asortymentowego pozycji BLOKUJE kalkulację (brak wpisu
  nie jest zgodą na zamawianie) [AUT: R. Myrta — domyślne „prowadzony" generuje zamówienia
  na asortyment, którego apteka nigdy nie miała].
- wyjścia: każde zapotrzebowanie ma odtwarzalne wyjaśnienie kalkulacji; zapotrzebowanie = 0 niesie
  jawny powód (nie potrzeba ≠ nie wolno).
- kontrole: jedna authority planowania; formuła netto na stanie brutto przed rezerwacjami;
  zapas wygasający przed datą popytu wykluczony z pokrycia.

**10. Skutki:** stock: NIE | pieniądze: NIE | księgowość: NIE — kalkulacja jest decyzją
planistyczną, wykonanie należy do zamówień i transferów.

**11. Warianty i wyjątki kluczowe:** brak zatwierdzonej prognozy → jawna metoda alternatywna
z polityki; pozycja wolnorotująca → reguła półkowa min-max zamiast prognozy [AUT]; pozycja
w trybie uzupełniania przez dostawcę → sygnał popytu zbierany, zapotrzebowanie zero z powodem;
limit przydziału hurtowni nieznany → planuj i oznacz jako niepotwierdzone [AUT].

**12. Bezpieczniki prawne (PL):** R: pending (kandydaci: reglamentacja obrotu lekami
deficytowymi — do powiązania z regulatory-matrix przy redakcji domeny).

**13. Powiązanie w górę:** (do uzupełnienia od fazy 1)

## 14. Bank pytań analityka

### A. Do biznesu
A1. Kto dziś decyduje, ile placówka zamawia: centrala, kierownik, czy system — i czy jednakowo
dla wszystkich kategorii? *(Rozstrzyga tryb planowania per kategoria — pierwsza oś konfiguracji.)*
A2. Co się dzieje z zamawianiem pozycji sprzedającej się 2-3 razy na kwartał? *(Prognoza
statystyczna zaokrągla ją do zera i pozycja znika z asortymentu; potrzebna reguła półkowa.)* [AUT]
A3. Czy hurtownie limitują ilości na produkty deficytowe i jak dziś to obchodzicie?
*(Reglamentacja wymaga limitu per dostawca-lokalizacja-artykuł-okno; bez tego system planuje
ilości, których nikt nie wyda.)* [AUT]

### B. Do legacy
B1. Z jakiego stanu system liczy propozycję (czy odejmuje rezerwacje?), z jakim oknem pokrycia,
i czy propozycję da się prześledzić do składników?

### C. Do vendora
C1. Czy system rozróżnia audytowalnie zatwierdzenie prognozy przez człowieka od systemowego?
Gdzie w dokumentacji jest tryb wyjątków?

### 🚩 Czerwone flagi
F1. Zapotrzebowanie = 0 bez jawnego powodu: „nie potrzeba" i „nie wolno" wyglądają identycznie —
wychodzi przy pierwszej reklamacji kierownika o brak towaru. [AUT]
