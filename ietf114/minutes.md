
# HTTPAPI WG Meeting - IETF 114
Friday July 29th 14:00 UTC (10:00 America/New York)
Chairs: Darrel Miller, Rich Salz
Meetecho: https://gce.conf.meetecho.com/conference/?group=httpapi
Minutes: https://codimd.ietf.org/notes-ietf-114-httpapi

## Administrivia

- Note well. Big thanks to Martin Thomson for volunteering!
- Note-taker
- Jabber Scribe (chairs via meetecho)
- Agenda bashing

## WG Document Presentations

## RateLimit Field for HTTP; ratelimit-headers – Roberto Polli

RP: Almost complete
Issue 60 - use delta-seconds
Issue 35 - use SF (yay)
Lots of other good changes

Issue 105 - proposal to defer handling for trailer

Issue 65 - combining all four fields into a single one

Decision not to support this change.  No operational experience with a combined field. Implementers found a single field confusing.  Where SF parsers are not available, the simple integer fields are easier to manage.

Mnot: I understand the arguments, but it is not appropriate to be made based on data that is not brought to the WG by the people taking that position.  We need to make a decision as a WG.
Roberto: I don't want to take freedom of decision from the WG.  We attempted to combine fields, but this was the outcome.  We did our homework and this was the result.
SF is not a goal; the goal is to consolidate a standard.  The ecosystem is not ready for that.
Darrel: we can separate the issue of SF from the other
Martin: multiple fields is awkward, but maybe there is some value in keeping stable values separate from ephemeral
Julian: what kind of support is needed in nginx etc..? If there was a ticket, we might consider adding support.

Poll: Do you have an opinion on 3v1?
Result: ample opinion

