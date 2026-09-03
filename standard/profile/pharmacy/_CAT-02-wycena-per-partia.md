# Profil: pharmacy — nakładka do ORPR-CAT-02 Price-to-POS

Status: surowiec profilu (nie karta rdzenia). Data: 2026-08-19.
Powód istnienia tego pliku: reguła P15. Rdzeń standardu zna wyłącznie pojęcia-klasy; instancje
branżowe mieszkają tutaj. Karta rdzenia ORPR-CAT-02 opisuje **wycenę per partia** jako klasę
(„występuje tam, gdzie towar jest identyfikowalny co do dostawy") i nie nazywa żadnej branży.

## Obserwacja branżowa

**Wycena per partia jest modelem typowym dla aptek w Polsce.** [AUT-R: R. Myrta, dyktando
19.08.2026] Jedno SKU bywa jednocześnie w kilku cenach, zależnych od dostawy; towar jest metkowany
razem z ceną przy przyjęciu, więc ten sam produkt leży na półce w różnych cenach.

Model przeciwstawny, częstszy w pozostałym retailu: każda nowa dostawa uspójnia cenę wszystkich
sztuk na półce do jednej wartości.

## Co z tego wynika dla wdrożenia w tej branży

Wszystkie konsekwencje opisane są w rdzeniu (ORPR-CAT-02) jako właściwości modelu partiowego,
nie jako właściwości apteki. Tutaj tylko wskazanie, że w tej branży model partiowy jest
domyślnym punktem wyjścia, a nie wariantem do sprawdzenia:

- klucz rekordu ceny to pozycja plus partia plus zakres plus kanał (rdzeń, oś 3);
- rozjazd metka kontra kasa jest strukturalny, bo kasa skanuje identyfikator pozycji, a nie partii
  (rdzeń, flaga F3);
- cena odniesienia przy wielu cenach jednocześnie wymaga rozstrzygnięcia, której ceny użyć
  (rdzeń, pole 12; zgłoszony GAP do regulatory-matrix).

## Czego tu NIE ma i mieć nie będzie

Warstwa regulacyjna specyficzna dla branży (kategorie z ceną urzędową, refundacja, ograniczenia
reklamy) nie jest opisywana ani tutaj, ani w rdzeniu. Wchodzi wyłącznie jako overlay w repozytorium
regulatory-matrix i jest linkowana, nie przepisywana (zasada bezpieczników R).

## Powiązania

- rdzeń: `standard/domeny/CAT/ORPR-CAT-02-price-to-pos.md`, oś 3 modelu pojęciowego
- druga nakładka tego profilu: `standard/profile/pharmacy/_CAT-03-surowiec.md`
- reguła separacji: wewnętrzny rejestr pułapek jakościowych, pułapka P15
