## Chráněné atributy a vlastnosti

Nyní se podíváme na další dva aspekty objektově orientovaného programování: chráněné atributy a vlastnosti

Ve třídě `Employee` jsme přidali způsob, jak mohou zaměstnanci "bezpečně" žádat o dovolenou, aby se nedostali do mínusu. Musíme si však uvědomit, že hodnotu atributů lze v Pythonu měnit přímo.

Můžeme přímo nastavit nějakou hodnotu.

```py
frantisek.holiday_entitlement = 10
```

Stejně tak je možné provést snížení hodnoty.

```py
frantisek.holiday_entitlement = frantisek.holiday_entitlement - 10
```

Většina objektově orientovaných jazyků umožňuje vytvořit tvz. soukromé atributy, které nejde měnit zvenku, ale pouze prostřednictvím method. Autoři jazyk Python se však rozhodli dát vývojářům a vývojářkám svobodu atributy objektu měnit libovolně. Můžeme ale vytvořit tzv. chráněný atribut. Chráněný atribut se vyznačuje tím, že jeho název začíná s podtržítkem. Sice je pořád možné měnit jej přímo, dáváme tím ale jasně najevo, že by se to **dělat nemělo**. Tento přístup funguje v realitě docela dobře, protože dnes je možné dohledat autora (autorku) každého řádku zdrojového kódu, takže si všichni dávají pozor, aby atributy měnili přímo pouze v případech krajní nouze.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self._holiday_entitlement = holiday_entitlement
    
    def __str__():
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."

    def take_holiday(self, days):
        if self._holiday_entitlement >= days:
            self._holiday_entitlement -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self._holiday_entitlement} dní."

frantisek = Employee("František Novák", "konstruktér", 25)
print(str(frantisek))
```

### Vlastnosti

Vlastnost (`property`) se zvenku tváří jako atribut, ve skutečnosti jde ale o "skrytou" metodu. Uvažujme například, že u zaměstnance (zaměstnankyně) budeme chtít evidovat i mzdu. U mzdy ale musíme rozlišovat mezi hrubou mzdou (před zdaněním) a čistou mzdou (po zdanění). Mzda se v průběhu pracovního poměru mění a pokud bychom evidovali obojí jako atribut, museli bychom přidat metodu, která vždy při změně hrubé mzdy přepočítá i čistou mzdu. Jednodušším řešením je ale použití vlastnosti. Vytvoříme metodu `net_salary()`, která spočítá výši čisté mzdy. Přidáme k ní ale "dekorátor" `@property`. Dekorátor je funkce, která "dekoruje" jinou funkci, třídu nebo metodu a umožňuje měnit jejích chování a způsob jejího používání.

```py
class Employee:
    def __init__(self, name, position, holiday_entitlement, gross_salary):
        self.name = name
        self.position = position
        self._holiday_entitlement = holiday_entitlement
        self.gross_salary = gross_salary
    
    @property
    def net_salary(self):
        return self.gross_salary * (1 - 0.15)
```

Dekorátor `@property` způsobí, že při volání metody není potřeba používat závorky. Zvenku tedy vlastnost vypadá jako obyčejný atribut, což zjednodušuje její volání.

```py
frantisek = Employee("František Novák", "konstruktér", 25, 80000)
print(f"Na účet pana Nováka pošleme {frantisek.net_salary} Kč.")
```

## Cvičení

::exc[excs>balik-3]

### Chráněné metody

Soukromé metody jsou metody, které mohou být volány pouze jinými metodami dané třídy, nikoli však zvenku. Python, na rozdíl od jiných programovacích jazyků, skutečně soukromé metody nemá. Všechny metody a atributy tříd jsou veřejné a není žádný způsob jak je opravdu skrýt před vývojářem.

Obecně platí, že atributy nebo metody začínající podtržítkem jsou soukromé a vývojář by je mimo danou třídu neměl číst, upravovat nebo volat. Takové metody nebo atributy se nezobrazí, pokud na třídu zavoláme funkci `help`. Zobrazí se až při bližším zkoumání, například pomocí funkce `dir`. Vývojář třídy tímto odhaluje všechny své karty a dává uživateli do rukou možnost tyto karty taktéž použít, pokud bude potřebovat.

```python
class Zamestnanec:
    def __init__(self, krestni_jmeno, prijmeni):
        self.krestni_jmeno = krestni_jmeno
        self.prijmeni = prijmeni

    @property
    def _delka_jmena(self):
        return len(self.krestni_jmeno + self.prijmeni)

    @property
    def business_card_data(self):
        if self._delka_jmena < 20:
            return f"{self.krestni_jmeno} {self.prijmeni}"
        else:
            return f"{self.krestni_jmeno[0]}. {self.prijmeni}"
```

