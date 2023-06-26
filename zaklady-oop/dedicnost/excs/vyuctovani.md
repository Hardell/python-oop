---
title: Celkova cena
demand: 3
---

Uvažujme nyní, že chceme nabízet možnost koupit si dohromady jízdenky na vlak i letenky a naším úkolem je spočítat celkovou cenu. Vytovř si seznam `tickets`, kam vlož alespoň jednu letenku a jednu jízdenku na vlak. Dále vytvoř cyklus, který všechny položky v seznamu projde a vypočítá celkovou cenu.

Pokud bys chtěl(a) mít kód bezpečný, můžeš využít funkci `isinstance()`, která zkontroluje, zda se do seznamu nepřipletlo něco, co tam nemá být. Než použiješ metodu `total_price()`, zkontroluj pomocí `isinstance()`, zda aktuální objekt pochází ze třídy, která dědí od třídy `Ticket`. Zamysli se také nad tím, zda by bylo možné využít funkci `hasattr()`.
