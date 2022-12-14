## Dědičnost

Třídy mají jednu zajímavou vlastnost - mohou od sebe **dědit**. Uvažujme třeba, že bychom chtěli vytvořit novou třídu `Manazer`, která reprezentuje zaměstnance, který má nějaké podřízené. U manažera bychom rádi evidovali počet jeho podřízených. Jinak se samozřejmě manažer od ostatních nijak neliší - má jméno, název pozice i nárok na dovolenou.

Ideální by tedy bylo mít kopii třídy `Zamestnanec`, která bude mít nový atribut `pocet_podrizenych` (seznam jeho podřízených). Samozřejmě bychom mohli kód třídy `Zamestnanec` zkopírovat a upravit, ale díky dědičnosti to můžeme udělat i lépe. Můžeme novou třídu `Manazer` postavit na základě třídy `Zamestnanec`. Třída `Manazer` tak zdědí od třídy `Zamestnanec` všechny atributy a metody, a my jen přidáme nebo upravíme, co potřebujeme.

Napíšeme tedy novou funkci `__init__`, protože potřebujeme vytvořit atribut `pocet_podrizenych`.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice, pocet_podrizenych):
        self.jmeno = jmeno
        self.pozice = pozice
        self.pocet_podrizenych = pocet_podrizenych
        self.pocet_dni_dovolene = 25
```

Zkusíme si nyní vytvořit objekt, který bude reprezentovat manažera. U objektu vyzkoušíme, zda u ní funguje metoda `__str__`. Tuto metodu jsme pro třídu `Manazer` neprogramovali, měla by být *zděděná* od třídy `Zamestnanec`.

```py
boss = Manazer("Marian Přísný", "vedoucí konstrukčního oddělení")
print(boss)
```

Zatím vše funguje, přesto můžeme náš kód ještě vylepšit. Ve funkci `__init__` musíme poněkud nešikovně opisovat tři řádky, které nastavují hodnoty atributů. Přitom ty stejné řádky už jsou v třídě `Zamestnanec`. Mohli bychom nějak existující kód z třídy `Zamestnanec` upravit?

Ve skutečnosti ano. Využijeme k tomu speciální funkci `super()`, kterou se odvoláme na **mateřskou třídu aktuální třídy**. Následně můžeme použít tečku a zavolat funkci `__init__`. Tím tedy voláme funkci `__init()__` mateřské třídy `Zamestnanec`.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice, pocet_podrizenych):
        super().__init__(jmeno, pozice)
        self.pocet_podrizenych = pocet_podrizenych
```

Pojďme ještě upravit výpis informace pomocí metody `__str__`. U třídy `Manazer` budeme chtít do výpisu přidat informaci o tom, kolik má manažer podřízených. Opět můžeme pomocí funkce `super()` zavolat metodu `__str__` z mateřské třídy `Zamestnanec` a připojit k ní větu o počtu podřízených.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice, pocet_podrizenych):
        super().__init__(jmeno, pozice)
        self.pocet_podrizenych = pocet_podrizenych

    def __str__(self):
        return super().__str__() + f" Má {self.pocet_podrizenych} podřízených."
```

Vyzkoušíme znovu dvojici příkazů, kterou jsme zkoušeli předtím.

```py
boss = Manazer("Marian Přísný", "vedoucí konstrukčního oddělení", 5)
print(boss)
```

Výsledkem je text:

```
Marian Přísný pracuje na pozici vedoucí konstrukčního oddělení. Má 5 podřízených.
```

```py

class Zamestnanec:
    def __init__(self, jmeno, pozice):
        self.jmeno = jmeno
        self.pozice = pozice
        self.dovolena = 160

    def __str__(self):
        return f"{self.jmeno} a pracuje na pozici {self.pozice}"

    def cerpej_dovolenou(self, pocet_hodin):
        if self.dovolena >= pocet_hodin:
            self.dovolena -= pocet_hodin
            return "Užij si to."
        else:
            return f"Máš nárok je na {self.dovolena} hodin."


class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice, pocet_podrizenych):
        super().__init__(jmeno, pozice)
        self.pocet_podrizenych = pocet_podrizenych

    def __str__(self):
        text = super().__str__()
        text = text + f" Počet podřízených: {self.pocet_podrizenych}"
        return text


frantisek = Zamestnanec("František Novák", "konstruktér")
klara = Zamestnanec("Klára Nová", "konstruktérka")
marian = Manazer("Marian Přísný", "vedoucí", 2)

print(marian)
```

## Cvičení: Dědičnost
::exc[excs>castecny-uvazek]
::exc[excs>cenny-balik]
