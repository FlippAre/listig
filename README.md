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
### Vem är listig riktad till? Följderna av det valet.
Listig är en produkt för både privatpersoner och företag som enkelt vill hålla koll på sin data, lite so en grafisk DIY-databas. Enkelhet är viktigare än avancerade funktioner, dock måste ett visst mått av "hackbarhet" finnas, så man kan bygga det man vill.

### Hur mycket av ett programmeringsspråk/Excel ska det bli? Följderna där?
Inte så mycket excel eller programeringsspråk. Mer åt en grafisk databas. Absolut att det kan finnas enklare formler, så som sumeringar eller medelvärden, men bör stanna där. All annan utbyggbarhet får ske via ett snyggt API, som tillåter de som vill att bygga precis vad de vill

### Vad ska det kunna användas till?
För privatpersoner:
- Gemensam packningslista
- Privatekonomi
- Hålla koll på inventarier
- Dela fakta
- Datatabeller enkelt tillgängliga, typ världens berg.

För förenigar:
- Medlemsregister
- Publicera sin data om verksamheten
- Event-listior
- Anmälningsformulär


För företag
- Samla data från t.ex web-formulär
- Bygga sitt eget verksamhetssystem, crm-system osv
- Dela datablad om produkter
- Bygga enkla rapporter


### Monetization
Gratis för publika listor. Månadskostnad per privat lista.

## Datatyper
Det är mycket lättare att resonera fram till ett hållbart dataformat om vi har koll på så många datatyper som möjligt som vi vill ha med (minst de som ska med i MVP):

_Ska värden kunna vara av `optional`-typ, eller krävs det värde i alla fält? Följderna av det valet (bl.a att formatet ska optimeras för sparse data - t.ex som Excel gör)?_
Ja, värden skall kunna vara tomma och är det som default. Kanske att man kan ange att vissa kolumner inte får vara tomma.


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
#### Hur ska referenserna se ut?
`Från listan 'valuta' hämta fält 2 'USD' där är kolumn 1='SEK', hämta fält i kolumn 2?`
När man refererar till en annan lista anger man vilken kolumn i den listan man vill skall visas, med kolumnnamn som referense. 
Exempel:`Thinkflipp/books::Author`
Exempel med pinnad version:
`Thinkflipp/books#46775763834::Author`

Kanske länkar man alltid automatiskt mot en pinnad version? 

Man kanske vill ha två referenser mot en lista, där den ena referensen är en slav under den andra. Exempel en lista med valutor och växlingskurser. I 'vår' lista lägger man till en rad oc väljer en valuta, SEK, och vill då att växlingskursen skall hämtas automatiskt i nästa kolumn. Förslag:

Kolumn1 (Valuta): `ListigGlobalLists/Money::Currency Name`

Kolumn2 (Växlingskurs) `MyUser/MyList::Valuta->Currency Value`


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

- Publika/privata listor ger att alla listor måste ha access rights. Ja!
  - Vi kör med CRUD behörigheter i alla listor. Där varje behörighet kan sättas per medlem i listan. Publika listor har alla som defeault R utan ägaren som har full CRUD
  - Personer bjuds in till en lista för att få full eller delar av CRUD.
  - En lista kan sätta globala världen för CRUD. Exemple alla i hela världen/organisationen kan läsa och skapa men inte ta bort eller uppdatera.
- Publika/privata listor ger att det förmodligen behövs organisationer. Ja! Jämför med GitHub
- Referenser till gamla versioner? Kräver det att servern har alla gamla versioner? Ja!
- ...

## Filformat?

### Metadata
Vad behöver vi veta om listan? 
- Fält 
- Ägare
- Skapad av
- Skapad datum
- Uppdaterad av
- Uppdaterad datum
- ID
-....

### Data

Skulle vi vilja att en lista kan representeras av en fil:
```
Heading1 (Text) | Heading2 (Number) | Heading3 ([Alt1, Alt2, Alt3])  | Heading4 (User/List#Version) |  
"Värde 1"       | 5                 | Alt2                           | ???                          |```

Sist?
