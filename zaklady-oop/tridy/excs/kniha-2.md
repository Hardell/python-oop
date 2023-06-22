---
title: Kniha podruhé
demand: 4
---

Vrať se k práci se třídou `Book`. Pokud jsi ji nestihl(a) v minulé části vytvořit, vrať se nejprve k zadání příkladu na předchozí stránce a třídu si vytvoř.

- U knihy budeme chtít evidovat, kolik kusů bylo prodáno. Přidej atribut `sold`, jehož hodnotu bude možné nastavit v metodě `__init__()`. Dále přidej atribut `costs`, které představují náklady na jednu knihu (např. tisk, doprava do knihkupectví, podíl autora(autorky) atd.).
- Přidej metodu `profit()`, která vrátí celkový zisk z knihy. Zisk vypočti na základě vzorce: prodané kusy * (cena - náklady).
- Přidej metodu `rating()`, která vrátí hodnocení knihy na základě jejího zisku. Pokud bude zisk méně než 50 tisíc, vrať hodnotu "propadák". Pokud bude zisk mezi 50 tisíc a 500 tisíc, vrať hodnotu "průměr". Pokud bude vyšší než 500 tisíc, vrať hodnotu "úspěch".
