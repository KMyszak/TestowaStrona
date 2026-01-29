## Panel powiadomień

System pozwala skonfigurować do **150 niezależnych powiadomień**, które uruchamiają się po wystąpieniu wybranych zdarzeń (np. alarm, usterka, sabotaż, zdarzenia SSWiN, zdarzenia kontroli dostępu). Każde powiadomienie może mieć **inny typ**, **odbiorców** oraz **sposób wysyłki** (SMS, e-mail, zdjęcia z kamer, zdarzenia w aplikacji).

Sekcja metod wysyłki jest wspólna dla wszystkich typów powiadomień.
Każde powiadomienie może korzystać z dowolnej kombinacji kanałów:

- **SMS**
- **E-mail**
- **KAM1 / KAM2**
- **APK** (powiadomienie aplikacji)

Zmienia się tylko **szablon** oraz **warunek wyzwolenia**, ale dostępne kanały powiadamiania są identyczne:

<img width="600" alt="obraz" src="https://github.com/user-attachments/assets/7c45b4dc-dedd-4788-9884-fdb4100c8e58" />


## Format powiadomienia

Każde powiadomienie składa się z trzech elementów:

### Typ zdarzenia <img width="320" align="right" alt="obraz" src="https://github.com/user-attachments/assets/5e5066e7-1147-494c-b0a7-db0a968c6d21" />


Określa, na jaki rodzaj sytuacji zareaguje system.
Typ może dotyczyć m.in.:

- wejścia / wyjścia kartą
- błędu czytnika
- alarmu SSWiN
- sabotażu
- usterki
- próby dostępu
- naruszenia czujek

Każdy typ ma własne szczegóły i wyzwalacze.

### Szablon 

Szablon decyduje o treści oraz formie powiadomienia.

W zależności od typu, szablon może zawierać:
<img width="320" align="right" alt="obraz" src="https://github.com/user-attachments/assets/547a905c-fa58-4829-95d9-f0cc1bad027d" />

- nazwę szablonu
- wybrany czytnik
- dane karty (prefix, numer, liczbę bitów)
- użytkowników
- numer telefonu
- adres e-mail

Szablony są różne, ponieważ różne zdarzenia wymagają innych danych.

### Odbiorcy i metody wysyłki

Do powiadomień można przypisać:

- użytkowników
- numery telefonów (SMS)
- adresy e-mail
- powiadomienia push
- zdjęcia z kamer (KAM1 / KAM2)
- treść tekstową

Każde powiadomienie może mieć własnych odbiorców i własne kanały wysyłki.
