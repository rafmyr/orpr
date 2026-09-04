# Regulatory Matrix — od przepisu do testowalnego wymagania systemowego

Regulatory Matrix (RM) jest wersjonowanym repozytorium wymagań regulacyjnych dla systemów
klasy POS/ERP. Porządkuje przepisy, źródła urzędowe i wynikające z nich zachowania systemu tak,
aby można było wykorzystać je podczas analizy, projektowania, implementacji i testowania.

Nie jest zwykłą listą aktów prawnych. Każda istotna norma zostaje przełożona na możliwie atomowe
wymaganie, otrzymuje stabilny identyfikator, dokładne źródło i lokalizator oraz sprawdzalne
scenariusze. Dzięki temu zespół może przejść od pytania „jakie przepisy mogą mieć znaczenie?” do
pytania „jak system powinien się zachować i jak potwierdzimy, że robi to poprawnie?”.

> [!IMPORTANT]
> Regulatory Matrix wspiera analizę i projektowanie. Nie jest opinią prawną, certyfikatem
> zgodności ani zapewnieniem, że konkretne wdrożenie spełnia wszystkie obowiązki. Zakres, data,
> stan faktyczny i aktywne luki muszą być sprawdzane dla każdego zastosowania.

## Jak łączy się z ORPR

ORPR opisuje proces biznesowy: jego cel, granice, odpowiedzialność, wejścia, wyjścia, wyjątki
i pytania diagnostyczne. Regulatory Matrix odpowiada na inne pytanie: które zachowania systemu
lub obowiązki dowodowe wynikają w danym miejscu z regulacji.

Typowy łańcuch wygląda następująco:

```text
źródło prawne lub urzędowe
        ↓
konkretny przepis albo fragment źródła
        ↓
atomowe wymaganie systemowe w notacji EARS
        ↓
scenariusz pozytywny, graniczny i negatywny
        ↓
pakiet funkcjonalny Regulatory Matrix
        ↓
proces, karta albo punkt kontrolny ORPR
```

Karta procesu nie kopiuje treści prawa. Odwołuje się do identyfikatorów RM, dzięki czemu
aktualizacja wymagania regulacyjnego nie wymaga przepisywania tej samej interpretacji w wielu
procesach.

## Notacja EARS

Wymagania są zapisywane w notacji EARS (Easy Approach to Requirements Syntax). Ograniczona,
powtarzalna składnia zmniejsza wieloznaczność i ułatwia zamianę normy na kryterium akceptacyjne.
Regulatory Matrix wykorzystuje pięć wzorców:

| Wzorzec | Schemat | Liczba wymagań |
|---|---|---:|
| sterowany zdarzeniem | `KIEDY [zdarzenie], system MUSI…` | 275 |
| niepożądane zachowanie | `JEŻELI [sytuacja niepożądana], system MUSI…` | 45 |
| sterowany stanem | `DOPÓKI [stan], system MUSI…` | 30 |
| wszechobecny | `System MUSI…` | 7 |
| opcjonalna cecha lub zakres | `JEŻELI [warunek stosowalności], system MUSI…` | 4 |
| **Razem** |  | **361** |

Atomowość oznacza, że jeden rekord opisuje jeden egzekwowalny skutek. Jeżeli norma prowadzi do
dwóch niezależnych zachowań systemu, powinna zostać rozbita na dwa wymagania. Ułatwia to ocenę
stosowalności, śledzenie zmian oraz wskazanie testu, który potwierdza konkretną regułę.

## Siła normy i pewność nie są tym samym

RM osobno zapisuje siłę normy oraz poziom pewności analizy. W aktualnym wydaniu rozkład siły
wymagań wygląda następująco:

| Siła | Znaczenie w modelu | Liczba |
|---|---|---:|
| `MUST` | wymagane zachowanie | 321 |
| `MUST_NOT` | zachowanie zabronione | 37 |
| `SHOULD` | rekomendowane zachowanie | 2 |
| `MAY` | zachowanie dopuszczalne | 1 |

