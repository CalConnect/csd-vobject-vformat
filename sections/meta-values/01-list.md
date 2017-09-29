### LIST

Some properties and parameters allow an unordered list of values. Values in a
list of values **MUST** be separated by a COMMA character. There is no
significance to the order of values in a list.

This construct is called the "LIST". Each value in the LIST **MUST** have the same
value type.

In vFormat syntax, an element within any LIST element **MUST NOT** contain
an unescaped the COMMA character to prevent breaking of the LIST syntax.

Syntax
:
  When used to describe a value type, the `LIST(value-type)` function is defined as
  a list of elements separated by the COMMA character, where each of its elements
  is of value type `value-type`.

Example
:
  The "NICKNAME" property of [@RFC6350] defines its value to be an unordered list of TEXT.
  In vObject notation its value type is defined to be:

```abnf
LIST(TEXT)
```

#### Normalizing a LIST

When normalizing a LIST, each value of it **MUST** be normalized,
and the values **MUST** be sorted alphabetically.

For example, values of [@RFC5545] RESOURCES, FREEBUSY, EXDATE, RDATE, CATEGORIES, **MUST**
be sorted alphabetically when normalized.


<!--
By default, the following basic value types accept LIST input

6350: DATE, TIME, DATE-TIME, DATE-AND-OR-TIME, and TIMESTAMP
  TEXT multivalue comma
  integer
  float

5545
- value types: date, date-time, duration, float, integer, period, text, time
-->

