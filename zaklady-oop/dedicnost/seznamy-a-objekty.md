## Kombinace seznamu a objektů

Pro personální systém firmy ale samotná informace o počtu podřízených zpravidla nebude dostatečná, je naopak potřeba podřízené a manažery přímo propojit. Jen tak bude jasné, za které zaměstnance manažer zodpovídá.

Upravme tedy třídu `Manazer` tím, že namísto atributu `pocet_podrizenych` vložíme seznam `podrizeni`, který bude na začátku prázdný. Dále přidáme metodu `pridej_podrizeneho()`, která vloží nového podřízeného do seznamu `podrizeni`.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice):
        self.jmeno = jmeno
        self.pozice = pozice
        self.pocet_dni_dovolene = 25
        self.podrizeni = []

    def pridej_podrizeneho(self, podrizeny):
        self.podrizeni.append(podrizeny)
```

Náš kód už bychom mohli spustit, ale nemohli bychom pořádně otestovat, že přidávání podřízených funguje. My je totiž ukládáme, ale zatím nemáme funkci pro jejich vypsání. Přidáme tedy funkci `vypis_podrizene`, která vrátí informaci o podřízených manažera.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice):
        super().__init__(jmeno, pozice)
        self.podrizeni = []

    def pridej_podrizeneho(self, novy_podrizeny):
        self.podrizeni.append(novy_podrizeny)

    def vypis_podrizene(self):
        podrizeni = ""
        for item in self.podrizeni:
        podrizeni += item.jmeno + ", "
        return podrizeni
```

Nyní můžeme vše vyzkoušet. Vedoucímu, který je uložený v proměnné `boss`, přiřadíme dva podřízené. Následně si zkusíme proměnné vypsat.

```py
frantisek = Zamestnanec("František Novák", "konstruktér")
klara = Zamestnanec("Klára Nová", "konstruktérka")

boss = Manazer("Marian Přísný", "vedoucí konstrukčního oddělení")
boss.pridej_podrizeneho(frantisek)
boss.pridej_podrizeneho(klara)
print(boss.vypis_podrizene())
```

Náš program tedy vytvoří tři objekty - dva zaměstnance a jednoho manažera. Manažerovi jsme přiřadili zaměstnance jako podřízené. A vidíme, že naše akce proběhla správně, protože tito dva zaměstnanci se objevili ve výpisu podřízených.

Jako poslední můžeme vrátit metodu `__str__`, která zjistí počet podřízených z délky seznamu `podrizeni`.

```py
class Manazer(Zamestnanec):
    def __init__(self, jmeno, pozice):
        super().__init__(jmeno, pozice)
        self.podrizeni = []

    def __str__(self):
        return super().__str__() + f" Má {len(self.podrizeni)} podřízených."

    def pridej_podrizeneho(self, novy_podrizeny):
        self.podrizeni.append(novy_podrizeny)

    def vypis_podrizene(self):
        podrizeni = ""
        for item in self.podrizeni:
        podrizeni += item.jmeno + ", "
        return podrizeni
```

## Kombinace seznamu a objektů
::exc[excs>ridic]
