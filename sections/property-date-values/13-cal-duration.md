### CAL-DURATION {#cal-duration}

<!-- This is the 5545 DURATION.  -->

Value Name
:
  CAL-DURATION

Purpose
:
  Representing a duration of time specified by [ISO.8604.2004] Section 4.4.3.2 complete representation basic format, simiar to ISO-DURATION, but with syntax tailored to calendaring.

Format Definition
:

```abnf
cal-duration         = cal-duration-sign cal-duration-no-sign
cal-duration-sign    = (["+"] / "-")
cal-duration-no-sign = "P" cal-duration-value

cal-duration-value   = ( cal-duration-date /
                         cal-duration-time /
                         cal-duration-week )

cal-duration-date   = cal-duration-day [cal-duration-time]

cal-duration-time   = "T" ( cal-duration-hour /
                            cal-duration-minute /
                            cal-duration-second )

cal-duration-week   = 1*DIGIT "W"
cal-duration-hour   = 1*DIGIT "H" [cal-duration-minute]
cal-duration-minute = 1*DIGIT "M" [cal-duration-second]
cal-duration-second = 1*DIGIT "S"
cal-duration-day    = 1*DIGIT "D"
```

Description
:

  The value format is similar to ISO-DURATION and based on the complete representation
  basic format specified in [@ISO.8601.2004] Section 4.4.3.2, but given extra flexibility
  to calendaring usage.

  It accepts the following formats ("nn" represents):

  * "PnnW" [@ISO.8601.2004] Section 4.4.3.2, complete representation,
    first basic format, for duration in weeks.

  * "PnnDTnnHnnMnnS" [@ISO.8601.2004] Section 4.4.3.2, complete representation,
    second basic format, with the omission of years and months,
    for duration in days, hours, minutes and seconds.

  * "PnnDTnnHnnM" Reduced accuracy with omission of seconds.

  * "PnnDTnnH" Reduced accuracy with omission of minutes.

  * "PnnD" Reduced accuracy with omission of hours.


  This format differs from the specification of [@ISO.8601.2004] Section 4.4.3.2
  in the following areas:

  * Years and months are not accepted in this syntax.

  * An optional, preceding "sign", element is used to indicate positive or negative
    duration. Negative durations are useful in representing reverse scheduling,
    such as the time to trigger an alarm before an associated time (see [@RFC5545]).

  * Reduced accuracy is allowed for in particular, the omission of the number and
    designators of hours, minutes or seconds is allowed with the omission starting
    from the extreme right-hand side. In the case of the omission of the time value,
    the "T" separator **MUST** also be omitted. The day ("D") portion **MUST**
    always be present.

  * The duration of a week or a day depends on its position in the calendar.

  In the case of discontinuities in the time scale, such
  as the change from standard time to daylight time and back, the
  computation of the exact duration requires the subtraction or
  addition of the change of duration of the discontinuity.  Leap
  seconds **MUST NOT** be considered when computing an exact duration.

  When computing an exact duration, the greatest order time
  components **MUST** be added first, that is, the number of days **MUST**
  be added first, followed by the number of hours, number of
  minutes, and number of seconds.


Example
:
  A duration of 0 days, 0 hours, and 20 seconds **SHOULD** be represented as

    P0DT0H0M20S

  A duration of 15 days, 5 hours, and 3 hours **SHOULD** be represented as

    P15DT5H3M

  A duration of 15 days, 5 hours **SHOULD** be represented as

    P15DT5H

  A duration of 15 days **SHOULD** be represented as

    P15D

  A duration of 7 weeks **SHOULD** be represented as:

    P7W

#### Normalization

No normalization procedures are needed.
