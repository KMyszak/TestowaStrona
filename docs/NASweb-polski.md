# Polski

## 1. Wprowadzenie

**NASwebio** to nowoczesny kontroler bezpieczeństwa i automatyki budynkowej, który posiada wbudowaną aplikację **NASweb**.  

Łączy w sobie funkcje, które zwykle są realizowane przez kilka osobnych urządzeń: 

- kontroler kontroli dostępu
- centralę sygnalizacji włamania (SSWiN) 
- moduł automatyki (np. HVAC)
- rejestrator zdarzeń powiązanych z obrazem 
- system powiadomień i integracji zewnętrznych  

!!! question ""
    Dzięki temu **jedno urządzenie** zastępuje wiele systemów, upraszczając instalację i obniżając koszty.  

---

## 2. Synergia systemów 1 + 1 = 3

Największą zaletą NASwebio jest **synergia** - połączenie funkcji daje znacznie więcej niż suma ich możliwości.  

### Przykład 1: Alarm + kontrola dostępu
**Osobno**

- alarm chroni budynek, kontrola dostępu wpuszcza tylko uprawnionych

**Razem** 

- karta nie tylko otwiera drzwi, ale też **uzbraja/rozbraja strefę**  
- dostęp kartą do strefy może być **zablokowany, gdy strefa jest uzbrojona**  
- jeśli ostatni użytkownik opuści strefę, system **automatycznie ją uzbroi**  

!!! success "Efekt"
    Mniej błędów, większe bezpieczeństwo, mniej interwencji ochrony.

### Przykład 2: HVAC + sterowanie środowiskowe
Czujniki temperatury sterują przekaźnikami w **trzech stanach**:  

- **poniżej zakresu** - (np.) włącz ogrzewanie  
- **w zakresie** - (np.) włącz wentylację  
- **powyżej zakresu** - (np.) włącz chłodzenie 

!!! info "Wyjścia przekaźnikowe"
    Dla **każdego stanu** wybiera się **dokładnie jedno** wyjście przekaźnikowe (może to być ten sam przekaźnik w&nbsp;różnych stanach). Jeżeli potrzebujesz zadziałać **kilkoma** wyjściami w tym samym stanie (np. jednocześnie wentylacja i chłodzenie), zrób to skryptem lub użyj zewnętrznego sprzęgła/rozgałęzienia.

!!! example "Przykład" 
    W strefie *Magazyn* kontroler włącza **wentylację** w przedziale 20–28 °C (stan „w zakresie”). 
    Po przekroczeniu 28 °C przełącza sterowanie na wyjście przypisane do stanu „powyżej” (np. **chłodzenie**).  

!!! success "Efekt" 
    Stabilne warunki i optymalizacja zużycia energii.

### Przykład 3: Rejestracja zdarzeń + wideo

- Każde zdarzenie (np. naruszenie czujnika, odczyt karty) może być powiązane ze zdjęciem z kamery 
- Administrator widzi: _Jan Kowalski otworzył drzwi o 10:05_ + **zdjęcie z tego momentu**

!!! success "Efekt"
    Szybsza weryfikacja i reagowanie.

---

## 3. Architektura systemu

### 3.1. Interfejs użytkownika

- dostęp z dowolnej przeglądarki (PC, tablet, smartfon)  
- role: 

    - **operator** - loguje się i zarządza systemem  
    - **użytkownik** - korzysta z przejść kartą/PIN-em 

### 3.2. Elementy systemu

- 16 wejść cyfrowych (czujniki drzwi, zalania, ruchu)  
- 6 wyjść przekaźnikowych 2 A @ 12 V DC  
- czujniki 1-Wire (temperatura/wilgotność) 
- do 4 czytników RS-485 (OSDP)  
- do 4 kamer (snapshot / ANPR)  
- moduł GSM (SMS sterowanie i powiadomienia)  
- serwer HTTP/HTTPS (lokalnie i w chmurze) 
- broadcasting TCP/IP (monitoring zdarzeń w czasie rzeczywistym)

---

## 4. Dashboard i aplikacja NASweb

<img width="1584" alt="Dashboard" src="https://github.com/user-attachments/assets/02bea178-1be1-4528-ada9-543a9612fea4" />  
📷 **Dashboard**

---

## 5. Kontrola dostępu - podstawy

### 5.1. Definicja
Kontrola dostępu decyduje **kto, kiedy i gdzie** ma wejście.  
Zamiast kluczy używane są karty, PIN-y, biometryka czy tablice rejestracyjne.  

### 5.2. Jak działa w NASweb

- użytkownik ma przypisane **identyfikatory** (karta, PIN, nr rejestracyjny)
- operator tworzy **wzorce uprawnień** - przejścia z harmonogramami i warunkami  
- użytkownik może mieć **wiele wzorców** i dodatkowe indywidualne prawa  

#### Dziedziczenie, sumowanie i negacja uprawnień

