# Listig

## En lista
- Innehåller ett antal kolumner och rader
- Varje kolumn är låst till en datatyp
  - Text
  - Tal
  - URL
  - Lista
  - Länk till annan lista. Kan länka till head på en lista eller en specifik version
- Varje kolumn har ett namn
- Listan är versionshanterad
- Bredden på en lista är <100
- Längden på en lista är <1 000 000

## Marknad
Vem är listig riktad till? Följderna av det valet.

Hur mycket av ett programmeringsspråk/Excel ska det bli? Följderna där?

Vad ska det kunna användas till?

### Monetization
Gratis för N publika listor. Månadskostnad för privata listor och M listor?

## Datatyper
Det är mycket lättare att resonera fram till ett hållbart dataformat om vi har koll på så många datatyper som möjligt som vi vill ha med (minst de som ska med i MVP):

Ska värden kunna vara av `optional`-typ, eller krävs det värde i alla fält? Följderna av det valet (bl.a att formatet ska optimeras för sparse data - t.ex som Excel gör)?

- Text
- Tal
- URL
- Lista
- Länk till annan lista. Kan länka till head på en lista eller en specifik version
- Tid/datum (absolut eller relativt tidzon med bättre namn)
- Alternativ (`enum`, där alternativen är av samma typ)
- Flervalsalternativ? (`options`, där alternativen är av samma typ) ???
- ...


### Referenser
Hur ska referenserna se ut? `Från listan 'valuta' hämta fält 2 'USD' där är kolumn 1='SEK', hämta fält i kolumn 2?`

Massor av fler exempel - imho det är detta som kommer bli svårt.

## Operationer
- Vad ska kunna göras med listorna?
- Vad är resultatet av operationer - en ny lista?
- Export - alla värden fixerade
- Det är detta en användare vill åt?

### Import / Export
- CSV, TSV, etc.
- JSON
- XML?
- Excel, etc.?

## Övrigt att komma ihåg

- Publika/privata listor ger att alla listor måste ha access rights.
- Publika/privata listor ger att det förmodligen behövs organisationer.
- Referenser till gamla versioner? Kräver det att servern har alla gamla versioner?
- ...

## Filformat?

### Metadata
Vad behöver vi veta om listan? Fält? Ägare?

### Data

Skulle vi vilja att en lista kan representeras av en fil:
```
Heading1 (Text) | Heading2 (Number) | Heading3 ([Alt1, Alt2, Alt3])  | Heading4 (User/List#Version) |  
"Värde 1"       | 5                 | Alt2                           | ???                          |```

Sist?