Jednocześnie 83 wymagania mają poziom `verified`, a 278 poziom `qualified`. `Verified` oznacza
spójny, sprawdzony strukturalnie ślad do wskazanego źródła — nie zewnętrzną opinię prawną.
Wymaganie może być obowiązkowe i nadal wymagać potwierdzenia jego zastosowania w konkretnym
produkcie albo stanie faktycznym.

## Co zawiera rekord wymagania

Rekord jest maszynowo przetwarzalnym obiektem. Oprócz zdania EARS może zawierać między innymi:

- stabilny identyfikator, domenę i tytuł;
- jurysdykcję oraz daty obowiązywania;
- profile biznesowe, kanały, role w łańcuchu dostaw i nakładki asortymentowe;
- aktorów, warunki wstępne i wyjątki;
- wejścia, wyjścia, wymagany ślad dowodowy i interfejsy zewnętrzne;
- rodzaj danych osobowych i odwołanie do zasad retencji;
- relacje do innych wymagań oraz interpretacji;
- identyfikator źródła, dokładny lokalizator i typ powiązania;
- trzy scenariusze weryfikacyjne.

Reguła może dzięki temu zostać aktywowana tylko wtedy, gdy rzeczywiście pasuje do profilu,
kanału, asortymentu i roli analizowanej organizacji. Sam fakt obecności wymagania w bazie nie
oznacza, że dotyczy ono każdego detalisty.

## Architektura techniczna

Repozytorium rozdziela trzy warstwy:

1. **Kanon** — źródła, wymagania, katalogi stosowalności, rejestry luk oraz definicje pakietów.
2. **Kontrola i publikacja** — model danych, walidatory, generatory i manifest integralności.
3. **Interfejs konsumpcyjny** — statyczne pakiety JSON i Markdown oraz indeksy CSV dla ludzi,
   narzędzi analitycznych i agentów AI.

Kanon jest źródłem prawdy, natomiast widoki konsumpcyjne są generowane. Nie edytuje się ich
ręcznie. Wydanie jest deterministyczne: ten sam kanon powinien utworzyć tę samą paczkę i te same
sumy kontrolne.

Każda paczka ma numer wersji, datę `legal_as_of`, status treści i deklarację gotowości
wdrożeniowej. Pola `effective_from` i `effective_to` pozwalają oceniać wymaganie na datę docelową,
a nie tylko według bieżącego dnia. Aktywny GAP albo defekt krytyczny zatrzymuje wykorzystanie
objętego nim zakresu zamiast pozwalać na uzupełnienie brakującej odpowiedzi domysłem.

## Liczby wydania 1.0.1

- Stan prawny wydania: **14 sierpnia 2026 r.**
- Status treści: **`qualified_with_known_gaps`**.
- Gotowość wdrożeniowa: **warunkowa**.

| Element | Liczba | Co liczba oznacza |
|---|---:|---|
| karty źródeł | 122 | wersjonowane opisy źródeł z organem, datą i lokalizatorem |
| dokumenty legislacyjne | 106 | ustawy, rozporządzenia, akty unijne, akty zmieniające, obwieszczenia i korekty |
| materiały urzędowe, techniczne i wytyczne | 16 | źródła pomocnicze, których siła jest odróżniona od prawa wiążącego |
| organy i instytucje źródłowe | 18 | unikalni wydawcy kart źródeł |
| atomowe wymagania EARS | 361 | osobne, identyfikowalne zachowania systemu |
| scenariusze weryfikacyjne | 1083 | dokładnie trzy na wymaganie: pozytywny, graniczny i negatywny |
| powiązania wymaganie–źródło | 514 | relacje prowadzące z wymagania do karty źródłowej |
| wskazania wykorzystanych przepisów lub fragmentów | 363 | lokatory zapisane w kartach źródeł |
| relacje pomiędzy wymaganiami | 272 | zależności i inne jawne krawędzie grafu |
| odwołania do reguł retencji | 140 | wymagania wskazujące kontrolowaną zasadę przechowywania |
| wymagania z interfejsem zewnętrznym | 186 | rekordy zależne od komunikacji z innym systemem lub podmiotem |
| przypisania do pakietów funkcjonalnych | 251 | członkostwa wymagań w pakietach konsumpcyjnych |
| pakiety funkcjonalne | 21 | gotowe, ograniczone konteksty dla konkretnej funkcji |
| domeny wymagań | 19 | obszary tematyczne w modelu danych |
| profile biznesowe | 5 | apteka, sklep spożywczy, drogeria, sklep sportowy i DIY |
| delegacje i zależności materialne | 77 | 44 pokryte, 32 nie dotyczą zakresu, 1 pozostaje luką |
| wymagania aktywne czasowo | 352 | rekordy aktywne dla daty wydania |
| wymagania z nierozstrzygniętym czasem lub zakresem | 9 | pozycje widoczne jako luka, a nie ukryte założenie |
| aktywne GAP-y | 9 | jawne ograniczenia wymagające rozstrzygnięcia |
| aktywne defekty P0 | 0 | brak znanych aktywnych defektów najwyższej rangi |

