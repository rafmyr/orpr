# ORPR-PAY-01 — Od kwoty do formy płatności

> [!NOTE]
> To publiczny skrót zweryfikowanej karty procesu. Ułatwia ocenę, czy proces jest istotny dla
> organizacji, ale nie jest instrukcją wdrożeniową ani pełną specyfikacją ORPR.

**Obszar:** Płatności klientów
**Dostępność:** skrót publiczny; pełna karta ma status `reviewed` i pozostaje poza publiczną próbką.

## Po co istnieje

Dla kwoty należnej istnieje zaakceptowany zestaw form rozliczenia (kompozycja pokrycia), czyli rozstrzygnięcie, jaką formą i w jakiej części kwota ma zostać uregulowana, w jakiej walucie i z jaką klasą momentu przyjęcia należności.

## Granice i odpowiedzialność

- **Granica procesu:** od kwoty do formy płatności.
- **Typowy właściciel:** Rola odpowiedzialna za rozliczenia klienta; przy transakcji rolę wykonawczą pełni operator sprzedaży.

## Przebieg w skrócie

1. Rozpoznanie sytuacji początkowej i zakresu konkretnego przebiegu.
2. Sprawdzenie danych, warunków rozpoczęcia i odpowiedzialności.
3. Przeprowadzenie głównego rozstrzygnięcia właściwego dla procesu.
4. Obsługa różnicy, odmowy albo wyjątku, jeżeli wystąpi.
5. Utrwalenie wyniku i przekazanie go do kolejnego procesu albo właściciela.

## Przykładowe pytania diagnostyczne

- Jaki jest zbiór form rozliczenia dopuszczonych w tej transakcji?
- Która rola ustala i zmienia ten zbiór?

## Przykładowe sygnały ostrzegawcze

- Proces jest wykazywany jako zakończony dopiero po potwierdzeniu przez zewnętrznego operatora, czyli granica z procesem autoryzacji jest przesunięta w stronę tej karty.
- Kompozycja niekompletna wobec ustalonej reguły albo ustalonej reguły jest widoczna dla procesu autoryzacji jako wybrana forma płatności.

## Co zawiera pełna karta

Pełna wersja rozwija granice, wejścia i wyjścia, niezmienniki, kontrakty danych, warianty,
wyjątki, kompletny bank pytań, czerwone flagi oraz powiązania z Regulatory Matrix. Dostęp do
pełnego materiału: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

[Wróć do katalogu kart](../KARTY-PROCESOW.md)
