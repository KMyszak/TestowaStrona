Panel umożliwia zmianę [typu](Wyjścia-(strefy)#dostępne-typy) oraz [limitu czasu](Wyjścia-(strefy)#limit-czasu--do-czego-służy) dla poszczególnych wejść.  
Edycji **wyjścia** dokonujemy przez przejście do kolumny `Opcje` i kliknięcie **zębatek** danego wyjścia (Ustawienia):  

<img width="890" alt="obraz" src="https://github.com/user-attachments/assets/95f5d0b1-8a89-4615-a021-7690a8a5c011" />

---

## Dostępne typy 

- **0: Nie używane**  

Wyjście jest **nieaktywne**, nie wykonuje żadnej akcji ani nie generuje alarmów  
- **1: Alarm**  

Wyjście aktywuje się podczas **alarmu włamaniowego** (głośnego)  
Najczęściej wykorzystywane do:
  - **syreny** zewnętrznej
  - **syreny** wewnętrznej
  - powiadomień do innych systemów

- **2: Usterka**  

Służy do powiadomień technicznych (np. sygnalizator LED, przekaźnik do **BMS** (system zarządzania budynkiem))  
Wyjście reaguje na stany awaryjne:

  - **brak** zasilania AC
  - niski akumulator centrali
  - **uszkodzenia** modułów
  - **awarie** komunikacji itp.  

- **3: Sabotaż**  

Używane do powiadamiania o naruszeniu zabezpieczeń obudowy  
Wyjście uruchamia się przy:

  - **otwarciu** obudowy
  - **przerwaniu** linii TAMPER
  - **zwarciu** linii tamperowych

- **4: Cichy alarm**  

Wyjście aktywuje się przy alarmie cichym (silent)  
Wykorzystywane przy:

  - **alarmie** napadowym
  - **monitoringu** dyskretnym
  - sygnałach dla stacji monitorowania

---

## Limit czasu – do czego służy?

Limit czasu (czas aktywacji wyjścia) określa jak długo wyjście ma pozostać aktywne po wystąpieniu zdarzenia:  

- To **NIE** jest opóźnienie przed zadziałaniem
- To jest **czas trwania** działania wyjścia

**Co dokładnie robi limit czasu?**

Kiedy wydarzy się zdarzenie (np. alarm), to:

- wyjście zostaje aktywowane
- pracuje przez ustawiony **limit czasu** (np. 30 s, 120 s, 3 min)
- po upływie tego czasu wyjście automatycznie się **wyłącza**

## Przykłady użycia limitu

**Syrena alarmowa (typ 1)**  
Limit czasu = 120 s  
↳ syrena wyje przez 120 sekund, potem wyłącza się automatycznie  

**Wyjście sabotażu (typ 3)**  
Limit czasu = 300 s  
↳ wyjście działa 5 minut, po wykryciu sabotażu, potem wyłącza się automatycznie

**Cichy alarm do monitoringu (typ 4)**  
Limit = 5 s  
↳ wysyła 5-sekundowy impuls do integracji lub nadajnika  