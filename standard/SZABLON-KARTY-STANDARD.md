# Szablon karty STANDARD (jednostka standardu od 25.08.2026)

Zatwierdzony: rafalmyrta, 2026-08-25 (rejestr decyzji projektowych: eksperyment minimalnej wystarczalności,
2 rodziny modeli, kryterium spełnione z zapasem). Karta STANDARD jest DOMYŚLNĄ jednostką
standardu dla każdego procesu mapy. Pełny szablon L1 (SZABLON-KARTY.md) pozostaje wyłącznie
dla kart pogłębionych (L2), tworzonych ZA POPYTEM adoptera.

Uzasadnienia decyzji projektowych: rejestr decyzji projektowych. Artefakty eksperymentu:
wewnętrzny materiał roboczy

---

## CZĘŚĆ I. Struktura karty

### Nagłówek
```
# ORPR-<DOM>-<NN> <Nazwa-EN>  ·  karta STANDARD
Ścieżka: <rodzaj> / <obszar> / <NN> · <Od X do Y> · ORPR-<DOM>-<NN>
Status: <draft|reviewed|released> · Wersja: <x.y> · regulatory-matrix <wersja>, legal_as_of <data>
Legenda tagów źródeł: [AUT-R data] [PROP] [PROP+ data] [LIT: ...] [R: ID] [HIP] (jak dotąd)
```

### 0. Jak używać tej karty (stała treść, identyczna w każdej karcie)
1. Ta karta jest zewnętrzną warstwą KONTROLNĄ dla analityka i agenta AI, nie specyfikacją do
   skopiowania. W specyfikacji cytuj identyfikatory (ORPR-..., Nx, Fx), nie przenoś treści.
2. Pytania klasy B (blokujące) zadaj biznesowi albo oznacz w specyfikacji jako OPEN z ID pytania.
   Brak odpowiedzi na pytanie B NIGDY nie staje się założeniem specyfikacji.
3. Pytania klasy W (warunkowe) zadawaj tylko, gdy wystąpi ich wyzwalacz.
4. Pytania klasy D (diagnostyczne) służą badaniu systemu zastanego przy migracji. NIE wchodzą
   do specyfikacji jako pytania do biznesu.
5. Odstępstwo od niezmiennika [N] albo kontraktu [K] jest dozwolone bez niczyjej zgody, ale
   wymaga jawnego wpisu: "odstępstwo od ORPR-<ID>/<Nx>: <powód>" i oznaczenia jako ryzyko.
   Twierdzenie z wiązaniem [R: ...] nie podlega odstępstwu na poziomie karty; to pytanie
   prawne do rozstrzygnięcia z właściwym doradcą.
6. Czerwone flagi F to testy akceptacyjne przy migracji z systemu zastanego.

### 1. Wynik i granice
Wynik procesu jednym akapitem (stan końcowy, po którym biznes poznaje, że proces zaszedł).
Start: ... Koniec: ... Wyniki alternatywne (jeśli są): ...
NIE obejmuje: lista ze wskazaniami "(→ obszar/ID)".
Właściciel: <rola>. Model operacyjny sieci zmienia obsadę uprawnień, nie kroki ani wynik.

### 2. Dane
Wejścia obowiązkowe: lista z tagami `[D! id]`.
Wejścia warunkowe: lista z tagami `[D: id]`.
Wyjścia: dokument/stan/zdarzenia wynikowe.

### 3. Niezmienniki (co zawsze musi być prawdą)
Nx. <Twierdzenie testowalne, 1-3 zdania, bez prozy uzasadnień.> [znacznik] [R: ID gdy dotyczy]

Znaczniki warstw normatywności:
- [N] niezmiennik biznesowy: co musi być prawdą w wyniku i w trakcie procesu;
- [K] kontrakt graniczny: co druga strona styku może ZAOBSERWOWAĆ i na czym może polegać
  (wyłącznie semantyka obserwowalna; struktura wewnętrzna i wybór mechanizmu NIGDY).

