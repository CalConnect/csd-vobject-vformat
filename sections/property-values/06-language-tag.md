### LANGUAGE-TAG


Value Name
:
  LANGUAGE-TAG

Purpose
:
  Representing a language tag, as defined in [@!RFC5646].

Format Definition
:
  Defined in [@!RFC5646].

Description
:
  A single language tag

Examples
:

      de
      en-US
      sr-Cyrl
      zh-yue-HK


#### Normalization

The normalization procedure of the LANGUAGE-TAG data type follows
the procedure described in Section 2.1.1 of [@RFC5646].

* language codes **MUST** be written in lowercase ('mn' Mongolian)
* script codes **MUST** be in lowercase when the initial letter capitalized ('Cyrl' Cyrillic)
* country codes **MUST** be capitalized ('MN' Mongolia)

As the language tag is comprised of a mixture of these components,
[@RFC5646] provides a rule that applies this procedure across all
language tags:

* All subtags, including extension and private use subtags, **MUST** use lowercase letters.
* Except: two-letter subtags that neither appear at the start of the tag
  nor occur after singletons **MUST** be in uppercase ("en-CA-x-ca" or "sgn-BE-FR").
* Except: four-letter subtags that neither appear at the start of the tag
  nor occur after singletons **MUST** be in titlecase ("az-Latn-x-latn").

