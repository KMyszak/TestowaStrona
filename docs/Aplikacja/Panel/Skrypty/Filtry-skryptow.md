# Filtry skryptów

Zakładka **Filtry skryptów** umożliwia definiowanie reguł (*wyzwalaczy*), które uruchamiają wybrane skrypty w&nbsp;reakcji na określone zdarzenia w systemie.

Dzięki filtrom można automatyzować działanie kontrolera - np. wykonywać skrypt przy zmianie stanu wejścia, aktywacji wyjścia lub wystąpieniu konkretnego zdarzenia systemowego.

<img width="890" alt="obraz" src="https://github.com/user-attachments/assets/85dc6729-1af1-4580-9fb4-136f6e829e47" />

### Dostępne pola

- **String** - numer **wejścia** lub **wyjścia** przypisanego do wyzwalacza (wartość `0` jest zarezerwowana dla samego kontrolera)
- **Typ** - rodzaj źródła wyzwalacza: wejście, wyjście lub kontroler
- **Akcja** - określa, co powoduje uruchomienie wyzwalacza (np. zmiana stanu wejścia, aktywacja wyjścia, zdarzenie z kontrolera)
- **Plik skryptu** - skrypt wykonywany po wywołaniu wyzwalacza

---

## Czytnik	  
	
#### `newPin`  

**Wyzwalanie:** wprowadzenie PIN przez użytkownika na klawiaturze czytnika   
**Zastosowanie:** weryfikacja kodów, otwarcia stref, zapisy do logów

#### `newCard`  

**Wyzwalanie:** odczyt karty przez czytnik   
**Zastosowanie:** kontrola dostępu, autoryzacja, rejestracja czasu pracy 

#### `newOnlineEvent`   

**Wyzwalanie:** czytnik zgłosił się lub odzyskał komunikację  
**Zastosowanie:** monitoring stanu urządzeń, powiadomienia      

#### `newOfflineEvent`  

**Wyzwalanie:** czytnik przeszedł w tryb offline lub utrata komunikacji     
**Zastosowanie:** alerty, diagnostyka, watchdog  

---

## Kontroler

#### `newLog`  

**Wyzwalanie:** wygenerowanie nowego zdarzenia systemowego przez kontroler  
**Zastosowanie:** centralny system logów, raportowanie, wyzwalanie automatyzacji    

#### `clientConn`  

**Wyzwalanie:** nowy klient (aplikacja/serwer) połączył się z kontrolerem   
**Zastosowanie:** monitorowanie połączeń, diagnostyka, integracje    

#### `clientDisConn` 

**Wyzwalanie:** klient rozłączył się z kontrolerem   
**Zastosowanie:** monitorowanie utraty komunikacji z aplikacją nadrzędną  

---

## Wejście		

#### `newState`     

**Wyzwalanie:** zmiana stanu wejścia cyfrowego (np. czujnik, styk, sabotaż, krańcówka)   
**Zastosowanie:** alarmy, powiadomienia, akcje zależne od stanu czujników   
