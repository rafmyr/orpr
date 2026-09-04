# ORPR-CSH-03 — Od przechwyconych płatności kartą do uzgodnienia wpływów dnia

> [!NOTE]
> To publiczny skrót zweryfikowanej karty procesu. Ułatwia ocenę, czy proces jest istotny dla
> organizacji, ale nie jest instrukcją wdrożeniową ani pełną specyfikacją ORPR.

**Obszar:** Rozliczanie kas i utargu
**Dostępność:** skrót publiczny; pełna karta ma status `reviewed` i pozostaje poza publiczną próbką.

## Po co istnieje

Przy zamknięciu zmiany raport terminala jest porównywany z płatnościami kartą zapisanymi w POS, a wynik dnia pozwala zejść do konkretnego stanowiska i wyjaśnić każdą różnicę.

## Granice i odpowiedzialność

- **Granica procesu:** od przechwyconych płatności kartą do uzgodnienia wpływów dnia.
- **Typowy właściciel:** Sales Operations.

## Przebieg w skrócie

1. Rozpoznanie sytuacji początkowej i zakresu konkretnego przebiegu.
2. Sprawdzenie danych, warunków rozpoczęcia i odpowiedzialności.
3. Przeprowadzenie głównego rozstrzygnięcia właściwego dla procesu.
4. Obsługa różnicy, odmowy albo wyjątku, jeżeli wystąpi.
5. Utrwalenie wyniku i przekazanie go do kolejnego procesu albo właściciela.

## Przykładowe pytania diagnostyczne

- Jaki jest maksymalny czas między zamknięciem zmiany a otrzymaniem raportu zamknięcia terminala, po którym zmiana staje się pozycją oczekującą?
- Czy terminal może być współdzielony przez więcej niż jedno stanowisko albo mobilny między stanowiskami w tej samej zmianie?

## Przykładowe sygnały ostrzegawcze

- Zmiany bez wyniku poziomu (1) nie mają wieku i znikają z widoku po zamknięciu dnia biznesowego.
- Różnice są zamykane wpisem o stałej, powtarzalnej treści bez wskazania przyczyny.

## Co zawiera pełna karta

Pełna wersja rozwija granice, wejścia i wyjścia, niezmienniki, kontrakty danych, warianty,
wyjątki, kompletny bank pytań, czerwone flagi oraz powiązania z Regulatory Matrix. Dostęp do
pełnego materiału: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

[Wróć do katalogu kart](../KARTY-PROCESOW.md)
