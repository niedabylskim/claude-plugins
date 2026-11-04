---
name: outlets-and-parcels
description: "Wprowadź punkty wylotów, dodaj działki i powiąż urządzenia z lokalizacją."
---

# Wyloty, punkty i działki

1. Wybierz projekt przez `projects_read` → `projects/list` i `overview`; jeśli potrzeba, utwórz go przez `projects_write` → `projects/create`. Sprawdź istniejące punkty, urządzenia i działki, aby ich nie powielać.
2. Ustal układ współrzędnych, jednostki, kolejność wylotów i zakres robót. W imporcie punktów EPSG:2180 `x` to północ, `y` to wschód. W geometrii mapy i działek kolejność to `[easting,northing]`. Dla długości i szerokości geograficznej użyj jawnych nazw `longitude`, `latitude`.
3. Użyj `water_design_write` → `characteristic-points/commands` z importem do 500 punktów. Zachowaj identyfikatory punktów do powiązania urządzeń. Nie zamieniaj osi bez sprawdzenia.
4. Dodaj działki pod wylotami przez `parcels_write` → `add-parcels`. Sprawdź wyniki bez działki i usuń duplikaty według identyfikatora ewidencyjnego. Pozyskanie szczegółów EGiB jest opcjonalne i nie warunkuje wniosków o dane.
5. Jeżeli zlecenie obejmuje działki drogi, odczytaj `maps_read` → `maps/roads/axis` dla pasa po 1 m i użyj jego geometrii w `add-parcels`. Pas po 10 m służy do obliczenia zlewni i może objąć sąsiednie nieruchomości. Wynik o maksymalnej liczbie kandydatów sprawdź na krótszych odcinkach.
6. Odczytaj bieżącą rewizję przez `water_design_read` → `water-design/query#revision`. Utwórz wyloty przez `water_design_write` → `water-design/commands#batch_devices`, wiążąc punkty i przyjęte działki. Zachowaj grupę „Wyloty”, rzeczywisty typ urządzenia i zakres robót. Zastąpienie istniejących urządzeń wymaga potwierdzenia.
7. Parametry techniczne wszystkich wylotów zapisz w tabeli opisu grupy przez `water-design/commands#put_description` w `water_design_write`, z `descriptionType: operat`. Odczytaj istniejący opis i jego rewizję; zachowaj niezwiązane wiersze. Nie dopisuj wymiarów ani materiału, których nie dostarczono.
8. Przez `water_design_write` → `water-design/commands#create_water_service` powiąż grupę z usługą `stormwater-discharge`, gdy odpowiada zleceniu. W operacie zakres tej usługi ma nazwę `rainwater`.
9. Podaj liczbę zapisanych punktów, urządzeń i działek, nierozwiązane lokalizacje oraz odnośnik do mapy. Oryginały PDF, zdjęcia i skany inżynier dodaje w plikach projektu. Załącznik rozmowy może dostarczyć wiersze CSV lub GeoJSON, ale nie oznacza zapisania oryginału.
