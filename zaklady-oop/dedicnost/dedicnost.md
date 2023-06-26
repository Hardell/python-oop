## Dědičnost

Třídy mají jednu zajímavou vlastnost - mohou od sebe **dědit**. Uvažujme třeba, že bychom chtěli vytvořit novou třídu `Manager`, která reprezentuje zaměstnance, který má nějaké podřízené. U manažera bychom rádi evidovali počet jeho podřízených. Jinak se samozřejmě manažer od ostatních nijak neliší - má jméno, pozici i nárok na dovolenou.

Ideální by tedy bylo mít kopii třídy `Employee`, která bude mít nový atribut `subordinates` (seznam jeho podřízených). Samozřejmě bychom mohli kód třídy `Employee` zkopírovat a upravit, ale díky dědičnosti to můžeme udělat i efektivněji. Můžeme novou třídu `Manager` postavit na základě třídy `Employee`. Třída `Manager` tak zdědí od třídy `Employee` všechny atributy a metody, a my jen přidáme nebo upravíme, co potřebujeme.

Napíšeme tedy novou funkci `__init__`, protože potřebujeme vytvořit atribut `subordinates`.

```py
# Do závorek píšeme, od jaké třídy dědíme
class Manager(Employee):
    def __init__(self, name, position, holiday_entitlement, subordinates):
        self.name = name
        self.position = position
        self._holiday_entitlement = holiday_entitlement
        self.subordinates = subordinates
```

Zkusíme si nyní vytvořit objekt, který bude reprezentovat manažera. U objektu vyzkoušíme, zda u ní funguje metoda `__str__`. Tuto metodu jsme pro třídu `Manager` neprogramovali, měla by být *zděděná* od třídy `Employee`.

```py
boss = Manager("Marian Přísný", "vedoucí konstrukčního oddělení", 25, 2)
print(boss)
```

Zatím vše funguje, přesto můžeme náš kód ještě vylepšit. Ve funkci `__init__` musíme poněkud nešikovně opisovat tři řádky, které nastavují hodnoty atributů. Přitom ty stejné řádky už jsou v třídě `Employee`. Mohli bychom nějak existující kód z třídy `Employee` upravit?

Ve skutečnosti ano. Využijeme k tomu speciální funkci `super()`, kterou se odvoláme na **mateřskou třídu aktuální třídy**. Následně můžeme použít tečku a zavolat funkci `__init__`. Tím tedy voláme funkci `__init()__` mateřské třídy `Employee`.

```py
class Manager(Employee):
    def __init__(self, name, position, holiday_entitlement, subordinates):
        # Volám metodu __init__() mateřské třídy
        super().__init__(name, position)
        self.subordinates = subordinates
```

Pojďme ještě upravit výpis informace pomocí metody `__str__`. U třídy `Manager` budeme chtít do výpisu přidat informaci o tom, kolik má manažer podřízených. Opět můžeme pomocí funkce `super()` zavolat metodu `__str__` z mateřské třídy `Employee` a připojit k ní větu o počtu podřízených.

```py
class Manager(Employee):
    def __init__(self, name, position, holiday_entitlement, subordinates):
        super().__init__(name, position, holiday_entitlement)
        self.subordinates = subordinates

    def __str__(self):
        # Volám metodu __str__() mateřské třídy a k výsledku přidávám další řetězec
        return super().__str__() + f" Má {self.subordinates} podřízených."
```

Vyzkoušíme znovu dvojici příkazů, kterou jsme zkoušeli předtím.

```py
boss = Manager("Marian Přísný", "vedoucí konstrukčního oddělení", 25, 5)
print(boss)
```

Výsledkem je text:

```
Marian Přísný pracuje na pozici vedoucí konstrukčního oddělení. Má 5 podřízených.
```

## Cvičení: Dědičnost

::exc[excs>cenny-balik]
