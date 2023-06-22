---
title: Balík podruhé
demand: 3
---

Vrať se k návrhu software pro zásilkovou společnost.

- U třídy `Package` přejmenuj metodu `get_info()` na `__str__()` a vyzkoušej, jestli nyní stačí k získání informací o balíku funkce `print()`.
- Přidej metodu `deliver()`. Půjde o obdobu tlačítka, které řidič nebo řidička zmáčkne při doručení balíku a zaznamená tak jeho doručení. Metoda nejprve zkontroluje, zda balík náhodou již není ve stavu `doručen`. Pokud ano, metoda vrátí zprávu "Balík již byl doručen". Tím bude řidič (řidička) informován(a) o tom, že se pravděpodobně spletl(a) a snaží se zaznamenat doručení u špatného balíku. Pokud balík není ve stavu `doručen`, změň jeho stav právě na `doručen` a vrať zprávu "Doručení uloženo".
- Vyzkoušej metodu `deliver()`. Co se stane, pokud ji u jednoho balíku zavoláš dvakrát?
