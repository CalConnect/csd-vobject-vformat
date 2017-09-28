# vObject Structure {#vobject}

Both vCard [@!RFC6350] and iCalendar [@RFC5545] data formats belong to a
family defined as "vObject". The "vObject" format is a generalized data
format of both vCard and iCalendar standards, and both these formats adhere
to the vObject format requirements.

## Compliant Formats

These formats are vObject "compliant formats" as they adhere to the rules of vObject:

* vCard version 4.0 [@!RFC6350]: the VCARD component
* Internet Calendaring and Scheduling Core Object Specification
  (iCalendar) [@!RFC5545], the VCALENDAR, VEVENT, VJOURNAL, VFREEBUSY,
  VTIMEZONE, VALARM, VTODO, STANDARD, DAYLIGHT components
* Calendar Availability Extensions [@!RFC7953]: the VAVAILABILITY,
  AVAILABLE components
* iCalendar Patching [@VPATCH]: the VPATCH component


## Elements

Data within a vObject is arranged through a hierarchy that is composed of
the following elements:

* component;
* property;
* property parameter;
* property value;
* property parameter value; and
* property group.

Parsing and modification operations that work on the vObject format
**SHOULD** work on all its downstream formats, including
iCalendar [@RFC5545] and vCard [@RFC6350].



## vObject Native Representation

vObject Native Representation (the "native format") is the syntax originated from the textual
representation of the iCalendar [@RFC5545] and vCard [@RFC6350] formats.
Its syntax is mostly tracable back to the original vCard and iCalendar
documents [@vCard21].

This is called the "native" format to distinguish it from
alternative representations of vObject data,
such as those in XML or in JSON.



### ABNF Format Definition

The following ABNF notation defines the vObject Native
Representation, in accordance to [@RFC5234], which also defines CRLF,
WSP, DQUOTE, VCHAR, ALPHA, and DIGIT.

The body of a vObject is defined by the following notation:

~~~ abnf
vobjects = 1*vobject

vobject = "BEGIN:" comp-name CRLF
          *contentline
          *vobject
          "END:" comp-name CRLF

comp-name = name

prop-name = name

prop-values = prop-value / prop-list / prop-structured

prop-value = VALUE-CHAR

prop-list = prop-value *("," prop-value)
  ; An unordered list containing multiple property values

prop-structured = prop-value *(";" prop-value)
  ; A structured list that consist of multiple property fields
  ; for multiple property values

contentline = [group "."] prop-name params ":" prop-values CRLF
  ; Folding and unfolding procedures described in Section 3.2 of
  ; [@!RFC6350] applies:
  ;   * When parsing a content line, folded lines **MUST** first be
  ;     unfolded accordingly.
  ;   * When generating a content line, lines longer than 75
  ;     characters **SHOULD** be folded accordingly.
  ;   * When normalizing a content line, the content line **MUST**
  ;     be folded when the line is longer than 75 characters.

group = name

params = *(";" param)

param = name "=" param-value *("," param-value)
  ; Allowed parameters depend on property name.

name = 1*(ALPHA / DIGIT / "-")

param-value = *SAFE-CHAR / DQUOTE *QSAFE-CHAR DQUOTE
param-values = param-value *("," param-single-value)

NON-ASCII = UTF8-2 / UTF8-3 / UTF8-4
  ; UTF8-{2,3,4} are defined in [@RFC3629]
  ; TODO: generalize this to UTF-32

QSAFE-CHAR = WSP / "!" / %x23-7E / NON-ASCII
  ; Any character except CTLs, DQUOTE

SAFE-CHAR = WSP / "!" / %x23-39 / %x3C-7E / NON-ASCII
  ; Any character except CTLs, DQUOTE, ";", ":"

VALUE-CHAR = WSP / VCHAR / NON-ASCII
  ; Any textual character

~~~


## Normalization

Normalization procedures are described within this document.


## Equivalence

Two vObjects are considered identical in content if their normalized
forms are textually equivalent.

