---
stand_alone: true
ipr: trust200902
docname: draft-bormann-senml-more-units-latest
keyword: Internet-Draft
cat: std
pi:
  toc: 'yes'
  tocompact: 'yes'
  tocdepth: '3'
  tocindent: 'yes'
  symrefs: 'yes'
  sortrefs: 'yes'
  comments: 'yes'
  inline: 'yes'
  strict: 'no'
  compact: 'no'
  subcompact: 'no'
title: Additional Units for SenML
abbrev: Additional Units for SenML
date: 2019-03-23
author:
-
  ins: C. Bormann
  name: Carsten Bormann
  org: Universitaet Bremen TZI
  street: Postfach 330440
  city: Bremen
  code: D-28359
  country: Germany
  phone: +49-421-218-63921
  email: cabo@tzi.org

normative:
  RFC8428: senml
  IANA.senml:
  IEC-80000-6:
    title: >
      Quantities and units –
      Part 6: Electromagnetism
    seriesinfo:
      IEC: 80000-6
      Edition: 1.0
    date: 2008-03-01
  IEC-80000-13:
    title: >
      Quantities and units –
      Part 13: Information science and technology
    seriesinfo:
      IEC: 80000-13
      Edition: 1.0
    date: 2008-03-01
  IEEE-1459:
    title: >
      IEEE Standard Definitions for the Measurement of Electric Power
      Quantities Under Sinusoidal, Nonsinusoidal, Balanced, or
      Unbalanced Conditions
    seriesinfo:
      IEEE Std: 1459-2010
    date: 2010-03-19

--- abstract

The Sensor Measurement Lists (SenML) media type supports the
indication of units for a quantity represented.
This short document registers a number of additional unit names in the
IANA registry for Units in SenML.

--- middle


# Introduction {#intro}


The Sensor Measurement Lists (SenML, {{-senml}}) media type supports the
indication of a unit, using the SenML field "u", for the quantity
given as a data value in a SenML record.   For this purpose, SenML
defines an IANA registry of defined Unit names and their meanings.

This short document registers a number of additional units in the IANA
registry for Units in SenML that appear to be
necessary for further adopting SenML in other Standards Development
Organizations (SDOs).

# New Units

IANA is requested to assign new units in the "SenML Units"
subregistry of the SenML registry {{IANA.senml}} (as defined in {{RFC8428}}):

| Symbol | Description                           | Type  | Reference |
|--------|---------------------------------------|-------|-----------|
| B      | Byte (information content)            | float | RFCthis   |
| VA     | volt-ampere (Apparent Power)          | float | RFCthis   |
| var    | volt-ampere reactive (Reactive Power) | float | RFCthis   |
| J/m    | joule per meter (Energy per distance) | float | RFCthis   |
| deg    | degrees (angle)*                      | float | RFCthis   |
{: #new-unit-tbl title="New units registered for SenML"}

# Rationale

SenML {{-senml}} takes the position that unscaled SI units should
always be used.  However, SenML makes one exception: The degree
Celsius (as Cel) is allowed as an alternative to the K (Kelvin).

This document takes the position that the same should apply to
a small number of alternative units in wide use:

* The Byte.  {{IEC-80000-13}} defines both the bit (item 13-9.b) and
  the byte (item 13-9.c, also
  called octet) as alternative names for the coherent unit one for the
  purpose of giving storage capacity and related quantities.  While
  the name octet is associated with the symbol o, this is in wide use
  only in French-speaking countries.  Globally more wide-spread is the
  symbol B for byte, even though B is already taken in SI for bel.
  {{-senml}} therefore registers dB as the SenML unit for logarithmic relative
  power, leaving B free for the usage proposed here.  While this is
  potentially confusing, the situation is widely understood in
  engineering circles and is unlikely to cause actual problems.
* The Volt-Ampere. {{IEC-80000-6}}} item 6-57.a defines the VA (volt
  ampere) as a unit for apparent power; items 6-59.a, 6-60.a and
  6-61.a also use the unit for complex, reactive, and non-active
  power.
* The Volt-Ampere-reactive.  {{IEC-80000-6}} item 6-60.b defines the
  var (volt ampere reactive) as an alternative (and fully equivalent)
  unit to VA specifically for reactive power (with the primary unit
  VA).  It is not presently known to this author how the upcoming
  revision of IEC 80000-6 will update this, but it has became clear
  since that there is strong interest in using this unit
  specifically for the imaginary content of complex power, reactive
  power {{IEEE-1459}}.

The unit "degrees" is unit in wide use in practice for plane angle (as
in heading, bearing, etc.).  It is marked with an asterisk because the
preferred coherent SI unit is radian ("rad").

The Joule per meter is not a traditional electromagnetic unit.  It and
its scaled derivatives (in particular Wh/km) are used to describe the
energy expended for achieving motion over a given distance, e.g. as an
equivalent for electrical cars of the inverse of "mileage".

# Security Considerations {#seccons}

The security considerations of {{-senml}} apply.
The introduction of new measurement units poses no additional security
considerations except from a possible potential for additional
confusion about the proper unit to use.

# IANA Considerations {#iana}

See {{new-units}}.

# Acknowledgements {#acks}
{: numbered="no"}

Ari Keranen pointed out the need for additional units in SenML.

--- back
