# ORPR-PAY-03 — Od przechwyconych płatności do rozliczenia partii z operatorem

> [!NOTE]
> To publiczny skrót zweryfikowanej karty procesu. Ułatwia ocenę, czy proces jest istotny dla
> organizacji, ale nie jest instrukcją wdrożeniową ani pełną specyfikacją ORPR.

**Obszar:** Płatności klientów
**Dostępność:** skrót publiczny; pełna karta ma status `reviewed` i pozostaje poza publiczną próbką.

## Po co istnieje

Dla wskazanej partii płatności należność od operatora jest rozliczona z kwotami przechwyconymi od klientów: każda przechwycona płatność objęta partią jest albo ujęta w raporcie operatora, albo nazwana jako nieujęta, przejście od kwoty brutto do kwoty netto ma nazwane pozycje z typem, a kwota, którą operator deklaruje jako należną firmie, jest uzgodniona.

## Granice i odpowiedzialność

- **Granica procesu:** od przechwyconych płatności do rozliczenia partii z operatorem.
- **Typowy właściciel:** Rola odpowiedzialna za rozliczenia z operatorami płatności, odrębna od operatora sprzedaży i roli uzgadniającej dzień w lokalizacji.

## Przebieg w skrócie

1. Rozpoznanie sytuacji początkowej i zakresu konkretnego przebiegu.
2. Sprawdzenie danych, warunków rozpoczęcia i odpowiedzialności.
3. Przeprowadzenie głównego rozstrzygnięcia właściwego dla procesu.
4. Obsługa różnicy, odmowy albo wyjątku, jeżeli wystąpi.
5. Utrwalenie wyniku i przekazanie go do kolejnego procesu albo właściciela.

## Przykładowe pytania diagnostyczne

- Co w raporcie operatora jest tożsamością partii?
- Który operator rozlicza każdą przechwyconą płatność?

## Przykładowe sygnały ostrzegawcze

- Ta sama przechwycona płatność jest w dwóch zamkniętych partiach albo nie jest w żadnej, choć raport ją zadeklarował.
- Przechwycone płatności poza każdym raportem znikają z widoku.

## Co zawiera pełna karta

Pełna wersja rozwija granice, wejścia i wyjścia, niezmienniki, kontrakty danych, warianty,
wyjątki, kompletny bank pytań, czerwone flagi oraz powiązania z Regulatory Matrix. Dostęp do
pełnego materiału: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

[Wróć do katalogu kart](../KARTY-PROCESOW.md)
