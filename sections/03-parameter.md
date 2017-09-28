# vObject Property Parameter

Each property is assigned a value, and the value is the content after
the colon delimiter until the end of the unfolded content line.

A property can have attributes associated with it.  These "property
parameters" can contain:

* information about the property; or
* information about the property value

A property **MAY** have multiple property parameters, for example, the
"TYPE" of the value or a category that applies to this value.

Property parameters are optional, and exist between the property name
and the colon delimiter.

Some properties allow assigning multiple property parameters in a list.
Each property parameter in a list of property parameters **MUST** be
separated by a SEMICOLON character.
There is no defined order among property parameters in a property parameter list.

The property parameter name and the property parameter value is separated with an
equal sign ("=").

When there are multiple instances of a property parameter on the same property,
such as in "TYPE=home;TYPE=work", it is considered equivalent to "TYPE=home\,work".


## Normalizing a Property Parameter

### Uppercased Property Parameter Names

The property parameter name **MUST** be normalized into uppercase letters
in form of a Unicode string ([@!RFC7159] Section 3).

Property parameter names (together with their values) **MUST** be sorted
alphabetically.

Example:

`TEL;VALUE=uri;type=home:tel:+1-888-888-8888`

The normalized form is:

`TEL;TYPE="home";VALUE="uri":tel:+1-888-888-8888`


### Join Identical Property Parameter Names

If a property parameter occurs more than once within a property, the
property parameter is considered to contain a list of property parameter
values joined by the parameter separator.

Such instances of property parameters with identical names **MUST** be
joined into one instance with its value a sorted list of the property
parameter values.

For example, the vCard `TEL` property's `TYPE` parameter [@!RFC6350]
describes that "TYPE=home,work" and "TYPE=work;TYPE=home" are considered
equivalent.

Example:

`TEL;TYPE=home;Type=work;VALUE=uri:tel:+1-888-888-8888`

The normalized form is:

`TEL;TYPE="home","work";VALUE=uri:tel:+1-888-888-8888`


### Express Default Property Value Types

<!-- TODO: **MUST** we really show the default property type? -->

In vObject formats including [@RFC5545] and [@RFC6350], each property
value has a specified data type either as specified by property
definition or optionally assigned.

When normalizing a property, the property data value type **MUST** always be
specified. If the value type is not explicitly specified, it **MUST** be
filled in according to the vObject format.

Example:

`TEL:+1-888-888-8888`

The normalized form is:

`TEL;VALUE="text":+1-888-888-8888`
