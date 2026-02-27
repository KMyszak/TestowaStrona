# Logi skryptów

Panel **Logi skryptów** wyświetla historię wszystkich operacji wykonanych przez skrypty uruchamiane w&nbsp;systemie.  
Zawiera szczegółowe wpisy pozwalające na **diagnozowanie błędów**, **analizę** działania automatyzacji oraz **śledzenie** danych przekazywanych do skryptów.

<img width="1663" height="392" alt="obraz" src="https://github.com/user-attachments/assets/61ea92aa-57c8-4769-9165-129b7e9da827" />

---

## Informacje w logach

Każdy wpis składa się z dwóch podstawowych elementów:

- **Data** - dokładny znacznik czasu , kiedy wywołanie skryptu zostało zarejestrowane
- **Info** - pełna struktura danych przekazana do skryptu podczas jego uruchomienia

Informacje te mają formę obiektu JSON i mogą zawierać m.in.:

- identyfikatory wejść i wyjść
- numery kart i liczbę bitów
- dane o zdarzeniach (np. *eventCode*)
- nazwę pliku skryptu
- źródło wywołania (czytnik, kontroler, strefa, itp.)

Widok logów można filtrować przy pomocy pola **Wyszukaj**, co ułatwia szybkie wyszukiwanie zdarzeń lub analitycznych danych.

## Zastosowanie panelu

Panel przydaje się zwłaszcza do:

- debugowania skryptów
- analizowania parametrów przekazywanych do skryptu
- wykrywania błędnych lub nieoczekiwanych wywołań
- monitorowania obciążenia i częstotliwości działania automatyzacji