---
title: Balík
demand: 3
---

Uvažuj, že navrhuješ software pro zásilkovou společnost.

- Vytvoř třídu `Package`, která bude mít tři atributy - `address`, `weight` a `state`. Vytvoř metodu `__init__`, která uloží hodnoty parametrů metody do atributů.
- Přidej metodu `get_info()`, která vrátí informace o balíku jao řetězec. Uvažuj například větu "Balík na adresu Václavské Náměstí 12, Praha má hmotnost 0.25 kg je je ve stavu nedoručen".
- Zkus si vytvořit alespoň dva objekty ze třídy `Balik`. U `address` uvažujeme typ řetězec (`str`), u `weight` desetinné číslo. U atributu `state` zadávej pro zjednodušení pouze dva stavy: `doručen` a `nedoručen`.
- Vypiš informace, které generuje metoda `get_info()`, na obrazovku, a ověř, že je vše v pořádku.
