---
name: operat-from-outlets
description: "Przygotuj wyloty, zlewnię, przepływy, operat i wniosek dla odwodnienia drogi."
---

# Operat z wylotów wzdłuż drogi

1. Odczytaj `projects_read` → `projects/list`, a po wyborze projektu `overview`. Gdy projekt nie istnieje, utwórz go przez `projects_write` → `projects/create`. Zachowaj identyfikator i sprawdź zakres zlecenia.
2. Wykonaj [wyloty, punkty i działki](https://tarvena.pl/docs/assistants/workflows/outlets-and-parcels.md). Dane CSV odczytaj z rozmowy lub wskazanego pliku. Zachowaj kolejność wylotów wzdłuż drogi.
3. Wykonaj [zlewnię odwodnienia drogi i przepływy](https://tarvena.pl/docs/assistants/workflows/catchment-for-road.md). Przed zapisem przedstaw szerokość pasa, czas dopływu, okres powtarzalności, źródło opadu i współczynniki ψ. Uzyskaj potwierdzenie założeń.
4. Jeśli zlecenie obejmuje dane EGiB, wykonaj [wnioski o dane z EGiB](https://tarvena.pl/docs/assistants/workflows/egib-forms.md).
5. Uruchom [dane źródłowe urządzeń](https://tarvena.pl/docs/assistants/workflows/device-evidence.md). Pozostałą pracę prowadź w czasie pozyskiwania danych.
6. Wykonaj [operat](https://tarvena.pl/docs/assistants/workflows/operat.md). Uwzględnij wybrane obliczenia i tabelę przepływów dla wylotów. Po zakończeniu pozyskiwania danych odśwież zależne sekcje.
7. Jeśli zlecenie obejmuje wniosek, wykonaj [wniosek o pozwolenie wodnoprawne](https://tarvena.pl/docs/assistants/workflows/operat-application.md).
8. Podaj tabelę Qmax w m³/s i l/s, roczną objętość w m³/rok, przyjęte założenia, ostrzeżenia oraz zwrócone odnośniki do mapy, operatu i plików. Nie ogłaszaj gotowego operatu, gdy pozostają nierozstrzygnięte uwagi inżynierskie.
