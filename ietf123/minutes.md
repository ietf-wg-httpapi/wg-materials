
# HTTPAPI at IETF 123

Wednesday, Session III, 12:30-13:30 UTC

## Chair

- Note well reminders

- Note taker(s): Rich Salz

- Brief document updates
    -- api-catalog published (RFC 9727)
    -- deprecation-header published (RFC 9745)

- JSON Structure update
    - We are planning to have an interim BoF for JSON Structure. 
Drafts at:
https://datatracker.ietf.org/doc/search?name=json-structure&sort=&rfcs=on&activedrafts=on&by=group&group=
Mailing list for discussion of JSON Structure:
https://mailman3.ietf.org/mailman3/lists/json-structure.ietf.org/


## Documents with Content Updates

- link-hint (MNot); previous version used JSON for data model, normalization was tricky; now using structured fields, which means you can't specify level of details, etc., using this. Limiting the richness, emphasizes that these are *hints* rather than pointers with full description.
    - Looking for feedback  *Chairs to post asking for review and confirmation of the change*
    - A few issues open, not many

- rest-api-mediatypes (now is just OpenAPI registration)
    - Rahul Gupta: do you describe the target formats? MNot: No, this is just about HTTP-layer resources
    - *Chairs to issue verify with Roberto and then start WGLC*

## Documents ready to move to WGLC?

- digest-fields-problem-types (Marius Kleidel); Extends 9457 to express multiple problems with digests because there can be multiple objects digested, and have multiple digests (e.g., different algorithnms). A new type, Unencoded (e.g., orig content, not compressed), adopted by HTTPBIS WG.
    - MNot and Mike Bishop (WG Chair and AD): "we trust Lucas" Ask Lucas to reference this doc.
    - *Chairs to issue WGLC and nudge WG members to **Read** this doc*

- httpapi-privacy (Marius); API keys and privacy. Inspired by a blog posting explainign API key leakage over HTTP. Draft lists a variety of ways to reduce the likelihood of plain-text requests and when to revoke (if credentials are sent) or not (if content just has a signature).
    - *Chairs to issue WGLC and nudge WG members to **Read** this doc*
    - *Chairs to request HTTP directorate review*

- ratelimit-headers (Darrel); minor reference change since last meeting. Three new problem types (reduction, temporary reduction, identified abnormal behavior). Ask for HTTP review, did not get much and nothing negative. Hearing that people want this.
    - *Chairs to issue WGLC and nudge WG members to **Read** this doc*
    - *Chairs to request HTTP directorate review*


## Expired documents

- patch-byterange (Austin); a media type for writing bytes at a resource (see slides for examples)
    - Issue 1: non-contiguous/sparse resources (proposal is to make it out of scope and send to http wg)
    - Issue 2: Add a VCDIFF (RFC 3284) media-type for splicing, compression, etc. (e.g., tar files also)
        - Mike Bishop: since the format exists, seems useful, do it
        - Marius: Are there any registered media-types for diff? Austin: "diff -E" via OpenGroup. Git would probably be popular
    - Issue 3: Add a media-type for "Append" (slide says adverts means, avoids)
    - Darrel (media-type reviewer) support both these
    - Rich: Having one endpoint instead of two for "append" seems very useful
    - Darrel is this a mix of separate media-types?
    - Austin: changing the title to be more generic could help


- authentication-link
    - Been expired for awhile, if nobody volunteers we'll just "drop" it


## New Documents

- HTTP Events Query (Rahul); remembering Josh Cohen. See slides for definitions and design goals
    - Defines an Events header field
    - Revised to use a QUERY method; Accept-Query indicates to client it is supported


## Any other business
