---
name: egib-forms
description: "Przygotuj wnioski o dane ewidencyjne dla działek projektu i zapisz DOCX."
---

# Wnioski o dane z EGiB

1. Odczytaj `projects_read` → `overview` i `projects/profile/get`. Sprawdź działki przez `parcels_read` → `location/get`. Najpierw dodaj działki zgodnie z [procedurą wylotów i działek](https://tarvena.pl/docs/assistants/workflows/outlets-and-parcels.md).
2. Wnioskodawcą jest pierwszy inwestor projektu. Sprawdź jego nazwę, adres i dane kontaktowe. Popraw wskazane dane przez `projects_write` → `projects/profile/mutate`, zachowując innych inwestorów. Biuro projektowe lub pełnomocnik nie staje się przez to inwestorem. Pierwszy „Projektant” dostarcza dane projektanta.
3. Odczytaj `parcels_read` → `location/egib-recipient-plan/build`. Wyjaśnij działki bez ustalonego adresata. Odczytaj `forms_read` → `forms/preview-batch-draft` z szablonem `egib.wniosek-jst`. Zachowane dane źródłowe EGiB i połączenie z Drive nie są wymagane do utworzenia wniosków.
4. Sprawdź adresatów, dane wnioskodawcy, ostrzeżenia, cel pozyskania danych i umocowanie pełnomocnika. Dane pełnomocnika wpisz w pola formularza, zachowując inwestora. Nie oświadczaj posiadania pełnomocnictwa ani załączników bez podstawy.
5. Użyj `forms_write` → `forms/create-batch` z odczytanym `sourceFingerprint` i poprawkami dla każdego `draftId`. Przechowaj identyfikatory zapisanych formularzy i ich `configRevision`. Po zmianie profilu użyj `forms/refresh-computed-values`; po zmianie działek przygotuj nowy podgląd adresatów. Usunięcie poprzednich wniosków wymaga zgody i narzędzia `delete_items`.
6. Sprawdź `forms_read` → `forms/get` i `forms/publication/readiness`. Zapisz przez `forms_write` → `forms/publication/save`. Gdy potrzeba połączenia lub wskazania folderu, użyj zwróconego odnośnika do przeglądarki i procedury `files_write`. Nie obchodź zgody na dostęp do Drive.
7. W razie niepewności odczytaj `forms_read` → `forms/publication/status`. Dokończ zwróconą operację, nie twórz nowej publikacji. Odczytaj `files_read` → `files/list` ze stronicowaniem.
8. Podaj liczbę wniosków, adresatów, ostrzeżenia i zwrócone odnośniki do pobrania DOCX z plików projektu. Nie używaj `forms/download` przez MCP.
