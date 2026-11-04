---
name: operat-application
description: "Przygotuj wniosek z danymi inwestora, właściwego urzędu i sekcji 14 operatu."
---

# Wniosek o pozwolenie wodnoprawne

1. Dokończ [operat](https://tarvena.pl/docs/assistants/workflows/operat.md), zwłaszcza S_14. Odczytaj `projects_read` → `projects/profile/get` i `documents_read` → `read-body` dla S_14. Sprawdź pierwszego inwestora, zakres wniosku i załączniki.
2. Odczytaj `forms_read` → `forms/preview-draft` dla `operat.wniosek`, z `config.linkedOperatDocumentId` wskazującym operat. Sprawdź wnioskodawcę, adres, właściwy Zarząd Zlewni i zakres skopiowany po akapicie wstępnym S_14, przed „Załączniki:”. Wiele urzędów lub brak adresu wymaga wyjaśnienia, nie zgadywania.
3. Pełnomocnika włącz tylko przy rzeczywistym umocowaniu. Dane osoby podaj w polach `representative.*`; dla biura pełną nazwę wpisz w `representative.lastName`, pozostawiając imię puste. Nie zmieniaj inwestora na pełnomocnika.
4. Uzgodnij załączniki formularza z S_14. Pola `attachments.attach_1` do `attachments.attach_10` są wartościami logicznymi; `attachments.attach_11` zawiera tekst innych załączników. Nie deklaruj dokumentów ani wniesionych opłat bez podstawy. Wyłącz pominięte załączniki i opłaty objęte zwolnieniem w obu wykazach.
5. Użyj `forms_write` → `forms/create` z odczytaną konfiguracją i poprawkami pól. Zachowaj identyfikator zapisanego formularza i jego `configRevision`. Po zmianie operatu, inwestora lub danych źródłowych użyj `forms/refresh-computed-values` i sprawdź wynik przez `forms_read` → `forms/get`.
6. Przy odświeżeniu pomiń `fieldValues`, aby zachować nadpisane pola. Przesłanie `fieldValues: {}` usuwa wszystkie nadpisania; wymaga świadomego zakresu zmiany. Do przywrócenia obliczanej wartości jednego pola użyj `resetFieldKeys`.
7. Zapisz DOCX do plików przez `forms_write` → `forms/publication/save`, po sprawdzeniu `forms_read` → `forms/publication/readiness`. Postępuj jak przy [publikacji wniosków EGiB](https://tarvena.pl/docs/assistants/workflows/egib-forms.md). Podaj odnośnik do pobrania, adresata, zakres i nierozstrzygnięte uwagi. Utworzenie dokumentu nie oznacza wysłania wniosku do urzędu.
