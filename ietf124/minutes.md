# HTTPAPI at IETF 124

- Tuesday Session 1, 14:30-16:00 UTC
- Centre Ville

## Chair

- Note well reminders

- Note taker(s): Rich Salz

## Documents with Content Updates

- link-hints, Mark Nottingham
Maybe an editorial pass.  *Are there hints we missed?* Anything about AI hints? WGLC soon, after the current WGLC docs move on.

- patch-byterange, Austin Wright
No new content changes. Open issue about specific content types or opaque byte stream. Avoided overlap with HTTP WG effort. Looking for another implementation.

## Brief document updates

-- digest-fields-problem-types
In WGLC ends Nov 10, so please review.

-- httpapi-privacy
Finished WGLC, minor update, Darrel to do shepherd writeup and send to IESG.

-- rest-api-mediatypes
Clarification on the version parameter to ref OpenAPI spec. WGLC done, Darrel to write shepherd writeup.

- Update on "JSON Structure" and "JSON Schema"
Had conversation with ART AD's about getting an IETF "final" version of JSON Schema. Lisa Dusseault will be a point of contact for efforts on this, wherever it ends up.

Andy, ART AD. We have a mailing list for JSON structure, no activity, indicates not much interest. Had call with ECMA about JSON Schema.

Austin: I think JStructure is interesting, I owe the list some mail.

## Documents ready to move to WGLC?

- idempotency.
Not ready, some open issues (e.g., caching of responses). Still needs some work to do.

- ratelimit-headers (waiting for HTTPDIR review)
Discussion about what the "t" parameter means, didn't work with sliding window algorithms as it was an absolute window and complete reset. Doc fixed. Main open issue #158, should the policy parameter a string (requires quotes) or a token?  MNot: fine to use a token as long as you understand the constraints. Or could be token-or-string. Darrel: would that work? MNot: yes. Lucas Pardue in chat says working on it is on his queue. MNot: don't take 9651 as "hallowed documents." Marius: use string, two quote characters are not a big deal. MNot: that's reasonable.

## New Documents

- HTTP Events Query; adoption?  Rahul Gupta
Uses QUERY method to request notifications. Defines an abstract data model, an Events header, response semantics. Supports streaming and polling. Design leverages all of HTTP facilities. See slides for design goals list, etc.
Austin: this space needs a new foundation, existing HTTP streams are not very interoperable. What are the benefits to intermediaries/CDNs? The standard is structured for response styles. Austin: the incremental header solves a lot of problems. Rahul: yes it helps, also to prevent buffering. Austin: what about indefinite content? And if a client requests, what do they get or does it block until finished uploading? Rahul: wait for the resource to be finished before notifications. Austin: how cacheable? Rahul: I don't see why intermediary doesn't work.
Austin: I think we need more exploration, there are a lot of interesting problems to be explored.
Discussion about byte-range draft overlap with this doc. To be discussed on the list.

Darrel: need to clarify value and drivers and then consider adoption.

## Expired documents

- authentication-link



## Any other business