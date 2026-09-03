# [ORPR-CAT-04] Commercial-Action-to-Effect

Podtytuł roboczy: od zakończonego działania handlowego do oceny wyniku i wiedzy przydatnej przy projektowaniu kolejnych działań.

| | |
|---|---|
| ID | ORPR-CAT-04 |
| Wersja karty | 0.8 |
| Status | reviewed |
| Stan redakcyjny | naprawa po trzeciej recenzji wydaniowej CODEX/GPT-5 22.08.2026: blokery 1-3 zamknięte (stara granica "zakończenie działania" domknięta per klasa; kontrakt danych na poziomach spójny; pytania złożone rozbite), bloker 4 zamknięty nośnikiem decyzji właściciela; wewnętrzny materiał roboczy EXIT 0; kandydat zmieniony, wymagana czwarta recenzja wydaniowa |
| Klasa treści | rdzeń retail-neutralny; warstwa branżowa w profile/ |
| Bezpieczniki R | regulatory-matrix v1.0.1, legal_as_of 2026-08-14; wartość odziedziczona z kart siostrzanych, bez bezpośredniego odczytu RM |
| Clean-room | 2026-08-21: dyktando właściciela i źródła publiczne; zero materiałów klientów i pracodawców |
| Główny autor | Sol, Codex |
| Dyktando | wewnętrzny materiał roboczy |
| Decyzje właściciela | wewnętrzny materiał roboczy |
| Decyzja o horyzoncie | wewnętrzny materiał roboczy (decyzja właściciela 22.08.2026 o regułach granicy i horyzontu obserwacji per klasa) |
| Samokontrola | wewnętrzny materiał roboczy |
| Modele operacyjne | `standard/mapowania/modele-operacyjne.md` |

## Zmiany w wersji 0.8

Naprawa po trzeciej recenzji wydaniowej CODEX/GPT-5 (22.08.2026, raport: wewnętrzny materiał roboczy). Blokery 1-3 zamknięte redakcją operatora, bloker 4 zamknięty nośnikiem decyzji właściciela wewnętrzny materiał roboczy.

- **bloker 1 (R12, stara granica "zakończenie działania" użyta globalnie):** pole 1 (cel), pole 6 (wyzwalacze) i pole 13 (miernik czasu zamknięcia) doprecyzowane osobnym zdaniem [PROP+ 22.08], że dla klas bez naturalnego końca "zakończone/zakończenie działania" oznacza wejście zmiany w życie plus upływ zadeklarowanego horyzontu obserwacji, nie koniec okna; pytanie A39 zawężone do działania z własnym oknem (promocji); dodane pytanie A42 o zadeklarowany horyzont obserwacji jako kontrola per wymiar (wartość, ustalenie przed startem, kto zatwierdził, co gdy horyzontu brak); w Bramce 1 dodana kontrola wejścia [PROP+ 22.08]: dla klas bez naturalnego końca ocena nie rusza bez horyzontu zadeklarowanego przed wejściem zmiany w życie.
- **bloker 2 (3a.2, kontrakt danych na poziomach):** dowody wykonania `wykonanie-zmiany-ceny` i `wykonanie-zmiany-asortymentu` przeniesione z analizy pogłębionej do nowej grupy pola 7 "Obowiązkowe warunkowo dla klasy: trwała cena albo asortyment"; do grupy kwalifikacyjnej dodane cztery przesłanki pogłębienia (`wartosc-finansowa`, `znaczenie-strategiczne`, `powtarzalnosc-problemu`, `ryzyko-sporu`) i skonsumowane przez Bramkę 1; minimalny zakres planktonu ujednolicony (wynik działania, wynik produktu, warunki korzyści, dane rozliczeniowe) między polami 7, 8, 9 i 11.
- **bloker 3 (3a.5, pytania złożone):** A37, A38, B17, B24, B25, C24 i C25 przekształcone w kontrolę per wymiar (tabela wymuszająca osobną odpowiedź na każdy wymiar) tym samym wzorcem co B19, C9, C13 i C16, bez zmiany numeracji.
- **bloker 4 (nośnik decyzji, zamknięty osobnym plikiem):** w nagłówku dodano wiersz wskazujący nośnik decyzji właściciela o regułach horyzontu; w legendzie klas twierdzeń dodano wiersz `[PROP+ 22.08]`.

Kandydat zmieniony, wymagana czwarta recenzja wydaniowa (zasady governance projektu).

## Zmiany w wersji 0.7

Naprawa po re-recenzji wydaniowej CODEX/GPT-5 (tura 2, 22.08.2026). Cztery blokery zamknięte:

- **granica czasowa per klasa (blokery 1 i 3.1, R12):** pole 2 i wyzwalacze rozróżniają działania z własnym oknem (promocja) od trwałej zmiany ceny i asortymentu; dla tych drugich start pomiaru to wejście zmiany w życie plus zadeklarowany przed startem horyzont obserwacji. Horyzont dodany do `[D! definicja-dzialania]`. Ocena cykliczna odłożona jako odcinek warunkowy (rejestr tematów odłożonych).
- **podział danych na poziomy (bloker 2, P21):** pole 7 przebudowane na cztery grupy; dodana grupa „do kwalifikacji poziomu” (przed Bramką 1) z `typ-marki`; `koszt-dzialania`, `dane-kanalowe` i `dane-regionalne` przeniesione z analizy pogłębionej na poziom, na którym warunek może zajść, i oznaczone warunkowo. Zbiór 27 identyfikatorów danych bez zmian.
- **F4 bez pytania atrybucji (bloker 3, 3a.3):** dodane A41 o rozdzieleniu wyniku obserwowanego od efektu przypisanego działaniu; przypisane do F4.
- **pytania złożone (bloker 4, 3a.5):** B19, C9, C13 i C16 zamienione na kontrolę per wymiar (odpowiedź na każdy wymiar osobno). B17, C24 i C25 zostawione świadomie: to atrybuty tego samego faktu, a definicja 3a.5 zwalnia doprecyzowanie tego samego faktu.

Kandydat zmieniony, wymagana trzecia recenzja wydaniowa (zasady governance projektu).

## Zmiany w wersji 0.6

- naprawa po recenzji wydaniowej FABLE 22.08.2026 (raport: wewnętrzny materiał roboczy)
- bloker 3a.3: dodano pytania A39 i A40 wykrywające flagi F19 i F20; zaktualizowano listy pytań obu flag
- bloker sprzeczności: pole 7 rozdzielono na obowiązkowe dla oceny minimalnej oraz dodatkowe dla podstawowej (plankton nie wymaga celu, założeń ani metody porównania, zgodnie z bramką 1 i dyktandem 21.08 par.16)
- bloker tagowania: rozdzielono „osobny proces rozliczenia" [AUT-R 21.08] od identyfikacji ORPR-PRC-04 [PROP+ 21.08] w polu 2 i bramce 6; pole 13 przetagowane [AUT-R] na [PROP+]
- pole 13: crosswalk wskazuje plik kanoniczny zamiast propozycji z wewnętrznego materiału roboczego
- bramka 6: rozdzielono nowy wniosek zwrotny od wejścia porównawczego `historia-mechaniki`
- pole 2: dodano notę, że ORPR-PRC-04 jest dopiero planowana (rejestr tematów odłożonych)
- status pozostaje `reviewed`; naprawa zmieniła kandydata, więc wymagana ponowna recenzja wydaniowa (zasady governance projektu)

## Zmiany w wersji 0.5

- nadano status `reviewed` po przejściu samokontroli 14/14 [PROP+ 21.08]
- dodano odwołanie do artefaktu samokontroli
- nie zmieniono treści biznesowej wersji 0.4

## Zmiany w wersji 0.4

- rozbito trzy pytania łączące niezależne decyzje o ustaleniu celu, zatwierdzeniu oceny i wykorzystaniu wniosku
- zaktualizowano całą numerację pytań oraz odwołania we flagach
- rozdzielono trzy zbiorcze tagi obejmujące po dwa twierdzenia
- status pozostaje `draft` do zakończenia ponownej samokontroli

## Zmiany w wersji 0.3

- cofnięto status do `draft` do czasu ukończenia crosswalku i ponownej samokontroli
- dodano powiązanie z warstwą modeli operacyjnych M0-M3 i pytanie otwierające bank
- dodano osobne kontrole wykonania trwałej zmiany ceny i zmiany asortymentowej
- doprecyzowano lokator APQC i przypisano źródło Leeflanga do efektów między kategoriami
- usunięto nieprecyzyjne twierdzenie o wymaganiach PRICE-001..005
- domknięto użycia danych o założeniach produktowych i koszcie działania
- termin „total” zastąpiono „wynikiem łącznym”; poprawiono literówkę i uproszczono legendę
- pole 10 przywrócono do trzech skutków wymaganych przez szablon

## Zmiany w wersji 0.2

