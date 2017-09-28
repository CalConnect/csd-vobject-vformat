### Binary (From RFC 5545)

Value Name
:  BINARY

Purpose
:
  This value type defines values that contain inline binary data encoded
  in characters. For example, an inline "ATTACH" property of an iCalendar
  object or an inline "PHOTO" property image inside a vCard object.

Format Definition
:

``` abnf
binary = *(4b-char) [b-end]
  ; A "BASE64" encoded character string, as defined by [@RFC4648].

b-end  = (2b-char "==") / (3b-char "=")

b-char = ALPHA / DIGIT / "+" / "/"
```

Description
:
  Property values with this value type **MUST** specify the parameter
  "ENCODING" with parameter value "BASE64", and the inline binary data
  **MUST** be character encoded using the "BASE64" encoding
  method defined in [@RFC2045].

<!-- No additional content value encoding
(i.e., BACKSLASH character encoding, see Section 3.3.11) is defined for
this value type. -->

<!--TODO: UPDATE EXAMPLE -->

Example:
  This value for the NOTE value of vCard:

  The following is an example of a "BASE64" encoded binary value data:

    ATTACH;FMTTYPE=image/vnd.microsoft.icon;ENCODING=BASE64;VALUE
    =BINARY:AAABAAEAEBAQAAEABAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAA
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAACAAAAAgIAAAICAgADAwMAA////AAAA
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    AAAAAAAAAAAAAAAAAAAAAAMwAAAAAAABNEMQAAAAAAAkQgAAAAAAJEREQgAA
    ACECQ0QgEgAAQxQzM0E0AABERCRCREQAADRDJEJEQwAAAhA0QwEQAAAAAERE
    AAAAAAAAREQAAAAAAAAkQgAAAAAAAAMgAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    AAAAAAAAAAAA
