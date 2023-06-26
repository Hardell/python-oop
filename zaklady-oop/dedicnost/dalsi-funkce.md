## Funkce pro práci s objekty

Často potřebujeme v programu zkontrolovat, zda nějaká funkce je objektem určité třídy. V opačném případě se může stát, že budeme volat metodu, kterou objekt vůbec nemá, protože pochází z jiné třídy, než jsme předpokládali. K tomu slouží funkce `isinstance()`. Ta ověří, zda je objekt založený na nějaké třídě, a vrátí pravdivostní hodnotu. Jako parametry funkce zadáváme objekt a třídu, u které prověřujeme, zda z ní projekt pochází.

Funkce `isinstance()` vrátí hodnnotu `True` i v případě, že objekt pochází z některého z potomků třídy, na které se ptáme. Například pokud bychom kontrolovali, zda objekt `boss` pochází ze třídy `Employee`, výsledkem je opět hodnota `True`.

```python
boss = Manager("Marian Přísný", "vedoucí konstrukčního oddělení", 25, 5)
# Podmínka bude vyhodnocena jako pravda
if isinstance(boss, Manager):
    print("Objekt pochází ze třídy Manager (nebo jejích potomků).")
else:
    print("Objekt nepochází ze třídy Manager (nebo jejích potomků).")

# Podmínka bude vyhodnocena jako pravda (třída Manager dědí od třídy Employee)
if isinstance(boss, Employee):
    print("Objekt pochází ze třídy Employee (nebo jejích potomků).")
else:
    print("Objekt nepochází ze třídy Employee (nebo jejích potomků).")
```

Další funkce je funkce `hasattr()`. Ta nám umožňuje zkontrolovat, zda má nějaký objekt atribut nebo metodu daného jména. Uvažujme například, že máme v proměnné `marketa` uloženou neznámou zaměstnakyni, o které nevíme, z jaké třídy pochází. Pokud bychom chtěli přečíst hodnotu atributu `subordinates`, program skončí chybou, protože tento atribut není k dispozici.

```py
# Tento řádek je na úplně jiném místě programu
marketa = Employee("Markéta Valčíková", "vývojářka", 25)
# Tento řádek skončí chybou - Markéta nemá podřízené
print(marketa.subordinates)
```

Mohli bychom samozřejmě použít metodu `isinstance()`, co když ale máme v naší aplikaci velké možství tříd? V personálním systému můžeme mít například třídy pro zaměstnance, kontraktory, brigádníky, ředitele oddělení, ředitele divize, bývalé zaměstnance, uchazeče o práci, stážisty, členy statutárních orgánů atd. V takovém případě je jednodušší zkontrolovat, zda daná třída nějaký atribut má.

Uvažujme například, že naše firma pořádá školení leadershipu. Naším úkolem je připravit pozvánky, ty ale logicky budeme posílát pouze lidem, kteří mají nějaké podřízené.

```py
marketa = Manager("Markéta Valčíková", "teamleader", 25, 12)
stefan = Employee("Štefan Novák", "lektor")
employee_list = [marketa, stefan]

expected_people = 0

for item in employee_list:
    if hasattr(marketa, "subordinates"):
        # Připravíme si pozvánku
        print(f"Pozvánka pro {item.name} na školení leadershipu.")
        # Započítáme si jednoho člověka navíc
        expected_people = expected_people + 1

print(f"Čekáme {expected_people} osob.")
```

## Cvičení: Dědičnost

::exc[excs>seznam-baliku]

## Bonus

::exc[excs>seznam-baliku-podruhe]
