---
name: device-evidence
description: "Pozyskaj i sprawdź informacje o JCWP, zagrożeniu powodziowym i uwarunkowaniach urządzeń."
---

# Dane źródłowe urządzeń

1. Odczytaj `water_design_read` → `water-design/query#tree` oraz `characteristic-points/list`. Sprawdź, czy każde urządzenie ma właściwe punkty i współrzędne. Dane EGiB i Drive nie warunkują pozyskania informacji o urządzeniu.
2. Użyj `water_design_write` → `evidence/refresh` dla profilu `hydro.water-device-evidence`, z listą wszystkich urządzeń w `targetRefs`. Jedno wywołanie obsługuje do 200 różnych celów. Przy limicie źródeł podziel listę lub zawęź zakres. Zachowaj tożsamość każdego urządzenia i uruchomienia.
3. Odczytuj `water_design_read` → `evidence/report` co 15–30 s, aż każdy raport ma `settled: true`. W czasie pozyskiwania danych kontynuuj niezależną pracę. Pierwsze wyniki pozwalają rozpocząć operat, a zakończenie pozyskiwania wymaga późniejszego odświeżenia zależnych sekcji.
4. Sprawdź `providerResults[].canonicalRecords`, w tym JCWP, Zarząd Zlewni i jego adres, oraz stany źródeł. `settled` oznacza koniec pracy źródeł, nie kompletność danych. Brak rekordu nie dowodzi braku zagrożenia, ochrony ani obowiązku.
5. Dla nieudanych odczytów użyj `water_design_write` → `evidence/retry` dla właściwego urządzenia. Brak raportu wymaga `evidence/refresh`; nieaktualny raport wymaga sprawdzenia zmienionych punktów i powiązań. Nie powtarzaj bez końca nieudanego źródła.
6. Podaj źródła, ustalone fakty i nierozstrzygnięte ostrzeżenia osobno dla urządzeń. Nie zgaduj JCWP ani właściwego urzędu. Wiele urzędów lub brak adresu pozostaje jawnym ostrzeżeniem. Po ustaleniu danych wykonaj [odświeżenie operatu](https://tarvena.pl/docs/assistants/workflows/operat.md).