- usunięto błędną logikę „werdyktu o powtórzeniu akcji” [AUT-R 21.08]
- wynikiem procesu jest wiedza o mechanikach i warunkach ich działania [AUT-R 21.08]
- wprowadzono ocenę minimalną, podstawową i pogłębioną [PROP+ 21.08]
- pozostawiono szeroki zakres: promocje, zmiany ceny regularnej i zmiany asortymentowe [PROP+ 21.08]
- przy ważnych działaniach dopuszczono badanie okresu po akcji i wpływu na inne produkty [PROP+ 21.08]
- marka własna jest przesłanką pogłębienia, ale nie tworzy automatycznego obowiązku [PROP+ 21.08]
- wiedza wraca do procesu źródłowego bez automatycznego polecenia wykonania [PROP+ 21.08]

## Klasy twierdzeń

| Tag | Znaczenie |
|---|---|
| `[AUT-R 21.08]` | wiedza właściciela zapisana w dyktandzie |
| `[PROP+ 21.08]` | propozycja redakcyjna przyjęta przez właściciela 21.08.2026 |
| `[PROP+ 22.08]` | propozycja redakcyjna przyjęta przez właściciela 22.08.2026 (nośnik: wewnętrzny materiał roboczy) |
| `[LIT: ...]` | źródło publiczne z lokatorem |
| `[do weryfikacji]` | kandydat na wiązanie regulacyjne, bez asercji prawa |
| `[D! id]` | deklaracja danej wejściowej w polu 7 |
| `[D: id]` | użycie danej przez kontrolę albo czerwoną flagę |

## Miejsce procesu

ORPR-CAT-04 nie jest procesem ponownego uruchamiania zakończonej akcji. [AUT-R 21.08]

Kolejne działanie zwykle powstaje od nowa, z innymi produktami, producentami albo warunkami. [AUT-R 21.08]

Przenoszona jest wiedza o mechanikach i warunkach ich działania, nie cała akcja. [AUT-R 21.08]

Proces może oceniać:

- akcję promocyjną [PROP+ 21.08]
- trwałą zmianę ceny regularnej [PROP+ 21.08]
- zmianę asortymentową [PROP+ 21.08]
- inne ograniczone w czasie działanie handlowe z własnym celem i wynikiem [PROP+ 21.08]

Sposób pomiaru może być inny dla każdej klasy działania. [PROP+ 21.08]

Sieć ocenia działanie wyłącznie według własnego celu. [AUT-R 21.08]

Cel producenta może być ukryty w warunku handlowym, ale nie zastępuje celu sieci. [AUT-R 21.08]

## Model operacyjny

Klasy M0-M3 oraz test T1-T3 są zdefiniowane w `standard/mapowania/modele-operacyjne.md`. [PROP+ 21.08]

Ta karta korzysta z klasyfikacji i nie powtarza wspólnej macierzy. [PROP+ 21.08]

W CAT-04 model operacyjny rozstrzyga, kto po stronie sieci ma prawo ustalić jej cel, zatwierdzić ocenę i zdecydować o wykorzystaniu wniosku. [PROP+ 21.08]

Model operacyjny nie zmienia etapów analizy. [PROP+ 21.08]

Relacja sieci z producentem jest odrębną osią. [AUT-R 21.08]

Producent może inicjować lub finansować działanie, ale sieć nadal ocenia je według własnego celu. [AUT-R 21.08]

Zarządzanie kategorią jest warunkowym wymiarem opisanym we wspólnej warstwie modeli. [PROP+ 21.08]

W tej karcie zarządzanie kategorią wpływa na obsadę decyzji, a nie tworzy osobnego wariantu procesu. [PROP+ 21.08]

## Model pojęciowy

### Akcja, cel, mechanika i kontekst

| Pojęcie | Znaczenie |
|---|---|
| działanie handlowe | zaplanowana całość mogąca obejmować wiele produktów, cen, mechanik i elementów komunikacji [AUT-R 21.08] |
| cel sieci | własny wynik, według którego sieć ocenia działanie [AUT-R 21.08] |
| założenie produktowe | oczekiwany wynik konkretnego produktu w ramach działania [AUT-R 21.08] |
| mechanika | sposób przyznania korzyści albo wywołania oczekiwanego zachowania [PROP+ 21.08] |
| wykonanie | faktyczna konfiguracja, dostępność towaru, ekspozycja i uruchomienie komunikacji [AUT-R 21.08] |
| kontekst | warunki rynkowe i inne okoliczności mogące wpłynąć na wynik [AUT-R 21.08] |
| wiedza po działaniu | zapis tego, co wiadomo o mechanice, wykonaniu i warunkach działania [PROP+ 21.08] |

Działanie jest oceniane jako całość. [AUT-R 21.08]

Standardowy wynik obejmuje także łączny wynik każdego produktu w ramach działania. [AUT-R 21.08]

Cele albo założenia produktowe mogą powstać przy projektowaniu każdej akcji. [AUT-R 21.08]

Zejście do regionów, sklepów, kanałów albo pojedynczych transakcji następuje tylko wtedy, gdy wymaga tego rozliczenie albo diagnoza ważnego działania. [AUT-R 21.08]

### Trzy poziomy oceny

#### Ocena minimalna

Ocena minimalna dotyczy działania o małym znaczeniu, nazywanego w praktyce „planktonem”. [AUT-R 21.08]

Jej celem jest potwierdzenie wyniku i warunku dodatkowej korzyści od producenta. [AUT-R 21.08]

Ocena minimalna nie musi tworzyć wniosku marketingowego. [PROP+ 21.08]

#### Ocena podstawowa

Ocena podstawowa porównuje wynik całego działania z własnym celem sieci. [AUT-R 21.08]

Ocena podstawowa porównuje wyniki produktów z założeniami produktowymi. [AUT-R 21.08]

Krótki wniosek powstaje tylko wtedy, gdy zawiera wiedzę użyteczną przy kolejnych działaniach. [PROP+ 21.08]

#### Analiza pogłębiona

Analiza pogłębiona sprawdza wykonanie mechaniki. [AUT-R 21.08]

Analiza pogłębiona sprawdza jakość prognozy i założeń. [AUT-R 21.08]

Analiza pogłębiona sprawdza dostępność towaru. [AUT-R 21.08]

Analiza pogłębiona sprawdza wykonanie ekspozycji, gazetki, mediów i innych elementów wsparcia. [AUT-R 21.08]

Analiza pogłębiona uwzględnia niespodziewane zmiany rynku i działania konkurencji. [AUT-R 21.08]

Analiza pogłębiona może zbadać okres po zakończeniu akcji. [PROP+ 21.08]

Analiza pogłębiona może zbadać wpływ działania na inne produkty. [PROP+ 21.08]

### Kiedy pogłębiać

Duża wartość finansowa jest przesłanką analizy pogłębionej. [AUT-R 21.08]

Znaczenie strategiczne jest przesłanką analizy pogłębionej. [AUT-R 21.08]

Powtarzający się problem jest przesłanką analizy pogłębionej. [AUT-R 21.08]

Możliwy spór z producentem jest przesłanką analizy pogłębionej. [AUT-R 21.08]

Produkt marki własnej jest przesłanką analizy pogłębionej. [AUT-R 21.08]

Marka własna nie tworzy automatycznego obowiązku pogłębionej analizy. [PROP+ 21.08]

### Kiedy zakończyć analizę

Analiza ma być proporcjonalna do wartości przyszłej decyzji. [AUT-R 21.08]

Nie zawsze da się precyzyjnie określić, co wpłynęło na wynik. [AUT-R 21.08]

Dopuszczalnym wynikiem jest „nie udało się jednoznacznie ustalić przyczyny”. [PROP+ 21.08]

Dalsza analiza nie jest wymagana, jeżeli jej koszt przewyższa oczekiwaną wartość wiedzy. [AUT-R 21.08]

### Wynik obserwowany i efekt przypisany

Wynik w okresie działania jest obserwowalny. [LIT: Brodersen i in., 2015, abstrakt]

Przypisanie całej różnicy samemu działaniu wymaga oszacowania wyniku, który wystąpiłby bez niego. [LIT: Brodersen i in., 2015, abstrakt i sekcja 2]

Karta nie wymaga zaawansowanego modelu statystycznego dla każdego działania. [PROP+ 21.08]

Karta nie wymaga grupy kontrolnej dla każdego działania. [PROP+ 21.08]

Raport wskazuje, jaki wynik zaobserwowano. [PROP+ 21.08]

Raport wskazuje zastosowany sposób porównania. [PROP+ 21.08]

Raport rozdziela efekt możliwy do przypisania działaniu od zwykłego współwystępowania. [PROP+ 21.08]

Raport ujawnia ograniczenia dostępnych danych. [PROP+ 21.08]

Badania promocji cenowych rozkładają krótkoterminowy wzrost na ekspansję kategorii, przesunięcia między produktami i przesunięcia między okresami. [LIT: van Heerde, Leeflang, Wittink, 2004, abstrakt]

Sam wzrost sprzedaży promowanego produktu nie dowodzi równoważnego wzrostu dla sieci. [PROP+ 21.08]

### Proces nauki

APQC rozdziela ocenę wyników promocji, poprawianie podejścia i włączanie wiedzy do przyszłych działań. [LIT: APQC PCF Cross-Industry v8.0, 3.3.4.6 (10170), 3.3.4.7 (10171), 3.3.4.8 (10172), sekcja Measure Scope, dostęp 22.08.2026]

