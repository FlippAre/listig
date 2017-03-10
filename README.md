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
- Längden på en lista är < 1 000 000


## Filformat?
Skulle vi vilja att en lista kan representeras av en fil:
```
Heading1 (Text) | Heading2 (Number) | Heading3 ([Alt1, Alt2, Alt3])  | Heading4 (User/List#Version) |  
"Värde 1"       | 5                 | Alt2                           | ???                          |```