- System **sumuje uprawnienia (OR)** z wielu wzorców oraz z praw indywidualnych - dzięki temu użytkownik zyskuje **wszystkie** dostępy nadane w którymkolwiek źródle
- **Negacja (odebranie prawa)** działa jak _uprawnienie z odwróconym znakiem_ i **kasuje dostęp**, nawet jeśli został on przyznany w innym miejscu 

- **Priorytety rozstrzygania konfliktów:**   

    1\. **Negacja** > **przyznanie** (negacja wygrywa)  
    2\. **Uprawnienia indywidualne** > **wzorcowe** (prawa indywidualne są nadrzędne)  
    3\. Harmonogram: dostęp jest aktywny, gdy jest aktywny w **co najmniej jednym** źródle (chyba że w tym czasie działa negacja)  

!!! example "Przykład negacji"
    Cała grupa „Pracownicy” ma dostęp do *Serwerowni*, ale jednemu użytkownikowi przypisujesz **indywidualne odebranie** - w efekcie **wszyscy** mają, a **on jeden nie**.

<img width="1180" alt="Edycja użytkownika" src="https://github.com/user-attachments/assets/cc01d60a-d9d2-4656-847d-c98ac232f87a" />  
📷 **Edycja użytkownika**

<img width="1479" alt="Konfiguracja wzorca" src="https://github.com/user-attachments/assets/3cfca29f-a443-4785-95c4-d3eb43f93ed0" />  
📷 **Konfiguracja wzorca uprawnień**

---

## 6. System sygnalizacji włamania (SSWiN)

### 6.1. Definicja
System SSWiN monitoruje czujniki (np. ruch, kontaktron).  
Przy naruszeniu - uruchamia alarm i powiadamia ochronę.  

### 6.2. W NASweb

- wejścia są przypisywane do **stref alarmowych** (np. biuro, magazyn) 
- strefy można uzbrajać/rozbrajać kartą  
- wyjścia sterują syrenami i automatyką 
- integracja z KD: karta rozbraja strefę przy wejściu  

<img width="1424" alt="Konfiguracja wejść" src="https://github.com/user-attachments/assets/b95df204-3a53-49bc-9c1f-cd022b3c3b29" />  
📷 **Konfiguracja wejść**

---

<img width="1345" alt="Konfiguracja stref 1" src="https://github.com/user-attachments/assets/c10dadea-1bf7-447d-9484-ff077551bdb1" />  
📷 **Konfiguracja stref**

<img width="1364" alt="Konfiguracja stref 2" src="https://github.com/user-attachments/assets/375c8b04-1329-4aa5-970d-9492a88bc34d" />  
📷 **Konfiguracja stref (widok szczegółowy)**

---

## 7. Automatyka i HVAC

- czujnik temperatury 1-Wire  
- **trzy stany** z dokładnie **jednym** wyjściem na każdy stan:  

    - poniżej zakresu – (np.) ogrzewanie  
    - w zakresie – (np.) wentylacja  
    - powyżej zakresu – (np.) chłodzenie

!!! warning "Wyjścia"
    **To samo wyjście** może być wskazane w różnych stanach, jeśli tak chcesz.  
    Jeśli potrzebujesz **kilku wyjść jednocześnie** dla danego stanu, użyj **skryptów** lub zewnętrznego sprzęgła.

!!! example "Przykład"
    W strefie *Magazyn* kontroler włącza wentylację w przedziale 20–28 °C.  
    Po przekroczeniu 28 °C steruje wyjściem zdefiniowanym dla stanu „powyżej” (np. chłodzenie).  

<img width="1178" alt="Konfiguracja HVAC" src="https://github.com/user-attachments/assets/9cc6816a-d7f5-4848-abed-ca9bfba9cb13" />  
📷 **Konfiguracja HVAC**

---

## 8. Rejestracja i monitoring wideo

<img width="1238" alt="Kamery / Campics" src="https://github.com/user-attachments/assets/5cba6870-c2ca-4372-b5fe-0f38b9b68e50" />  
📷 **Kamery / Campics**

- powiązanie zdarzeń z obrazami (moduł *Campics*) 
- obsługa kamer **ANPR**  
- filtrowanie i szybka weryfikacja  

---

## 9. Powiadomienia

**Najważniejsze** zdarzenia elementarne (spośród setek dostępnych):  

1. Wejście uprawnione  
2. Wyjście uprawnione  
3. Próba nieuprawniona  
4. Za długo otwarte drzwi  
5. Otworzenie przyciskiem  
6. Alarm w strefie  
7. Rozbrojenie strefy  
8. Sabotaż czytnika  
9. Sabotaż wejścia (czujnika)  
10. Usterka czujki  
11. Naruszenie czujnika  
12. Awaria zasilania AC  
13. Awaria akumulatora  
14. Brak odpowiedzi z serwera  
15. Błędny PIN  

<img width="1266" alt="Powiadomienia 1" src="https://github.com/user-attachments/assets/2d6e72f0-260c-4197-93dd-5eb922a2cfca" />  
📷 **Konfiguracja powiadomień**