Poll: 3v1 (3 is raise hand; 1 is don't)
Result: 7 for three headers; 6 for one

Rifaat: What is the rationale behind merging into one?
Mnot: I don't see any reason to spread across multiple.  If we are specifying these as structured fields, but make them appear to be simple integers; it's an attractive nuisance.  If you don't want SF, then don't use SF.  But that means specifying parsing and error handling to a similar standard as SF does.  No point doing that.  I don't find the arguments for 3 headers persuasive
MT: one is more efficient; one would have been easier to consume
Darrel: you return these on every response, which creates a burden on the network; the simpler from a processing perspective, the better.  One header to parse is easier and simpler.
Roberto: I think that if it would be easier and simpler, then someone else would have done it that way.  Implementers have done it this way, maybe that was wrong, but there is value in what community of implementers do.  Three headers matches that.  Would like to see data that one field is better.
Darrel: is it possible for an implementer to use the fields in isolation?
Roberto: you might use remaining and reset together (without limit).

Chair: please encourage people to provide feedback on the issue

## Yaml mediatype; yaml-mediatypes – Roberto Polli

Just focused on yaml and +yaml.

Issue 50 - fragment on +yaml documents
Roberto: I would favour the ability to use yaml ??? missed this, very, very hard to understand Roberto here.
Darrel: open API's use of yaml is what yaml calls JSON schema - the concept in YAML of the subset of YAML that will round trip to JSON. Does that include anchors?
Roberto: JSON schema that is defined in YAML is not really compatible with JSON, which includes +INT and NaN which are not in JSON.
Darrel: that feels like an error in the YAML spec, but the intent is to make the format round-trip-able.
Roberto: the native YAML fragment supports JSON pointers when it starts with '/'. If we do no enforce that openapi must use the structured syntax suffix, then it can define its own fragment identifier.  It can be different from the one in application/yaml.  Since the media type is openapi+yaml it is a different media type.  Each media type that uses a structured syntax suffix can define its own fragment identifier.  We should not hinder the ability to use XXX+yaml, because people are already using this.
Darrel: what now?
Roberto: ????
Darrel: application/yaml defines fragment IDs.  existing media types like openapi and json schema, when they use yaml tend to use JSON pointer, sort of pretending that the yaml is JSON (which works because it uses a JSON-ish-compatible syntax).  Roberto is suggesting that maybe just because application/yaml use this fancy format, +yaml types don't have to, but they can opt into that fancy format if they want.
Darrel: because RFC 6838 doesn't require X and +X to have the same fragment identifier definition, we can simply ask specs to be explicit
Mnot: the pattern is to rely on the common definition for the fragid, so that the +X specs get that syntax unless they define something else.  That's the pattern I've seen in the past.

Taking this to the list.

Issue 59 YAML -> JSON

Darrel: prefer to defer to the YAML spec; we can ask the YAML people to close any holes that might exist
Rich: if we try to define a conversion, that would not be in our charter; if there are people who want to do this, bring it to the list


## WG Documents - Status Update

### Problem Details for HTTP APIs

7807bis: Q to mnot, do we need a revision
mnot: need to check; we have a PR for a JSON-LD context (appendix); lots of discussion there but no resolution; I don't know JSON-LD well enough to decide; not sure about putting it in the specification
Darrel: why does this need to go into the specification?
mnot: this is a mapping into JSON-LD native language, though I do wonder about extension fields; don't have a good answer for why it needs to be in the spec
dret: it is not about JSON-LD; that's just mapping JSON to RDF data model.  To do that you need to define a vocabulary that the JSON maps to.  This is why it is so hard, because just putting a mapping in is not good enough, because JSON-LD is just JSON, but the point is determining what the RDF vocab is; this isn't going to resolve soon, not sure taht this community can get an answer in a short time
mnot: very helpful comment, but this will go into an immutable RFC; we can close that down then

### Deprecation Header

deprecation header: Current state of SF conversion discussion?
dret: lots of discussion on the issue, maybe we can poll.  draft follows Sunset syntax; discussion was to maybe switch to structured fields.  my feeling was that it would be better to match Sunset on balance. there was an idea to have a generic header for lifecycle information and maybe other lifecycle stages (experimental, GA).  That could use SF.  I kind of like that idea, apart from having to start from scratch.  Want to know what wins in a poll: match existing, or forward-oriented model.  Or what people think about the Lifecycle idea.  The lifecycle thing might take a lot longer.
mnot: separate from it being SF, I find the idea of lifecycle really intruiging.  one place to look and learn about the API status seems really nice.  I don't think that it would take a long time, it involves shuffling text around.  the hard part is the semantics.  We could do this pretty quickly.  I'd like to see things go in that direction.
mnot: in HTTP WG we are considering adding a date type to SF.  Lots of dates involved already; now is a good time to get these all right.  @\<RFC3339> or @\<int>.  Need input on this.  People are mostly headed toward the latter.  Feedback here would be very useful to take things back to HTTP WG.
dret: it would also be useful to have that.  a date type would be very useful.  we would definitely use that format if we go with lifecycle.  lots of other places can use date-time information.
Darrel: Julian points out in chat that we could start with just sunset+deprecation
dret: we do need extensibility if we do this, but we need to think about it being future proof.  if it is only two fields, no point in the lifecycle idea
Darrel: Julian was suggesting including an extensibility mechanism.
mnot: it would be super easy, because SF makes it easy.  We could update the document rather than defining a registry
Darrel: On date integer+epoch.  the origin time for the epoch matters.
mnot: just specify it
Darrel: it's not in the message
mnot: it is in the semantics

Poll: Align deprecation syntax with sunset syntax
Result: Not many votes

Poll: should we explore the use of lifecycle as an alternative/replacement to the sunset and deprecation fields
Result: 9:3 in favour

Will confirm that result on the list.

Julian: martin and mark might explain their discontent with the first question.  do we have any data about the adoption of sunset?
dret: I've seen sunset recommended in a few places, but it has been adopted in some places; received a few questions about deprecation

Darrel: bring discussion to the list regarding a consolidated field definition
dret: not buying the argument that this is simple
Darrel: for julian: it's an iso date
dret: oui

Julian: the fact that this uses HTTP-date is a good reason to keep consistency.  Even though it is a bad format, at least it has support everywhere.
Darrel: if we keep two headers, then you are saying keep the two the same, without introducing the ISO date



### Linkset

dret: request for cheesy fireworks for the first RFC from this working group

### Idempotency Key
Darrel: Sanjay not here. Only Eric following this specification.
Eric: Not following closely
Darrel: Expired, but updated to have a non expired version.
Eric: Thinks ISO date not good
Julian: Would prefer ISO, but maybe keeping consistency is better. Not inventing a new bad representation.

### Link Template
mnot: Structured field. Small inconsistencies ok.
Darrel: Linked template come up for OpenAPI world

## Proposed WG Documents

### Using The Date Header Field in HTTP Requests date-requests – Martin Thomson

abandoning the work on generic stuff.  OHAI are taking the important bits for them into their document

## Discussions/Any Other Business
None, meeting closed.