ORPR-CAT-04 łączy te funkcje w jednym procesie L1. [PROP+ 21.08]

Wiedza do ponownego użycia dotyczy mechaniki. [AUT-R 21.08]

Wiedza do ponownego użycia opisuje warunki działania mechaniki. [PROP+ 21.08]

Wiedza do ponownego użycia może dotyczyć błędu wykonania albo błędu prognozy. [AUT-R 21.08]

Wniosek nie tworzy automatycznego polecenia wykonania kolejnej akcji. [PROP+ 21.08]

## 1. Cel biznesowy

Ocenić zakończone działanie handlowe według własnego celu sieci. [AUT-R 21.08]

Dla klas bez naturalnego końca (trwała zmiana ceny regularnej, zmiana asortymentowa) "zakończone działanie" w tym celu oznacza wejście zmiany w życie i upływ zadeklarowanego przed startem horyzontu obserwacji, nie zakończenie okna działania. [PROP+ 22.08]

Potwierdzić warunki należnych korzyści od producenta. [AUT-R 21.08]

Zachować wiedzę przydatną przy projektowaniu kolejnych działań. [AUT-R 21.08]

Domyślnym celem, gdy nie wskazano innego, może być wzrost łącznej kwoty marży brutto. [AUT-R 21.08]

Akcja marketingowa prawie nigdy nie ma na celu podniesienia procentowej marży. [AUT-R 21.08]

## 2. Granice

Proces zaczyna się po zakończeniu działania, gdy dostępny jest wynik z okresu jego trwania. [AUT-R 21.08] Reguła ta dotyczy działań z własnym oknem czasowym, czyli promocji. [PROP+ 22.08]

Klasy bez naturalnego końca kończą wdrożenie, nie oddziaływanie, więc moment startu pomiaru i okno oceny rozstrzyga się per klasa, a horyzont obserwacji jest deklarowany przed działaniem w `[D: definicja-dzialania]`: [PROP+ 22.08]

- promocja: po wygaśnięciu okna działania; [PROP+ 22.08]
- trwała zmiana ceny regularnej: po zdarzeniu `cena-weszła-w-życie` z ORPR-CAT-02 i po upływie zadeklarowanego horyzontu obserwacji; [PROP+ 22.08]
- zmiana asortymentowa: po potwierdzeniu zmiany statusu pozycji z ORPR-CAT-01 i po upływie zadeklarowanego horyzontu obserwacji; [PROP+ 22.08]
- ocena późniejsza albo cykliczna trwałej zmiany wymaga jawnego ponownego wyzwalacza i jest odcinkiem warunkowym (patrz rejestr tematów odłożonych). [PROP+ 22.08]

Proces kończy się zapisaniem oceny realizacji własnego celu sieci. [PROP+ 21.08]

Jeżeli działanie obejmowało korzyść od producenta, proces kończy się również potwierdzeniem spełnienia albo niespełnienia jej warunku. [AUT-R 21.08]

Jeżeli powstała użyteczna wiedza, proces kończy się zapisaniem wniosku o mechanice, wykonaniu, prognozie albo kontekście. [PROP+ 21.08]

Proces nie tworzy ani nie uruchamia promocji. [PROP+ 21.08]

ORPR-CAT-03 prowadzi promocję od zatwierdzonej definicji do aktywacji i zaplanowanego wygaśnięcia. [PROP+ 21.08; lokator: `standard/domeny/CAT/ORPR-CAT-03-promotion-to-pos.md`, pole 2]

Proces nie ustala ceny regularnej ani nie zmienia cennika. [PROP+ 21.08]

ORPR-CAT-02 prowadzi zdarzenie cenowe do potwierdzonego obowiązywania i zapisu w historii. [PROP+ 21.08; lokator: `standard/domeny/CAT/ORPR-CAT-02-price-to-pos.md`, pole 2]

Proces nie podejmuje decyzji asortymentowej. [PROP+ 21.08]

ORPR-CAT-01 prowadzi decyzję o wprowadzeniu pozycji przez dopuszczenie do sprzedaży, zmiany, wycofanie i następstwo. [PROP+ 21.08; lokator: `standard/domeny/CAT/ORPR-CAT-01-item-to-sellable.md`, pole 2]

Proces nie rozlicza należności ani korzyści z producentem. [AUT-R 21.08]

Potwierdzony warunek i podstawa wyliczenia są przekazywane do procesu rozliczenia korzyści. [AUT-R 21.08] Tym procesem jest ORPR-PRC-04. [PROP+ 21.08]

Karta ORPR-PRC-04 jest na dzień tej redakcji dopiero planowana (wewnętrzny rejestr tematów odłożonych). CAT-04 definiuje kontrakt wyjściowy do rozliczenia, a jego odbiór zostanie potwierdzony przy redakcji PRC-04.

## 3. Właściciel

Właścicielem wyniku jest osoba biznesowo odpowiedzialna za działanie. [AUT-R 21.08]

Analizę przygotowuje analityk albo controlling. [AUT-R 21.08]

Biznes decyduje, jak wykorzystać wnioski. [AUT-R 21.08]

Producent często kreuje politykę promocyjną, gdy sieć działa głównie jako kanał dystrybucji. [AUT-R 21.08]

Duża sieć z category managementem częściej prowadzi własną politykę. [AUT-R 21.08]

## 4. Aktorzy

- osoba biznesowo odpowiedzialna za działanie [AUT-R 21.08]
- analityk albo controlling [AUT-R 21.08]
- category manager, jeżeli organizacja prowadzi category management [AUT-R 21.08]
- przedstawiciel producenta jako inicjator albo partner działania [AUT-R 21.08]
- osoba odpowiedzialna za konfigurację mechaniki [PROP+ 21.08]
- logistyka albo planowanie dostępności [PROP+ 21.08]
- marketing odpowiedzialny za ekspozycję i komunikację [AUT-R 21.08]
- właściciel danych sprzedażowych i marżowych [PROP+ 21.08]
- osoba odpowiedzialna za rozliczenie korzyści w ORPR-PRC-04 [PROP+ 21.08]

## 5. Systemy

- rejestr definicji i założeń działania [PROP+ 21.08]
- silnik promocji albo system cennikowy [PROP+ 21.08]
- POS i kanały sprzedaży [PROP+ 21.08]
- system zapasu i dostępności [PROP+ 21.08]
- system kosztów i marży brutto [PROP+ 21.08]
- narzędzie analityczne albo warstwa raportowa [PROP+ 21.08]
- rejestr działań marketingowych i ekspozycji [PROP+ 21.08]
- rejestr warunków handlowych z producentem [PROP+ 21.08]
- repozytorium wniosków po działaniach [PROP+ 21.08]

## 6. Wyzwalacze

- zakończenie działania oznaczonego przed startem jako wymagające analizy [AUT-R 21.08]
- zakończenie działania, które po fakcie okazało się istotne [AUT-R 21.08]
- potrzeba potwierdzenia warunku korzyści od producenta [AUT-R 21.08]
- powtarzający się błąd prognozy albo wykonania [AUT-R 21.08]
- możliwy spór z producentem [AUT-R 21.08]
- zakończenie ważnego działania dotyczącego marki własnej [AUT-R 21.08]
- dla trwałej zmiany ceny albo asortymentu: upływ zadeklarowanego horyzontu obserwacji po wejściu zmiany w życie, w miejsce zakończenia działania [PROP+ 22.08]

Wyzwalacze oparte na "zakończeniu działania" dotyczą działań z własnym oknem czasowym (promocji); dla trwałej zmiany ceny i zmiany asortymentowej obowiązuje powyższy wyzwalacz upływu zadeklarowanego horyzontu obserwacji. [PROP+ 22.08]

## 7. Wejścia

### Do kwalifikacji poziomu (zbierane przed Bramką 1)

- `[D! definicja-dzialania]` zakres, produkty, mechaniki, okres i kanały [PROP+ 21.08]; dla działań bez naturalnego końca dochodzi zadeklarowany przed startem horyzont obserwacji [PROP+ 22.08]
- `[D! typ-dzialania]` promocja, trwała zmiana ceny, zmiana asortymentowa albo inna jawnie zdefiniowana klasa [PROP+ 21.08]
- `[D! model-operacyjny]` klasa M0-M3 wyznaczona testem T1-T3 [PROP+ 21.08]
- `[D! typ-marki]` oznaczenie marki własnej albo marki producenta [AUT-R 21.08]
- `[D! warunki-korzysci]` warunki korzyści od producenta [AUT-R 21.08]
- `[D! wartosc-finansowa]` szacowana wartość finansowa działania, przesłanka pogłębienia [PROP+ 22.08]
- `[D! znaczenie-strategiczne]` znaczenie strategiczne działania, przesłanka pogłębienia [PROP+ 22.08]
- `[D! powtarzalnosc-problemu]` czy podobny problem powtarza się w innych działaniach, przesłanka pogłębienia [PROP+ 22.08]
- `[D! ryzyko-sporu]` ryzyko sporu z producentem, przesłanka pogłębienia [PROP+ 22.08]

### Obowiązkowe dla oceny minimalnej

