## Čtení na doma: Dvojité podtržítko

Dvojité podtržení z jedné strany u atributu nebo metody má svůj význam, a překvapivě docela jiný než dvojité podržítko z obou stran jména metody. Jde o soukromé atributy a metody, které navíc "zdědí" jméno své třídy. Tím dává vývojář nebo vývojářka třídy najevo, že tato by opravdu za žádných okolností neměla být volána zvenku.

Atribut `__holiday_entitlement` ze třídy `Employee` se po spuštění pro veřejnost přemění na `_Employee__holiday_entitlement` a pro svou instanci zůstane jako `__holiday_entitlement`. Díky tomuto nedojde v dědící třídě k přejmenování pomocných funkcí, které jsou zásadní pro fungování ostatních funkcí. I tyto funkce se nezobrazí po dosazení třídy nebo instance do napovídající funkce `help`.

```python
class Employee:
    def __init__(self, name, position, holiday_entitlement):
        self.name = name
        self.position = position
        self.__holiday_entitlement = holiday_entitlement
    
    def __str__(self):
        return f"Zaměstnanec {self.name} pracuje na pozici {self.position}."

    def take_holiday(self, days):
        if self.__holiday_entitlement >= days:
            self.__holiday_entitlement -= days
            return f"Užij si to."
        else:
            return f"Bohužel už máš nárok jen na {self._holiday_entitlement} dní."

frantisek = Employee("František Novák", "konstruktér", 25)
print(str(frantisek))

# print(frantisek.__holiday_entitlement) # chyba
print(frantisek._Employee__holiday_entitlement)
```
