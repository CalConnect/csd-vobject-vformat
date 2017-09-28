### ISO-DATE-FLEX

<!-- This is 6350 DATE -->

Representation of a calendar date [@ISO.8601.2004] that does not require
complete representation.


Value Name
: ISO-DATE-FLEX

Purpose
: This value type defines a calendar date format that allows entry of a
  complete calendar date [@ISO.8601.2004], a reduced accuracy date [@ISO.8601.2004]
  and a truncated date [@ISO.8601.2004].

Format Definition
:

``` abnf
iso-date-flex   = iso-date /
                  iso-date-reduced /
                  iso-date-truncated

iso-date-reduced = iso-date-fullyear / iso-date-year-month
iso-date-year-month = iso-date-fullyear "-" iso-date-month

iso-date-truncated =  iso-date-truncated-month-day /
                      iso-date-truncated-month-only /
                      iso-date-truncated-day-only

iso-date-truncated-month-day  = "--" iso-date-month iso-date-mday
iso-date-truncated-month-only =  "--" iso-date-month
iso-date-truncated-day-only   =  "---" iso-date-mday
```

Description
:
  This value format accepts:

  * a complete calendar date, specified in [@ISO.8601.2004] Section 4.1.2.2 "Complete representations",
  * a reduced accuracy calendar date, specified in [@ISO.8601.2004] Section 4.1.2.3 "Representations with reduced accuracy", and
  * a truncated representation calendar date, specified in [@ISO.8601.2000] Section 5.2.1.3 "Truncated representations".

  The value can be represented in these ways:

  * "YYYYMMDD" Complete representation basic format, specified in [@ISO.8601.2004] 4.1.2.2.
  * "YYYY-MM" Reduced accuracy representation, specified in [@ISO.8601.2004] 4.1.2.3 a).
  * "YYYY" Reduced accuracy representation, specified in [@ISO.8601.2004] 4.1.2.3 b).
  * "--MMDD" Truncated representation for a specific day of a month in the implied year, basic format, specified in [@ISO.8601.2000] Section 5.2.1.3 d).
  * "--MM" Truncated representation for a specific month in the implied year, basic format, specified in [@ISO.8601.2000] Section 5.2.1.3 e).
  * "---DD" Truncated representation for a specific day in the implied month, basic format, specified in [@ISO.8601.2000] Section 5.2.1.3 f).

Example:

    20170712
    2017-07
    2017
    --0712
    --07
    ---12

#### Normalization

No normalization procedures are needed.