- `[D! wynik-dzialania]` łączny wynik działania [AUT-R 21.08]
- `[D! wynik-produktu]` łączny wynik każdego produktu [AUT-R 21.08]
- `[D! dane-rozliczeniowe]` poziom szczegółowości wymagany do rozliczenia [AUT-R 21.08]
- `[D! dane-regionalne]` wynik per region, jeżeli wymaga go rozliczenie albo diagnoza [AUT-R 21.08]

### Obowiązkowe warunkowo dla klasy: trwała cena albo asortyment

- `[D! wykonanie-zmiany-ceny]` potwierdzenie wejścia ceny regularnej w życie w planowanym czasie i zakresie [PROP+ 21.08]; obowiązkowe dla oceny trwałej zmiany ceny, sprawdzane w Bramce 3 przed interpretacją wyniku [PROP+ 22.08]
- `[D! wykonanie-zmiany-asortymentu]` potwierdzenie wejścia zmiany asortymentowej w życie w planowanym czasie i zakresie [PROP+ 21.08]; obowiązkowe dla oceny zmiany asortymentowej, sprawdzane w Bramce 3 przed interpretacją wyniku [PROP+ 22.08]

### Dodatkowe obowiązkowe dla oceny podstawowej

- `[D! cel-glowny]` własny cel główny sieci [AUT-R 21.08]
- `[D! zalozenia-produktowe]` cele albo założenia dla produktów [AUT-R 21.08]
- `[D! metoda-porownania]` sposób porównania ustalony dla danego działania [AUT-R 21.08]
- `[D! marza-brutto]` kwota marży brutto, jeżeli jest celem albo miarą pomocniczą [AUT-R 21.08]
- `[D! koszt-dzialania]` koszty poniesione przez sieć [PROP+ 21.08]; wchodzi warunkowo, gdy oceniany jest wynik finansowy po kosztach [PROP+ 22.08]
- `[D! dane-kanalowe]` wynik per kanał, jeżeli wymaga go cel albo diagnoza [PROP+ 21.08]

### Dodatkowe dla analizy pogłębionej

- `[D! konfiguracja-mechaniki]` faktyczna konfiguracja mechaniki [AUT-R 21.08]
- `[D! test-mechaniki]` dowód poprawnego naliczania mechaniki [AUT-R 21.08]
- `[D! dostepnosc-towaru]` dostępność produktów w zakresie działania [AUT-R 21.08]
- `[D! wykonanie-merch]` wykonanie ekspozycji albo innych elementów merchandisingowych [AUT-R 21.08]
- `[D! wykonanie-mediow]` wykonanie gazetki, kampanii i pozostałej komunikacji [AUT-R 21.08]
- `[D! kontekst-rynkowy]` znane działania konkurencji i istotne zmiany rynku [AUT-R 21.08]
- `[D! prognoza]` prognoza i przesłanki użyte do jej budowy [AUT-R 21.08]
- `[D! okres-po-dzialaniu]` wynik z uzasadnionego okresu po zakończeniu działania [PROP+ 21.08]
- `[D! wyniki-innych-produktow]` wyniki produktów mogących podlegać substytucji albo efektowi uzupełniającemu [PROP+ 21.08]
- `[D! historia-mechaniki]` wcześniejsze wnioski dotyczące mechaniki [PROP+ 21.08]

## 8. Wyjścia

### Ocena minimalna

- wynik działania i produktów [AUT-R 21.08]
- potwierdzenie spełnienia albo niespełnienia warunku korzyści [AUT-R 21.08]
- dane wymagane do rozliczenia w ORPR-PRC-04 [PROP+ 21.08]

### Ocena podstawowa

- porównanie wyniku działania z własnym celem sieci [AUT-R 21.08]
- porównanie wyników produktów z założeniami [AUT-R 21.08]
- krótki wniosek, jeżeli powstała użyteczna wiedza [PROP+ 21.08]

### Analiza pogłębiona

- diagnoza wykonania mechaniki [AUT-R 21.08]
- ocena jakości prognozy i założeń [AUT-R 21.08]
- opis znanych ograniczeń logistycznych i komunikacyjnych [AUT-R 21.08]
- opis istotnych zmian rynku [AUT-R 21.08]
- ocena wpływu na inne produkty, jeżeli została wykonana [PROP+ 21.08]
- ocena okresu po działaniu, jeżeli została wykonana [PROP+ 21.08]
- wniosek o mechanice i warunkach jej działania [PROP+ 21.08]
- zapis „przyczyna nierozstrzygnięta”, jeżeli dalsze badanie nie ma uzasadnienia [PROP+ 21.08]

### Zdarzenia

- działanie-ocenione [PROP+ 21.08]
- warunek-korzyści-potwierdzony [PROP+ 21.08]
- analiza-pogłębiona-uruchomiona [PROP+ 21.08]
- wniosek-o-mechanice-zapisany [PROP+ 21.08]
- dane-do-rozliczenia-przekazane [PROP+ 21.08]

## 9. Bramki decyzyjne i kontrole

### Bramka 1: wybór poziomu oceny

Obsada decyzji wynika z `[D: model-operacyjny]`, zgodnie ze wspólną warstwą modeli M0-M3. [PROP+ 21.08]

Sposób oceny jest dobierany do `[D: typ-dzialania]`; promocja, trwała zmiana ceny i zmiana asortymentowa nie muszą korzystać z identycznych miar. [PROP+ 21.08]

Działanie o małym znaczeniu może zostać ograniczone do danych wymaganych przez `[D: warunki-korzysci]`. [AUT-R 21.08]

Działanie ważne przechodzi co najmniej ocenę podstawową. [PROP+ 21.08]

Działanie może zostać skierowane do analizy pogłębionej po zakończeniu, jeżeli wynik albo zdarzenie okaże się istotne. [AUT-R 21.08]

Marka własna rozpoznana przez `[D: typ-marki]` zwiększa zasadność analizy pogłębionej. [AUT-R 21.08]

Wybór poziomu bierze pod uwagę przesłanki pogłębienia znane przed Bramką 1: `[D: wartosc-finansowa]`, `[D: znaczenie-strategiczne]`, `[D: powtarzalnosc-problemu]` i `[D: ryzyko-sporu]`. [PROP+ 22.08]

Minimalny zakres oceny działania o małym znaczeniu obejmuje zawsze `[D: wynik-dzialania]`, `[D: wynik-produktu]`, `[D: warunki-korzysci]` i `[D: dane-rozliczeniowe]`; ograniczenie do samego warunku korzyści nie znosi wyniku działania, wyniku produktu ani danych rozliczeniowych, i jest zgodne z polami 7, 8 i 11. [PROP+ 22.08]

Dla działania bez naturalnego końca (trwała zmiana ceny albo zmiana asortymentowa) ocena nie rusza, dopóki nie potwierdzono, że horyzont obserwacji zadeklarowano w `[D: definicja-dzialania]` przed wejściem zmiany w życie; brak zadeklarowanego horyzontu jest błędem wejścia, nie wynikiem oceny. [PROP+ 22.08]

### Bramka 2: możliwość oceny celu

Cel z `[D: cel-glowny]` musi być własnym celem sieci. [AUT-R 21.08]

Cel sieci musi być oddzielony od celu producenta. [AUT-R 21.08]

Brak jawnego celu nie może być zastąpiony miarą wybraną po zakończeniu działania. [PROP+ 21.08]

Jeżeli nie wskazano innego celu, można zastosować wzrost kwoty `[D: marza-brutto]`. [AUT-R 21.08]

Wynik jest porównywany metodą zapisaną w `[D: metoda-porownania]`. [AUT-R 21.08]

Wynik działania z `[D: wynik-dzialania]` jest pokazywany osobno. [AUT-R 21.08]

Wyniki produktów z `[D: wynik-produktu]` są pokazywane osobno. [AUT-R 21.08]

Założenia z `[D: zalozenia-produktowe]` są porównywane z odpowiadającymi im wynikami produktów. [AUT-R 21.08]

Jeżeli ocena dotyczy wyniku finansowego po kosztach działania, `[D: koszt-dzialania]` wchodzi do kalkulacji i jest pokazywany oddzielnie. [PROP+ 21.08]

### Bramka 3: zgodność wykonania z planem

Dla promocji przy słabym wyniku najpierw porównuje się `[D: konfiguracja-mechaniki]` z `[D: definicja-dzialania]`. [AUT-R 21.08]

Poprawność naliczania promocji sprawdza się przez `[D: test-mechaniki]`. [AUT-R 21.08]

Dla trwałej zmiany ceny najpierw sprawdza się `[D: wykonanie-zmiany-ceny]`. [PROP+ 21.08]

Brak wejścia ceny w życie w planowanym czasie i zakresie jest błędem wykonania, nie dowodem nietrafności celu. [PROP+ 21.08]

Dla zmiany asortymentowej najpierw sprawdza się `[D: wykonanie-zmiany-asortymentu]`. [PROP+ 21.08]

Brak wdrożenia statusu w planowanym czasie i zakresie jest błędem wykonania, nie dowodem nietrafności decyzji. [PROP+ 21.08]

Brak produktu w `[D: dostepnosc-towaru]` jest oddzielany od nieskuteczności mechaniki. [AUT-R 21.08]

