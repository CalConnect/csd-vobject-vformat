### INTEGER

<!--If the property permits, multiple "integer" values are
specified by a COMMA-separated list of values. -->

<!--
6350 uses 64-bit integer
5545 uses 32-bit integer
-->

Value Name
:
  INTEGER
  (INTEGER-32 for storing 32-bit integer, INTEGER-64 for storing 64-bit integer)

Purpose
:
  Representation of a signed integer value.

Format Definition
:

```abnf
integer = (["+"] / "-") 1*DIGIT
```

Description
:

  If a preceding sign is not specified, the value is assumed positive "+".
  While the format accepts the optional "+" PLUS sign, a writer that conforms
  to this document **SHOULD** not write the "+" sign for clarity reasons.

  The valid ranges for INTEGER-32 and INTEGER-64 are:

  * INTEGER-32: -2147483648 (-2^31) to 2147483647 (2^31 - 1)
  * INTEGER-64: -9223372036854775807 (-2^63) to 9223372036854775808 (2^63 - 1)


Examples
:

      1234567890
      -1234567890
      +1234567890
      432109876

#### Normalization

A positive integer when normalized **MUST** not have the optional "+" sign.
