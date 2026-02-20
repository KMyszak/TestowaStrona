# HAOS

## Czym jest HAOS?

**HAOS** (**Home Assistant Operating System**) to dedykowany system operacyjny do uruchamiania Home Assistant - popularnej platformy do automatyzacji domu. Zapewnia pełne środowisko z pełną konfiguracją systemu.

Prezentowane rozwiązanie opiera się na urządzeniu wykorzystującym system [**NASweb**](https://www.chomtech.pl/nasweb/) firmy [**Chomtech**](https://www.chomtech.pl/).  

Aby przejść do panelu zarządzania:

1. Otwórz przeglądarkę
2. Wprowadź adres **IP** brokera i zaloguj się do panelu
3. Przejdź do zakładki **Haos**:

    !!! example "Przykładowe ustawienia **HAOS Configuration**"

        <img width="1206" height="766" alt="obraz" src="https://github.com/user-attachments/assets/15b88f49-3a0a-464d-9ddb-1fe32a8dad32" />

4. Wprowadź odpowiednie zmiany
5. Kliknij **Save**, żeby zapisać ustawienia  
6. Kliknij **Start HAOS.APP**, aby uruchomić aplikację  
7. Zaloguj się do interfejsu Home Assistant poprzez adres `https://twoja_domena.haos.app`

---

## Panel webowy

Panel webowy dostępny pod adresem `twoja_domena.haos.app` umożliwia:

-  **zarządzanie** urządzeniami
-  **konfigurację** i **instalację** dodatków
-  **personalizację** panelu głównego (dashboardu) 


## Edycja elementów na pasku bocznym

1. Zaloguj się do interfejsu Home Assistant przez adres:   

    `https://twoja_domena.haos.app`

2. Wybierz na lewym pasku bocznym:  

    `Użytkownik → Ogólny → Ustawienia użytkownika → Zmień kolejność i ukryj elementy na pasku bocznym`

    <img width="598" height="290" alt="obraz" src="https://github.com/user-attachments/assets/bca43343-f422-4b78-8103-61ee6a3dc724" />
   
    !!! info ""

        W tym widoku możesz **dodawać, usuwać i reorganizować** dashboardy widoczne na pasku.  

!!! tip "Szybka edycja"

    Tryb można także uruchomić przytrzymując *Home Assistant* (lewy górny róg ekranu) lewym przyciskiem myszy przez 2 sekundy.

---

## Dodawanie panelu

Aby utworzyć nowy panel wybierz:  

`Ustawienia → Panele → Dodaj panel (prawy dolny róg)`  

Dostępne opcje:

- **Nowy panel od podstaw**  
    Tworzy pusty panel do ręcznego konfigurowania
- **Przegląd**  
    Automatycznie dodaje wszystkie połączone urządzenia i ich encje
- **Mapa**  
    Widok z mapą geograficzną z lokalizacjami
- **Strona internetowa**  
    Osadza zewnętrzny adres URL (należy pamiętać o `https://`) 