Niewykonanie `[D: wykonanie-merch]` jest oddzielane od błędu założeń. [AUT-R 21.08]

Niewykonanie `[D: wykonanie-mediow]` jest oddzielane od błędu założeń. [AUT-R 21.08]

### Bramka 4: zakres analizy pogłębionej

Odchylenie od `[D: prognoza]` może uruchomić sprawdzenie założeń. [AUT-R 21.08]

Znane zdarzenie w `[D: kontekst-rynkowy]` jest pokazywane obok oceny. [PROP+ 21.08]

Wpływ zdarzenia rynkowego nie jest przedstawiany jako precyzyjnie wyliczony bez odpowiedniej metody. [PROP+ 21.08]

Dane `[D: dane-regionalne]` analizuje się tylko wtedy, gdy wymaga tego cel, rozliczenie albo diagnoza. [AUT-R 21.08]

Dane `[D: dane-kanalowe]` analizuje się tylko wtedy, gdy wymaga tego cel albo diagnoza. [PROP+ 21.08]

Dane `[D: okres-po-dzialaniu]` analizuje się tylko w uzasadnionym przypadku. [PROP+ 21.08]

Dane `[D: wyniki-innych-produktow]` analizuje się tylko w uzasadnionym przypadku. [PROP+ 21.08]

### Bramka 5: zakończenie analizy

Analiza kończy się po uzyskaniu użytecznego wniosku. [AUT-R 21.08]

Analiza kończy się również wtedy, gdy dalsze badanie nie ma uzasadnionej wartości biznesowej. [AUT-R 21.08]

Brak jednoznacznej przyczyny jest poprawnym wynikiem, jeżeli zapisano wykonane sprawdzenia. [PROP+ 21.08]

Wniosek nie może przypisywać całego odchylenia działaniu, jeżeli zastosowano wyłącznie proste porównanie okresów. [LIT: Brodersen i in., 2015, abstrakt i sekcja 2]

### Bramka 6: przekazanie dalej

Potwierdzony warunek z `[D: warunki-korzysci]` trafia do procesu rozliczenia. [AUT-R 21.08]

Dane z `[D: dane-rozliczeniowe]` trafiają do procesu rozliczenia. [AUT-R 21.08]

Do procesu źródłowego wraca nowy wniosek o mechanice i warunkach jej działania; `[D: historia-mechaniki]` jest przy tym wejściem porównawczym, nie ładunkiem zwrotnym. [PROP+ 21.08]

Wiedza o zmianie asortymentowej wraca do ORPR-CAT-01. [PROP+ 21.08]

Wiedza o trwałej zmianie ceny wraca do ORPR-CAT-02. [PROP+ 21.08]

Wiedza o promocji wraca do ORPR-CAT-03. [PROP+ 21.08]

Przekazany wniosek nie tworzy automatycznego polecenia wykonania. [PROP+ 21.08]

## 10. Skutki

**Stock: NIE bezpośrednio.** Analiza nie zmienia zapasu. [PROP+ 21.08]

Analiza może wykazać, że brak dostępności wpłynął na wynik. [AUT-R 21.08]

**Pieniądze: NIE bezpośrednio.** Proces nie rozlicza płatności. [AUT-R 21.08]

Proces może potwierdzić należną korzyść od producenta. [AUT-R 21.08]

**Księgowość: NIE bezpośrednio.** Ujęcie korzyści należy do ORPR-PRC-04 i FIN. [PROP+ 21.08]

## 11. Warianty i wyjątki kluczowe

### Akcja o małym znaczeniu, „plankton”

Akcja może służyć głównie uzyskaniu dodatkowej korzyści od producenta. [AUT-R 21.08]

Przykładem jest korzyść za uczestnictwo w materiale promocyjnym. [AUT-R 21.08]

Taka akcja zwykle nie wymaga pogłębionej analizy. [AUT-R 21.08]

Minimalny wynik obejmuje wynik łączny działania i produktów. [AUT-R 21.08]

Minimalny wynik obejmuje dane potrzebne do potwierdzenia korzyści. [AUT-R 21.08]

Minimalny zakres planktonu jest jednolity w polach 7, 8, 9 i 11 i obejmuje `[D: wynik-dzialania]`, `[D: wynik-produktu]`, `[D: warunki-korzysci]` oraz `[D: dane-rozliczeniowe]`. [PROP+ 22.08]

### Trwała zmiana ceny regularnej

Ocena sprawdza realizację własnego celu sieci i faktyczne wejście nowej ceny w życie. [PROP+ 21.08]

Nie stosuje automatycznie diagnostyki mechaniki promocyjnej. [PROP+ 21.08]

Korzysta z potwierdzenia wykonania z ORPR-CAT-02 oraz z metody porównania ustalonej dla tej zmiany. [PROP+ 21.08; lokator: `standard/domeny/CAT/ORPR-CAT-02-price-to-pos.md`, pole 8, zdarzenie `cena-weszła-w-życie`]

### Zmiana asortymentowa

Ocena sprawdza realizację własnego celu sieci i faktyczne wdrożenie zmiany zakresu oferty. [PROP+ 21.08]

Nie utożsamia braku sprzedaży z wynikiem decyzji, dopóki nie sprawdzi wdrożenia statusu i dostępności produktu. [PROP+ 21.08]

Potwierdzenie wykonania może korzystać ze zdarzeń zmiany zakresu sprzedawalności i stanu pozycji z ORPR-CAT-01. [PROP+ 21.08; lokator: `standard/domeny/CAT/ORPR-CAT-01-item-to-sellable.md`, pole 8]

### Ważne działanie

Ważne działanie może mieć bardziej szczegółowe założenia produktowe. [AUT-R 21.08]

Ważne działanie może wymagać diagnozy wykonania. [AUT-R 21.08]

Ważne działanie może wymagać sprawdzenia okresu po jego zakończeniu. [PROP+ 21.08]

Ważne działanie może wymagać sprawdzenia wpływu na inne produkty. [PROP+ 21.08]

### Marka własna

Przy marce własnej sieć działa także jako producent. [AUT-R 21.08]

Pogłębiona analiza marki własnej jest częstsza. [AUT-R 21.08]

Decyzja o pogłębieniu nadal zależy od wartości wiedzy. [PROP+ 21.08]

### Działanie producenta

Producent może zaproponować mechanikę. [AUT-R 21.08]

Producent może prowadzić własny cel. [AUT-R 21.08]

Sieć ocenia wyłącznie realizację własnego celu. [AUT-R 21.08]

Próg wymagany do rabatu retro może być własnym celem sieci. [AUT-R 21.08]

### Sieć z category managementem

Duża sieć z category managementem częściej projektuje własną politykę promocyjną. [AUT-R 21.08]

W takim modelu producent jest partnerem albo źródłem finansowania, ale nie musi być właścicielem polityki. [PROP+ 21.08]

### Wynik częściowy

Jeżeli wynik wzrósł, ale nie osiągnął celu, analiza skupia się na jakości prognozy. [AUT-R 21.08]

Analiza może również sprawdzić błędne założenia i niespodziewane warunki rynkowe. [AUT-R 21.08]

Nie ma obowiązku znalezienia jednej przyczyny odchylenia. [AUT-R 21.08]

### Efekty poza okresem działania

Ocena podstawowa korzysta z danych z okresu działania. [AUT-R 21.08] Dla działań bez naturalnego końca „okres działania" zastępuje zadeklarowany horyzont obserwacji liczony od wejścia zmiany w życie. [PROP+ 22.08]

Analiza pogłębiona może sprawdzić przesunięcie zakupów między okresami. [PROP+ 21.08]

Badania wskazują, że trwałe efekty promocji cenowych mogą być nieobecne. [LIT: Pauwels, Hanssens, Siddarth, 2002, abstrakt]

Krótkoterminowy wzrost może podlegać późniejszej korekcie. [LIT: Pauwels, Hanssens, Siddarth, 2002, abstrakt]

## 12. Bezpieczniki prawne i regulacyjne

Regulatory-matrix nie było dostępne w sesji.

Wersję `regulatory-matrix v1.0.1, legal_as_of 2026-08-14` odziedziczono z ORPR-CAT-02 i ORPR-CAT-03.

Wartość wymaga potwierdzenia przez operatora main.

Nie potwierdzono wiązania R właściwego wyłącznie dla procesu oceny efektu. [PROP+ 21.08]

| Kandydat | Status | Rola w karcie |
|---|---|---|
| wykorzystanie danych klientowskich do oceny zachowania albo personalizacji | `[do weryfikacji]` | ustalić, czy analiza wymaga wiązania dotyczącego danych osobowych |
| dowód spełnienia warunku korzyści handlowej | `[do weryfikacji]` | ustalić wymagany ślad dla sporu i rozliczenia w ORPR-PRC-04 |
| wymiana danych o wyniku kategorii z producentem | `[do weryfikacji]` | ustalić ograniczenia dotyczące zakresu przekazywanych danych |

CAT-04 nie tworzy ani nie publikuje ceny. [PROP+ 21.08]

CAT-04 może korzystać z historii ceny i dowodów jej publikacji jako danych wejściowych. [PROP+ 21.08]

CAT-04 nie dziedziczy automatycznie wiązań PRICE-001..005. [PROP+ 21.08]

