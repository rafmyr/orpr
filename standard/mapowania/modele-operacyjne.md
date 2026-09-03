# Modele operacyjne sieci: kto ma prawo decydować na której bramce

Artefakt współdzielony standardu ORPR. Wersja 0.11 | 19.08.2026, przebudowy i chirurgiczne domknięcie 26.08.2026 |
Status: kandydat zamknięty — faza B1 (GO DO F2a w zamrożonym zakresie, ratyfikacja właściciela)

> **PRZEBUDOWA v0.3 [AUT-R 2026-08-26, handoff naprawczy]** — konsumuje findingi B-03/B-04/D-02
> recenzji Sola (własny falsyfikator warstwy „Co obali tę warstwę" pkt 3 ZADZIAŁAŁ — oś nie
> klasyfikowała wszystkich sześciu typów i przeczyła definicji sieci własnej):
> 1. T1 bada **wspólną kontrolę właścicielską**, nie tożsamość osoby prawnej. Odrębność
>    prawna lokalizacji/centrali jest ODRĘBNYM polem opisowym (konsumowanym przez #8,
>    konsolidację i rozliczenia), nie bramką klasy.
> 2. Dodana **bramka uprzedniej zgody** rozdzielająca sieć partnerską (M1a) od franczyzy
>    miękkiej (M1b) — poprzednie sklejenie ich w jedną klasę M1 przeczyło definicjom A1.
> 3. Dodany wynik dla **grupy zakupowej** (M-GZ): relacja istnieje, ale nie ogranicza
>    swobody handlowej i nie daje prawa zmiany ceny.
> 4. Klasyfikuje się **jednostkę**: `relacja × sklep/lokalizacja × kanał × okres` — firma
>    mieszana nie dostaje jednej etykiety dla całej organizacji [AUT-R 2026-08-26].
> 5. Usunięty nieaktualny zapis o „pięciu modelach / 259 kombinacjach".
> Definicje typów: BIEŻĄCY krajobraz wewnętrznego materiału roboczego sekcje A/A1;
> trzeci opis relacji (własność zapasu, strony, ryzyko, pieniądz, zobowiązania): tamże, sekcja A3.

> **KOREKTA [AUT-R 2026-08-26, rano]** (falsyfikator pkt 3/4 przy pracy nad krajobrazem;
> wpis: rejestr decyzji projektowych):
> 1. Utożsamienie twardej franczyzy z kontrolą CAŁEGO asortymentu i cennika zostało
>    SFALSYFIKOWANE. Franczyza jest twarda **w takim zakresie, w jakim umowa pozwala
>    centrali jednostronnie ustalać albo zmieniać zasady; poza tym zakresem sklep może
>    zachować swobodę** [AUT-R 2026-08-26, handoff naprawczy — brzmienie ratyfikowane].
>    Szerokość kontroli i sposób jej zmieniania to DWA odrębne wymiary.
> 2. RODZAJ POWIĄZANIA sieci jest ODRĘBNYM polem opisowym (6 typów) — oś M mierzy prawa
>    decyzyjne; typ powiązania opisuje konstrukcję sieci.
> 3. Kontrola cen: warianty zwykłe = cena lokalna / rekomendowana / maksymalna; cena
>    sztywna lub minimalna = wyjątek wymagający osobnej oceny prawnej (wytyczne KE
>    2022/C 248/01) — nie przedstawiać jako zwykłego wariantu.

> **AKTUALIZACJA v0.4 [AUT-R 2026-08-26, decyzje R2/R8 po reteście]:**
> R2 — dodany dwustopniowy filtr wejściowy osi M (T0a rola detaliczna, T0b zakres
> organizowania): agent i dystrybutor selektywny odpadają PRZED klasyfikacją sieciową
> i trafiają do trzeciego opisu A3. R8 — jawnie: firma może prowadzić kilka modeli
> jednocześnie; wynik M dotyczy relacji×formatu×okresu, nie całej firmy.

> **AKTUALIZACJA v0.6 [AUT-R 2026-08-26, ZZ1 domknięcie B1]:** do filtra T0b dodana reguła
> „kanał sprzedaży vs format detaliczny" — marketplace 3P jest kanałem (poza typologią, A3),
> nie typem sieci; z jawnym wyjątkiem i trzema sytuacjami platforma/sprzedawca.