Reguły sekcji: każdy niezmiennik testowalny (da się orzec: spełnia / nie spełnia); mechanizmy
realizacji (kolejki, TTL, klucze, retry) nie wchodzą do karty; jeśli warte utrwalenia, idą do
aneksu informacyjnego "wzorce realizacji" poza kartą. Niezmienniki uniwersalne ("oczywiste")
ZOSTAJĄ: eksperyment 25.08 wykazał, że słabszy model gubi także mechanikę generyczną.

### 4. Pytania analityka (wg klas)
Klasa B, blokujące (bez odpowiedzi nie wolno pisać specyfikacji):
B1. <pytanie rozstrzygalne>? (dlaczego ważne: <jedno zdanie>)
Klasa W, warunkowe (jawny wyzwalacz w treści):
W1. Jeśli <wyzwalacz>: <pytanie>? (dlaczego ważne: ...)
Klasa D, diagnostyczne (badanie systemu zastanego; patrz sekcja 0 pkt 4):
D1. <pytanie>? (dlaczego ważne: ...)

### 5. Czerwone flagi (sygnały wadliwej implementacji lub wadliwego systemu zastanego)
Fx. <sygnał>. (Wykrywa: <ID pytań>) [R: ID gdy flaga stoi na wymaganiu prawnym]

### 6. Wiązania regulacyjne
regulatory-matrix <wersja>, legal_as_of <data>: <lista ID>. Zero treści prawa w karcie;
brak pokrycia = jawny GAP w rejestrze tematów odłożonych, nigdy cisza.

---

## CZĘŚĆ II. Budżety i bramki

| Sekcja | Budżet | Egzekutor |
|---|---|---|
| Niezmienniki [N]+[K] łącznie | 5-12 | K-BUDZET (ostrzeżenie; do wdrożenia w bramka.py, do tego czasu recenzent) |
| Pytania B+W+D łącznie | 15-30 | K-BUDZET (jw.) |
| Czerwone flagi | 5-12 | K-BUDZET (jw.) |
| Rdzeń karty łącznie | ~150-250 linii | K-BUDZET (jw.) |
| Każde pytanie ma klasę B/W/D; każde W zaczyna się od "Jeśli" | twarde | K-KLASY (do wdrożenia w bramka.py; do tego czasu recenzent liczy ręcznie) |
| Słowa-mechanizmy (kolejka, TTL, retry, idempotenc*) poza sekcją pytań | ostrzeżenie | K-MECH (jw.) |
| Dotychczasowe: em-dash 0, P15 sektorowy, D-tagi (K8), tagi źródeł | bez zmian | bramka.py jak dotąd |

Przekroczenie budżetu miękkiego nie blokuje commita; wymaga jednego zdania uzasadnienia
w opisie zmiany. Cel budżetu: sygnał ucieczki treści do L2 albo do pytań, nie cel sam
w sobie (P2).

## CZĘŚĆ III. Warstwy poza kartą

| Warstwa | Status | Kiedy powstaje |
|---|---|---|
| Karta STANDARD (powyższa) | normatywna | dla każdego procesu mapy po teście granulacji |
| Karta pogłębiona (L2, SZABLON-KARTY.md) | normatywna | wyłącznie za popytem adoptera |
| Bank rozszerzony pytań | normatywna, opcjonalna | za popytem (warsztat u adoptera) |
| Aneks "wzorce realizacji" (mechanizmy) | INFORMACYJNA | przy etykietowaniu rejestru styków; nigdy w karcie |
| Crosswalk APQC/ARTS/GS1 | referencyjna | jak dotąd, standard/mapowania/ |
| Profil branżowy | nakładka | za popytem, nigdy w rdzeniu (P15) |

## CZĘŚĆ IV. Karta repo vs karta pakietowa

Karta w repo nosi tagi źródeł ([AUT-R]/[PROP+]/...) i pola statusowe: to warstwa governance.
PAKIET dla agentów/analityków jest POCHODNĄ generowaną skryptem z kart repo: zdejmuje tagi
źródeł i status, zachowuje sekcję 0 i całą treść normatywną. Jedno źródło prawdy (P13):
edytuje się kartę repo, pakiet się generuje, nigdy odwrotnie. Generator: rejestr tematów odłożonych
(warunek: KROK 1 planu, pierwsza ekstrakcja pakietu).
