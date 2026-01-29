**Format karty** - sposób zakodowania danych na karcie dotępu:

**H10301**    
  **Najpopularniejszy** format zawierający numer obiektu (facility code) i numer karty

  - **Ilość bitów:** 26
  - **Bity Prefixu:** 2-9
  - **Bity Numeru:** 10-25

**H10302**  
  **Bardzo duży** zakres numerów kart (bez kodu obiektu) - kontroler identyfikuje kartę **wyłącznie po numerze**

  - **Ilość bitów:** 37
  - **Bity Prefixu:** brak
  - **Bity Numeru:** 2-36

**H10304**   
  **Rozszerzona** wersja dla większej liczby pracowników i wielu obiektów

  - **Ilość bitów:** 37
  - **Bity Prefixu:** 2-17
  - **Bity Numeru:** 18-36

**dodatkowe**   
Umożliwia **pełną** konfigurację karty

  - **Nazwa**
  - **Ilość bitów**
  - **Bity Prefixu**
  - **Bity Numeru**

!!! note "Phasellus posuere in sem ut cursus"

    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla et euismod
    nulla. Curabitur feugiat, tortor non consequat finibus, justo purus auctor
    massa, nec semper lorem quam in massa.


!!! warning "Uwaga"

    To jest tekst ostrzegawczy.
    Może zawierać **formatowanie**, listy, a nawet kod:

    - punkt 1
    - punkt 2

---
