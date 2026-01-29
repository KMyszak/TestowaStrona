## Ustawienia skrzynki pocztowej

Konfiguracja serwera **SMTP**, który służy do wysyłania wiadomości **e-mail** przez system, najczęściej **automatycznie**, bez udziału użytkownika.

## Do czego w systemie używany jest e-mail?

### Powiadomienia o zdarzeniach

System może wysyłać e-maile w reakcji na określone sytuacje, np.:

- alarm SSWiN
- naruszenie wejścia
- awaria urządzenia
- restart systemu
- utrata łączności 
- błędy krytyczne
<img width="450" align="right" alt="obraz" src="https://github.com/user-attachments/assets/47af9a4d-49ab-4590-9a05-2a0d40cde886" />

E-mail trafia do administratora / ochrony / serwisu.

- **Użytkownik** - nazwa użytkownika
- **Hasło** - hasło do konta
- **Server** - adres serwera SMTP
- **Port** - port serwera SMTP
- **TLS/LSS** - opcja szyfrowania

### Powiadomienia użytkowników

W systemach z kontami użytkowników e-mail bywa używany do:

- wysyłania informacji o zdarzeniach przypisanych do użytkownika
- resetu hasła
- powiadomień systemowych
- raportów okresowych

### Raporty i logi

System może okresowo wysyłać:

- raporty zdarzeń
- raporty alarmów
- podsumowania dzienne / tygodniowe
- logi techniczne

### Integracja z innymi systemami

Czasem e-mail pełni rolę najprostszej integracji, np.:

- wysłanie alarmu do systemu ticketowego
- przekazanie informacji do zewnętrznego operatora
- archiwizacja zdarzeń na skrzynce pocztowej

