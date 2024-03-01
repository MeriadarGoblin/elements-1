This is a list of logic used for general code specific to XML content.

## Boolean Logic

| Operator | Boolean Login | Result                                                        |
|----------|---------------|---------------------------------------------------------------|
| `!`      | NOT           | Requires not needing X requirement/node                       |
| `[]`     | Separator     | Separates between different stats, such as a list of elements |
| `&#124;` | OR            | Separates for one or the other                                |
| `,`      | AND           | Basically a list                                              |

## Requirement Logic

Valid inputs:

- IDs

```xml
requirements="!ID_WOTC_PHB_MULTICLASS_BARBARIAN"
```

- Stats

```xml
requirements="[innate speed:burrow:1]"
```

## Support Logic

Valid inputs:

- IDs
- Supports
- $(spellcasting:list)
- $(spellcasting:slots)

**Note:** IDs and Supports CANNOT be used within the same support statement.

## Level Logic

Valid inputs:

- Integers

```xml
level="1"
```

- Value

```xml
value="level"
```
