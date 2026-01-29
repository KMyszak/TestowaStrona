Panel 


<img width="890" alt="obraz" src="https://github.com/user-attachments/assets/85dc6729-1af1-4580-9fb4-136f6e829e47" />

- **String** - 
- **Typ** - 
- **Akcja** - 
- **Plik skryptu** -

## CZYTNIK	  
	
`newPin`  
**Wyzwalanie:** użytkownik wprowadzi PIN na klawiaturze czytnika    
**Zastosowanie:** weryfikacja kodów, otwarcia stref, zapisy do logów

`newCard`  
**Wyzwalanie:** odczyt karty przez czytnik   
**Zastosowanie:** wejścia, autoryzacja, rejestracja czasu  

`newOnlineEvent`     
**Wyzwalanie:** czytnik właśnie się zgłosił / odzyskał komunikację  
**Zastosowanie:** monitoring stanu urządzeń, powiadomienia      

`newOfflineEvent`   
**Wyzwalanie:** czytnik przeszedł w tryb offline / utrata komunikacji     
**Zastosowanie:** alerty, diagnostyka, watchdog  

## KONTROLER

`newLog`  
**Wyzwalanie:** kontroler wygenerował nowe zdarzenie systemowe    
**Zastosowanie:** centralny system logów, raportowanie, wyzwalanie automatyzacji    

`clientConn`  
**Wyzwalanie:** nowy klient (aplikacja/serwer) połączył się z kontrolerem   
**Zastosowanie:** monitorowanie połączeń, diagnostyka, integracje    

`clientDisConn`  
**Wyzwalanie:** klient rozłączył się z kontrolerem   
**Zastosowanie:** monitorowanie utraty komunikacji z aplikacją nadrzędną  

## WEJŚCIE		

`newState`     
**Wyzwalanie:** zmiana stanu wejścia cyfrowego (np. czujnik, styk, sabotaż, krańcówka)   
**Zastosowanie:** alarmy, powiadomienia, akcje zależne od czujników   