Lokatory zakresu w kartach sąsiednich: `standard/domeny/CAT/ORPR-CAT-02-price-to-pos.md`, pole 12, tabela PRICE-001..005; `standard/domeny/CAT/ORPR-CAT-03-promotion-to-pos.md`, pole 12, lista PRICE-001..005.

Własne wiązanie CAT-04 wymaga potwierdzenia w RM, że dotyczy tego samego przedmiotu. [PROP+ 21.08]

## 13. Powiązanie w górę i mierniki

Value stream: działanie handlowe -> wykonanie -> sprzedaż -> ocena celu -> wiedza do kolejnego działania. [PROP+ 21.08]

Wnioski wpływają na przyszłe decyzje, ale nie uruchamiają ich automatycznie. [PROP+ 21.08]

Crosswalk: `standard/mapowania/crosswalk-frameworki.md`, sekcja ORPR-CAT-04 (propozycja źródłowa z lokatorami: wewnętrzny materiał roboczy).

### Mierniki procesu

- realizacja celu głównego: wynik faktyczny wobec celu [PROP+ 21.08]
- dodatkowa kwota marży brutto: wynik wobec punktu odniesienia wybranego dla działania [AUT-R 21.08]
- realizacja założeń produktowych: wynik produktu wobec jego założenia [AUT-R 21.08]
- potwierdzona korzyść od producenta: spełnione warunki wobec warunków zapisanych [AUT-R 21.08]
- kompletność wykonania: elementy wykonane wobec zaplanowanych [PROP+ 21.08]
- czas zamknięcia oceny: od granicy startu pomiaru właściwej dla klasy działania (pole 2) do zapisu wyniku [PROP+ 21.08]; dla klas bez naturalnego końca granicą jest upływ zadeklarowanego horyzontu obserwacji liczonego od wejścia zmiany w życie, nie koniec działania [PROP+ 22.08]
- użyteczność analizy pogłębionej: analizy zakończone użytecznym wnioskiem wobec analiz pogłębionych [PROP+ 21.08]

Każdy miernik raportuje licznik i mianownik osobno tam, gdzie wynik jest udziałem. [PROP+ 21.08]

## 14. Bank pytań analityka

### A. Do biznesu

A1. Kto po stronie sieci ma prawo ustalić cel działania: lokalizacja, centrala czy obie strony w różnych zakresach? *(Dlaczego ważne: model operacyjny M0-M3 zmienia obsadę tej decyzji.)*

A2. Kto po stronie sieci ma prawo zatwierdzić ocenę działania? *(Dlaczego ważne: autor analizy nie musi mieć prawa zaakceptowania jej wyniku.)*

A3. Kto po stronie sieci decyduje o wykorzystaniu wniosku? *(Dlaczego ważne: zapis wiedzy nie tworzy automatycznego polecenia wykonania.)*

A4. Jaki jest własny cel sieci dla tego działania? *(Dlaczego ważne: cel producenta nie może zastąpić celu sieci.)*

A5. Który cel jest główny, jeśli działanie ma kilka celów? *(Dlaczego ważne: cel główny wyznacza podstawową ocenę.)*

A6. W jakiej jednostce wyrażono cel? *(Dlaczego ważne: jednostka celu wyznacza wymagane dane.)*

A7. Czy domyślnym celem jest wzrost łącznej kwoty marży brutto? *(Dlaczego ważne: kwota i procent marży mogą prowadzić do różnych ocen.)*

A8. Jaką metodę porównania ustalono przed rozpoczęciem działania? *(Dlaczego ważne: metoda wybrana po wyniku może potwierdzać oczekiwaną tezę.)*

A9. Jaki wynik zakładano dla całego działania? *(Dlaczego ważne: wynik łączny działania jest podstawowym poziomem oceny.)*

A10. Jakie założenia zapisano dla produktów? *(Dlaczego ważne: wyniki produktów mogą wyjaśnić wynik łączny.)*

A11. Czy działanie oznaczono przed startem jako wymagające analizy? *(Dlaczego ważne: zakres potrzebnych danych powinien być znany wcześniej.)*

A12. Czy po zakończeniu wydarzyło się coś, co uzasadnia pogłębienie? *(Dlaczego ważne: znaczenie wyniku może ujawnić się po fakcie.)*

A13. Czy działanie dotyczy marki własnej? *(Dlaczego ważne: sieć działa wtedy również jako producent.)*

A14. Kto zainicjował działanie: sieć, producent czy obie strony? *(Dlaczego ważne: inicjator wpływa na założenia, ale nie zastępuje celu sieci.)*

A15. Jaki cel producenta jest widoczny w warunkach działania? *(Dlaczego ważne: pomaga zrozumieć mechanikę i oczekiwania partnera.)*

A16. Czy cel sieci obejmuje próg potrzebny do uzyskania rabatu retro albo innej korzyści? *(Dlaczego ważne: próg jest częścią oceny i wejściem do rozliczenia.)*

A17. Jakie produkty, ceny i mechaniki tworzyły jedno działanie? *(Dlaczego ważne: wynik musi mieć ten sam zakres co plan.)*

A18. Jakie dodatkowe elementy zaplanowano? *(Dlaczego ważne: brak wykonania wsparcia nie jest dowodem słabości mechaniki.)*

A19. Czy wynik całego działania osiągnął cel? *(Dlaczego ważne: to podstawowe rozstrzygnięcie oceny.)*

A20. Które produkty osiągnęły swoje założenia? *(Dlaczego ważne: wynik łączny może ukryć przeciwne wyniki produktów.)*

A21. Czy do rozliczenia potrzebny jest wynik regionalny albo kanałowy? *(Dlaczego ważne: szczegół powinien wynikać z potrzeby.)*

A22. Czy wartość finansowa uzasadnia pogłębioną analizę? *(Dlaczego ważne: koszt analizy powinien odpowiadać stawce.)*

A23. Czy działanie ma znaczenie strategiczne? *(Dlaczego ważne: wartość wiedzy może przewyższać bieżący wynik.)*

A24. Czy podobny problem powtarza się w innych działaniach? *(Dlaczego ważne: powtarzalność zwiększa wartość znalezienia przyczyny.)*

A25. Czy istnieje ryzyko sporu z producentem? *(Dlaczego ważne: spór wymaga mocniejszego śladu danych.)*

A26. Czy mechanika zadziałała w systemie zgodnie z planem? *(Dlaczego ważne: błąd konfiguracji nie jest porażką pomysłu handlowego.)*

A27. Czy produkty były dostępne w okresie działania? *(Dlaczego ważne: brak towaru ogranicza możliwość oceny popytu.)*

A28. Czy ekspozycja i merchandising zostały wykonane? *(Dlaczego ważne: element niewykonany nie powinien być oceniany jak wykonany.)*

A29. Czy gazetka, media i pozostała komunikacja wystartowały zgodnie z planem? *(Dlaczego ważne: mechanika bez komunikacji może nie dotrzeć do klientów.)*

A30. Czy konkurencja uruchomiła silne działanie w tej samej kategorii? *(Dlaczego ważne: zmiana rynku może wpłynąć na wynik bez błędu własnego działania.)*

A31. Które założenie prognozy okazało się nietrafne? *(Dlaczego ważne: poprawa założeń może być najważniejszym wynikiem analizy.)*

A32. Czy dane pozwalają odróżnić błąd wykonania od błędu założeń? *(Dlaczego ważne: brak możliwości rozstrzygnięcia powinien być jawny.)*

A33. Jaki wniosek o mechanice warto zachować? *(Dlaczego ważne: ponownie używana jest wiedza, nie cała akcja.)*

A34. W jakich warunkach ten wniosek może nie obowiązywać? *(Dlaczego ważne: mechanika bez kontekstu łatwo staje się fałszywą regułą.)*

A35. Czy dalsza analiza może zmienić przyszłą decyzję? *(Dlaczego ważne: jeśli nie, warto zakończyć pracę.)*

A36. Do której klasy należy działanie: promocja, trwała zmiana ceny, zmiana asortymentowa czy inna jawnie zdefiniowana klasa? *(Dlaczego ważne: klasa działania wyznacza właściwe kontrole wykonania i metodę pomiaru.)*

A37. Czy trwała zmiana ceny weszła w życie zgodnie z planem osobno w każdym z poniższych wymiarów? *(Dlaczego ważne: niewdrożonej ceny nie można oceniać jako nietrafnej decyzji.)*

| Wymiar | Zgodne z planem? |
|---|---|
| czas wejścia w życie | |
| zakres wejścia w życie | |

A38. Czy zmiana asortymentowa weszła w życie zgodnie z planem osobno w każdym z poniższych wymiarów? *(Dlaczego ważne: niewdrożonej zmiany nie można oceniać po wyniku sprzedaży.)*

| Wymiar | Zgodne z planem? |
|---|---|
| czas wejścia w życie | |
| zakres wejścia w życie | |

A39. Czy dla ważnej promocji, czyli działania z własnym oknem czasowym, badamy okres po zakończeniu tego okna, żeby wykryć przesunięcie zakupów w czasie? *(Dlaczego ważne: krótkoterminowy wzrost w oknie akcji może być przesunięciem sprzedaży z okresu po akcji, a nie trwałym przyrostem.)*

