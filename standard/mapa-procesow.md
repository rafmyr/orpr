# Mapa procesów ORPR (nawigacja)

Status: zatwierdzona przez właściciela 2026-08-31 (przepisanie ze spisu F2b, pozycja długu H16;
decyzje i przydziały NN: wewnętrzny rejestr decyzji, wpis 2026-08-31 o wydaniu v0.1).
Poprzednia wersja zatwierdzona 24.08 przy 39 procesach.

To jest warstwa NAWIGACYJNA (spis obszarów i procesów), nie diagram przepływu. Krawędzie handoffu
(proces → proces), bramki i wywołania procesów przekrojowych powstają w kartach szkieletowych
(pole 2/8/9) oraz w `standard/mapowania/rejestr-stykow-L0.md`.

Zastępuje planowany `L0-katalog.md` (README sekcja struktury). freeze notacji: obowiązuje od v0.1.0.

Źródło zawartości: warstwa A wewnętrznego spisu (74 procesy,
status wierszy PROPOSAL), przypisanie procesu do obszaru wg kolumny `home_id`, nazwa procesu wg
kolumny `nazwa`. Nazwy obszarów: kanoniczne z wewnętrznego krajobrazu obszarów
tabela B (#1 do #22). Rodzaj obszarów #1 do #10 zatwierdzony 24.08; rodzaj obszarów #11 do #22
ratyfikowany 31.08 (wszystkie przekrojowe z dwoma wyjątkami: #13 i #14 to Przepływy biznesowe).
Stara struktura 10 domen (CAT, SAL...) = checklista pokrycia i stałe ID techniczne, NIE struktura
nawigacyjna (P13, MAPA-NOTACJI DEPRECATED jako struktura).

Referencja wizualna notacji: `standard/mapa-procesow-prototyp.html` (układ, dwie kategorie, semantyka
linii; ilustracyjny, nie jest dowodem prawdziwości narysowanych sekwencji; pokazuje układ 39 procesów
zatwierdzony 24.08, sprzed przepisania).

## A. Zasady notacji

Gramatyka ścieżki procesu:

```
<rodzaj> / <obszar> / <NN> · <Od X do Y> · <stałe ID techniczne>
rodzaj ∈ { Przepływ, Proces przekrojowy }
```

Reguły:

1. Obszar identyfikujemy NAZWĄ, nie numerem. Adres numeryczny obszaru (wariant `1.01`, `3.04`)
   został odrzucony: wymaga klucza, żeby wiedzieć czym jest obszar 3, i łamie samowyjaśnialność
   (rejestr decyzji projektowych 2026-08-24). Kanoniczny adres czytelny dla człowieka: `Zakupy i płatności dla
   dostawców / 01`, `Planowanie i dostępność / 03`, `Zapas / 01`, `Księgowość / 01`.
2. `NN` to dwucyfrowy numer porządkowy w obszarze, NIE krok sekwencji. Nadawany zgodnie
   z naturalną kolejnością tam, gdzie istnieje. Kolejność wykonania pokazują strzałki i handoffy,
   nie numer.
3. Nazwa procesu ma formę zdania `Od X do Y` (np. `Od zapotrzebowania do zamówienia`). Strzałka `→`
   jest zarezerwowana dla JEDNEGO znaczenia: przekazanie między procesami na diagramie. Dlatego
   strzałka NIE występuje wewnątrz nazwy procesu (decyzja 2026-08-24 zastępująca wcześniejszą
   formę `X → Y`; freeze notacji obowiązuje od v0.1.0).
4. Proces ma jedno miejsce główne na mapie; inne obszary linkują, nie duplikują.
5. Stałe ID techniczne (`ORPR-CAT-04`, na mapie skrót `CAT-04`) jest stabilne — przeniesienie
   procesu między obszarami go NIE zmienia. To NIE jest alias historyczny: to trwały identyfikator
   używany w plikach, odwołaniach i automatyzacji. Adres nawigacyjny (`Oferta handlowa / 04`) może
   się zmienić po przebudowie mapy; stałe ID techniczne — nie.
6. Kody bytów (`LEX`, `SFT`, `FIN`...) NIE wchodzą do ścieżki nawigacyjnej; żyją w modelu
   technicznym (rejestr styków), na mapie najwyżej jako opcjonalny tag.
7. Kandydat bez zatwierdzonej granicy nie dostaje numeru ani stałego ID: `Kandydat · <nazwa>`.
8. Dwie kategorie procesów: „Przepływy biznesowe" i „Procesy przekrojowe"; w ścieżce rodzaj to
   „Przepływ" albo „Proces przekrojowy". Nazewnictwo „Pas I / Pas II" wycofane (decyzja 2026-08-24).
9. Po freeze stałe ID techniczne są NIEZMIENNE (zmiana = decyzja rangi wydania, z deprecation).
   Freeze notacji PENDING.

Trójpodział znaczeń (sedno czytelności):

| Pytanie | Odpowiada |
|---|---|
| Który to stabilny obiekt standardu? | stałe ID techniczne `ORPR-CAT-04` |
| Gdzie go znajdę na aktualnej mapie? | ścieżka `Oferta handlowa / 04` |
| Co ten proces robi? | `Od akcji handlowej do efektu` |

## B. Mapa procesów

Adres czytelny dla człowieka = nazwa obszaru (nagłówek) + `NN` przy procesie. Skrót w nawiasie
po nazwie to stałe ID techniczne (na mapie bez prefiksu `ORPR-`). Znacznik `(#n)` przy nagłówku
obszaru to odsyłacz techniczny do krajobrazu v0.11 tabela B i kolumny `home_id` spisu F2b;
nie jest częścią adresu nawigacyjnego (reguła 1 bez zmian).

### Przepływy biznesowe

**Zakupy i płatności dla dostawców** (#1)
- 01 Od zapotrzebowania do zamówienia · `PRC-01`
- 02 Od dokumentu dostawy do przyjęcia · `PRC-02`
- 03 Od faktury do zobowiązania · `PRC-03`
- 04 Od zobowiązania do zapłaty · `FIN-04`
- 05 Od warunków handlowych do rozliczenia korzyści pozafakturowych · `PRC-04`

**Planowanie i dostępność** (#2)
- 01 Od popytu do zapotrzebowania netto · `DEM-01`
- 02 Od zapotrzebowania do zakupu (ścieżka ręczna) · `DEM-02`
- 03 Od sygnału popytu do prognozy · `DEM-03`
- 04 Od ograniczeń do alokacji · `DEM-04`
- 05 Od stanu zapasu do obiecywalnej dostępności · `DEM-05`

**Oferta handlowa** (#3)
- 01 Od pozycji do dopuszczenia do sprzedaży · `CAT-01`
- 02 Od ceny do kasy · `CAT-02` *(wydana, v1.0)*
- 03 Od promocji do kasy · `CAT-03`
- 04 Od akcji handlowej do efektu · `CAT-04`

**Realizacja sprzedaży** (#4)
- 01 Od koszyka do sprzedaży · `SAL-01` *(wydana, v1.0)*
- 02 Od sprzedaży do dokumentu fiskalnego · `SAL-02`
- 03 Od sprzedaży do wydania towaru · `SAL-03`

**Płatności klientów** (#5)
- 01 Od kwoty do formy płatności · `PAY-01`
- 02 Od autoryzacji do przechwycenia · `PAY-02`
- 03 Od przechwyconych płatności do rozliczenia partii z operatorem · `PAY-03`

**Zwroty** (#6)
- 01 Od sprzedaży do anulowania · `RTN-01`
- 02 Od sprzedaży do zwrotu · `RTN-02`
- 03 Od zwrotu do zwrotu środków · `RTN-03`
- 04 Od zwrotu do rozdysponowania · `RTN-04`

**Sprzedaż internetowa i na odległość** (#13)
- 01 Od złożonego zamówienia zdalnego do przyjętego zamówienia klienta · `ORD-01`
- 02 Od przesyłki gotowej do ostatniej mili do potwierdzonego wyniku dostawy · `DLV-01`

**Obsługa klienta i reklamacje** (#14)
- 01 Od zgłoszonej sprawy klienta do przekazanego rozstrzygnięcia · `SVC-01`

### Procesy przekrojowe

**Zapas** (#7)
- 01 Od przyjęcia do dostępności · `INV-01`
- 02 Od transferu do przyjęcia · `INV-02`
- 03 Od inwentaryzacji do korekty · `INV-03`
- 04 Od straty do odpisu · `INV-04`
- 05 Od przyjętego zamówienia do rezerwacji zapasu · `INV-07`
- 06 Od rozbieżności przesunięcia do uzgodnienia · `INV-08`
- 07 Od zdarzeń zapasowych do wiarygodnego stanu · `INV-09`

**Księgowość** (#8)
- 01 Od sprzedaży do księgi · `FIN-01`
- 02 Od zapasu do kosztu własnego · `FIN-02`
- 03 Od podatku do zobowiązania · `FIN-03`

**Rozliczanie kas i utargu** (#9)
- 01 Od otwarcia do zamknięcia kasy · `CSH-01`
- 02 Od gotówki do wpłaty · `CSH-02`
- 03 Od przechwyconych płatności kartą do uzgodnienia wpływów dnia · `CSH-03`
- 04 Od rozliczenia do banku · `CSH-04`

**Kontrola i zgodność** (#10)
- 01 Od transakcji do uzgodnienia · `CTL-01`
- 02 Od wyjątku do rozwiązania · `CTL-02`
- 03 Od zdarzenia do audytu · `CTL-03`
- 04 Od planu kontroli do zarejestrowanej niezgodności · `CTL-04`

**Zarządzanie asortymentem i dostawcami** (#11)
- 01 Od potrzeby pozyskania do warunków handlowych · `SUP-01`
- 02 Od potrzeby zmiany asortymentu do decyzji i danych produktu · `AST-01`
- 03 Od kierunku do strategii kategorii · `AST-02`
- 04 Od zobowiązań dostawcy do pełnego rozliczenia · `SUP-02`
- 05 Od potrzeby ekspozycji do planu przestrzeni i ekspozycji · `AST-03`

**Logistyka sieci** (#12)
- 01 Od zlecenia transportu do potwierdzonego odbioru · `LOG-01`
- 02 Od wymagań magazynu do gotowości operacyjnej magazynu · `LOG-02`

**Marketing i relacje z klientami** (#15)
- 01 Od kontaktu z klientem do mierzalnej relacji · `CRM-01`
- 02 Od celu komunikacyjnego do zmierzonego efektu kampanii · `MKT-01`
- 03 Od potrzeby marki do zatwierdzonego standardu · `BRD-01`
- Kandydat · Program lojalnościowy: naliczanie i umarzanie punktów *(bez numeru i bez stałego ID
  do zatwierdzenia początku, wyniku i granicy)* **[AUT-R 2026-08-31]**: kandydat przeniesiony
  z obszaru Płatności klientów do #15 na podstawie krajobrazu v0.11 tabela B #15 („program
  lojalnościowy = proces warunkowy tego obszaru, styki #5/#8").

**Operacje i utrzymanie lokalizacji** (#16)
- 01 Od uzupełnienia do półki · `INV-05`
- 02 Od braku towaru do rozwiązania · `INV-06`

**Rozwój sieci i lokalizacji** (#17)
- 01 Od potrzeby lokalizacyjnej do decyzji o portfelu lokalizacji · `LOC-01`
- 02 Od decyzji lokalizacyjnej do domkniętej zmiany lokalizacji · `LOC-02`

**Planowanie i zarządzanie finansami** (#18)
- 01 Od założeń do zatwierdzonego planu finansowego · `FIN-05`
- 02 Od prognozy przepływów do decyzji o płynności · `FIN-06`
- 03 Od wyników okresu do wniosków zarządczych · `FIN-07`

**Pracownicy i kadry** (#19)
- 01 Od potrzeby obsady do zapewnionej obsady · `HRM-01`
- 02 Od luki kompetencyjnej do potwierdzonych kompetencji · `HRM-02`
- 03 Od zdarzenia zatrudnieniowego do aktualnego stanu zatrudnienia · `HRM-03`

**Technologia i systemy** (#20)
- 01 Od potrzeby systemowej do udostępnionego systemu · `SYS-01`
- 02 Od udostępnionego systemu do potwierdzonej dostępności i bezpieczeństwa · `SYS-02`
- 03 Od ryzyka przerwy do przetestowanej gotowości odtworzeniowej · `SYS-03`

**Prawo i umowy** (#21)
- 01 Od uzgodnionych warunków do prawnie skutecznej umowy · `LEG-01`
- 02 Od sprawy prawnej do formalnego zamknięcia · `LEG-02`

**Zarządzanie i nadzór nad firmą** (#22)
- 01 Od potrzeby ustalenia kierunku do zatwierdzonych celów i decyzji · `GOV-01`
- 02 Od informacji o wynikach i ryzykach do zamkniętego przeglądu zarządczego · `GOV-02`
- 03 Od potrzeby relacji z interesariuszami do zrealizowanych obowiązków relacyjnych · `GOV-03`
- 04 Od strategii i szans rozwojowych do zweryfikowanego portfela rozwoju · `GOV-04`

## C. Kontrola liczb

Liczby przeliczone z sekcji B tego pliku (nie przepisane ze spisu), a następnie porównane
z kolumną `spisane` rejestru jednostek spisu F2b: pełna zgodność per obszar, 22 na 22.

- Przepływy biznesowe (8 obszarów): 5 + 5 + 4 + 3 + 3 + 4 + 2 + 1 = **27 procesów**
  (#1: 5, #2: 5, #3: 4, #4: 3, #5: 3, #6: 4, #13: 2, #14: 1).
- Procesy przekrojowe (14 obszarów): 7 + 3 + 4 + 4 + 5 + 2 + 3 + 2 + 2 + 3 + 3 + 3 + 2 + 4 =
  **47 procesów** (#7: 7, #8: 3, #9: 4, #10: 4, #11: 5, #12: 2, #15: 3, #16: 2, #17: 2, #18: 3,
  #19: 3, #20: 3, #21: 2, #22: 4).
- Razem: **74 istniejące + 1 kandydat** (program lojalnościowy, obszar #15).
- Zgodność ze spisem F2b: 74 wiersze warstwy A = 74 procesy na mapie, zero wierszy pominiętych,
  zero dodanych (kontrola diff posortowanych list `process_id`, 2026-08-31).
- Kandydat lojalnościowy = nowa treść (brak w kamieniołomie); wymaga początku, wyniku i granicy
  wobec Oferty handlowej / Realizacji sprzedaży / Płatności klientów zanim dostanie numer.

## D. Znaczenie linii i układ mapy (semantyka wizualna)

Reguły wizualne mapy i diagramów obszarówych (spójne z decyzją o reprezentacji diagramu,
rejestr decyzji projektowych 2026-08-24):

1. Linia ciągła — przekazanie POTWIERDZONE w karcie procesu (pole 2 „komu oddaje pałeczkę").
2. Linia przerywana — propozycja przekazania WYMAGAJĄCA walidacji (hipoteza z silnika/rejestru styków).
3. Brak linii — relacja lub miejsce w sekwencji NIE zostały potwierdzone.
4. Proces należący do obszaru, ale bez potwierdzonego przekazania, zostaje na osobnej PÓŁCE
   wewnątrz obszaru. Nie łączymy go linią hipotetyczną.
5. Procesy przekrojowe NIE mają na mapie globalnej linii do przepływów biznesowych. Użycie procesu
   przekrojowego przez konkretny proces pokazujemy dopiero w widoku obszaru lub procesu, po potwierdzeniu
   w kartach.
6. Bez rombów BPMN i bez swimlane'ów po bytach. Mapa pozostaje na poziomie proces–proces i ma być
   czytelna bez klucza domen.

Do potwierdzenia w kartach (obecnie WYŁĄCZNIE propozycje na prototypie, nie fakty): sekwencje
`Zakup do zapłaty 01→02→03→04` (proces 05 bez linii); `Plan i dostępność 03→01→04→05`
(procesy 02 i 06 bez linii); `Oferta handlowa 01→02/03` (proces 04 bez linii);
`Realizacja sprzedaży 01→02/03`; `Płatności 01→02→03`; `Zwrot 01` jako osobna ścieżka,
`02→03/04`. Docelowa mapa dowodowa jest generowana z pola przekazania w kartach; prototyp notacji
i mapa dowodowa to dwa odrębne artefakty.

Powyższe sekwencje odnoszą się do stanu mapy z 24.08 (stare nazwy obszarów i ówczesne numery NN,
m.in. INV-05 jako `Plan i dostępność / 05`) i po przepisaniu mapy wymagają przeglądu (nota operatora 2026-08-31, przegląd przy kartach szkieletowych).

## E. Relacja do modelu technicznego

- Byty L0 (16), styki (STK-01..44), projekcje ⊗: `standard/mapowania/rejestr-stykow-L0.md` v1.0.
- Karta procesu wiąże się z bytami po NAZWIE w polu uczestników; kody bytów nie wchodzą do ścieżki.
- Diagram przepływu per obszar (proces → proces, bramki, wywołania procesów przekrojowych) powstaje przy
  kartach szkieletowych Etapu B, zaczynając od „Zakup do zapłaty" (protokół P2P gotowy w rejestrze,
  sekcja C.6).

---