> **AKTUALIZACJA v0.7 [AUT-R 2026-08-26, naprawa B1 po recenzji Sola]:**
> D-B1 — profil M (bramki T0-T3) i kwalifikacja typu (K5) to DWA niezależne pola wyniku; K5-4
> (wynagrodzenie) ani odpłatność NIE przepisują profilu M. D-B2 — wyjątek T0b przekrojony na
> jednostkę `relacja × lokalizacja × kanał × okres`: format kanałowy (virtual brand) wchodzi
> do osi M bez tworzenia nowego typu. D-T2z — zgoda na wejście ≠ zgoda na akcje; opt-in do
> zdefiniowanego programu = M1a w zakresie; zamknięty obowiązkowy zakres = M1b; jednostronne
> rozszerzanie = M2 (domyka klasyfikacyjną część E.28).

## Po co ten plik istnieje

Trzy karty domeny CAT niezależnie od siebie natrafiły na **tę samą oś**: model relacji między siecią
a lokalizacją odwraca kierunek decyzji. Nie zmienia kroków procesu, tylko **to, kto na której bramce
ma prawo głosu**.

| Karta | Co się odwraca | Gdzie w karcie |
|---|---|---|
| ORPR-CAT-01 Item-to-Sellable | kto decyduje o wprowadzeniu pozycji do asortymentu | oś wstępna |
| ORPR-CAT-02 Price-to-POS | kierunek przepływu ceny regularnej | oś 1 |
| ORPR-CAT-03 Promotion-to-POS | kto prowadzi politykę promocyjną | oś wstępna |

Wszystkie trzy wystąpienia pochodzą z dyktand właściciela standardu, nie z researchu, i pojawiły się
**zanim ktokolwiek szukał wzorca**. To jest powód, dla którego oś dostaje osobny artefakt zamiast
być powtarzana w każdej karcie [AUT-R 19.08, potwierdzone].

## Czego ten plik NIE robi

**Nie mnoży kart.** Rozważano wariant, w którym każdy proces dostaje wersję per klasa osi.
Odrzucone jako dryf głębi i utrzymanie ponad możliwości właściciela (pułapki P1 i P11). Karta
opisuje **pełny przebieg**, a ten plik mówi, kto obsadza którą bramkę.

**Nie jest listą typów sieci do celów handlowych.** Klasyfikacja służy jednej rzeczy: rozstrzygnięciu
praw decyzyjnych na bramkach procesu. Nazwy klas są robocze i mogą nie pokrywać się z tym, jak
klient sam siebie nazywa. **Nazwa u klienta nie jest odpowiedzią; odpowiedzią jest wynik testu
poniżej.**

**Nie klasyfikuje relacji spoza typologii sieciowej.** Agencja i dystrybucja selektywna to relacje
POZA sześcioma typami powiązania — opisuje je trzeci opis relacji (krajobraz sekcja A3), a oś M
zwraca dla nich wynik „poza typologią sieciową" (patrz tabela wyników).

## Jednostka klasyfikacji [AUT-R 2026-08-26]

Typ i klasę osi ustala się osobno dla **`relacji × sklepu/lokalizacji × kanału × okresu`**.
Wynik M dotyczy KONKRETNEJ relacji między organizatorem a sklepem, w konkretnym formacie
i okresie — NIE całej organizacji.

**Firma może prowadzić kilka modeli jednocześnie** [AUT-R 2026-08-26, R8]. Oś M nie wciska
całej firmy do jednej kategorii. Każdy model współpracy klasyfikuje się osobno, np.:
- sklepy własne (→ zwykle M3),
- franczyza (→ M1b albo M2 wg zakresu),
- partnerzy (→ M1a),
- grupa zakupowa (→ M-GZ),
- inne formaty prowadzone przez tę samą firmę.

Jedna firma może mieć równocześnie kilka wyników M; różne wyniki współistnieją na jednej
mapie (zasada A2.2 krajobrazu). Relacje agencyjne, dropshippingowe i inne pozasieciowe
NIE dostają wyniku M — opisuje je trzeci opis relacji (A3). Każde rozstrzygnięcie wymaga
faktu, roli/decydenta, zakresu i daty (A2.3).

## Oś główna: test bramkowy, rozstrzygany zachowaniem, nie nazwą

Pytania zadawane w kolejności, dla JEDNEJ jednostki klasyfikacji:

### T0 — bramka wstępna

| # | Pytanie | Jeżeli NIE |
|---|---|---|
| **T0** | Czy dla tej jednostki istnieje relacja z **drugą stroną — kandydatem na organizatora** (centralą, grupą, platformą, dostawcą)? Charakter tej roli (czy druga strona FAKTYCZNIE organizuje sieć/format) rozstrzygają dopiero T0a/T0b. | brak jakiejkolwiek takiej relacji → **M0 sklep niezależny**; klasyfikacja kończy się i nie uruchamia T0a/T0b |

