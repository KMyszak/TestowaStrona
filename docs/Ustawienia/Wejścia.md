## Wybór modułu dla poszczególnych wejść
Każde wejście może pracować w jednym z poniższych trybów: 

  - [**Kontrola dostępu**](#kontrola-dostępu-kd)
  - [**SSWiN**](#sswin-system-sygnalizacji-włamania-i-napadu)
  - [**SSWiN** + **KD**](#sswin--kd)

!!! info "Wybór trybu"

    Wybrany tryb określa, jak **interpretowany** jest sygnał z wejścia oraz do jakiego **systemu** trafiają zdarzenia.

### Kontrola dostępu (KD)

Wejście pracuje **wyłącznie** w ramach systemu kontroli dostępu.

**Działanie wejścia:**

- rejestruje zdarzenia związane z ruchem osób (np. otwarcie drzwi, przycisk wyjścia, kontaktron)
- stan wejścia wpływa na logikę przejścia (otwarcie / zamknięcie / naruszenie)

**Przykładowe zastosowania:**
- kontaktron drzwiowy
- przycisk wyjścia 
- czujnik stanu drzwi

**Obsługiwane zdarzenia:**

- otwarcie drzwi
- zamknięcie drzwi
- drzwi otwarte zbyt długo
- próba nieautoryzowanego otwarcia

**Uwaga:**

- wejście **nie generuje** alarmów **SSWiN** - zdarzenia są widoczne **wyłącznie** w module **KD**

---

### SSWiN 

Wejście pracuje **wyłącznie** jako linia alarmowa.

**Działanie wejścia:**

- monitoruje stan czujnika alarmowego
- naruszenie wejścia powoduje wygenerowanie zdarzenia alarmowego

**Przykładowe zastosowania:**

- czujnik ruchu PIR
- kontaktron okna
- czujnik zbicia szyby
- przycisk napadowy

**Obsługiwane zdarzenia:**

- naruszenie linii
- alarm
- sabotaż
- powrót do stanu normalnego


!!! warning "Widoczność zdarzeń"
    
    Wejście **nie wpływa** na kontrolę przejścia - zdarzenia są widoczne **tylko** w module **SSWiN**.

---

### SSWiN + KD

Wejście pracuje jednocześnie w obu systemach.

**Działanie wejścia:**

- ten sam sygnał wejściowy jest analizowany równolegle przez **KD** i **SSWiN**
- zależnie od kontekstu, wejście może generować zdarzenia dostępu lub alarmowe

**Przykładowe zastosowania:**

- kontaktron drzwiowy chronionych stref
- drzwi wejściowe do obiektu
- drzwi w strefie alarmowej

**Obsługiwane zdarzenia:**

- otwarcie / zamknięcie drzwi (**KD**)
- alarm otwarcia przy uzbrojonym systemie (**SSWiN**)
- nieautoryzowane otwarcie drzwi
- alarm sabotażowy

**Przykład logiki:**  

- system rozbrojony → wejście działa jak **KD**  
- system uzbrojony → otwarcie drzwi powoduje alarm **SSWiN**  
- zdarzenia są rejestrowane w **obu** modułach  

**Uwaga:**

- tryb **zalecany** dla wejść drzwiowych w chronionych strefach
