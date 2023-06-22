## Funkce pro práci s objekty

Často potřebujeme v programu zkontrolovat, zda nějaká funkce je objektem určité třídy. V opačném případě se může stát, že budeme volat metodu, kterou objekt vůbec nemá, protože pochází z jiné třídy, než jsme předpokládali. K tomu slouží funkce `isinstance()`. Ta ověří, zda je objekt založený na nějaké třídě, a vrátí pravdivostní hodnotu. Jako parametry funkce zadáváme objekt a třídu, u které prověřujeme, zda z ní projekt pochází.

Funkce `isinstance()` vrátí hodnnotu `True` i v případě, že objekt pochází z některého z potomků třídy, na které se ptáme. Například pokud bychom kontrolovali, zda objekt `boss` pochází ze třídy `Employee`, výsledkem je opět hodnota `True`.

```python
boss = Manager("Marian Přísný", "vedoucí konstrukčního oddělení", 25, 5)
if isinstance(boss, Manager):
    print("Objekt pochází ze třídy Manager (nebo jejích potomků).")
else:
    print("Objekt nepochází ze třídy Manager (nebo jejích potomků).")

if isinstance(boss, Employee):
    print("Objekt pochází ze třídy Employee (nebo jejích potomků).")
else:
    print("Objekt nepochází ze třídy Employee (nebo jejích potomků).")
```

