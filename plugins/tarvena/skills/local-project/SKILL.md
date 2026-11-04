---
name: local-project
description: "Pracuj z projektem na dysku przez zainstalowane Tarvena CLI."
---

# Projekt w folderze lokalnym

1. Połączenie z `https://tarvena.pl/mcp` widzi projekty w chmurze. Dla projektu na dysku odpowiedz: „Ten projekt jest w folderze lokalnym na Twoim komputerze, więc to połączenie go nie widzi. Otwórz go w Claude Code z Tarvena CLI.” Nie twórz kopii projektu w chmurze bez polecenia.
2. W Claude Code odczytaj `tarvena --local help agent-docs`, aby użyć dokumentacji zgodnej z instalacją. Sprawdź `tarvena --local runtime ping`, a następnie `tarvena --local cloud-project list`. Ustal właściwy projekt i folder na podstawie odczytu.
3. Postępuj według zainstalowanego przewodnika i `tarvena --local …`. Sprawdź pomoc konkretnego polecenia przed pierwszym użyciem. Nie zastępuj operacji lokalnych wywołaniami zdalnego MCP.
4. Przed zapisem przedstaw założenia inżynierskie, jednostki i układ współrzędnych. Przed usunięciem, zastąpieniem treści lub udostępnieniem uzyskaj zgodę. Zachowuj tożsamość żądania przy ponowieniu zgodnie z przewodnikiem CLI.
5. Sprawdź zapisany stan i wynikowe dokumenty. Podaj ścieżki plików, wykonane zmiany i ostrzeżenia, bez sugerowania, że projekt jest dostępny przez połączenie zdalne.
