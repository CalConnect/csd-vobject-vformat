# vObject Property

Each vObject **MAY** contain multiple "properties" that represent
attributes of the vObject itself.

A property can be represented by one content line (a line that ends with
a line break), but can also be "folded" (Section 3.1 of [@RFC5545])
to use multiple lines.

A property generally begins with the property name (e.g., "TEL"), followed
by a COLON delimiter and the property's value.


## Normalizing a vObject Property

### Uppercased Property Name

The property name **MUST** be normalized to uppercase letters.

### Normalized Values

A normalized property **MUST** have normalized values.

### Normalized Parameters

A normalized property **MUST** have normalized property parameters.

Property parameters within the same property **MUST** each be normalized, and then
sorted by parameter name alphabetically. According to the normalization procedure
of a vObject property parameter, no two parameters of the same property could
have identical names.

The last property parameter of a property **MUST NOT** have a trailing SEMICOLON.

### Wrapped Content Line

When exporting a normalized property content line, it **MUST** be folded at the
character limit when it exceeds 75 characters. Each folded line **MUST** be delimited
by the character sequence of a line break and a single white space (CRLF, SPACE (U+0020)).
This rule only applies to normalized output.

<!-- TODO: figure out how to demonstrate line wrapping without overflowing! -->

For example, the original form:

```
NOTE:This is a very long description on a long line that exceeds 75 characters.
```

When exported to normalized output **MUST** give out:

```
NOTE:This is a very long description on a long line that exceeds 75 charac
 ters.
```
