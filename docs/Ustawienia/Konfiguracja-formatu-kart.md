# Konfiguracja formatu kart

## Format karty 

**Format karty** określa sposób rozmieszczenia i interpretacji bitów zakodowanych na karcie dostępu.  
Aplikacja umożliwia wybór trzech popularnych formatów standardu **Wiegand** oraz przygotowanie **własnego, w pełni konfigurowalnego** schematu kodowania.

<div class="grid cards" markdown>

- __H10301__

    ---

    Najpopularniejszy format zawierający kod obiektu (*facility code*) i numer karty.

    ---

    - **Liczba bitów:** 26  
    - **Bity Prefixu:** 2–9  
    - **Bity Numeru:** 10–25

    ---


- __H10302__

    ---

    Bardzo duży zakres numerów kart, bez kodu obiektu (*facility code*).

    ---

    - **Liczba bitów:** 37  
    - **Bity Prefixu:** brak  
    - **Bity Numeru:** 2–36

    ---

- __H10304__

    ---

    Rozszerzona wersja dla większej liczby pracowników i wielu obiektów.

    ---

    - **Liczba bitów:** 37  
    - **Bity Prefixu:** 2–17  
    - **Bity Numeru:** 18–36

    ---

- __Dodatkowe__

    ---

    Umożliwia **pełną** konfigurację karty.

    ---

    - **Nazwa**  
    - **Liczba bitów**  
    - **Bity Prefixu**  
    - **Bity Numeru**

    ---

</div>
