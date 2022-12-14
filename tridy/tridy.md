## Objekty a třídy

Dalším konceptem, se kterým se v tomto kurzu seznámíme, jsou objekty (`objects`). Na objektech je založeno **objektově orientované programování** (Object-oriented programming - OOP), tedy princip psaní programů, ve kterém jsou bloky kódu poskládané do **tříd** a **objektů**.

Objekty mají často reprezentovat nějaké entity v realitě. Pokud bychom například vyvíjeli administrativní software pro firmy, vytvoříme tam objekty reprezentující zaměstnance, pracoviště, firemní automobily atd. U zásilkové společnosti bychom vytvářeli objekty, které reprezentují balíky, řidiče atd.

Na začátku si musíme vytvořit **třídu** (`class`). Vztah mezi třídou a objekty si můžeme představit na příkladu formulářů. Třída je prázdný formulář - obsahuje kolonky, které by měly být vyplněny. Objekt je pak vyplněný formulář, který už má v sobě nějaká konkrétní data. Podobně jako formulářů můžeme vyplnit více, může na základě jedné třídy vzniknout několik objektů. Objekty jsou vzájemně **nezávislé**, takže práce s jedním objektem neovlivňuje ostatní. Analogicky, pokud upravujeme jeden formulář, nijak tím neměníme ostatní.

Třídy mají dvě důležité charakteristiky - mají **atributy** (v nich uchováváme hodnoty) a **metody** (vykonávají nějaké příkazy). Atributy jsou vlastně proměnné, pouze jsou navázané na konkrétní objekt. Funkce jsme poznali v předchozí kapitole, metody jsou pak funkce navázané na konkrétní objekt a pracují s jeho atributy.

Popišme si konkrétně náš příklad software pro firmy. V něm můžeme mít například třídu `Zamestnanec`, který reprezentuje zaměstnance. Třída může mít jméno, pracovní pozici, oddělení, plat, zbývající dny dovolené atd. Zaměstnanec může mít i metody - například metodu na vybrání dovolené, vytištění výplatní pásky, výpočet věku atd. Název třídy bychom měli začínat vždy **velkým písmenem**.

Před vytvářením objektů je třeba mít připravenou třídu, na základě které objekt vznikne. K tomu použijeme klíčové slovo `class`. Za něj přijde **název třídy** a opět **dvojtečka**. Pro začátek si vytvořme třídu jen s jednou metodou `vypis_informace`, která vypíše informace o zaměstnanci.

Všimni si parametru `self` u metody. Pomocí `self` se **odkazujeme na atributy objektu**. Pokud chceme získat hodnotu atributu, napíšeme klíčové slovo `self`, **tečku** a **název atributu**. Tečky při práci s objekty používáme velmi často a jsou jakousi analogií k hranatým závorkám u sekvencí.

```py
class Zamestnanec:
    def vypis_informace(self):
        return f"{self.jmeno} pracuje na pozici {self.pozice}."
```

Protože pracujeme s metodou, můžeme (ale nemusíme) použít klíčové slovo `return` a vrátit nějakou hodnotu.

Zkusme si nyní vytvořit objekt, který reprezentuje zaměstnance Františka. Objekt vytvoříme podobně, jako bychom volali funkci - použijeme **název třídy** a **kulaté závorky**. Objekt uložíme do proměnné `frantisek`. Dále přiřadíme proměnné `frantisek` hodnoty atributů `jmeno` a `pozice` a vyzkoušíme metodu `vypis_informace`.

```py
frantisek = Zamestnanec()
frantisek.jmeno = "František Novák"
frantisek.pozice = "konstruktér"
print(frantisek.vypis_informace())
```

Zkusíme přidat ještě jednu zaměstnankyni.

```py
klara = Zamestnanec()
klara.jmeno = "Klára Nová"
klara.pozice = "konstruktérka"
```

Nyní vyzkoušíme vypsat informace obou zaměstnanců.

```py
print(frantisek.vypis_informace())
print(klara.vypis_informace())
```
