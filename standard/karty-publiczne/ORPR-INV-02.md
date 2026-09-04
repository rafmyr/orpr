# ORPR-INV-02 — Od transferu do przyjęcia

> [!NOTE]
> To publiczny skrót zweryfikowanej karty procesu. Ułatwia ocenę, czy proces jest istotny dla
> organizacji, ale nie jest instrukcją wdrożeniową ani pełną specyfikacją ORPR.

**Obszar:** Zapas
**Dostępność:** skrót publiczny; pełna karta ma status `reviewed` i pozostaje poza publiczną próbką.

## Po co istnieje

Ilość przemieszczana między dwiema ewidencyjnymi lokalizacjami tej samej organizacji ma zapisane OBA BOKI na wspólnym kluczu pozycji przesunięcia i pozostaje otwarta do uzgodnienia, a po terminalnym rozstrzygnięciu każdej materialnej pozycji przesunięcie jest domknięte jednym zdarzeniem kanonicznym, które niesie wyłącznie ilość uzgodnioną.

## Granice i odpowiedzialność

- **Granica procesu:** od transferu do przyjęcia.
- **Typowy właściciel:** Operacje zapasu, z rolą uprawnioną do zatwierdzenia przesunięcia po stronie lokalizacji źródłowej i rolą potwierdzającą przyjęcie po stronie docelowej.

## Przebieg w skrócie

1. Rozpoznanie sytuacji początkowej i zakresu konkretnego przebiegu.
2. Sprawdzenie danych, warunków rozpoczęcia i odpowiedzialności.
3. Przeprowadzenie głównego rozstrzygnięcia właściwego dla procesu.
4. Obsługa różnicy, odmowy albo wyjątku, jeżeli wystąpi.
5. Utrwalenie wyniku i przekazanie go do kolejnego procesu albo właściciela.

## Przykładowe pytania diagnostyczne

- Kto ma prawo zatwierdzić przesunięcie i czy to samo prawo obejmuje przesunięcie zwrotne?
- Który zapis jest dowodem wydania: potwierdzenie roli w lokalizacji źródłowej czy potwierdzenie odbioru przez przewoźnika?

## Przykładowe sygnały ostrzegawcze

- Przesunięcie jest domykane automatycznie po upływie czasu, bez zarejestrowanego boku przyjęcia i bez klasy terminalnej pozycji.
- Rozchód w lokalizacji źródłowej i przychód w docelowej są dwoma niezależnymi dokumentami, bez wspólnego identyfikatora pozycji.

## Co zawiera pełna karta

Pełna wersja rozwija granice, wejścia i wyjścia, niezmienniki, kontrakty danych, warianty,
wyjątki, kompletny bank pytań, czerwone flagi oraz powiązania z Regulatory Matrix. Dostęp do
pełnego materiału: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

[Wróć do katalogu kart](../KARTY-PROCESOW.md)
