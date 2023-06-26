---
title: Jízdenky a letenky
demand: 3
---

Nyní je naším cílem práce pro společnost, která se zabývá prodejem jízdenek a letenek. Uvažujeme možnost koupit si lístek na vlak a letenku.

- Vytvoř abstraktní třídu `Ticket`, která bude mít atributy `basic_price` (základní cena bez služeb) a `fare_class` (třída, kterou cestující letí, uvažujeme možnosti `economy` a `business`). Dále vytvoř abstraktní metodu `total_price()` (celková cena).
- Vytvoř třídu `TrainTicket`, která bude dědit od abstraktní třídy `Ticket`. Naprogramuj metodu `total_price()`, která bude vracet hodnotu stejnou jako `basic_price`, pokud atribut `fare_class` je `economy`, a cenu o 20 % vyšší oproti `basic_price`, pokud `fare_class` je `business`.
- Dále vytvoř třídu `PlaneTicket`, která bude mít navíc atribut `checkout_luggages`, který udává počet odbavených zavazadel. Naprogramuj metodu `total_price()`, která bude vracet hodnotu stejnou jako `basic_price`, pokud atribut `fare_class` je `economy`, a cenu o 50 % vyšší oproti `basic_price`, pokud `fare_class` je `business`. Dále připočti 2000 za každé odbavené zavazadlo (bez ohledu na třídu).
- Zkus vytvořit objekt na základě třídy `Ticket`. Vidíš podobnou chybu, jaká byla v lekci?
- Vytvoř jízdenku na vlak se základní cenou 150 do tříd `economy` i `business`. Zkontroluj, jakou hodnotu vrací metoda `total_price()`.
- Vytvoř letenku se základní cenou 6000 do tříd `economy` i `business` s jedním odbaveným zavazadlem. Zkontroluj, jakou hodnotu vrací metoda `total_price()`.