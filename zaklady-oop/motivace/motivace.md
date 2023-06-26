## Pro používáme OOP

Objektově orientované programování (OOP) patří mezi tzv. paradigmata, neboli přístupy k tomu, jak psát programy. Na rozdíl od například znalosti cyklů či podmínek, nám OOP nepřináší nějaké zásadní a nové možnosti ve psaní programů. Pomáhá nám ale programy lépe strukturovat a psát tak, aby byly v budoucnu snáze rozšiřitelné o další funkce.

Pro použití objektově orientovaného programování potřebujeme používat jazyk, který toto paradigma podporuje. Mezi takové jazyky patří například Java, C++, Python, C#, Swift nebo Scala. Naopak mezi jazyky, které OOP nepodporují, patří C, Haskell, Fortran nebo Pascal.

Uvažujme nyní, že je naším úkolem vytvoření personálního systému pro firmu. V rámci systému budeme evidovat zaměstnance a zaměstnankyně, konkrétně jejich jména, pracovní pozice a jejich nárok na dovolenou. K uložení informací můžeme využít řadu struktur, které už známe. Začněme například se seznamem, do kterého si uložíme jméno, pozici a počet dní dovolené dvou zaměstnanců.

```py
employee_1 = ["Jan Novák", "konstruktér", 25]
employee_2 = ["Klára Nová", "konstruktérka", 25]
```

Vytvoření seznamu je poměrně jednoduché. Naším kolegyním a kolegům ale nemusí být na první pohled zřejmý význam především poslední hodnoty, mohou ho považovat například za číslo kanceláře. To jde vyřešit přidáním komentáře, toho si ale kolegové nemusí všimnout.

Další možnost, jak data uložit, je s využitím slovníku. Ten zapíšeme do složených závorek a všechny informace do něj ukládáme ve dvojicích, tj. nejprve napíšeme "označení hodnoty" (klíč), poté dvojtečku a za ní samotnou hodnotu.

```py
employee_1 = {"name": "Jan Novák", "position": "konstruktér", "holiday_entitlement": 25}
employee_1 = {"name": "Klára Nová", "position": "konstruktérka", "holiday_entitlement": 25}
```

Dále uvažujme kód, který řeší čerpání dovolené. Uvažujme, že Jan si chce vzít 10 dní dovolené, snížíme tedy jeho nárok o 10 dní.

```py
employee_1["holiday_entitlement"] = employee_1["holiday_entitlement"] - 10
```

Tento řádek kódu sice sníží nárok na dovolenou, před schválením dovolené a snížení nároku je ale vhodné zkontrolovat, jestli se už zaměstnanec nedostane čerpáním "do mínusu". K tomu můžeme využít podmínku.

```py
days = int(input("Zadejte počet dní dovolené: "))
if days > employee_1["holiday_entitlement"]:
    employee_1["holiday_entitlement"] = employee_1["holiday_entitlement"] - days
    print("Dovolená schválena.")
else:
    print("Na tolik dní už nemáš nárok.")
```

Tento kód už je poměrně dlouhý a pokud bychom ho potřebovali na více místech (např. máme individuální žádosti a hromadné zadávání dovolené o Vánocích), bylo by dobré umístit jej do funkce.

```py
def holiday_request(days):
    if days > employee_1["holiday_entitlement"]:
        employee_1["holiday_entitlement"] = employee_1["holiday_entitlement"] - days
        print("Dovolená schválena.")
    else:
        print("Na tolik dní už nemáš nárok.")

employee_1 = {"name": "Jan Novák", "position": "konstruktér", "holiday_entitlement": 25}
days = int(input("Zadejte počet dní dovolené: "))
holiday_request(days)
```

Tím máme náš program hotový. Má však několik nevýhod, které nám budou komplikovat život při jeho rozšiřování.

* Pokud nový člen nebo členka týmu bude vytvářet dalšího zaměstnance, musí si otevřít dokumentaci nebo najít už nějaký stávající záznam, aby věděl(a), které hodnoty jsou pro správné fungování potřeba.
* V rozsáhlém programu bude spousta funkcí a nemusí být úplně zřejmé, která funkce pracuje s jakými typy záznamů. Někdo například může přehlédnout funkci `holiday_request()` a naprogramovat to samé znovu. Současně může být se zaměstnancem svázáno velké množství dalších funkcí a nemusí být na první pohled zřejmé, které k němu patří a které ne.

Oba tyto problémy řeší konpect OOP, protože ten umožńuje svázat data a kód pro jejich úpravy a zpracování do jednoho celku.