### Filtr wejściowy osi M (dwustopniowy) [AUT-R 2026-08-26, R2]

Dopiero gdy T0 = „tak”, sprawdzamy, czy istniejąca relacja W OGÓLE należy do typologii
sieciowej. Dwa pytania, oba muszą dać „tak", aby przejść dalej:

| # | Pytanie | Jeżeli NIE |
|---|---|---|
| **T0a — rola detaliczna** | Czy badany sklep sprzedaje klientowi WE WŁASNYM IMIENIU i NA WŁASNY RACHUNEK, ponosząc odpowiedzialność sprzedawcy? | relacja jest **poza typologią M** → opis przez A3 (np. agent działający na rachunek principala) |
| **T0b — zakres organizowania** | Czy druga strona ORGANIZUJE sposób prowadzenia albo zaopatrywania sklepu jako część wspólnego formatu, sieci lub wspólnego przedsięwzięcia zakupowego uczestników — a nie tylko ustala warunki sprzedaży WŁASNYCH produktów lub usług (jako dostawca/pośrednik)? | relacja jest **poza typologią M** → opis przez A3 (np. dostawca ustalający warunki sprzedaży swoich towarów, dystrybucja selektywna) |

**Samo narzucenie ekspozycji, szkolenia personelu lub warunków sprzedaży produktów dostawcy
NIE wystarcza** do uznania relacji za franczyzę lub sieć. Filtr chroni przed dwoma błędami
wykrytymi w reteście: agent klasyfikowany jako franczyza twarda (pada na T0a), dystrybutor
selektywny jako franczyza miękka (pada na T0b).
**Grupa zakupowa PRZECHODZI T0b** [AUT-R 2026-08-26, B-3]: wspólne negocjowanie/organizowanie
zakupów uczestników to organizowanie wspólnego formatu ZAKUPOWEGO — inaczej niż dostawca,
który ustala warunki sprzedaży WŁASNYCH produktów (ten pada na T0b). Grupa zakupowa jest
pełnoprawnym typem sieciowym (A0) i przechodzi filtr; jej ubóstwo praw decyzyjnych rozstrzyga
się dalej na bramkach (wynik M-GZ).
**Kanał sprzedaży vs format detaliczny — marketplace 3P** [AUT-R 2026-08-26, ZZ1; D-B2]:
korzystanie ze wspólnego kanału sprzedaży oraz podleganie zasadom tego kanału NIE oznacza
organizowania sieci detalicznej. Format ocenia się na poziomie jednostki klasyfikacji
`relacja × lokalizacja × kanał × okres` — **format może istnieć wyłącznie w kanale marketplace**
(nie musi wykraczać poza platformę). T0b przechodzi na „TAK" dopiero wtedy, gdy organizator
kształtuje POWTARZALNY FORMAT działalności sprzedawcy, a nie tylko sposób zawierania i obsługi
transakcji. Samo prowadzenie platformy, regulamin transakcyjny, prowizja, ranking, standard
oferty, SLA, obsługa płatności, dostawa ani wymagania kontaktu z klientem NIE wystarczają.
**Wymagane łącznie:** (i) odrębna tożsamość/marka LUB narzucony model operacyjny sprzedawcy;
(ii) obowiązkowe standardy WYKRACZAJĄCE poza obsługę transakcji (np. marka, receptury/menu,
opakowanie, procedury lokalu); (iii) prawo organizatora do ich egzekwowania. Spełnione łącznie →
osobną relację (kanałowy format) przepuszcza się przez oś M; niespełnione → marketplace 3P jest
KANAŁEM, relację platforma–sprzedawca opisuje A3. **Nie tworzy się nowego typu „virtual brand"**
— dalszą kwalifikację (M1a/M1b/M2, w tym zakresowość i granicę K5) wykonuje oś M i pozostałe
testy. Sprzedawca klasyfikuje SWOJĄ własną sieć niezależnie od platformy.
Trzy sytuacje: (a) sprzedawca 3P bez narzuconego formatu korzysta z platformy → A3, ale kanałowy
format spełniający (i)-(iii) → oś M; (b) platforma sama sprzedaje klientowi → platforma jest
detalistą i klasyfikuje własny model; (c) jeden podmiot pełni obie role → każdą relację ocenia się osobno.

