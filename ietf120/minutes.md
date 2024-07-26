# HTTPAPI at IETF 120

Thursday, 25 July 2024, Session IV 1700-1800 America/Vancouver (0:00-1:00 UTC)
Room Name: Georgia A [Breakout 5] (size: 190)

## Admin

- Note takers - Rich
- Note well - it's a reminder of policies
- Agenda bashing/updates - no changes

## Doc status

- See the chair slides

## **draft-ietf-httpapi-idempotency-key-header**

Austin: I am concerned about the growing scope creep.  HTTPBIS someone suggested an idempotent HTTP-POST method. Perhaps we define a media-type parameter that contains the idempotennt key. There is some overlap wioth this and the braid in httpbis

Marius: I am surprised to hear the stripe uses an intermediate, given financial requirements. Glad it's working for them but I am in favor of supporting it.

Darrel (as individual): the interop in the draft is not well defined, it relied on common understanding of client and server. When we allowed client to send the key no matter what, scope expanded. I think we'll get lots of issues if we expand.

*Chairs to bring discussion to consensus by end of August.*

### **draft-ietf-httpapi-authentication-link**

Darrel: We got early review from SECDIR. *We will put it into github*

### **draft-ietf-httpapi-link-hint**

Darrel: link hints: has some open issues, Mark not here to talk to them.

### **draft-ietf-httpapi-patch-byterange**

Austin: Byterange: patch to write segments to a resource, the "reverse" of partial GET. Latest draft has text on indeterminate upload ranges. (Such as uploading streaming media.) Have another revision almost ready, addressing IANA considerations. Have questions on some of the field names. Want to know how this fits with braid.

Mike: I saw some discussion of units other than bytes. In HTTP we decided to allow other units, but in practice nobody uses them. It would be interesting if you could drive new uses. Interesting use-case when resource is gzip'd and you want to be able to talk about the 'uncompressed' content.

Marius: if you support other than bytes, maybe some things fields need to be renamed

Austin, will post questions to list after new draft is posted.

### **draft-ietf-httpapi-ratelimit-headers**

Darrel: Taken over ratelimit from Roberto. Have several updates that address previous reviews.  E.g., added a "unit" property and a "scope" which is "partition" so you can assign quota's to a set of resources. This is common on servers, but now we would have a way for the server to tell the client which partition to use and do appropriate self-limiting. Expect to have a new draft soon. Looking for feedback.

### **draft-ietf-httpapi-rest-api-mediatypes**

Darrel: openapi/json scheme mediatype registration. Blocking issue for security considerations resolved. Mediaman is discussing future of suffixes, like "openapi+json" and "openapi+yaml", etc. TBD what to do. But seems not worth waiting for them to respond.  Does "application/openapi" by itself make sense?  Post to the list.

## New work

### Problem types for HTTP digest fields (Marius Kleidl)

Marius presented slides on "problem types for HTTP digest fields" which are defined in RFC 9530.
Marius: problem types for HTTP digest fields. RFC 9530. There is no standard way for server to report digest mis-matches back to the client. (Deliberate decision) We can use problem-details RFC RFC 9457.  Define a new type (URL) "mismatching-digest-values" for example, and indiciation of what digest algorithm didn't match (in case client sends multiple digest) and the original digest value.  Small number of hihg-oevel problems: mismatch digest, unsupport algorithm, invalid value (e.g., length doesn't match the algorithm). Could also be useful for HTTP message signatures, RFC 9421.

Rich: http or httpapi WG?

Marius: I think this is more for machines, so I prefer httpapi

Darrel: the digest header includes the algorithm, so probably don't need it in the problem response.

Marius: useful to identify, in case client sends multiple digests.

Darrel: problem types are in an iana registry, so is the intent to describe the fields for the problem type?

Lucas Pardue: Not much to add to Marius, but there is HTTP signature drafts and they can use this.

Perhaps JonathanRichter can talk about signatures at IETF 121.

Austin: there are other things in HTTP that don't have standard ways of indiciating problems.

*Chairs to issue a call for adoption*

## AOB?