A40. Czy dla ważnego działania badamy wpływ na inne produkty: substytucję, kanibalizację albo efekt uzupełniający? *(Dlaczego ważne: wzrost promowanego produktu może być odebrany innym produktom sieci, więc wynik łączny bywa mniejszy niż wynik samego produktu.)*

A41. Czy raport oddziela wynik zaobserwowany od efektu przypisanego działaniu? *(Dlaczego ważne: nazwanie całej zaobserwowanej różnicy „efektem" zawyża wynik bez podstawy atrybucji.)*

A42. Dla działania bez naturalnego końca (trwała zmiana ceny albo zmiana asortymentowa) odpowiedz osobno na każdy wymiar zadeklarowanego horyzontu obserwacji. *(Dlaczego ważne: horyzont zadeklarowany dopiero po wejściu zmiany w życie można dobrać pod wygodny wynik, a bez horyzontu ocena trwałej zmiany nie ma zamkniętego okna.)*

| Wymiar horyzontu | Odpowiedź |
|---|---|
| jaki horyzont obserwacji zadeklarowano | |
| czy zadeklarowano go przed uruchomieniem zmiany | |
| kto zatwierdził horyzont | |
| co robimy, gdy horyzontu brak | |

### B. Do legacy i danych

B1. Czy system przechowuje definicję działania w wersji faktycznie uruchomionej? *(Dlaczego ważne: plan i konfiguracja produkcyjna mogą się różnić.)*

B2. Czy da się odtworzyć mechanikę obowiązującą w każdym dniu działania? *(Dlaczego ważne: nadpisana konfiguracja uniemożliwia sprawdzenie wykonania.)*

B3. Czy dane rozróżniają sprzedaż objętą mechaniką od pozostałej sprzedaży produktu? *(Dlaczego ważne: wynik łączny produktu nie zawsze pokazuje użycie mechaniki.)*

B4. Czy wynik jest liczony na tych samych produktach i okresach co założenie? *(Dlaczego ważne: różny zakres tworzy pozorne odchylenie.)*

B5. Czy system przechowuje kwotę marży brutto na wymaganym poziomie? *(Dlaczego ważne: sam obrót nie odpowiada na domyślny cel marżowy.)*

B6. Czy koszt użyty do prognozy i wyniku jest liczony tak samo? *(Dlaczego ważne: różna podstawa kosztowa zmienia ocenę.)*

B7. Czy można potwierdzić faktyczne naliczenie mechaniki na transakcjach? *(Dlaczego ważne: status „aktywna” nie dowodzi poprawnego działania.)*

B8. Czy dane pokazują dostępność produktów? *(Dlaczego ważne: sprzedaż zerowa przy braku towaru nie mierzy popytu.)*

B9. Czy widzimy okresy braku towaru? *(Dlaczego ważne: częściowa dostępność ogranicza wiarygodność wyniku.)*

B10. Czy wykonanie ekspozycji jest rejestrowane? *(Dlaczego ważne: sama deklaracja ogranicza możliwość diagnozy.)*

B11. Czy system zna rzeczywistą datę publikacji komunikacji? *(Dlaczego ważne: data planowana może różnić się od wykonania.)*

B12. Czy wynik działania i produktów pochodzi ze spójnego źródła? *(Dlaczego ważne: różne źródła mogą inaczej traktować sprzedaż i zwroty.)*

B13. Czy zwroty i anulowania pomniejszają wynik? *(Dlaczego ważne: wynik przed zwrotami może być zawyżony.)*

B14. Czy wynik regionalny jest dostępny w formacie wymaganym do rozliczenia? *(Dlaczego ważne: brak poziomu rozliczeniowego blokuje przekazanie do PRC-04.)*

B15. Gdzie zapisano warunki rabatu retro? *(Dlaczego ważne: nie można potwierdzić warunku, którego nie da się odtworzyć.)*

B16. Czy istnieje wersja prognozy zatwierdzona przed startem? *(Dlaczego ważne: prognoza poprawiona po wyniku nie jest punktem odniesienia.)*

B17. Czy dane o rynku i konkurencji mają potwierdzony osobno każdy z poniższych atrybutów? *(Dlaczego ważne: pamięć uczestników nie wystarcza do mocnego wniosku.)*

| Atrybut | Potwierdzony? |
|---|---|
| źródło | |
| data | |

B18. Czy system przechowuje wcześniejsze wnioski o tej samej mechanice? *(Dlaczego ważne: bez zapisu proces nauki zaczyna się od zera.)*

B19. Czy wniosek jest powiązany osobno z każdym z poniższych wymiarów? *(Dlaczego ważne: etykieta „zadziałało” bez mechaniki i bez kontekstu nie mówi, co powtórzyć ani kiedy.)*

| Wymiar | Powiązany? |
|---|---|
| mechanika działania | |
| kontekst i warunki działania | |

B20. Czy można zapisać „przyczyna nierozstrzygnięta”? *(Dlaczego ważne: system nie powinien wymuszać fałszywej pewności.)*

B21. Czy system zapisuje, kto po stronie sieci ustalił cel? *(Dlaczego ważne: ślad celu musi odpowiadać modelowi operacyjnemu.)*

B22. Czy system zapisuje, kto zatwierdził ocenę? *(Dlaczego ważne: trzeba odtworzyć odpowiedzialność za przyjęcie wyniku.)*

B23. Czy dane rozróżniają promocję, trwałą zmianę ceny i zmianę asortymentową? *(Dlaczego ważne: różne klasy wymagają innych kontroli wykonania.)*

B24. Czy da się odtworzyć osobno każdy z poniższych wymiarów wejścia ceny regularnej w życie? *(Dlaczego ważne: planowana zmiana ceny może nie zostać wykonana wszędzie.)*

| Wymiar | Odtwarzalny? |
|---|---|
| moment wejścia w życie | |
| zakres wejścia w życie | |

B25. Czy da się odtworzyć osobno każdy z poniższych wymiarów wejścia zmiany asortymentowej w życie? *(Dlaczego ważne: plan i faktyczny status oferty mogą się różnić.)*

| Wymiar | Odtwarzalny? |
|---|---|
| moment wejścia w życie | |
| zakres wejścia w życie | |

### C. Do vendora lub zespołu budującego rozwiązanie

C1. Czy rozwiązanie rozdziela cel sieci, cel producenta i warunki handlowe? *(Dlaczego ważne: te elementy nie są tym samym.)*

C2. Czy jedno działanie może obejmować wiele produktów, cen i mechanik? *(Dlaczego ważne: model danych nie może sztucznie rozbijać akcji.)*

C3. Czy produkt może mieć własne założenie w ramach celu całego działania? *(Dlaczego ważne: ocena działa na dwóch poziomach.)*

C4. Czy metoda porównania jest zapisywana przed startem? *(Dlaczego ważne: chroni przed doborem wygodnego porównania po wyniku.)*

C5. Czy system oznacza wymagany poziom analizy? *(Dlaczego ważne: nie każde działanie wymaga tego samego kosztu pracy.)*

C6. Czy działanie można skierować do analizy po zakończeniu? *(Dlaczego ważne: znaczenie wyniku może ujawnić się po fakcie.)*

C7. Czy raport pokazuje osobno wynik działania i produktów? *(Dlaczego ważne: oba poziomy są potrzebne.)*

C8. Czy raport może ograniczyć się do wyniku łącznego dla działania o małym znaczeniu? *(Dlaczego ważne: narzędzie nie powinno wymuszać kosztownej analizy.)*

C9. Czy szczegół jest uruchamiany na żądanie osobno dla każdego wymiaru? *(Dlaczego ważne: szczegół ma wynikać z potrzeby, a obsługa jednego wymiaru nie dowodzi drugiego.)*

| Wymiar | Na żądanie? |
|---|---|
| regionalny | |
| kanałowy | |

C10. Czy marża brutto ma jawną, wersjonowaną definicję? *(Dlaczego ważne: zmiana definicji tworzy fałszywe odchylenie.)*

C11. Czy da się sprawdzić naliczenie mechaniki na próbce transakcji? *(Dlaczego ważne: agregat może nie pokazać błędu konfiguracji.)*

C12. Czy rozwiązanie łączy sprzedaż z dostępnością? *(Dlaczego ważne: diagnoza musi oddzielić brak popytu od braku towaru.)*

C13. Czy można rejestrować wykonanie osobno dla każdego elementu? *(Dlaczego ważne: ekspozycja i komunikacja to osobne elementy planu działania.)*

| Element | Rejestrowane? |
|---|---|
| ekspozycja | |
| komunikacja | |

C14. Czy raport pokazuje ograniczenia danych? *(Dlaczego ważne: użytkownik musi odróżnić brak efektu od braku możliwości pomiaru.)*

C15. Czy analizę można zakończyć bez wskazania jednej przyczyny? *(Dlaczego ważne: wiele zmiennych może uniemożliwić rozstrzygnięcie.)*

C16. Czy wnioski są wyszukiwalne osobno po każdym z poniższych kluczy? *(Dlaczego ważne: obsługa jednego klucza nie dowodzi pozostałych.)*

| Klucz | Wyszukiwalny? |
|---|---|
| mechanika | |
| kategoria | |
| produkt | |
| typ marki | |

C17. Czy wniosek przechowuje warunki działania mechaniki? *(Dlaczego ważne: sama ocena bez kontekstu jest trudna do wykorzystania.)*

C18. Czy potwierdzony warunek korzyści można przekazać do ORPR-PRC-04? *(Dlaczego ważne: ocena musi zasilać rozliczenie.)*

C19. Czy rozwiązanie rozróżnia markę własną od marki producenta? *(Dlaczego ważne: marka własna częściej uzasadnia szerszą analizę.)*

C20. Czy uprawnienia oddzielają dane sieci od danych udostępnianych producentowi? *(Dlaczego ważne: strony mają odrębne cele.)*

C21. Czy rozwiązanie odwzorowuje, kto w modelu M0-M3 ustala cel? *(Dlaczego ważne: prawo ustalenia celu może należeć do centrali albo lokalizacji.)*

C22. Czy rozwiązanie odwzorowuje, kto w modelu M0-M3 zatwierdza ocenę? *(Dlaczego ważne: jedno centralne uprawnienie nie pasuje do wszystkich modeli operacyjnych.)*

C23. Czy rozwiązanie wybiera kontrole wykonania odpowiednie dla klasy działania? *(Dlaczego ważne: promocja, trwała zmiana ceny i zmiana asortymentowa nie są wykonywane w ten sam sposób.)*

C24. Czy ocena trwałej zmiany ceny może pobrać z ORPR-CAT-02 osobno dowód każdego z poniższych wymiarów jej wejścia w życie? *(Dlaczego ważne: analiza musi odróżnić skutek ceny od błędu wdrożenia.)*

| Wymiar dowodu | Dostępny z ORPR-CAT-02? |
|---|---|
| czas wejścia w życie | |
| zakres wejścia w życie | |

C25. Czy ocena zmiany asortymentowej może pobrać z ORPR-CAT-01 osobno dowód każdego z poniższych wymiarów zmiany statusu pozycji? *(Dlaczego ważne: analiza musi odróżnić skutek decyzji od błędu wdrożenia.)*

| Wymiar dowodu | Dostępny z ORPR-CAT-01? |
|---|---|
| czas zmiany statusu | |
| zakres zmiany statusu | |

### Czerwone flagi

F1. **Cel producenta zastąpił cel sieci.** Wykrywa porównanie `[D: cel-glowny]` z warunkami działania. Pytania: A4, A14, A15, C1. [AUT-R 21.08]

F2. **Marża procentowa zastąpiła kwotę marży brutto.** Raport pokazuje poprawę procentu przy spadku `[D: marza-brutto]`. Pytania: A6, A7, B5, C10. [AUT-R 21.08]

F3. **Punkt odniesienia wybrano po wyniku.** Brak zatwierdzonej `[D: metoda-porownania]`. Pytania: A8, B16, C4. [PROP+ 21.08]

F4. **Cały wzrost nazwano efektem działania.** Wynik z `[D: wynik-dzialania]` nie rozróżnia trendu i innych zmian. Pytania: A8, A30, A41, B17, C14. [LIT: Brodersen i in., 2015, abstrakt]

F5. **Wynik łączny działania ukrywa przeciwne wyniki produktów.** `[D: wynik-dzialania]` osiąga cel mimo odchyleń `[D: wynik-produktu]`. Pytania: A10, A20, C7. [PROP+ 21.08]

F6. **Mechanika nie została poprawnie uruchomiona.** `[D: konfiguracja-mechaniki]` albo `[D: test-mechaniki]` nie zgadza się z planem. Pytania: A26, B1, B2, B7, C11. [AUT-R 21.08]

F7. **Brak towaru odczytano jako brak popytu.** `[D: dostepnosc-towaru]` nie pokrywa działania. Pytania: A27, B8, B9, C12. [AUT-R 21.08]

F8. **Niewykonana ekspozycja obciąża mechanikę.** `[D: wykonanie-merch]` nie potwierdza planu. Pytania: A18, A28, B10, C13. [AUT-R 21.08]

F9. **Niewykonana komunikacja obciąża mechanikę.** `[D: wykonanie-mediow]` nie potwierdza planu. Pytania: A18, A29, B11, C13. [AUT-R 21.08]

F10. **Działanie konkurencji pominięto w ocenie.** Zdarzenie z `[D: kontekst-rynkowy]` nie jest pokazane obok wyniku. Pytania: A30, B17. [AUT-R 21.08]

F11. **Prognozę poprawiono po fakcie.** `[D: prognoza]` nie ma zatwierdzonej wersji. Pytania: A31, B16. [PROP+ 21.08]

F12. **Analiza nie ma końca.** Dalsze badanie nie może już zmienić przyszłej decyzji. Pytania: A32, A35, B20, C15. [AUT-R 21.08]

F13. **Raport wymusza jedną przyczynę.** Dane wspierają kilka możliwych wyjaśnień. Pytania: A32, B20, C14, C15. [AUT-R 21.08]

F14. **„Plankton” dostał pełny projekt analityczny.** Koszt analizy przekracza wartość działania opartego na `[D: warunki-korzysci]`. Pytania: A11, A22, C8. [AUT-R 21.08]

F15. **Ważne działanie oceniono tylko wynikiem łącznym.** Brak pogłębienia mimo wysokiej stawki. Pytania: A22, A23, A24, A25. [AUT-R 21.08]

F16. **Markę własną oceniono jak zwykłą akcję producenta.** `[D: typ-marki]` nie został uwzględniony przy wyborze poziomu analizy. Pytania: A13, C19. [AUT-R 21.08]

F17. **Brakuje danych do rozliczenia.** `[D: dane-rozliczeniowe]` nie mają poziomu wymaganego przez warunek handlowy. Pytania: A16, A21, B14, B15, C18. [AUT-R 21.08]

F18. **Wniosek mówi „powtórzyć akcję”.** `[D: historia-mechaniki]` przechowuje kopię działania zamiast wiedzy o mechanice. Pytania: A33, A34, B18, B19, C16, C17. [AUT-R 21.08]

F19. **Przesunięcie zakupów uznano za trwały przyrost.** Analiza ważnej promocji pomija `[D: okres-po-dzialaniu]`. Pytania: A34, A39, C14. [LIT: van Heerde, Leeflang, Wittink, 2004, abstrakt]

F20. **Wpływ na inne produkty pominięto bez decyzji.** Analiza ważnego działania nie rozważa `[D: wyniki-innych-produktow]`. Pytania: A20, A34, A40, C14. [LIT: Leeflang, Parreño Selva, van Dijk, Wittink, 2008, abstrakt]

F21. **Cele stron zostały zlane.** System nie rozróżnia celu sieci, celu producenta i `[D: warunki-korzysci]`. Pytania: A4, A14, A15, A16, C1. [AUT-R 21.08]

F22. **Ocena została zatwierdzona przez niewłaściwą stronę sieci.** Uprawnienie nie odpowiada `[D: model-operacyjny]`. Pytania: A1, A2, A3, B21, B22, C21, C22. [PROP+ 21.08]

F23. **Trwałą zmianę ceny oceniono bez potwierdzenia jej wykonania.** Brakuje `[D: wykonanie-zmiany-ceny]` dla planowanego czasu albo zakresu. Pytania: A36, A37, B23, B24, C23, C24. [PROP+ 21.08]

F24. **Zmianę asortymentową oceniono bez potwierdzenia jej wykonania.** Brakuje `[D: wykonanie-zmiany-asortymentu]` dla planowanego czasu albo zakresu. Pytania: A36, A38, B23, B25, C23, C25. [PROP+ 21.08]

## Źródła publiczne użyte w wersji 0.5

1. [APQC, PCF Cross-Industry v8.0, sekcja Measure Scope: 3.3.4.6-3.3.4.8, elementy 10170-10172](https://www.apqc.org/what-we-do/benchmarking/open-standards-benchmarking/measures/customer-sales-promotions-percentage), dostęp 2026-08-22.
2. [Brodersen i in., Inferring causal impact using Bayesian structural time-series models](https://research.google/pubs/inferring-causal-impact-using-bayesian-structural-time-series-models/), `Annals of Applied Statistics`, 2015, 9(1), s. 247-274.
3. [van Heerde, Leeflang, Wittink, Decomposing the Sales Promotion Bump with Store Data](https://pubsonline.informs.org/doi/abs/10.1287/mksc.1040.0061), `Marketing Science`, 2004, 23(3), s. 317-334.
4. [Pauwels, Hanssens, Siddarth, The Long-Term Effects of Price Promotions on Category Incidence, Brand Choice, and Purchase Quantity](https://journals.sagepub.com/doi/abs/10.1509/jmkr.39.4.421.19114), `Journal of Marketing Research`, 2002, 39(4), s. 421-439.
5. [Leeflang, Parreño Selva, van Dijk, Wittink, Decomposing the sales promotion bump accounting for cross-category effects](https://www.sciencedirect.com/science/article/pii/S0167811608000347), `International Journal of Research in Marketing`, 2008, 25(3), s. 201-214.
