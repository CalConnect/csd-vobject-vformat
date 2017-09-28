#  IANA Considerations

New vObjects specifications produced as Standards Track RFCs **MUST**
adhere to the normalization format described in this document, and any
exceptions or further instructions for normalization **MUST** be
described.


## vObject Component Uniqueness Properties Registration Procedure

This section defines the process to register new or modified
uniqueness properties for vObject components with IANA.

<!-- TODO: text below is from RFC 5545 -->
The IETF will create a mailing list, vobject@ietf.org, which can be
used for public discussion of iCalendar elements proposals prior to
registration.

<!-- Use of the mailing list is strongly encouraged.  The
IESG will appoint a designated expert who will monitor the
icalendar@ietf.org mailing list and review registrations. -->

Registration of new vObject Component Uniqueness Properties **MUST**
be reviewed by the designated expert and published in an RFC.
A Standards Track RFC is
**REQUIRED** for the registration of new vObject components
and its uniqueness property, as well as for the modification of
existing registrations.

The registration procedure begins when a completed registration
template, defined in the sections below, is sent to
vobject@ietf.org and iana@iana.org.  The designated expert is
expected to tell IANA and the submitter of the registration within
two weeks whether the registration is approved, approved with minor
changes, or rejected with cause.  When a registration is rejected
with cause, it can be re-submitted if the concerns listed in the
cause are addressed.  Decisions made by the designated expert can be
appealed to the IESG Applications Area Director, then to the IESG.
They follow the normal appeals procedure for IESG decisions.


###  Registration Template for vObject Component Uniqueness Properties

A registration for a vObject Component Uniqueness Property is defined by
completing the following template.

Component
: The name of the component.

Property
: The property of the component that is used to uniquely identify the
  component it belongs to.

Scope
: The uniqueness scope of the aforementioned property.

Reference
: The document that defines the component syntax and the uniqueness identifying
  property. Generally, this is where the component was originally defined, but
  if the uniqueness property is defined in an extension document, a reference
  to the extension document **SHOULD** be given instead.

Description
: Any special notes about the usage of the uniqueness identifying property,
  how it is to be used, etc.

Example(s)
: One or more examples of instances of the component need
  to be specified.


### Initial vObject Component Uniqueness Identifiers Registry {#vobject-uid-registry}

The IANA created and maintains this registry for vObject Component Uniqueness
Identifiers with pointers to appropriate reference documents.

The following table has been used to initialize the registry.

Component     | Property       | Scope         | Reference
:--------     | :----          | :-----        | :-----
VCALENDAR     | UID            | Global        | [@RFC7986], Section 5.3
VCARD         | UID            | Global        | [@RFC6350], Section 6.7.6
VEVENT        | UID            | Global        | [@RFC5545], Section 3.6.1
VTODO         | UID            | Global        | [@RFC5545], Section 3.6.2
VJOURNAL      | UID            | Global        | [@RFC5545], Section 3.6.3
VFREEBUSY     | UID            | Global        | [@RFC5545], Section 3.6.4
VTIMEZONE     | TZID           | Global        | [@RFC5545], Section 3.6.5
STANDARD      | DTSTART        | Within parent | [@RFC5545], Section 3.6.5
DAYLIGHT      | DTSTART        | Within parent | [@RFC5545], Section 3.6.5
VALARM        | UID            | Global        | [@I-D.daboo-valarm-extensions], Section 4
VAVAILABILITY | UID            | Global        | [@RFC7953], Section 3.1
AVAILABLE     | UID            | Global        | [@RFC7953], Section 3.1
VPOLL         | UID            | Within parent | [@I-D.york-vpoll], Section 4.5.1
VVOTER        | VOTER          | Within parent | [@I-D.york-vpoll], Section 4.5.2
VOTE          | POLL-ITEM-ID   | Within parent | [@I-D.york-vpoll], Section 4.5.3
<!--TODO: daboo-icalendar-vpatch is not yet available -->
<!-- VPATCH        | UID            | Global        | [I-D.daboo-icalendar-vpatch], Section 10.1 -->
<!-- PATCH         | TODO: Add UID? | Global        | [I-D.daboo-icalendar-vpatch], Section 10.1.1 -->
