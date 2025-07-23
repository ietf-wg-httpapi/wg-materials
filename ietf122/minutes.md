# HTTPAPI at IETF 122

- Wednesday, Session I, 02:30-04:30 UTC
- Boromphimarn 5

## Chair

- Note well reminders

- Note taker(s): Rich

- ADs
Thanks for your work Francesca, welcome Mike.

- Brief document updates
-- api-catalog in RPC queue
-- deprecation-header in RPC queue (one of our first docs!)

## Documents with Content Updates

- link-hint
Please review and provide feedback

- rest-api-mediatypes
It's really now registering OpenAPI media types.
Two open issues, hope for WGLC before next IETF meeting.

- ratelimit-headers
Much feedback last time, very appreciated.
More explicit and obvious use of structured fields.
New problem types introduced to explain why client was rate-limited. Would like feedback on them.
Darrel has an implementation on GitHub to check this is implementable; URL in the slides.
Mike: maybe add a response field that server can send to indicate the true cost
*WG FOLKS* Please think about adding such as response field, if we get feedback we can move to WGLC by IETF 123.

## "New JSON Schema"
A major rationale: is hard to make tooling for JSON Schema, Avro is also better suited for data-binding.
You can think of this as a refactoring of JSON Schema; some features removed, more data types (that can have attributes). They also have serialization rules to/from JSON string.
Restrictions on $defs/$ref for reusable types.
Documents, etc., at https://github.com/clemensv/json-cs/tree/main/jsc (also posted to list)
Andy Newton as individual: I like this, hope it moves forward
AN as ART Ad: Need to be careful about the name "Json Schema"; might be question of venue. Please also send to art@ietf.org
Clemens: Not wedded to the name, but do want to leverage the existing JSON schema drafts for mindshare.
Darrel as individual: agree JSON Schema is hard to do code-generation and it seems to be stuck right now.
Andy: I think the confusion about JSON is reason enough to look at this.
*Chairs and ADs to determine a proposed way forward.*
Darrel talked about politics of personal views of various JSON authors, IETF relationship, etc.

## Documents ready to move to WGLC ?

- httpapi-privacy
Mike Bishop (as co-author): need to do some work, not ready for WGLC.

- digest-fields-problem-types
*Chairs to request SECDIR early review*
Question about adding Message Signature (RFC 9421) problem types to this doc?
Justin (author of 9421): I think it makes sense to keep them separate; signatures are pretty complex and have oracle considerations, etc. Consensus to keep them separate

## Expired documents

If anyone wants to work on either one, contact the Chairs

- patch-byterange

- authentication-link

## Any other business

