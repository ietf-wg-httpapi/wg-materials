# HTTPAPI at IETF 111

* Tuesday 2021-07-27 14:30 PDT (21:30 UTC)
* Chairs: Darrel Milller, Rich Salz
* Secretary: Mark Nottingham


## Last call for Linkset draft-ietf-httpapi-linkset-03 (Darrel Miller)

https://datatracker.ietf.org/doc/draft-ietf-httpapi-linkset/

Approaching WGLC; one open issue on mailing list to discuss.

[Should JSON representation include multi-lingual titles?](https://mailarchive.ietf.org/arch/msg/httpapi/lTMEGZS-vFQVDrc7CFscrLAeTn0/)

Consistency vs. complexity trade-off

Should take to list; not all stakeholders are present.

Phil:  Implemented as-is, wasn't a problem; would prefer it not change now.

Mark:  Need to dig in more.

Conversation returned to list.

## Update on RFC7807bis (Mark Nottingham)

https://datatracker.ietf.org/doc/draft-ietf-httpapi-rfc7807bis/

Close to WGLC after these issues are dealt with.

### Multiple Problems - #6

HTTP status code for multiple statuses is "quite obscure"

Recommendation is "pick one to surface"; some support on issue, but unsure on consensus

Sanjay:   Lack of support for multiple errors has led us to custom error responses in the past. Bad for acceptance of 7807.

Mark:     Unclear whether that's because of lack of guidance or because it's actually needed.

Darrel:   MS follows from OData, but not much used. Mostly seen on batched operations where some succeed and some fail; not generalized.

Mike A.:  Pick first and stop there. Don't invent something that messes with status codes.

Mark:     Advice about granularity is probably useful here.

Jayadeba: Could not use 7807 for this reason; supporting this would aid adoption.

Sanjay:   Multiple instances is more common; multiple problems is limited.

Mark will author a PR to see if that gets consensus.

### Repository of common types - #7/#24

HTTP or URN prefix?

Max:      Linked to error page; would this make that impossible?

Mark:     This isn't for custom errors. Advertisement for registry versus potential load issue and compactness.

Jayadeba: This could be used for non-HTTP protocols; is HTTP appropriate?

Mark:     Just an identifier; no dereferencing. Also, this is HTTPAPI.

Sanjay:   HTTP response might come from another source.

Mike A.:  URN is less likely to be dereferenced accidentally.

Mark will try URN and see if it sticks.

### Indication of URI resolvability - #15

7807 doesn't allow new fields, for better or worse.

Derk-Jan: Encourage people to make docs resolvable. Put in Link header or a new member with a short name.

Mark:     If your docs aren't intended to be resolvable, use a URN.

Sanjay:   Separate Link header might not help; should be with the object. Should help consumer resolve the issue.

Derk-Jan: Link indicates resolvable; use URN if it's not resolvable.

Mike:     Use URN when it shouldn't be resolvable.

Keep default that type is resolvable to docs. Refine text to clarify principles.

## Introduction to Idempotency Key draft (Sanjay Dalal & Jayadeba Jena)

https://datatracker.ietf.org/doc/draft-ietf-httpapi-idempotency-key-header/

Lots of similar approaches to this problem, including Post-Once-Exactly.  Draft standardizes header usage.

Several users already.

### Behavior on repeat posting - #2

Should it return the result of the previous operation, or the current state if it has changed since?

Proposal: Previous result; client can make conditional GET to check if state is current.

Should the status code indicate whether the request has already been made?

Proposal: Previous status code; just indicate that it was done.

Should the server retry when the previous status was a recoverable error?

Proposal: Want to clarify that server has option to retry.

### Similar OASIS Standard - #5

Will invite OASIS to discuss with WG on how they align.

Mark:     History shows cross-SDO standards are rough. Invite OASIS folks here or our folks can go there, but joint efforts are fraught.

Rich:     Agree, different rules for participation.

### Comparison with conditional requests - #4

Will discuss other approaches in appendix.

Mike A.:  Examples so far rely on server state; conditional requests have been around for a while.

Mark:     New conditional request mechanism isn't trivial; need to involve HTTP WG.

Mike A.:  Talking about applying to POST, not creating new ones.

Mike & Mark will sync about http-core.

## GitHub Discussions

Please review discussions at https://github.com/ietf-wg-httpapi/discussion/discussions

# No time for other topics.
