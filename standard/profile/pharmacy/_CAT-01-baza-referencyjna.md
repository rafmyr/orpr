# Profil: pharmacy, nakładka do ORPR-CAT-01 Item-to-Sellable

Status: surowiec profilu (nie karta rdzenia). Data: 2026-08-19.
Powód istnienia tego pliku: reguła P15. Rdzeń standardu zna wyłącznie pojęcia-klasy; instancje
branżowe mieszkają tutaj. Karta rdzenia ORPR-CAT-01 opisuje **branżową bazę referencyjną danych
produktowych** jako klasę systemu i nie nazywa żadnej branży ani produktu.

## Obserwacja branżowa

**W polskiej farmacji istnieje wspólna baza referencyjna danych produktowych, obsługująca cały
rynek: BLOZ.** [AUT-R: R. Myrta, dyktando 19.08.2026, tura 2, arkusz decyzyjny CAT-01 pytanie 4]

Pełna nazwa rozwinięcia skrótu, podmiot prowadzący, model licencyjny i zakres pokrycia:
**[do potwierdzenia]**. Nie wpisujemy tych danych z pamięci, bo profil ma być użyteczny u adoptera,
a nie prawdopodobny.

## Dlaczego to zmienia proces, a nie tylko listę systemów

W modelu bez bazy branżowej detalista **zakłada pozycję od zera**: zbiera dane od dostawcy, z etykiety,
z systemu informacji produktowej, i sam odpowiada za ich kompletność. Bramka dopuszczenia z pola 9
karty rdzenia pilnuje wtedy pracy własnej organizacji.

W modelu z bazą branżową pozycja jest **zaciągana ze źródła, które zna produkt, zanim detalista go
zobaczy**. Konsekwencje dla wdrożenia:

1. **Reguła rozstrzygania konfliktu danych przestaje być teoretyczna.** Karta rdzenia wymaga jej
   zapisania (pole 9, kontrola „jawna reguła, które źródło wygrywa"). Tutaj konflikt jest codzienny:
   dane z bazy branżowej kontra dane własne detalisty kontra dane od konkretnego dostawcy. Trzy
   źródła, nie dwa.
2. **Wykrywanie duplikatów przenosi się na inny poziom.** Jeśli identyfikator pochodzi z bazy
   wspólnej dla rynku, klasyczny duplikat „ta sama rzecz pod dwoma numerami" jest rzadszy, ale
   pojawia się nowy przypadek: pozycja własna założona ręcznie obok pozycji z bazy.
3. **Migracja kartoteki wygląda inaczej.** Pozycje bez powiązania z bazą branżową są osobną klasą
   ładunku migracyjnego i wymagają własnego kryterium odbioru.
4. **Zależność od jednego dostawcy danych staje się ryzykiem architektonicznym.** Warto zapytać, co
   się dzieje z kartoteką, gdy baza jest niedostępna albo gdy detalista przestaje z niej korzystać.

## Pytania warsztatowe, których nie ma w rdzeniu

- Czy korzystacie z bazy branżowej dla wszystkich pozycji, czy tylko dla części asortymentu?
  (Apteka sprzedaje też towary spoza tej klasy: kosmetyki, sprzęt, artykuły spożywcze.)
- Które pola pochodzą z bazy, a które utrzymujecie sami?
- Co wygrywa przy rozbieżności: baza czy Wasza poprawka?
- Jak często synchronizujecie i co robicie z pozycjami, które w bazie zniknęły?

## Czego tu NIE ma

Wymagań prawnych specyficznych dla obrotu produktami leczniczymi. Te należą do bezpieczników R
i do overlaya w regulatory-matrix, nie do tego pliku.
