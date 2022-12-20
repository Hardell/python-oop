## Čtení na doma - datové třídy

Obsah metody `__init__` je příklad `boilerplate code`. Název se odkazuje na kovové štítky, které jsou umístěny na bojlerech. V programování to znamená kód, který se často opakuje bez nějakých velkých změn.

V Pythonu ve verzi 3.7 přibyly datové třídy (`dataclass`), které si obsah metody vytvoří samy. Do datové třídy pouze napíšeme seznam jejích atributů spolu s jejich typy hodnot. Můžeme přidat i výchozí hodnotu, jak je vidět u atributu `pocet_dni_dovolene`

```py
from dataclasses import dataclass

@dataclass
class Zamestnanec:
    jmeno: str
    pozice: str
    pocet_dni_dovolene: int = 25

    def cerpani_dovolene(self, days):
        if self.pocet_dni_dovolene >= days:
            self.pocet_dni_dovolene -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self.pocet_dni_dovolene} dní."

    def vypis_informace(self):
        return f"{self.jmeno} pracuje na pozici {self.pozice}."

frantisek = Zamestnanec("František Novák", "konstruktér")
print(frantisek.cerpani_dovolene(5))
print(frantisek.cerpani_dovolene(15))
print(frantisek.cerpani_dovolene(10))
```

Více o datových třídách najdeš v [v dokumentaci](https://docs.python.org/3/library/dataclasses.html).
