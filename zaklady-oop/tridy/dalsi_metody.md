## Další metody

Oproti motivačnímu příkladu stále nemáme vyřešeno "bezpečné" čerpání dovolené. Na to se podíváme nyní. Zkusme nyní naši třídu obohatit o novou metodu - `taky_holiday()`. Budeme hlídat i to, aby zaměstnanec/zaměstnankyně nárok na dovolenou nepřečerpal(a).

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self.holiday_entitlement = holiday_entitlement
    
    def get_info():
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."

    def taky_holiday(self, days):
        if self.holiday_entitlement >= days:
            self.holiday_entitlement -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self.pocet_dni_dovolene} dní."
```

Nyní se podívejme, jak budou vyřizovány Františkovy žádosti o dovolenou.

```py
frantisek = Employee("František Novák", "konstruktér", 25)

print(frantisek.taky_holiday(5))
print(frantisek.taky_holiday(15))
print(frantisek.taky_holiday(10))
```

Pojďme ještě použití naší třídy trochu zjednodušit. Naše třída umí přehledně vypsat informace díky metodě `get_info()`. Třídu ale může používat někdo, kdo si této metody nevšimne a tak intuitivně vyzkouší funkci `print()`.

```python
print(frantisek)
```

Odpovědí bude poněkud záhadný text ve stylu

```python
<__main__.Employee object at 0x00000126F0084850>
```

Funke `print()` se totiž pokusí převést objekt na typ řetězec. Protože naše třída nemá tuto funkci naprogramovanou, použije se standardní formát, který nám říká, že jde o objekt třídy `Employee` a kde je uložený v paměti (což je nám platné jako mrtvému zimník). Místo toho by bylo mnohem užitečnější získat informaci, jak ji máme připravenou v metodě `get_info()`.

Převod na řetězec zařídíme tím, že třídě přidáme metodu `__str__`. Dvě lomítka opět značný zvláštní význam. Ten spočívá v tom, že Python využije tuto metodu vždy, když jej požádáme o převod objektu na řetězec. Můžeme tedy přejmenovat metodu `get_info()` na `__str__`. Výstupem našeho programu pak bude text o tom, jak se zaměstnanec jmenuje a kde pracuje.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self.holiday_entitlement = holiday_entitlement
    
    def __str__():
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."

    def taky_holiday(self, days):
        if self.holiday_entitlement >= days:
            self.holiday_entitlement -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self.pocet_dni_dovolene} dní."

frantisek = Employee("František Novák", "konstruktér", 25)
print(str(frantisek))
```

Tím jsme si ukázali, jak vytvořit třídu, objekty a jak s nimi pracovat.

## Cvičení

::exc[excs>balik-2]

## Bonus

::exc[excs>kniha-2]
::exc[excs>zkusebka]
