Panel kontroli wszystkich [ustawionych](Ustawienia) wejść w **SSWiN**.  
Do każdego z nich możemy przypisać jeden [typ](Wejścia#dostępne-typy) oraz jedną [akcję](Wejścia#dostępne-akcje):
<img width="890" height="279" alt="obraz" src="https://github.com/user-attachments/assets/02ddd2ff-f04d-4c2f-b76c-ac9b45df8b91" />

Dodatkowo, do dyspozycji mamy jedno wejście **INtemp** z czujnikiem **temperatury** 1-Wire, które można wykorzystać jako np. Termostat:

<img width="527" alt="obraz" src="https://github.com/user-attachments/assets/e232658a-dc20-49f0-b80c-03c03557086b" />  

---
  
<img width="370" alt="obraz" align="right" src="https://github.com/user-attachments/assets/147869ac-0248-4c4c-afe5-f053bf39e84d" />


**Trzy stany** z dokładnie jednym wyjściem na każdy stan:

- w zakresie - (np.) wentylacja
- poniżej zakresu - (np.) ogrzewanie
- powyżej zakresu - (np.) chłodzenie  
przy czym **to samo wyjście** może być wskazane w różnych stanach

ℹ️ Jeśli potrzebujesz kilku wyjść jednocześnie dla danego stanu, użyj skryptów lub zewnętrznego sprzęgła

**Przykład:**  
W strefie **Magazyn** kontroler włącza wentylację w przedziale 20-28 °C.  
Po przekroczeniu 28 °C steruje wyjściem zdefiniowanym dla stanu „powyżej” (np. chłodzenie)


---

## Dostępne typy
#### PODSTAWOWE:
- **NO** - Normalnie otwarte:

  - styk jest **rozwarty** w stanie spoczynku
  - alarm (lub zdarzenie) pojawia się po **zamknięciu** obwodu
  - stosowane np. w przyciskach, niektórych czujkach **KD**
- **NC** - Normalnie zamknięte:

  - styk jest **zwarty** w stanie spoczynku
  - alarm (lub zdarzenie) pojawia się po **otwarciu** obwodu
  - standard w czujkach **SSWiN**
#### Z NADZOREM REZYSTOROWYM (EOL / 2EOL):
**EOL** to nadzór rezystorowy linii, w którym jeden rezystor pozwala centrali rozróżnić stan normalny, alarm i sabotaż.  
**2EOL** używa dwóch rezystorów, dzięki czemu centrala dokładniej rozpoznaje stany i zapewnia najwyższą kontrolę nad czujką.
- **EOL/NO** - Jedno rezystorowe, normalnie otwarte

  - styk główny **NO**
  - linia z jednym rezystorem końcowym  
  - centrala rozpoznaje stan:
    - normalny
    - alarm
    - sabotaż / przerwa / brak rezystora
- **EOL/NC** - Jedno rezystorowe, normalnie zamknięte

  - styk główny **NC**
  - linia z jednym rezystorem końcowym
  - centrala rozpoznaje stan:
    - normalny
    - alarm
    - sabotaż / przerwa / brak rezystora
- **2EOL/NO** - Podwójny rezystor, normalnie otwarte

  - styk główny **NO**
  - linia z dwoma rezystorami końcowym
  - centrala rozpoznaje stan:
    - normalny
    - alarm
    - sabotaż
    - zwarcie linii
    - rozwarcie linii
- **2EOL/NC** - Podwójny rezystor, normalnie zamknięte

  - styk główny **NC**
  - linia z dwoma rezystorami końcowym
  - centrala rozpoznaje stan:
    - normalny
    - alarm
    - sabotaż
    - zwarcie linii
    - rozwarcie linii

#### Z INTEGRACJĄ SSWiN + Kontrola Dostępu (I&A + ACC)

Wejście jest częścią kontroli dostępu, ale jednocześnie integruje się z systemem alarmowym i centrala może zgłosić alarm naruszenia lub sabotaż.

**ACC** (**KD**) → wejście pracuje jako element **kontroli dostępu** (np. kontaktron drzwi, przycisk wyjścia)  
**I&A** (**SSWiN**) → wejście może dodatkowo wywołać **Intrusion & Alarm** (klasyczne stany alarmowe w systemie **SSWiN**)

- **NO ACC+I&A**

  - styk **NO**
  - pracuje jako czujnik kontroli dostępu (np. drzwi otwarte)
  - ale może także generować alarm/naruszenie w **SSWiN**
- **NC ACC+I&A**

  - styk **NC**
  - pracuje jako czujnik kontroli dostępu (np. drzwi otwarte)
  - ale może także generować alarm/naruszenie w **SSWiN**
- **EOL/NO ACC+I&A**

  - wejście **NO** z nadzorem (jeden rezystor)
  - ACC + alarm systemowy
- **EOL/NC ACC+I&A**

  - wejście **NC** z nadzorem (jeden rezystor)
  - ACC + alarm systemowy
- **2EOL/NO ACC+I&A**

  - podwójny nadzór rezystorowy w wejściu **NO**
  - dokładne monitorowanie (normaly/alarm/sabotaż/zwarcie/rozwarcie)
  - jednocześnie wejście uczestniczy w kontroli dostępu
- **2EOL/NC ACC+I&A**

  - podwójny nadzór rezystorowy w wejściu **NC**
  - dokładne monitorowanie (normaly/alarm/sabotaż/zwarcie/rozwarcie)
  - jednocześnie wejście uczestniczy w kontroli dostępu

---

## Dostępne akcje
- **0: Brak**

  - wejście nie wykonuje **żadnej** akcji
  - używane do **testów**, **diagnostyki** lub wejść **nieaktywnych**
- **1: 24h (ciche)**

  - alarm 24-godzinny, aktywny **zawsze**, niezależnie od stanu uzbrojenia
  - **brak** sygnalizacji syreną - tylko powiadomienie/system
  - używane dla:
    - przycisków antynapadowych (silent panic)
    - czujników technicznych, które nie mają wywoływać hałasu
- **2: Wejście/Wyjście**

  - standardowe wejście z opóźnieniem naruszenia przy uzbrojeniu i rozbrojeniu
  - stosowane:
     - w drzwiach wejściowych
     - przy ścieżkach komunikacji
     - gdy użytkownik ma mieć czas na wejście/wyjście
- **3: 24h**

  - alarm 24-godzinny, aktywny **zawsze**
  - głośny alarm / syrena
  - używane dla:
    - czujników pożaru
    - sabotażu obudów
    - zabezpieczeń specjalnych
- **4: Uzbrojenie strefy**

  - naruszenie wejścia powoduje uzbrojenie wskazanej **strefy**
  - stosowane do: 
     - kluczyków
     - przełączników alarmowych
     - systemów zewnętrznych
- **5: Rozbrojenie strefy**

  - naruszenie wejścia powoduje rozbrojenie **strefy**
  - typowe dla:
     - czytników **KD**
     - układów automatyki
     - zewnętrznych systemów sterowania
- **6: Rozbrojenie/Uzbrojenie strefy (switch)**

  - wejście działa jak przełącznik **bistabilny**
  - jeden stan → uzbrój, drugi stan → rozbrój
  - idealne dla:
     - przełączników kluczykowych 
     - styczników automatyki
- **7: Rozbrojenie/Uzbrojenie strefy (button)**

  - wejście działa jako przycisk **monostabilny**
  - krótkie naruszenie → zmienia stan uzbrojenia
  - typowe dla:
     - przycisków ściennych
     - impulsowego sterowania systemem
- **8: Włamanie**

  - standardowy alarm włamaniowy (głośny)
  - podstawowa akcja dla:
     - czujek PIR (ruchu)
     - kontaktronów
     - czujników zbicia szkła
- **9: Włamanie - cichy**

  - alarm włamaniowy bez syreny - tylko powiadomienia
  - przydatne gdy chcemy:
     - złapać intruza na gorącym uczynku
     - monitorować **strefę** bez wzbudzania hałasu
- **10: Wyczyść alarm**

  - naruszenie wejścia resetuje / kasuje aktywne alarmy
  - używane w:
     - trybach serwisowych 
     - integracjach z automatyką
- **11: Problem z zasilaniem**

  - wejście sygnalizuje awarię zasilania  
  - aktywność niezależna od stanu strefy
- **12: Problem z baterią**

  - sygnalizacja niskiego napięcia / uszkodzonej baterii w czujce lub urządzeniu
  - najczęściej wykorzystywane przy komunikacji z modułami bezprzewodowymi lub czujkami bateryjnymi

