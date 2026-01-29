# Home Assistant

**HAOS (Home Assistant Operating System)** to dedykowany system operacyjny do uruchamiania Home Assistant - popularnej platformy do automatyzacji domu. Zapewnia pełne środowisko z wbudowaną obsługą dodatków, aktualizacji i łatwą konfiguracją sprzętową.

Prezentowane rozwiązanie opiera się na urządzeniu wykorzystującym system `NASweb`.  
Aby przejść do panelu zarządzania:

1. Otwórz przeglądarkę
2. Wprowadź adres **IP** brokera i zaloguj się do panelu
3. Przejdź do zakładki **HAOS**

Przykładowe ustawienia **HAOS Configuration**:

<img width="919" height="563" alt="obraz" src="https://github.com/user-attachments/assets/15e4a6a4-249f-44e4-a77f-bc743e50ce55" />

4. Wprowadź odpowiednie zmiany
5. Kliknij **Save**, aby zapisać ustawienia  
6. Kliknij **Start HAOS.APP**, aby uruchomić aplikację  
7. Zaloguj się do interfejsu Home Assistant poprzez adres `https://twoja_domena.haos.app`

--- 

## Panel webowy

Panel webowy dostępny pod adresem `twoja_domena.haos.app` umożliwia:

-  zarządzanie urządzeniami
-  konfigurację i instalację dodatków
-  personalizację panelu głównego (dashboardu) 

---

## Edycja elementów na pasku bocznym 

1. Zaloguj się do interfejsu Home Assistant przez adres:   

 `https://twoja_domena.haos.app`

2. Wybierz na lewym pasku bocznym:  

`Użytkownik → Panel Ustawienia użytkownika → Zmień kolejność i ukryj elementy na pasku bocznym`

<img width="256" height="261" alt="obraz" src="https://github.com/user-attachments/assets/d01e069c-f987-4db6-b5b5-970cb204a053" />

W tym widoku możesz **dodawać, usuwać i reorganizować** dashboardy widoczne na pasku.  

!!! tip "Wskazówka"

    Tryb można także uruchomić przytrzymując `Home Assistant` (lewy górny róg ekranu) lewym przyciskiem myszy przez 2 sekundy:
    
    <img width="256" height="57" alt="obraz" src="https://github.com/user-attachments/assets/c7d912a6-1ae0-4c92-90d8-c2b8ebe76540" />

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