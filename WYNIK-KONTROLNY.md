# Wynik kontrolny: agent zamówień sieci handlowych

Liczby poniżej policzono niezależnie z plików w katalogu `dane-cwiczeniowe/`. Jeśli agent oddaje inne wartości, procedura nie działa poprawnie w Waszym narzędziu.

## Sprawdź wynik na danych kontrolnych

Porównaj odpowiedź z tabelami poniżej. Liczby policzyliśmy niezależnie z tych samych plików.

| Lp. | Indeks | Ilość | Palety | Cena kontr. | Wartość wg kontraktu | Dostępne | Uwagi |
|---|---|---|---|---|---|---|---|
| 1 | REG-DAB-80 | 96 | 8 pełnych (12 szt.) | 389,00 zł | 37 344,00 zł | 520 | dopasowanie po EAN |
| 2 | LAM-STO-01 | 180 | 1 pełna + 36 szt. (144 szt.) | 79,00 zł | 14 220,00 zł | 1 600 | ilość nie tworzy pełnych palet |
| 3 | KRZ-TAP-01B | 120 | 2 pełne + 24 szt. (48 szt.) | 152,50 zł | 18 300,00 zł | 340 | KRZ-TAP-01 wycofany; zamiennik 152,50 zł, w zamówieniu 149,00 zł; potwierdzić z odbiorcą; niepełne palety |
| 4 | STL-ROZ-140 | 300 | 37 pełnych + 4 szt. (8 szt.) | 612,00 zł | 183 600,00 zł | 120 | brakuje 180 szt.; w planie 400 szt., zwolnienie 11.09.2026 — przed oknem, bez zapasu czasu; ryzyko kary 3 304,80 zł; niepełne palety |
| 5 | SZF-3D-150 | 40 | 10 pełnych (4 szt.) | 899,00 zł | 35 960,00 zł | 34 | brakuje 6 szt.; brak partii w planie; ryzyko kary 3% (161,82 zł) |
| 6 | — | 60 | — | — | — | — | EAN 5905555000117 nie występuje w kartotece; do wyjaśnienia z odbiorcą |

| Pozycja | Wartość |
|---|---|
| Wartość według cen kontraktowych (linie 1–5) | 289 424,00 zł |
| Wartość według cen z zamówienia | 289 004,00 zł |
| Różnica do potwierdzenia (linia 3) | 420,00 zł |
| Czas realizacji z kontraktu | 10 dni; od zamówienia do okna jest 12 dni |
| Awizacja | do 11.09.2026, w dniu zwolnienia partii stołów |
| Kara za spóźnione okno | 1 500 zł |
| Etykieta | GS1-128 z numerem SSCC na każdej palecie |
| Termin płatności | 60 dni |

Na liście wyjątków powinno się znaleźć siedem spraw: zamiennik i różnica ceny w linii 3 (handlowiec z odbiorcą), niepełne palety w liniach 2, 3 i 4 (handlowiec z odbiorcą: zaokrąglić do pełnych palet albo zgoda na paletę mieszaną), brak 180 stołów pokryty partią zwalnianą w dniu awizacji (handlowiec z planistą: potwierdzić pełną ilość z ryzykiem czy zaproponować dostawę częściową), brak 6 szaf bez partii w planie (handlowiec i planista) oraz nieznany EAN w linii 6 (handlowiec z odbiorcą). Prawidłowa rekomendacja to **potwierdzić pięć linii z zastrzeżeniami, linię szóstą odesłać do wyjaśnienia**; decyzję o potwierdzeniu terminu przy ryzyku partii podejmuje handlowiec.

Jeśli linia 3 ma cenę 149,00 zł, agent uwierzył zamówieniu zamiast kontraktowi. Jeśli linia 4 pokazuje dostępne 520, agent dopasował stół do regału po pierwszym EAN z listy. Jeśli suma wynosi 289 004,00 zł, agent wziął ceny z zamówienia.

## Krok z rzeczywistością

Dane w firmie się zmieniają, a agent musi to zauważyć bez zmiany instrukcji. Następnego dnia magazyn zwalnia rezerwację szaf dla innego odbiorcy. Otwórz `stany.xlsx` i w wierszu SZF-3D-150 zmień `zarezerwowane_szt` z 12 na 0. Usuń stary plik z wiedzy projektu, dodaj nowy i zadaj w nowej rozmowie to samo pytanie.

Agent powinien teraz pokazać dla linii 5 dostępne **46** sztuk, brak zniknie, a razem z nim ryzyko kary 161,82 zł. Wartości się nie zmieniają: nadal 289 424,00 zł według kontraktu i 420,00 zł różnicy w linii 3. Zostaje sześć wyjątków: zamiennik, trzy niepełne palety, partia stołów zwalniana w dniu awizacji i nieznany EAN.

Jedna zwolniona rezerwacja zdjęła jedną sprawę z biurka planisty, ale żadnej z biurka handlowca. Jeśli agent po tej zmianie uzna zamówienie za „czyste”, nie trzyma się instrukcji.
