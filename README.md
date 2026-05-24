# Analiza platformy e-commerce-Olist
Kompleksowy projekt analityczny Power BI przedstawiający analizę wyników sprzedaży, zachowań klientów, wydajności sprzedawców oraz procesów logistycznych na bazylijskiej platformie e-commerce Olist. 
</br>
Źródło danych: https://www.kaggle.com/datasets/sangamsharmait/ecommerce-orders-data-analysis



## Opis projektu
Celem dashboardu było zanalizowanie danych brazylisjskiej platformy e-comerce **Olist**.
Projekt obejmuje kompleksową analizę działalności biznesowej marketplace’u z perspektywy:
- wyników sprzedażowych,
- zachowań klientów,
- efektywności produktów i sprzedawców,
- operacji logistycznych i dostaw.
---

# Zbiór danych

Projekt wykorzystuje publiczny **Olist Brazilian E-Commerce Dataset**, zawierający rzeczywiste dane transakcyjne marketplace’u działającego w Brazylii.

W analizie wykorzystano następujące zbiory danych:

- **Orders** – informacje o zamówieniach, statusach, datach zakupu i dostawy
- **Customers** – dane klientów oraz ich lokalizacja
- **Payments** – metody płatności, liczba rat i wartości płatności
- **Products** – informacje o produktach i ich kategoriach
- **Sellers** – dane dotyczące sprzedawców i ich lokalizacji
- **Category Translation Mapping** – tłumaczenie nazw kategorii produktów z portugalskiego na angielski - źródło https://github.com/olist/work-at-olist-data/blob/master/datasets/product_category_name_translation.csv 

---

# Strony dashboardu

## 1. Executive Overview

Strona przedstawia najważniejsze wskaźniki biznesowe w formie szybkiego podsumowania wyników działalności.

Zawiera kluczowe KPI:

- **Całkowity przychód - Revenue**
- **Liczba zamówień - Orders**
- **Średnia wartość zamówienia (Average Order Value)**
Dodatkowo pokazuje kwartalny trend przychodów, co pozwala obserwować rozwój biznesu w czasie. Klikając na ikonę filtrów, użytkownik może szczegółowo zobaczyć jak wyglądał przychód w danym roku.
### Wartość biznesowa
Sekcja ta pozwala zobaczyć ogólny zarys przychodów, oraz przenalizować który kwartał zapewnił największy przychód.

---

## 2. Product & Sales Analysis

Strona skupia się na analizie wyników sprzedażowych produktów jak i efektywności sprzedawców.

Zawiera:

- **Top 5 kategorii pod względem sumarycznego przychodu - Top Product Categories by Product Revenue**
- **Top 5 miast pod wzlędem przychodu - Top Seller Cities by Product Revenue**
- **Informacja o strukturze przychodu - Revenue Structure**
- **Top 5 kategorii pod względem średniego przychodu - Top 5 Highest Average Product Price by Category**

Przeprowadzono transformację danych polegającą na tłumaczeniu kategorii produktów z portugalskiego na język angielski 

### Wartość biznesowa

Analiza pozwala zidentyfikować najbardziej opłacalne segmenty produktowe, najsilniejsze lokalizacje sprzedawców oraz relację między przychodem a kosztami logistycznymi. Może wspierać decyzje dotyczące strategii cenowej, asortymentu i współpracy ze sprzedawcami.

---

## 3. Customer Analysis

Strona koncentruje się na analizie zachowań klientów.

Zawiera:

- **Top 5 miast z których osiągnięto największy przychód - Top 5 Cities with the Highest Revenue**
- **Średnia wartość zamówienia - Average Order Value**
- **Liczba unikalnych klientów - Unique Customers**
- **Sposób płatności - Payment Method Share**
- **średnia wartość zamówienia w zależności od liczby rat - Average Order Value by Payment Installments**


### Wartość biznesowa

Analiza pozwala zrozumieć koncentrację klientów geograficznie, dominujące metody płatności - karta kredytowa oraz zależność między zakupami ratalnymi a wartością zamówień. 
Wspiera segmentację klientów i optymalizację strategii płatności.

---

## 4. Operations Analysis

Strona skupia się na analizie efektywności operacyjnej i procesów logistycznych.

Zawiera:

- **Procentowy sukces dostaw - Delivery Success Rate**
- **Średnia ilość dni dostawy szybszej niż zakładane -  Number of average days earlier Than estimate**
- **Dostarczone zamówienia - Delivered Orders**
- **Średni czas dostawy - Average Delivery Time**
- **Dostawy na kwartał - Delivered Orders per Quarter**
- **Informacje o niedostarczonych dostawach - Statistics of not dedlivered orders**

Zamiast analizować wyłącznie sukces dostaw, dashboard uwzględnia także analizę przypadków problematycznych.

### Wartość biznesowa

Analiza wspiera monitorowanie jakości operacyjnej, identyfikację problemów logistycznych i ocenę efektywności dostaw. Szczególnie przydatna do wykrywania obszarów wymagających usprawnienia.
Analiza podkreśla także wysoką efektywność dostaw, szybszy czas dostawy niż zakładany oraz procentowy sukces dostaw.  





