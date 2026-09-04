# ORPR-PAY-02 — Od autoryzacji do przechwycenia

> [!NOTE]
> To publiczny skrót zweryfikowanej karty procesu. Ułatwia ocenę, czy proces jest istotny dla
> organizacji, ale nie jest instrukcją wdrożeniową ani pełną specyfikacją ORPR.

**Obszar:** Płatności klientów
**Dostępność:** skrót publiczny; pełna karta ma status `reviewed` i pozostaje poza publiczną próbką.

## Po co istnieje

Pieniądze klienta są skutecznie pobrane, ale wyłącznie dla tych pozycji kompozycji pokrycia, które wymagają potwierdzenia przez zewnętrznego operatora.

## Granice i odpowiedzialność

- **Granica procesu:** od autoryzacji do przechwycenia.
- **Typowy właściciel:** Sales Operations.

## Przebieg w skrócie

1. Rozpoznanie sytuacji początkowej i zakresu konkretnego przebiegu.
2. Sprawdzenie danych, warunków rozpoczęcia i odpowiedzialności.
3. Przeprowadzenie głównego rozstrzygnięcia właściwego dla procesu.
4. Obsługa różnicy, odmowy albo wyjątku, jeżeli wystąpi.
5. Utrwalenie wyniku i przekazanie go do kolejnego procesu albo właściciela.

## Przykładowe pytania diagnostyczne

- Które formy z kompozycji wymagają potwierdzenia operatora, zanim zapłata stanie się skuteczna?
- Przy rozdzieleniu w czasie: jakie zdarzenie dopuszcza przechwycenie po autoryzacji?

## Przykładowe sygnały ostrzegawcze

- Sprzedaż jest cofnięta, należność została tylko zablokowana, a blokada nie ma zwolnienia.
- Kwota albo chwila przechwycenia zostaje zmieniona po zapisie.

## Co zawiera pełna karta

Pełna wersja rozwija granice, wejścia i wyjścia, niezmienniki, kontrakty danych, warianty,
wyjątki, kompletny bank pytań, czerwone flagi oraz powiązania z Regulatory Matrix. Dostęp do
pełnego materiału: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

[Wróć do katalogu kart](../KARTY-PROCESOW.md)