<img width="1634" alt="Powiadomienia 2" src="https://github.com/user-attachments/assets/4e862005-9564-4208-9bea-6dcca9b6818e" />  
📷 **Konfiguracja powiadomień (szczegóły)**

---

## 10. Integracja i komunikacja

- synchronizacja z LDAP 
- integracja z haos.app  
- eksport zdarzeń TCP/IP  
- integracja z Home Assistant

---

## 11. Skrypty i logika

Silnik skryptowy (składnia podobna do `JavaScript`): 

- definiowanie reakcji na zdarzenia (np. czujnik → wyjście)  
- logika śluz (door A otworzy się, jeśli B zamknięte)  
- reguły czasowe (np. dostęp po 22:00 tylko z PIN)  
- powiązania między modułami (np. karta + wysterowanie wyjścia)  
- rozszerzenia HVAC (np. równoległe załączanie wielu wyjść dla jednego stanu) 
- niestandardowe scenariusze projektowe bez zewnętrznego programowania

---

## 12. Aplikacje projektowe

- np. posterunek wjazdu/wyjazdu z **ANPR**  
- rejestracja zdjęć załadunku  
- czasowe uprawnienia transportowe  

<img width="1382" alt="Posterunek wjazdu" src="https://github.com/user-attachments/assets/db768285-0aa8-4442-bb9e-d924617de6f9" />  
📷 **Posterunek wjazdu**

---

## 13. Panel administratora

- konfiguracja sieci  
- aktualizacje  
- diagnostyka

---

## 14. Specyfikacja techniczna

| Parametr              | Wartość                                                 |
|-----------------------|---------------------------------------------------------|
| Procesor              | ARM Quad-Core                                           |
| RAM                   | 4 GB                                                    |
| Pamięć wewnętrzna     | 32 GB eMMC                                              |
| Wyświetlacz           | 1,4’’                                                   |
| Przyciski funkcyjne   | 4                                                       |
| Sieć                  | 1× uplink FastEthernet (PoE+), 2× downlink FastEthernet |
| Zasilanie             | 12 VDC + PoE+ (redundancja, praca równoległa)           |
| Obudowa               | Szyna DIN, 10 modułów                                   |
| Terminale             | Rozłączalne bloki                                       |
| USB                   | pamięci i urządzenia USB                                |
| Wyjścia przekaźnikowe | 6× (2 A @ 12 V DC)                                         |
| Wejścia cyfrowe       | 16×                                                     |
| Czytniki              | do 4 (RS-485 OSDP)                                      |
| Kamery                | do 4 (snapshot / ANPR)                                  |
| Wyjście sterujące     | przekaźnik zasilający dla resetu urządzeń               |
| System operacyjny     | Embedded Linux                                          |
| Integracja chmurowa   | VPN do haos.app                                         |
| Home Assistant        | strefy, wejścia, wyjścia, termostat                     |
| Aplikacje dodatkowe   | np. posterunek ANPR                                     |
| OEM/ODM               | personalizacja przy zamówieniach wolumenowych           |
| Warianty              | różne wersje I/O i obudów                               |

!!! info "Redundancja zasilania"
    Dwa niezależne źródła (PoE+ i 12 V DC) mogą pracować równocześnie - odłączenie jednego **nie przerywa pracy**. Przewaga nad pojedynczym zasilaniem: większa niezawodność bez dodatkowych UPS/adapterów w małych instalacjach.

---

## 15. Podsumowanie

!!! quote ""
    **NASwebio** + **NASweb** = kontroler bezpieczeństwa + automatyka + monitoring  

!!! success ""
    Mniejsze koszty, większe bezpieczeństwo, pełna kontrola w jednym panelu.

---

## 16. Wariant haos.app - optymalizacja i ekologia

NASwebio dostępny także jako **haos.app**:  

- pełny kontroler bezpieczeństwa  
- host Home Assistant  
- switch sieciowy  
- redundancja zasilania  
- host automatyki SOHO  

### Zalety

- **all-in-one** w jednej obudowie DIN  
- **oszczędność miejsca** - 1 zamiast 3-4 urządzeń  
- **mniej energii i ciepła** 
- **niższe koszty**  
- **ekologia** - mniej plastiku, metalu, elektroniki  

<img width="1500" alt="HAOS instalacja 1" src="https://github.com/user-attachments/assets/c1a6d8ba-f9d2-4d24-92b4-20bf02450188" />  
📷 **Instalacja NASweb z HAOS**

<img width="1245" alt="HAOS instalacja 2" src="https://github.com/user-attachments/assets/3e15c1bb-6942-46fc-b46c-b39cc66199e9" />  
📷 **NASwebio w wariancie haos.app**

---

## 17. Uwagi końcowe

- Dostępna także wersja wspierająca Tuya  
- Logotypy Tuya i Home Assistant są własnością twórców, użyte wyłącznie poglądowo
