#  Normalization Examples

TODO!

## vObject Native Representation

Original:

{align="left"}
```
BEGIN:VOBJECT
PROPERTY1:10
PROPERTY2:20
END:VOBJECT
```

Normalized:

{align="left"}
```
BEGIN:VOBJECT
PROPERTY1:10
PROPERTY2:20
END:VOBJECT
```

## vCard

Original:

{align="left"}
```
BEGIN:VCARD
VERSION:4.0
KIND:individual
FN:Martin Van Buren
N:Van Buren;Martin;;;Hon.
TEL;VALUE=uri;PREF=1;TYPE="voice,home":tel:+1-888-888-8888;ext=8888
END:VCARD
```

Normalized:

{align="left"}
```
BEGIN:VCARD
VERSION:4.0
KIND:individual
FN:Martin Van Buren
N:Van Buren;Martin;;;Hon.
TEL;VALUE=uri;PREF=1;TYPE="voice,home":tel:+1-888-888-8888;ext=8888
END:VCARD
```

## iCalendar

## xCard

## jCard

## xCal

## jCal