W 514 relacjach wymaganie–źródło występuje bezpośrednio 78 różnych kart źródłowych. Pozostałe
karty zachowują między innymi kontekst zmian, pokrycia i historii legislacyjnej. Liczby opisują
strukturę wydania, a nie liczbę porad prawnych ani liczbę funkcji gotowych do bezpośredniego
wdrożenia.

## Zakres merytoryczny

Wydanie obejmuje polskie systemy POS/ERP i składa się ze wspólnego rdzenia retailowego, głębokiego
profilu apteki ogólnodostępnej oraz nakładki drogerii. Nakładka drogerii obejmuje między innymi
kosmetyki, detergenty, warunkowe produkty biobójcze oraz wymagania CLP i REACH.

Zakres może być składany według:

- profilu biznesowego;
- kanału, np. sklepu, sprzedaży na odległość, click and collect lub marketplace;
- roli, np. detalisty, dystrybutora, importera, właściciela marki albo producenta;
- rodzaju asortymentu i aktywowanych nakładek;
- cech konkretnej placówki lub procesu.

RM nie deklaruje pełnego pokrycia całego prawa dotyczącego każdego przedsiębiorstwa. Koncentruje
się na obowiązkach, zakazach, wyjątkach, terminach i dowodach, które zmieniają zachowanie albo
dane systemu POS/ERP w zdefiniowanym zakresie.

## Użycie w projekcie

Najbezpieczniejszy sposób pracy polega na wybraniu pakietu funkcjonalnego albo konkretnego
identyfikatora wymagania, sprawdzeniu daty i stosowalności, a następnie zachowaniu kompletnego
śladu: wymagania, źródła, lokalizatora, scenariuszy, ostrzeżeń i aktywnych GAP-ów.

Regulatory Matrix może wspierać:

- discovery i analizę wpływu regulacji;
- tworzenie specyfikacji oraz kryteriów akceptacji;
- projektowanie modelu danych i integracji;
- przygotowanie testów pozytywnych, granicznych i negatywnych;
- przegląd luk przed wdrożeniem;
- kontrolowany retrieval dla agentów AI bez przekazywania całego repozytorium do kontekstu.

Nie należy kopiować pojedynczego zdania bez jego źródła, daty, warunków stosowalności i relacji.
W szczególności status `verified` nie zastępuje oceny prawnej konkretnego wdrożenia.

## Dostęp do pełnego materiału

Pełne repozytorium Regulatory Matrix nie jest częścią publicznej próbki ORPR. Jeżeli rozważasz
zastosowanie ORPR lub RM w projekcie i chcesz zobaczyć pełny zakres, skontaktuj się bezpośrednio
z Rafałem Myrtą: [myrta.me](https://myrta.me) lub
[LinkedIn](https://www.linkedin.com/in/rafalmyrta/).

---

Liczby przeliczono z wydania Regulatory Matrix `1.0.1` 4 września 2026 r. Walidacja struktury
danych i audyt grafu zakończyły się bez błędu. W kolejnych wersjach liczby mogą się zmienić wraz
z zakresem, aktualizacją prawa i zamykaniem jawnych luk.