Dopiero po T0=„tak” i przejściu obu filtrów zadaje się pozostałe bramki:


| # | Pytanie testowe | Po co |
|---|---|---|
| T1 | Czy lokalizacja i organizator pozostają pod **wspólną kontrolą właścicielską**? (NIE: czy są tą samą osobą prawną) | rozdziela sieć własną od relacji umownych |
| T1g (bramka graniczna) | Czy relacja ogranicza się WYŁĄCZNIE do wspólnego negocjowania warunków u dostawców — bez własnego programu handlowo-marketingowego organizatora i bez centralnej odsprzedaży jako stałego elementu normalnego działania? | tak ⇒ M-GZ; nie ⇒ dalsza klasyfikacja relacji umownej |
| T1b (pole opisowe, nie bramka) | Czy lokalizacja i organizator są odrębnymi osobami prawnymi? | zasila #8, konsolidację i rozliczenia (pakiet 6); NIE zmienia klasy |
| T2 | Czy **umowa bazowa (samo wejście do relacji)** nakłada na jednostkę OBOWIĄZKOWY zakres oferty, działań lub zasad — NIEZALEŻNIE od odrębnego, dobrowolnego opt-in do programu? | rozdziela grupę zakupową i partnerstwo od franczyz; zakres z odrębnego opt-in liczy się osobno (T2z/D-T2z) |
| T2z (bramka zgody) [D-T2z] | Czy w OBOWIĄZKOWYM zakresie z umowy bazowej akcja może związać sklep bez zgody per akcja? (zgoda na samo wejście do relacji NIE wystarcza). **Odrębny, dobrowolny opt-in do zdefiniowanego programu NIE jest zakresem bazowym — daje M1a w swoim zakresie, nie M1b.** | rozdziela sieć partnerską (M1a) od franczyzy miękkiej (M1b) |
| T3 | Czy umowa upoważnia organizatora do JEDNOSTRONNEGO ustalania lub zmieniania zasad (w tym cen) w określonym zakresie — i czy system faktycznie tak się zachowuje? | rozdziela franczyzę twardą (w jej zakresie) od miękkiej; weryfikacja zachowaniem, nie deklaracją |

Tabela wyników — **każda dopuszczalna kombinacja odpowiedzi ma wynik albo jawnie kieruje do
statusu „nierozstrzygnięty"**:

| Wynik | T0 | T1 | T1g | T2 | T2z | T3 |
|---|---|---|---|---|---|---|
| **M0 sklep niezależny** | nie ma relacji | — | — | — | — | — |
| **M-GZ grupa zakupowa** | jest | nie | **tak** — wyłącznie wspólne negocjowanie | nie | nie (relacja nie dotyczy akcji handlowych) | nie |
| **M1a sieć partnerska** | jest | nie | **nie** — istnieje program organizatora lub stała centralna odsprzedaż | nie | **nie** — nic nie wiąże bez opt-in do akcji albo zdefiniowanego programu/okresu | nie |
| **M1b** | jest | nie | nie | **tak, zakres ZAMKNIĘTY w umowie** | tak — obowiązuje bez zgody per akcja | nie — zmiana zakresu wymaga zgody |
| **M2** (w zakresie umowy) | jest | nie | nie | tak | tak (w zakresie) | **tak — jednostronne ustalanie/zmiana zasad w ustalonych granicach** |
| **M3 sieć własna** | jest | **tak — wspólna kontrola właścicielska** | — | (stosunek właścicielski/pracy, nie umowa handlowa) | — | tak, na wszystkich pozycjach jednostki |
| **poza typologią sieciową** (agencja, dystrybucja selektywna, inne relacje dostawcze) | relacja istnieje, ale nie jest powiązaniem sklepu z organizatorem SIECI (np. sprzedaż na rachunek principala; kryteria autoryzacyjne dostawcy) | — | — | — | — | — → opis w trzecim opisie relacji (A3) |
| **nierozstrzygnięty** | każda kombinacja, w której brakuje obserwowalnego faktu dla potrzebnej bramki | | | | | → status A2.3, analiza nieukończona |

