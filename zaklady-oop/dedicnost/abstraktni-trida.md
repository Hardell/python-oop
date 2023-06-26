## Abstraktní třída

Abstraktní třída má speciální význam v tom, že z ní rovnou **nevytváříme objekty**, je ale šablonou pro třídy, které od ní dědí.

Např. uvažujme program, který počítá obvody a obsahy geometrických obrazců. Začneme vytvořením mateřské třídy `Figure`, která bude mít metody `get_circ()` a `get_area()`. Název metody `get_circ()` vznikl zkrácením příěerného slova circumference.

U neznámého obrazce ale nemá smysl do těchto tříd implementovat výpočet, protože nevíme, jaký vzorec bychom měli použít. Proto vytvoříme třídu `Figure` jako **abstraktní třídu**. To v Pythonu uděláme tak, že jí nastavíme jako mateřskou třídu třídu `ABC` z modulu `abc`. Její metody poté budou též abstraktní. To zařídíme tak, že nad ně vložíme značku `@abstractmethod`. Tato prozvláštní značka se v jazyce Pythonu označuje jako **dekorátor** (`decorator`).

Smyslem abstraktních tříd je být základem pro další třídy. Pokud tedy dva různí členové nebo členky týmu budou přidávat nové třídy pro nové obrazce (např. pro čtverec a obdélník), bude jim jasné, které atributy a metody mají do své třídy přidat.

```python
from abc import ABC, abstractmethod

class Figure(ABC):
    @abstractmethod
    def get_circ():
        pass

    @abstractmethod
    def get_area():
        pass
```

Dále přidáme třídy `Square` a `Rectangle`, které budou dědit od třídy `Figure`. Těmto třídám už můžeme implementovat metody `get_circ()` a `get_area()`, založit na jejich základě objekty a pracovat s nimi.

```python
class Square(Figure):
    def __init__(self, a):
        self.a = a

    def get_circ(self):
        return 4 * self.a

    def get_area(self):
        return self.a * self.a


class Rectangle(Figure):
    def __init__(self, a, b):
        self.a = a
        self.b = b

    def get_circ(self):
        return 2 * (self.a + self.b)

    def get_area(self):
        return self.a * self.b


small_square = Square(10)
large_rectangle = Rectangle(20, 25)
total_area = maly_Square.get_area() + velky_Rectangle.get_area()
print(f"Celková plocha obou obrazců je {plocha_total_areacelkem}.")
```

Pokud bys chtěl(a) vytvořit objekt se třídy `Figure`, Python vrátí chybu "`TypeError: Can't instantiate abstract class Figure with abstract methods get_area, get_circ`". Slovo `instance` označuje pojem "instance objektové třídy", což je jen jiný výraz pro model.

## Cvičení: Abstraktní třídy

::exc[excs>jizdenky-letenky]

### Čtení na doma: Abstraktní třídy a vlastnosti

U našich obrazců máme implementované metody metody `get_circ()` a `get_area()`. Obvod a obsah jsou hodnoty, které jsou pro nějaký obrazec konkrétní velikosti konstantní. Bylo by tedy zajímavé pro ně použít vlastnosti. Jíž víme, že vlastnosti označíme pomocí dekorátoru `@property`. U abstraktní třídy pak použijeme speciální dekorátor `@abstractproperty`.

```python
from abc import ABC, abstractproperty

class Figure(ABC):
    @abstractproperty
    def circ():
        pass

    @abstractproperty
    def area():
        pass

class Square(Figure):
    def __init__(self, a):
        self.a = a

    @property
    def circ(self):
        return 4 * self.a

    @property
    def area(self):
        return self.a * self.a


class Rectangle(Figure):
    def __init__(self, a, b):
        self.a = a
        self.b = b

    @property
    def circ(self):
        return 2 (self.a + self.b)

    @property
    def area(self):
        return self.a * self.b


maly_ctverec = Square(10)
velky_obdelnik = Rectangle(20, 25)
plocha_celkem = maly_ctverec.obsah + velky_obdelnik.obsah
print(f"Celková plocha obou obrazců je {plocha_celkem}.")
```

