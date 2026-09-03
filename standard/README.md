# standard/ — treść ORPR

Struktura docelowa (wypełniana od Etapu 0):

```
standard/
  L0-katalog.md               mapa domen i value streams, jedna strona
  domeny/
    <DOMENA>/
      karta-domeny.md         po co, granice, powiązania
      ORPR-<DOM>-<NN>-*.md    karty procesów L1 (+ bank pytań analityka)
      bezpieczniki-R.md       wymogi regulacyjne (link do regulatory-matrix, wersja+as_of)
      L2/                     scenariusze i kroki — TYLKO wg popytu (pułapka P1)
  profile/
    pharmacy/                 nakładka apteczna (pierwsza)
  agent-pack/                 eksport strukturalny per moduł (dla agentów AI)
```

## Notacja (freeze: PENDING — do decyzji właściciela przed wydaniem 0.x)

Dwie warstwy, rozdzielone (decyzja 2026-08-24, rejestr decyzji projektowych):

**1. Alias techniczny (stabilny obiekt standardu).**
- Proces: `ORPR-<KOD DOMENY 3 lit.>-<NN>` np. ORPR-SAL-01. Na mapie skrót bez prefiksu: `SAL-01`.
- Dokument: `ORPR-DOC-<nazwa>` | Reguła: `ORPR-BR-<nazwa>` | Scenariusz: `ORPR-SCN-<...>`
- Alias jest stabilny: przeniesienie procesu między obszarami go NIE zmienia.
- Po freeze identyfikatory są NIEZMIENNE (zmiana = decyzja rangi wydania, z deprecation).

**2. Ścieżka nawigacyjna (gdzie proces jest na aktualnej mapie).**
- Gramatyka: `<rodzaj> / <obszar> / <NN> · <początek → wynik> · <alias>`, rodzaj ∈ {Przepływ, Wspólne}.
- Obszar identyfikowany NAZWĄ, nie numerem. `NN` = numer porządkowy w obszarze, nie krok sekwencji.
- Kody bytów (LEX/SFT/FIN) NIE wchodzą do ścieżki (żyją w rejestrze styków).
- Pełna mapa i reguły: `standard/mapa-procesow.md`. Kody domen jako checklista pokrycia: `standard/mapa-procesow.md` (DEPRECATED jako struktura, P13).

## Zasady treści

1. Każde twierdzenie nieoczywiste ma klasę źródła: [LIT: pozycja, wersja, lokator — bez
   reprodukcji treści] albo [AUT: R. Myrta + jedno zdanie uzasadnienia z praktyki].
2. Zero materiałów klientów/pracodawców (clean-room, zasady governance projektu D5). Deklaracja clean-room
   w karcie każdego modułu, z datą.
3. Bezpieczniki prawne: pokryte → link do RM; niepokryte → jawne „R: pending".
4. Język: PL do wydania dla pierwszego adoptera; EN od publikacji (zasady governance projektu, fazy).
5. Sektorowa neutralność rdzenia: karta w `domeny/` jest branżowo neutralna; treść sektorowa (produkty, ustawy branżowe) wyłącznie w `profile/<branża>/` i bezpiecznikach R. Pułapka P15.