Zakresowość M2: jedna jednostka może być M2 w zakresie objętym upoważnieniem umowy i zachowywać
swobodę poza nim — wynik zapisuje się z zakresem („M2 w zakresie X; poza X: swoboda jak M1b").
Reguła pierwszeństwa przy nakładaniu: **prawo jednostronnej zmiany w jakimkolwiek zakresie ⇒ M2
w tym zakresie**; obowiązkowy zamknięty fragment bez prawa zmiany ⇒ M1b; nic bez uprzedniej
zgody ⇒ M1a.

**Zgoda: wejście vs program (T2z)** [AUT-R 2026-08-26, D-T2z]:
- zgoda na samo WEJŚCIE do relacji NIE jest zgodą na każde późniejsze działanie;
- odrębny, dobrowolny opt-in do zdefiniowanego działania lub programu daje **M1a wyłącznie w tym zakresie**;
- jeśli wejście do relacji wiąże sklep ZAMKNIĘTYM obowiązkowym zakresem programu → profil **M1b**;
- jeśli organizator może JEDNOSTRONNIE zmieniać lub rozszerzać obowiązkowy zakres → profil **M2** (w tym zakresie);
- zgoda programowa liczy się jako opt-in (M1a) TYLKO gdy zakres został określony PRZED zgodą i nie
  może być jednostronnie rozszerzony. Ten warunek domyka KLASYFIKACYJNĄ część rejestru granic E.28.

**Profil M vs kwalifikacja typu — dwa niezależne pola wyniku** [AUT-R 2026-08-26, D-B1]: wynik
klasyfikacji ma DWA niezależne pola.
- **Profil M** (orzekany przez bramki T0/T0a/T0b/T1/T1g/T2/T2z/T3, tabela wyników powyżej): opisuje WYŁĄCZNIE prawa
  decyzyjne, zgodę i możliwość jednostronnej zmiany. **Ani K5-4 (wynagrodzenie za markę/system),
  ani żadna inna odpłatność NIE mogą przepisać profilu M** — profil wynika wyłącznie z tych bramek.
- **Kwalifikacja typu** (osobne pole A2.3): czy relacja jest FRANCZYZĄ w rozumieniu A1/K5 —
  rozstrzygają ŁĄCZNIE cztery kryteria (marka, obowiązki, narzucone standardy, wynagrodzenie).
  Kryterium (4) K5 należy TU, nie do osi M.

Skutek. Jednostka z obowiązkowym, zamkniętym zakresem, ale bez wynagrodzenia za markę/system ma
**profil M1b** (T2=tak, zakres zamknięty, bez prawa jednostronnej zmiany) i JEDNOCZEŚNIE
**kwalifikację typu = sieć partnerska** (nie spełnia K5-4 → nie jest franczyzą). Zapis wyniku:
„profil M1b; typ: sieć partnerska — brak spełnienia K5-4". Etykiety „franczyza miękka/twarda"
w wierszach tabeli to TYPOWA kwalifikacja typu, gdy K5 spełnione w całości; sam profil M zapisuje
się kodem (M0/M-GZ/M1a/M1b/M2/M3) niezależnie od K5-4.

**Dlaczego T3 jest osobnym pytaniem, choć wygląda na powtórzenie T2.** Bo umowa i praktyka
rozjeżdżają się w obie strony. Sieć deklarująca pełną kontrolę bywa w praktyce niezdolna wymusić
cenę, a sieć deklarująca partnerstwo bywa w praktyce twarda. **Pytamy o zachowanie systemu, nie
o treść umowy.** To jest ten sam bezpiecznik co w bankach pytań kart: zachowanie legacy weryfikuje
deklarację biznesu.

**Grupa zakupowa (M-GZ) na bramkach procesu zachowuje się jak M0** (organizator nie obsadza
żadnej bramki handlowej lokalizacji) — różnica wobec M0 leży w istnieniu relacji negocjacyjnej
(#11 organizatora w postaci zdegenerowanej, umowa uczestnictwa #21) i w potencjalnych
rozliczeniach prowizyjnych (trzeci opis relacji; pakiet 6 tylko przy realnych rozliczeniach).

## Oś warunkowa: zarządzanie kategorią

Drugi wymiar, **warunkowy wobec pierwszego**. Zarządzanie kategorią w rozumieniu tego standardu
**występuje wyłącznie przy M2 i M3** [AUT-R 19.08, rozstrzygnięcie właściciela]. Przy M0, M-GZ,
M1a i M1b roli o takim prawie decyzji się nie spotyka: sklep nie oddaje nikomu prawa do odrzucenia
pozycji, która mu się sprzedaje.

Test: **czy istnieje osoba albo rola, która odpowiada za wynik całej kategorii, a nie za pojedyncze
pozycje, i czy ma prawo odrzucić pozycję, która sprzedaje się dobrze, bo psuje strukturę kategorii?**
Odpowiedź „mamy kierownika działu" nie wystarcza; pytanie brzmi o prawo do odrzucenia mimo dobrej
sprzedaży.

Zarządzanie kategorią **nie jest kolejnym stopniem usieciowienia** i nie należy go doklejać do osi
głównej: M2 albo M3 **może** mieć CM i może nie mieć. Warunkowość działa w jedną stronę, czyli CM
implikuje M2 albo M3, ale nie odwrotnie.

**Falsyfikator tej reguły:** znaleziona sieć klasy M0/M-GZ/M1a/M1b, w której istnieje rola z prawem
odrzucenia dobrze sprzedającej się pozycji ze względu na strukturę kategorii. Jedno takie
udokumentowane wystąpienie przywraca wersję „oś niezależna" i wymusza poprawkę w CAT-01.

## Macierz: kto decyduje na której bramce

Wiersze to bramki decyzyjne wyjęte z kart, kolumny to klasy osi. Zawartość komórki opisuje
**prawo decyzji**, nie krok procesu. Treść komórek = dyktanda właściciela [AUT-R 19.08];
kolumna dawnego M1 obsługuje ŁĄCZNIE M1a i M1b — różnice między nimi oznaczone (a)/(b)
[adnotacje wyprowadzone z definicji A1, AUT-R 2026-08-26; klasy M-GZ macierz nie wymienia,
bo organizator M-GZ nie obsadza żadnej bramki — zachowanie jak M0].

### Domena CAT

| Bramka | M0 niezależny (i M-GZ) | M1a partnerska / M1b miękka | M2 twarda | M3 własna |
|---|---|---|---|---|
| **wprowadzenie pozycji do asortymentu** [CAT-01] | właściciel, bez ograniczeń | kierownik albo właściciel sklepu, czasem kierownik działu; centrala **sugeruje** (a: wyłącznie za zgodą), może **wymusić umownie wąski zakres** (b: w zamkniętym zakresie umowy) | zakupy, marketing albo category manager; sklep zgłasza, centrala **może odmówić** | jak M2 |
| **założenie pozycji lokalnej** [CAT-01] | zawsze wolno | zwykle wolno | czasem wolno; przy zarządzaniu kategorią zamienia się w **obowiązek zgłoszenia**, na które centrala może odmówić | zwykle **brak** prawa |
| **wycofanie pozycji z oferty** [CAT-01] | właściciel | kierownik lokalizacji | centrala; przy braku zarządzania kategorią pozycja zwykle **wypada sama**, bo przestaje się sprzedawać | jak M2 |
| **ustalenie ceny regularnej** [CAT-02] | właściciel | **kierownik lokalizacji tworzy cennik**; centrala nakłada wyłącznie wybrane pozycje (a: tylko za uprzednią zgodą; b: w obowiązkowym zakresie umowy) | centrala tworzy cennik; kierownik co najwyżej koryguje lokalnie | jak M2 |
| **korekta ceny lokalnie** [CAT-02] | nie dotyczy, cena i tak jest lokalna | domyślne uprawnienie kierownika | uprawnienie ograniczone; **cennik lokalny przy zarządzaniu kategorią przechodzi przez akceptację centrali** | jak M2 |
| **przyjęcie albo odrzucenie cennika z centrali** [CAT-02] | nie dotyczy | prawo do opóźnienia albo odrzucenia bywa **kontraktowe i realne** (a: zawsze — nic bez zgody; b: poza obowiązkowym zakresem) | zwykle **brak** prawa odmowy | brak prawa odmowy |
| **uruchomienie promocji** [CAT-03] | właściciel | **lokalizacja prowadzi własną politykę promocyjną** | centrala; lokalizacja robi nakładki w zakresie, na który centrala pozwala | jak M2 |
| **udział w promocji centralnej** [CAT-03] | nie dotyczy | (a) **zaproszenie**: lokalizacja wykonuje je u siebie za zgodą; (b) obowiązkowy w zakresie umowy (np. promocje gazetkowe) | wykonanie obowiązkowe | wykonanie obowiązkowe |
| **przymus asortymentowy z akcji reklamowej** [CAT-03 -> CAT-01] | nie dotyczy | (b) bywa **zapisem umownym**: obowiązek posiadania całego asortymentu objętego akcją; (a) niemożliwy bez uprzedniej zgody | obowiązek | obowiązek |

**Uwaga cenowa [AUT-R 2026-08-26, B-1, odsyłacz do A2.4 krajobrazu]:** w kolumnach M1b/M2
zapis „centrala tworzy/nakłada cennik; kierownik co najwyżej koryguje; brak prawa odmowy"
opisuje kierunek prawa decyzji, NIE dopuszcza automatycznie ceny sztywnej/minimalnej.
Narzucanie niezależnemu franczyzobiorcy (M1b/M2) ceny SZTYWNEJ lub MINIMALNEJ = wyjątek
prawny wymagający osobnej oceny (A2.4 krajobrazu, Wytyczne KE 2022/C 248/01), a nie zwykły
wariant macierzy. Zwykłe warianty na bramce cennika: cena lokalna / rekomendowana / maksymalna.

Źródło zawartości: dyktanda właściciela zapisane w trzech kartach jako `[AUT-R 19.08]`. Ten plik ich
nie interpretuje ani nie uzupełnia; zestawia je w jednym miejscu [PROP+ 19.08, redakcja; adnotacje
(a)/(b) — AUT-R 2026-08-26 przez definicje A1].

### Co zmienia zarządzanie kategorią w obrębie M2 i M3

| Bramka | Bez zarządzania kategorią | Z zarządzaniem kategorią |
|---|---|---|
| wycofanie pozycji | pozycja wypada, bo przestaje się sprzedawać; decyzji nie ma | pozycja przechodzi przez bramki rozstrzygające, czy zostaje w ofercie |
| pozycja lokalna | prawo albo jego brak, wprost z klasy osi | obowiązek zgłoszenia do centrali, z prawem odmowy |
| cennik lokalny | uprawnienie kierownika | wymaga akceptacji centrali, bo lokalizacja nie zna strategii kategorii |
| promocja lokalna | decyzja lokalna | mieści się w planie kategorii albo nie mieści |

## Odcinek warunkowy

**Definicja.** Odcinek warunkowy to część procesu, która **istnieje albo nie istnieje** zależnie od
klasy osi lub od obecności zarządzania kategorią. Nie jest wariantem wykonania tej samej
czynności; jest obecnością albo nieobecnością czynności.

**Zasada zapisu w karcie.** Karta opisuje pełny przebieg, łącznie z odcinkami warunkowymi, i oznacza
je jawnie. **Odcinek oznaczony jako warunkowy nie jest wymaganiem wobec klienta, u którego warunek
nie zachodzi.** Analityk, który zażąda go od wszystkich, wyprodukuje wymagania na proces, którego
u klienta nie ma.

### Rejestr odcinków warunkowych

| Odcinek | Warunek istnienia | Karta |
|---|---|---|
| zarządzanie cyklem życia pozycji | zarządzanie kategorią | CAT-01 pole 11 |
| pozycja lokalna zakładana przez lokalizację | klasa M0/M-GZ/M1a/M1b, częściowo M2 | CAT-01 pole 11 |
| planowanie opłacalności promocji i wskazania zakupowe | istnienie forecastu (**większość sieci go nie ma**) | CAT-03 model pojęciowy |
| promocje wspólne dla wielu kanałów | prowadzenie sprzedaży wielokanałowej | CAT-03 model pojęciowy |
| nakładka centralna na cennik lokalny | klasa M1a (za zgodą) / M1b (w zakresie umowy) | CAT-02 oś 1 |

Rejestr rośnie. Nowy odcinek warunkowy dopisuje się tutaj i oznacza w karcie, nie odwrotnie.

## Jak karty mają tego używać

1. Karta **linkuje** do tego pliku i nie powtarza macierzy.
2. Karta zachowuje **własną tabelę osi** tylko wtedy, gdy zawiera rozstrzygnięcie, którego macierz
   nie ma. Wtedy rozstrzygnięcie **przenosi się tutaj** przy najbliższej redakcji.
3. Karta oznacza odcinki warunkowe i dopisuje je do rejestru wyżej.
4. Bank pytań każdej karty otwiera się pytaniem o klasę osi (per jednostka klasyfikacji), bo bez
   niej reszta warsztatu jest zgadywaniem.

## Granularność: gdzie oś ma znaczenie, a gdzie go nie ma

Trzy karty użyły **różnej liczby klas**, i to nie jest niespójność, tylko informacja:

| Karta | Ile klas rozróżnia | Dlaczego |
|---|---|---|
| CAT-01 | 4 | prawo do pozycji lokalnej rozróżnia M2 od M3, a przymus asortymentowy rozróżnia M0 od M1b |
| CAT-02 | 2 | na bramce cennika liczy się wyłącznie kierunek: kto tworzy, kto nakłada |
| CAT-03 | 2 | jak wyżej |

**Wniosek do wykorzystania na warsztacie:** pełny test klasyfikacyjny (T0/T0a/T0b/T1/T1g/T2/T2z/T3) wykonuje się raz, na
początku, per jednostka. Przy konkretnej bramce zwykle wystarcza gruby podział na „centrala
prowadzi" kontra „lokalizacja prowadzi". Rozróżnienie M1a/M1b staje się istotne dopiero tam, gdzie
bramka pyta o obowiązkowość (udział w promocji, przymus asortymentowy, nakładka cennika).

## Kryterium sukcesu i uczciwa ocena

Kryterium ustalone **z góry**, przed budową (wewnętrzny rejestr tematów odłożonych, wpis z 19.08.2026):

> jeśli macierz wchłonie wszystkie różnice z dyktand i żadna karta nie potrzebuje wariantu,
> warstwa działa i rozciągamy ją dalej

**Ocena na dziś, po trzech kartach i recenzji pakietu B1:**

| Sprawdzenie | Wynik |
|---|---|
| Czy macierz wchłonęła wszystkie różnice z dyktand? | **Tak** dla dziewięciu bramek z trzech kart |
| Czy któraś karta potrzebowała wariantu? | **Nie.** Wszystkie trzy opisują jeden przebieg z oznaczonymi odcinkami warunkowymi |
| Czy oś pojawiła się niezależnie? | **Tak, trzy razy**, za każdym razem z dyktanda, nie z researchu |
| Czy test klasyfikował wszystkie typy? | **NIE w v0.2** — falsyfikator pkt 3 zadziałał (recenzja B-03/B-04): brak wyniku dla grupy zakupowej, sklejenie M1, błędna bramka osoby prawnej. Przebudowa v0.3 = odpowiedź; jej PASS wymaga retestu (profile falsyfikacyjne w zestawie retestu) |

**Czego ta ocena NIE dowodzi.** Trzy karty pochodzą z **jednej domeny** i z **jednego źródła
wiedzy**, czyli od tego samego właściciela. Zgodność może wynikać z tego, że tak samo o tym myśli,
a nie z tego, że tak działa rynek. Rozciągnięcie warstwy na kolejne domeny jest **testem, nie
potwierdzeniem**.

## Co obali tę warstwę

Zapisane teraz, żeby nie dało się później dopasować kryterium do wyniku:

1. **Karta, która potrzebuje wariantu, a nie odcinka warunkowego.** Jeśli jakiś proces przy klasie
   M1a/M1b ma inne KROKI, a nie inną obsadę bramek, warstwa nie wystarcza.
2. **Bramka, na której klasy się nie porządkują.** Jeśli M1x zachowuje się jak M3, a M2 jak M0,
   to oś nie jest osią, tylko listą przypadków.
3. **Jednostka, której test bramkowy (T0/T0a/T0b/T1/T1g/T2/T2z/T3) nie klasyfikuje.** Test ma dawać jednoznaczną odpowiedź albo
   jawny wynik „poza typologią sieciową" / „nierozstrzygnięty". Pierwszy realny przypadek bez
   żadnego z tych wyników = test źle zbudowany. (Wystąpienie 26.08: grupa zakupowa i typy
   partnerska/miękka — skonsumowane przebudową v0.3; kolejne wystąpienie obala v0.3.)
4. **Domena, w której klasa osi nie zmienia niczego.** To akurat nie obala warstwy, tylko
   ogranicza jej zasięg, i też trzeba to zapisać.

Pierwsze wystąpienie któregokolwiek z tych czterech idzie do wewnętrznego rejestru decyzji z werdyktem,
co dalej z tym artefaktem.

## Stan i następny krok

Zbudowane na trzech kartach domeny CAT; oś przebudowana 26.08 po recenzji pakietu B1.
**Stan testów:** oś przetestowana w retestach #1-#3 (falsyfikatory 11/11 PASS, obie kontrole
negatywne PASS) + kontrola domknięcia 3.1 PASS 7/7. Zmiany naprawy B1 (D-B1/B2/T2z) = wejście
do WĄSKIEGO retestu regresyjnego (kontrprzykłady RB-1..RB-11, klucz TESTY v2.2). Wąski retest chirurgiczny v0.11: **PASS** — RB-1..RB-11 = 11/11 oraz NEG-1 (kontrola mutacyjna); zakres i surowe wyjście w komponencie 6.
