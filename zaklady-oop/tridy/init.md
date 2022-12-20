## Metoda `__init__`

Z výpisů vidíme, že se informace zaměstnanců nijak nepomíchaly a každý zaměstnanec má uložené své vlastní údaje.

Tento postup ale působí lehce chaoticky. V naší analogii s formuláři to vypadá, že si každý může do formuláře vyplnit, co chce. Abychom měli objekt více pod kontrolou, můžeme využít metodu `__init__` (název zapisujeme včetně podtržítek). Tato metoda je speciální v tom, že je **zavolána při vytvoření objektu**. Můžeme jí (jako jakékoli jiné metodě) přiřadit parametry a zajistit, aby hodnoty parametrů uložila jako atributy objektu.

```py
class Zamestnanec:
    def __init__(self, jmeno, pozice):
        self.jmeno = jmeno
        self.pozice = pozice

    def vypis_informace(self):
        return f"{self.jmeno} pracuje na pozici {self.pozice}."
```

Tento styl je standardní - parametry jsou pojmenované stejně jako atributy objektu, kam se jejich hodnoty ukládají. Mezi `self.jmeno` a `jmeno` je důležitý rozdíl:

- `jmeno` je parametr metody `__init__` a jeho hodnota **není přístupná** pro ostatní funkce objektu.
- `self.jmeno` je atribut objektu, který v objektu **zůstane** a můžou s ním pracovat ostatní metody.

Díky metodě `__init__` máme zjednodušené vytváření objektu, protože hodnoty parametrů nyní vepíšeme přímo do závorek při vytváření objektu.

```py
frantisek = Zamestnanec("František Novák", "konstruktér")
klara = Zamestnanec("Klára Nová", "svářeč")

print(frantisek.vypis_informace())
print(klara.vypis_informace())
```

Nyní již víme, že každý objekt třídy `Zamestnanec` má vyplněné jméno a pozici. Zkusme nyní naši třídu obohatit o novou metodu - čerpání dovolené. Na začátku bude mít každý zaměstnanec nárok na dovolenou, kterou může v průběhu roku čerpat. Čerpání zajistíme pomocí metody `cerpani_dovolene`. Budeme hlídat i to, aby zaměstnanec nárok na dovolenou nepřečerpal.

```py
class Zamestnanec:
    def __init__(self, jmeno, pozice):
        self.jmeno = jmeno
        self.pozice = pozice
        self.pocet_dni_dovolene = 25

    def vypis_informace(self):
        return f"{self.jmeno} pracuje na pozici {self.pozice}."

    def cerpani_dovolene(self, days):
        if self.pocet_dni_dovolene >= days:
            self.pocet_dni_dovolene -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self.pocet_dni_dovolene} dní."
```

Nyní se podívejme, jak budou vyřizovány Františkovy žádosti o dovolenou.

```py
frantisek = Zamestnanec("František Novák", "konstruktér")

print(frantisek.cerpani_dovolene(5))
print(frantisek.cerpani_dovolene(15))
print(frantisek.cerpani_dovolene(10))
```
