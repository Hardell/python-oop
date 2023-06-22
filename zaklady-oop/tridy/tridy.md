## Objekty a třídy

Základ objektově orientovaného programování (OOP) je využívání **tříd** a **objektů**.

Objekty mají často reprezentovat nějaké entity v realitě, například právě zaměstnance. Na rozdíl od slovníků nám ale objekty umožní svázat data o zaměstnancích a kód, který slouží ke zpracování těchto dat.

Na začátku si musíme vytvořit **třídu** (`class`). Vztah mezi třídou a objekty si můžeme představit na příkladu formulářů, který na personálním oddělení vyplňují při nástupu do firmy. Třída je prázdný formulář - obsahuje kolonky, které by měly být vyplněny (v našem případě jméno, pozice a nárok na dovolenou). Objekt je pak vyplněný formulář, který už má v sobě nějaká konkrétní data. 

Podobně jako formulářů můžeme vyplnit více, může na základě jedné třídy vzniknout několik objektů. Objekty jsou vzájemně **nezávislé**, takže práce s jedním objektem neovlivňuje ostatní. Analogicky, pokud upravujeme jeden formulář, nijak tím neměníme ostatní. Tento princip se nazývá zapouzdření (encapsulation).

Třídy mají dvě důležité charakteristiky - mají **atributy** (v nich uchováváme hodnoty) a **metody** (vykonávají nějaké příkazy). Atributy jsou podobné hodnotám, které jsme vkládali do našeho slovníku. Podobně jako hodnota ve slovníku má svůj klíč, má i atribut své jmeéno.

Metody jsou obdobou funkci. Každou metodu sice programoujeme pouze jednou (její kód vkládáme do třídy), ale metoda vždy pracuje s daty konkrétního objektu.

Začneme tím, že vytvoříme třídu `Employee`, který reprezentuje zaměstnance. Třída bude mít atributy jméno, pracovní pozici a nárok na dovolenou. Zaměstnanec může mít i metody - například metodu na vybrání dovolené, vytištění výplatní pásky, výpočet věku atd. Název třídy bychom měli začínat vždy **velkým písmenem**.

Před vytvářením objektů je třeba mít připravenou třídu, na základě které objekt vznikne. K tomu použijeme klíčové slovo `class`. Za něj přijde **název třídy** a opět **dvojtečka**. 

Jako první vytvoříme speciální metodu s podivným názvem `__init__()`. Tato metoda se stará o vytvoření objektu a nastavení hodnot jeho atributů. Metoda má čtyři parametry: `self`, `name`, `position` a `holiday_entitlement`. Kromě záhadného `self` jsou to hodnoty, které budeme chtít zadat při vytvoření nového objektu.

K čemu sloučí parametr `self`? S jeho pomocí **přistupujeme k atributům objektu**. Existuje totiž zásadní rozdíl mezi `name` a `self.name`. Zatímco `name` je parametr funkce a po opuštění metody `__init__()` zmizí, `self.name` je atribut objektu, který může být používán ve všech metodách. Naším cílem je uložit jméno, které uživateli zadáme, do atributu, abychom s ním mohli pracovat v ostatních metodách. Proto napíšeme absurdně vypadající řádek `self.name = name`.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self.holiday_entitlement = holiday_entitlement
```

Dále vytvořme třídu jen s jednou metodou `get_info()`, která vypíše informace o zaměstnanci. Protože pracujeme s metodou, můžeme (ale nemusíme) použít klíčové slovo `return` a vrátit nějakou hodnotu.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self.holiday_entitlement = holiday_entitlement
    
    def get_info():
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."
```

Zkusme si nyní vytvořit objekt, který reprezentuje zaměstnance Františka. Objekt vytvoříme podobně, jako bychom volali funkci - použijeme **název třídy** a **kulaté závorky**. Objekt uložíme do proměnné `frantisek`. Dále přiřadíme proměnné `frantisek` hodnoty atributů `jmeno` a `pozice` a vyzkoušíme metodu `get_info`.

```py
frantisek = Employee("František Novák", "konstruktér", 25)
print(frantisek.get_info())
```

Zkusíme přidat ještě jednu zaměstnankyni.

```py
klara = Employee("Klára Nová", "konstruktérka", 25)
```

Nyní vyzkoušíme vypsat informace obou zaměstnanců.

```py
print(frantisek.get_info())
print(klara.get_info())
```

## Cvičení

::exc[excs>balik]

## Bonus

::exc[excs>kniha]
