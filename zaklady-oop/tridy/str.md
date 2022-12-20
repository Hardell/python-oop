## Metoda `__str__`

Pojďme ještě použití naší třídy trochu zjednodušit. Naše třída umí přehledně vypsat informace díky metodě `cerpani_dovolene()`. Třídu ale může používat i jiný programátor a ten o této metodě nemusí vědět a tak intuitivně vyzkouší funkci `print()`, které vloží nějaký objekt třídy `Zamestnanec`.

```python
print(frantisek)
```

Odpovědí bude poněkud záhadný text ve stylu

```python
<__main__.Zamestnanec object at 0x00000126F0084850>
```

Funke `print()` se totiž pokusí převést objekt na typ řetězec. Protože naše třída nemá tuto funkci naprogramovanou, použije se standardní formát, který nám říká, že jde o objekt třídy `Zamestnanec` a kde je uložený v paměti. Bylo by však dobré místo toho získat nějaký srozumitelný výpis, třeba takový, který poskytuje metoda `vypis_informace()`.

Převod na řetězec zařídíme tím, že třídě přidáme metodu `__str__`. Dvě lomítka opět značný zvláštní význam. Ten spočívá v tom, že Python využije tuto metodu vždy, když jej požádáme o převod objektu na řetězec. Můžeme tedy přejmenovat metodu `vypis_informace()` na `__str__`. Výstupem našeho programu pak bude text o tom, jak se zaměstnanec jmenuje a kde pracuje.

```python
class Zamestnanec:
    def __init__(self, jmeno, pozice):
        self.jmeno = jmeno
        self.pozice = pozice

    def __str__(self):
        return f"{self.jmeno} pracuje na pozici {self.pozice}."

frantisek = Zamestnanec("František Novák", "konstruktér")
print(str(frantisek))
```

Tím jsme si ukázali, jak vytvořit třídu, objekty a jak s nimi pracovat.
