# Jak korzystać ze standardu ORPR

Katalog `standard/` zawiera publiczną część Open Retail Process Reference. Najlepiej zacząć od
pytania, na które chcesz odpowiedzieć:

| Potrzeba | Punkt wejścia |
|---|---|
| zobaczyć cały krajobraz procesów | [Mapa 74 procesów](mapa-procesow.md) |
| znaleźć pełną kartę albo publiczny skrót | [Katalog 74 kart](KARTY-PROCESOW.md) |
| prześledzić przepływ między procesami | katalog [`przeplywy/`](przeplywy/) |
| sprawdzić wariant organizacyjny | [Modele operacyjne](mapowania/modele-operacyjne.md) |
| zobaczyć styki i pokrycie modelu | katalog [`mapowania/`](mapowania/) |
| zobaczyć przykład nakładki sektorowej | katalog [`profile/pharmacy/`](profile/pharmacy/) |

## Co zawiera publiczna próbka

- mapę 74 procesów w 22 obszarach oraz jednego kandydata;
- katalog wszystkich 74 kart: sześć pełnych przykładów i 68 publicznych skrótów;
- dziesięć opisów przepływów oraz mapowania i przykładowe profile;
- dwa szablony: skróconej karty standardowej i karty pogłębionej.

Pełne wersje pozostałych 68 kart oraz Regulatory Matrix nie są częścią publicznego repozytorium.
Informacja o pełnym zakresie i kontakt znajdują się w [głównym README](../README.md).

## Notacja

Każdy proces ma stabilny identyfikator techniczny:

```text
ORPR-<KOD DOMENY>-<NN>
```

Przykład: `ORPR-SAL-01`. Na mapie prefiks `ORPR-` jest pomijany i proces występuje jako `SAL-01`.
Identyfikator nie zmienia się, gdy proces zostaje przeniesiony do innego obszaru mapy.

Adres nawigacyjny ma postać:

```text
<rodzaj> / <obszar> / <NN> · <od czego do czego> · <ID>
```

`NN` jest numerem porządkowym w obszarze, a nie krokiem procesu. Kolejność wykonania wynika z
opisanych przekazań i przepływów, nie z numerów.

Notacja identyfikatorów jest zamrożona od wydania `v0.1.0`. Jej zmiana wymaga nowego wydania i
jawnego oznaczenia wycofywanego identyfikatora.

## Jak czytać karty

Najpierw przeczytaj: cel biznesowy, granice, właściciela, wyzwalacze, wejścia, wyjścia i bramki.
Bank pytań oraz czerwone flagi służą późniejszemu warsztatowi analitycznemu. Metadane i klasy
źródeł zachowują ślad pochodzenia twierdzeń:

- `[AUT-R]` — potwierdzona wiedza właściciela standardu;
- `[PROP+]` — przyjęta propozycja redakcyjna;
- `[LIT]` — źródło publiczne z lokatorem;
- `[R: ID]` — powiązanie z wymaganiem Regulatory Matrix;
- `[HIP]`, `[do potwierdzenia]`, `[do weryfikacji]` — treść, której nie należy traktować jako
  potwierdzonego faktu lub wymagania prawnego.

## Zasady publicznej treści

1. Rdzeń procesu jest neutralny sektorowo; treść sektorowa trafia do `profile/`.
2. Materiał powstaje w trybie clean-room, bez danych klientów i pracodawców.
3. Regulatory Matrix wspiera analizę, ale nie jest opinią prawną ani certyfikatem zgodności.
4. Językiem źródłowym bieżącego wydania jest polski.
5. Ograniczenia wydania są opisane w [`ZNANE-OGRANICZENIA.md`](../ZNANE-OGRANICZENIA.md).
