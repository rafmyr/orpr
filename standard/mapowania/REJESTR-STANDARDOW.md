# Rejestr standardów sieci — szablon i zasady [AUT-R 2026-08-26, R3]

Artefakt współdzielony standardu ORPR. Rozstrzyga dom „obowiązkowej marki i standardów"
(rejestr granic E.27; krajobraz sekcja A4). Jeden wspólny rejestr dla wszystkich standardów,
które organizator sieci narzuca lub udostępnia uczestnikom (franczyza miękka/twarda,
partnerstwo). Status: szablon; wypełnienie per konkretna sieć jest pracą wdrożeniową (F2+).

## Po co ten rejestr

Franczyza i sieć partnerska opierają się na standardach. Bez jednego miejsca, które mówi
„co obowiązuje, czyje to i gdzie", proces mapowania nie domyka punktu „obowiązkowa marka
i standardy" dla T3b/T2. Rejestr jest tym miejscem. Nie zastępuje obszarów merytorycznych —
wskazuje właściciela TREŚCI każdego standardu i spina wdrożenie (#16), kontrolę (#10)
i umocowanie prawne (#21).

## Podział ról (za krajobrazem A4)

| Rola | Obszar |
|---|---|
| tworzy i aktualizuje standard MARKI | #15 Marketing |
| właściciel treści standardu operacyjnego / zakupowego / asortymentowego / bezpieczeństwa / IT | odpowiedni obszar merytoryczny (#16 / #11 / #10 / #20 …) |
| wykonuje standard w lokalizacji | #16 Operacje lokalizacji |
| kontroluje wykonanie, rejestruje niezgodności, nadzoruje naprawy | #10 Kontrola i zgodność |
| reguluje tytuł do marki i umowny obowiązek stosowania | #21 Prawo i umowy |

Zasada: **nie wszystkie standardy mieszkają w Marketingu.** Marketing jest domem wyłącznie
standardu MARKI. Reszta zostaje u właściciela merytorycznego; #16/#10/#21 to wspólny
mechanizm wdrożenia-kontroli-umocowania.

## Szablon rejestru (pola obowiązkowe)

| Pole | Opis |
|---|---|
| `nazwa_standardu` | jednoznaczna nazwa (np. „Ekspozycja witryny", „Minimalny asortyment obowiązkowy", „Standard obsługi kasy") |
| `wlasciciel` | obszar merytoryczny odpowiedzialny za treść (np. #15 dla marki, #11 dla asortymentu) |
| `wersja_i_data` | wersja standardu oraz data obowiązywania (od kiedy) |
| `placowki_lub_formaty` | placówki lub formaty objęte standardem (np. „wszystkie sklony franczyzy twardej", „format convenience") |
| `charakter` | **[Z4/W1]** słownik kontrolowany: `wiążący_jednostronnie` (M2) / `obowiązkowy_zamknięty` (M1b) / `rekomendowany` (bez mocy wiążącej) — rozróżnia standard narzucony od udostępnianego; wartość spoza słownika = status „nierozstrzygnięty" |
| `zatwierdzone_wyjatki` | wyjątki zatwierdzone dla konkretnych placówek/okresów (kto i kiedy zatwierdził) |

Pole `charakter` [Z4/W1] jest OBOWIĄZKOWE dla franczyzy twardej (M2) ORAZ miękkiej (M1b): dla
M2 rozróżnia standard wiążący jednostronnie od rekomendowanego, dla M1b — obowiązkowy zamknięty
od rekomendowanego. Pola opcjonalne przy wdrożeniu: mechanizm
kontroli (#10), podstawa umowna (#21), sankcja za niezgodność, kanał publikacji standardu.

## Przykład wypełnienia (ilustracyjny, nie dane realnej sieci)

| nazwa_standardu | wlasciciel | charakter | wersja_i_data | placowki_lub_formaty | zatwierdzone_wyjatki |
|---|---|---|---|---|---|
| Ekspozycja i logo w witrynie | #15 Marketing | wiążący jednostronnie (M2) | v3, od 01.09.2026 | wszystkie placówki z szyldem | placówki zabytkowe — zgoda działu marki, bezterminowo |
| Minimalny asortyment obowiązkowy | #11 Asortyment | obowiązkowy zamknięty (M1b) | v2, od 01.07.2026 | franczyza twarda | sklep #217 (mała powierzchnia) — zakres skrócony, do 31.12.2026 |
| Standard obsługi klienta przy kasie | #16 Operacje | rekomendowany | v1, od 15.08.2026 | wszystkie formaty | brak |

## Powiązanie z testem

Rejestr domyka punkt 1 protokołu testu (przypisanie obszaru) dla profili opartych na
obowiązkowej marce i standardach: **T3b (franczyza miękka)** i **T2 (franczyza twarda)**.

**Konsekwencja braku pola `charakter`** [AUT-R 2026-08-26, ZZ3]: standard bez wpisanego
`charakter` ma status „nierozstrzygnięty" co do mocy wiążącej — nie wiadomo, czy mieści się
w zakresie upoważnienia M2 (wiążący) czy poza nim (sklep zachowuje swobodę). Brak `charakter` **blokuje ustalenie profilu ZARÓWNO M2 (zakres wiążący), JAK I M1b
(obowiązkowy zamknięty vs rekomendowany)** [W1] — analogicznie do braku właściciela blokującego
punkt 1; nie zmienia typu relacji.
Kontrola negatywna retestu: po USUNIĘCIU właściciela standardu z rejestru profil T3b NIE
powinien się złożyć (rdzeń definicyjny bez domu).
