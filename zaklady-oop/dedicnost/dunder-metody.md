## Dvojité podtržítko — dunder metody

`dunder` (double under) jsou metody začínající a končící dvěma podtržítky. Dvěma z nich je již známé funkce `__init__` pro inicializaci třídy a `__str__` pro převod na řetězec. Mají svůj význam také mimo třídy, například `__file__` pro zjištění cesty, kde se soubor nachází. Jedná se o funkce či atributy, které jsou něčím výjimečné, v Pythonu mají předdefinované chování a Python ví, jak s nimi pracovat.

Několika dunder funkcemi můžeme upravit svou třídu tak, aby se chovala podobně a nebo stejně jako například `list`. Mimo dalších je touto dunder funkcí i  `__len__`, která vrací informaci o délce instance a je zavolána dosazením instance do funkce `len`. Délkou instance se rozumí to, co v daném kontextu dává smysl, pro firmu by mohlo jít o počet zaměstnanců a pro rok by šlo o měsíce.

```python
class Company:
    def __init__(self, Zamestnanecs):
        self.Zamestnanecs = Zamestnanecs

    def __len__(self):
        return len(self.Zamestnanecs)

    def __iter__(self):
        return iter(self.Zamestnanecs)
```

### Dědičnost a dvojité podtržítko

Dvojité podtržení z jedné strany má také svůj význam. Jde o soukromé metody, které navíc zdědí jméno své třídy. Tím dává vývojář třídy najevo, že tato by opravdu za žádných okolností neměla být volána zvenku.

`__join_names` ze třídy `Zamestnanec` se po spuštění pro veřejnost přemění na `_Zamestnanec__join_names` a pro svou instanci zůstane jako `__join_names`. Díky tomuto nedojde v dědící třídě k přejmenování pomocných funkcí, které jsou zásadní pro fungování ostatních funkcí. I tyto funkce se nezobrazí po dosazení třídy nebo instance do napovídající funkce `help`.

```python
class Zamestnanec:
    def __init__(self, krestni_jmeno, prijmeni):
        self.krestni_jmeno = krestni_jmeno
        self.prijmeni = prijmeni

    def __join_names(self):
        return (self.krestni_jmeno + self.prijmeni).lower()

    @property
    def email(self):
        return self.__join_names() + "@goodcompany.com"

class GoodCompanyZamestnanec(Zamestnanec):
    def __join_names(self):
        return self.prijmeni + self.krestni_jmeno

    @property
    def skype(self):
        return self.__join_names()

Zamestnanec = GoodCompanyZamestnanec("Alžběta", "Nováková")

print(Zamestnanec.skype)
print(Zamestnanec.email)
# print(Zamestnanec.__join_names()) # chyba
print(Zamestnanec._GoodCompanyZamestnanec__join_names()))
```