## Utworzone miary
W projekcie utworzono dedykowany folder **_Measures**, zawierający własne miary biznesowe wykorzystywane w dashboardzie.
- **Total Revenue**  
  Oblicza całkowity przychód na podstawie wszystkich płatności klientów.

- **Total Orders**  
  Zlicza całkowitą liczbę zamówień.

- **Average Order Value**  
  Oblicza średnią wartość pojedynczego zamówienia.

- **Unique Customers**  
  Zlicza unikalnych klientów w zbiorze danych.

- **Delivered Orders**  
  Zlicza zamówienia zakończone sukcesem.

- **Delivery Success Rate**  
  Oblicza procent zamówień zakończonych dostarczeniem względem wszystkich zamówień.

- **Avg Delivery Days**  
  Oblicza średni czas dostawy od momentu zakupu do dostarczenia.

- **Days Early**  
  Oblicza średnią liczbę dni, o które zamówienie dotarło przed deklarowanym terminem.

- **Avg Delivery Delay**  
  Miara wspierająca analizę opóźnień logistycznych.

- **Non Delivered**  
  Zlicza wszystkie zamówienia, które nie zostały skutecznie dostarczone.

- **Total Revenue Text**  
  Miara pomocnicza służąca do niestandardowego formatowania KPI.

## Przykładowa miara DAX

```DAX
Delivery Success Rate =
DIVIDE(
    [Delivered Orders],
    [Total Orders],
    0
)
```

Powyższa miara oblicza procent zamówień zakończonych sukcesem i jest wykorzystywana jako kluczowy wskaźnik efektywności operacyjnej.


# Dodatkowo zaimplementowane funkcjonalności

## Interaktywna nawigacja
Dashboard posiada własny system nawigacji oparty na przyciskach i bookmarkach, umożliwiający wygodne przechodzenie między sekcjami:

- Executive Overview
- Product & Sales Analysis
- Customer Analysis
- Operations Analysis

---

## Dynamiczne przełączanie filtrów (Filters ON / OFF)
Za pomocą bookmarków zaimplementowano możliwość dynamicznego pokazywania i ukrywania panelu filtrów.

Dzięki temu dashboard:

- pozostaje czytelny,
- zapewnia lepszy UX,
- umożliwia szybki dostęp do filtrów tylko wtedy, gdy są potrzebne.

---

## Selektywne działanie slicerów
Skonfigurowano interakcje między filtrami a wizualizacjami.

Przykłady:

- filtr **Payment Type** wpływa wyłącznie na sekcję Customer Analysis,
- filtr **Year** wpływa tylko na wybrane wykresy operacyjne,
- filtr **Order Status** steruje wyłącznie analizą non-delivered orders.

Zapobiega to przypadkowemu filtrowaniu całego dashboardu.

---

## Transformacje danych w Power Query
W projekcie wykonano dodatkowe transformacje danych:
- tłumaczenie kategorii produktów z portugalskiego na angielski,
- merge tabel,
- uzupełnianie brakujących kategorii jako **Non Category**,
- przygotowanie danych pod analizę logistyczną,
- formatowanie danych liczbowych,
- zduplikowane kategorie produktów (np. warianty oznaczone sufiksem _2) zostały scalone w jedną kategorię w celu poprawy spójności danych i czytelności analizy.
---



## Accessibility
Dashboard uwzględnia elementy poprawiające dostępność:

- alternatywne opisy wizualizacji (Alt Text),
- logiczny układ stron,
- czytelne tytuły wykresów,
- spójną strukturę dashboardu.

---

# Technologie

Projekt został wykonany z wykorzystaniem:

- Power BI
- Power Query
- DAX
- Data Modeling
- Bookmark Navigation
- Interactive Slicers
- Accessibility Features

---

# Umiejętności zaprezentowane w projekcie

Projekt pokazuje praktyczne wykorzystanie umiejętności takich jak:

- analiza biznesowa,
- modelowanie danych,
- transformacja danych,
- tworzenie miar DAX,
- projektowanie dashboardów BI,
- storytelling danych,
- analiza klientów,
- analiza operacyjna,
- analiza sprzedaży,
- UX dashboard design,
- interaktywne raportowanie.

---

# Raport

# Kluczowe insighty biznesowe

- Karty kredytowe stanowią dominującą metodę płatności klientów.
- Niewielka liczba miast generuje znaczną część przychodów.
- Przychód produktowy znacząco przewyższa koszty dostawy.
- Delivery success rate przekracza 97%
- Czas dostaw jest szybszy niż zakładany.
- Większość problematycznych dostaw utyka na etapie wysyłki (status shipped), anulowania (canceled) lub jest niedostępne (unavailable).
- Jest korelacja między liczną rat a wartością zamówienia, czyli wyższa liczba rat wpływa na  większą wartością zamówienia.
