---
name: catchment-for-road
description: "Wyznacz pas odwodnienia drogi, oblicz przepływ i roczną objętość odpływu."
---

# Zlewnia odwodnienia drogi i przepływy

1. Odczytaj `projects_read` → `overview` oraz punkty przez `water_design_read` → `characteristic-points/list`. Sprawdź kolejność wylotów i nazwę drogi. Nie wyznaczaj osi z punktów posortowanych przypadkowo.
2. Przed zapisem przedstaw edytowalne założenia: przykładowo pas po 10 m z każdej strony osi, czas dopływu 20 min, okres powtarzalności 5 lat i minimalny czas opadu 10 min. Uzasadnij wartości i uzyskaj potwierdzenie. Pas drogowy nie jest działem wodnym wyznaczonym z rzeźby terenu.
3. Użyj `calculations_write` → `road-catchment`. Sprawdź wybraną drogę, długość, powierzchnię i odległości dociągnięcia punktów do osi. Wyloty oddalone o ponad 20 m oznacz do sprawdzenia. Przy przerwie osi uzupełnij rzeczywiste punkty pośrednie lub skróć odcinek, nie łącz dróg na ślepo.
4. Odczytuj `projects_read` → `overview` albo `calculations_read` → `water-design/query#calculation`, aż pokrycie terenu się ustali. Oczekiwanie lub odmowa analizy pokrycia nie oznaczają zerowej powierzchni. Podaj stan pracy, gdy dane jeszcze napływają.
5. Sprawdź udziały pokrycia i ψ dla każdej klasy. Wartości domyślne są jawnymi założeniami, nie pomiarem. Uwzględnij możliwość korekty według pomiaru nawierzchni; próbki pokrycia mają rozdzielczość 1 m. Nieznane pokrycie zachowaj jako osobną pozycję z oznaczonym założeniem.
6. Odczytaj `calculations_read` → `calculations/methods/get` dla `surfaceRunoff.designStorm`. Użyj `calculations_write` → `surface-runoff` z właściwym punktem i opadem PMAXTP. Sprawdź źródło `PMAXTP_STORM_RAINFALL`, zakres metody, Qmax i roczną objętość. Nie zastępuj nieudanego odczytu opadu przykładowymi 15 mm. Roczny opad 600 mm jest wartością przykładową do uzasadnienia lub zmiany, nie opadem lokalnym. Dla zlewni terenowej wskazanej punktem służy `point-catchment` w tym samym narzędziu.
7. Jeżeli inżynier przyjmie równy podział między N wylotów, oblicz A/N, Ared/N, Q/N i Vrok/N. To podział umowny, nie zlewnie poszczególnych wylotów ani trasowanie hydrauliczne. Nie przeliczaj rocznej objętości z przepływu szczytowego.
8. Odczytaj istniejący opis grupy przez `water_design_read` → `water-design/query#description`. Zapisz tabelę wszystkich wylotów i podstawę podziału przez `water_design_write` → `water-design/commands#put_description`, z typem `operat`, zachowując inne wiersze i aktualną rewizję opisu. W konfiguracji operatu wybierz `surface-runoff/peak` i `surface-runoff/annual`; odśwież S_2_1 i S_6 zgodnie z [procedurą operatu](https://tarvena.pl/docs/assistants/workflows/operat.md).
9. Podaj Qmax, Vrok, powierzchnię, źródła opadu, przyjęte ψ, sposób podziału i ostrzeżenia. Dołącz odnośniki zwrócone przez narzędzia.
