# moja-firma-produkcja

**Agent zamówień sieci handlowych dla polskiej firmy: produkcja seryjna.** Czyta zamówienie sieci z PDF, dopasowuje linie do kartoteki po EAN i indeksie, sprawdza palety, stany, plan produkcji i kontrakt, liczy ryzyko kar i oddaje szkic potwierdzenia z listą wyjątków.

Pakiet branżowy paczki [moja-firma](https://github.com/majchrzycki-com/moja-firma). Procedura w formacie [Agent Skills](https://agentskills.io/specification) (`SKILL.md`) działa w Anthropic Claude, OpenAI ChatGPT i OpenAI Codex, Microsoft 365 Copilot, Google Gemini oraz OpenClaw.

## Czego agent nie zrobi

Nie potwierdzi odbiorcy terminu, gdy stan nie wystarcza, nie przyjmie ceny z zamówienia zamiast ceny z kontraktu i nie zdecyduje, czy awizować dostawę, której część zależy od partii zwalnianej w dniu awizacji. Dwie pierwsze decyzje należą do handlowca, trzecia do handlowca z planistą. Agent pokazuje, ile każda z nich kosztuje w złotych kary z kontraktu i kto ma się pod nią podpisać, żeby ta rozmowa zajęła minutę, a nie pół dnia.

Ślepa automatyzacja szkodzi tu w jednym konkretnym miejscu: przy dopasowaniu po nazwie. Odbiorca pisze „Krzesło Lora szare” i podaje indeks, który u Was jest wycofany. Agent, który dopasuje linię po nazwie do pierwszego krzesła Lora w kartotece, potwierdzi cenę starego indeksu i przeoczy, że następca kosztuje więcej. Dlatego instrukcja każe dopasowywać po EAN i indeksie, a nazwy używać tylko pomocniczo.

Warunek brzegowy jest prosty. Jeśli ten sam wyrób ma u Was dwa indeksy, a ceny kontraktowe sieci żyją w PDF-ie i w pamięci handlowca, agent policzy wszystko na złych danych, tyle że szybciej niż ludzie. Najpierw jedna kartoteka z ceną kontraktową przy odbiorcy, potem agent.

## Wypróbuj na danych ćwiczeniowych

W katalogu [`dane-cwiczeniowe/`](dane-cwiczeniowe/) są fikcyjne dane firmy: `indeksy.csv`, `indeksy.xlsx`, `kontrakt-odbiorcy.csv`, `kontrakt-odbiorcy.xlsx`, `stany.csv`, `stany.xlsx`, `zamowienie.pdf`. Pliki XLSX i CSV mają tę samą treść.

1. Zainstaluj procedurę `zamowienie-sieci` (niżej).
2. Dodaj pliki ćwiczeniowe do wiedzy agenta albo załącz je do rozmowy.
3. Napisz:

```text
Nowe zamówienie od sieci. Przeprowadź analizę według instrukcji projektu, licząc kodem na plikach z wiedzy.
```

4. Porównaj odpowiedź z [WYNIK-KONTROLNY.md](WYNIK-KONTROLNY.md). Jest tam też „krok z rzeczywistością”: jedna zmiana w danych i wynik, który agent powinien po niej pokazać.

## Instalacja

### Anthropic Claude Code

```text
/plugin marketplace add majchrzycki-com/moja-firma
/plugin install moja-firma-produkcja@moja-firma
```

### Pozostałe narzędzia

```bash
node scripts/build.mjs
```

Skrypt tworzy `dist/skills/` dla Anthropic Claude, OpenAI Codex, Google Gemini, OpenClaw i Microsoft 365 Copilot Cowork oraz `dist/instrukcje/` z tekstem do wklejenia w agencie Microsoft 365 Copilot Agent Builder albo w projekcie OpenAI ChatGPT. Szczegóły instalacji w każdym narzędziu: [README rdzenia moja-firma](https://github.com/majchrzycki-com/moja-firma#instalacja).

## Ten sam agent krok po kroku

- [Agent zamówień sieci handlowych w Anthropic Claude](https://majchrzycki.com/blog/agent-zamowien-sieci-w-claude-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci)
- [Agent zamówień sieci handlowych w Microsoft 365 Copilot](https://majchrzycki.com/blog/agent-zamowien-sieci-w-microsoft-365-copilot-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci)
- [Agent zamówień sieci handlowych w OpenAI ChatGPT](https://majchrzycki.com/blog/agent-zamowien-sieci-w-chatgpt-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci)
- [Agent zamówień sieci handlowych w Google Gemini](https://majchrzycki.com/blog/agent-zamowien-sieci-w-gemini-krok-po-kroku?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci)

Gdzie ten agent mieści się w całej firmie i jakich jeszcze agentów potrzebuje produkcja seryjna: [darmowy poradnik branżowy](https://majchrzycki.com/transformacja-agenci-ai/produkcja-seryjna?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci#pobierz).

## Na własnych danych

Zacznij od procedury `kontrola-danych` z rdzenia moja-firma na eksporcie z Waszego programu. Jeśli kolumny nazywają się inaczej, agent pokaże przypisanie i poprosi o potwierdzenie. Pierwszy tydzień puść agenta obok normalnej pracy jednej osoby i porównuj wyniki.

Procedura nie jest poradą prawną, podatkową ani handlową. Wynik sprawdza osoba, która za niego odpowiada.

## Licencja

[MIT](LICENSE), dla procedur, skryptów i danych ćwiczeniowych.

Autor: [Krzysztof Majchrzycki](https://majchrzycki.com/o-mnie?utm_source=github&utm_medium=referral&utm_campaign=moja-firma&utm_content=zamowienie-sieci), wdrożenia AI w polskich firmach.

---

**English:** moja-firma-produkcja is an industry pack of the open [moja-firma](https://github.com/majchrzycki-com/moja-firma) Agent Skills for Polish SMBs. It contains one `SKILL.md` procedure (in Polish), fictional practice data and expected results. MIT licence.
