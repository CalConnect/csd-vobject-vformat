### FIELDSET

Some properties and parameters require values defined in terms of multiple parts.

This construct of multiple structured values is called a "FIELDSET".
These structured property values **MUST** have their value parts separated by a
SEMICOLON character. Each value in FIELDSET **MUST** have the same value type as defined.

Example 1.

The "CLIENTPIDMAP" property of [@RFC6350] takes a tuple of "INTEGER" and "URI" separated
by a SEMICOLON.

The notation in vObject given for its value type would be this indicating that the first value is an INTEGER, while the latter value is a URI:

```abnf
FIELDSET(INTEGER, URI)
```

Example 2.

The "N" property of [@RFC6350] defines its value of having 5 values at once, and
each of these values are a LIST of TEXT.

The notation in vObject given for its value type would be this indicating that there are 5 fields in this FIELDSET,
and each value element of it **MUST** be a LIST of TEXT elements:

```abnf
FIELDSET(5\*LIST(TEXT))
```

#### Normalizing a FIELDSET

When normalizing a FIELDSET, each value **MUST** have been normalized,
but the order of FIELDSET elements **MUST NOT** be rearranged.
