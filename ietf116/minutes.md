# HTTPAPI AT IETF 116

Minutes: https://codimd.ietf.org/notes-ietf-116-httpapi

## Administrivia

- Note well
- Francesca on leave 1 April -- 31 August
- Note-taker; Rich
- Zulip/Meetecho Scribe
- Agenda bashing

## WG Documents - Status Update

- Link-Template HTTP Header Field Submitted
Francesca did her AD review, another AD has been assigned to carry it forward. We'll work to give background to them and keep the document moving forward.

- Problem Details Waiting for announcement
MNot: [issue 74](https://github.com/ietf-wg-httpapi/rfc7807bis/issues/74). 72? Erik Wilde noticed that future standard-defined elements start with a an asterisk, which doesn't work for XML since field names must start with alphanumeric. Proposed to start with "STD-", subsequent discussion was to do this "properly" and make an XML namespace. Think this is too comlicated and not backwards compatible.

Another issue Erik noticed post-IESG review, body text in 400 status responses doesn't really much best practice. Will do a PR and show on mailing list.

Austin: I suggested *sorry lost network*

MNot: Do we need to change the XML serialization to be more comprehensive?

**To be confirmed on list, stick with STD- and document XML serialization limitations.**

- YAML Media Type Submitted; hand-off being decided
Roberto shared slides; see the meeting materials.
Was blocked by waiting for feedback from JSON schema and OpenAPI community; JSON-LD removed from draft and sent to W3C.
Sent to IESG. Two issues:
- Deprecated media-types were never registered, should be documented
- Should we RECOMMEND .yaml instead of .yml? Right now we say "prefer"

**To confirm, we want to RECOMMEND .yaml over .yml**

## WG Document Presentations

- The Idempotency-Key HTTP Header Field
One open issue, #21, about structured fields.  Should we use a binary SF instead of a string SF?
As sf-string, a UUID is "123456" as sf-binary it is "12:34:56"
Binary makes it clear to remove strings and not be case-sensitive, string comparisons *could* be implemented sloppily. We should follow common practice, if there is any.

Justin: as someone coming from the outside, UUIDs as binary seems wierd to me.
Rich (as an individual): agree with Justin.

**To be confirmed (sf-string) on the list.** Have another draft, then go to WGLC by end of April.

- Rate Limit Headers
Latest draft merges three headers into a single header using structured-fields.
Roberto: backward compat is not an issue since this is a new header. That was a big concern for me.
Bringing on a new co-author to help finish off, since Alex doesn't do API work much any more.
Darrel to be a new co-author.

- Deprecation Header
There are some open issues. Perhaps main one is structured field Date.
Erik: Sunset header used old-fashioned string format/syntax for dates. That was model for Deprecation header, then got guidance to use SF for now work. Got the suggestion to just use integers (not readable, no sub-second resolution). Should we use old (string) or new (SF) value?
Darrel: Do you know current state of sf-bis document, which defines dates?
MNot: strong consensus about the right way to do it, the draft (sf-bis) is nearing completion. In London we talked here about takling a step back and looking at the whole lifecycle.  Not much discussion. Any views?
Erik: I think an API lifecycle header field is interesting, but would stop Deprecation work, and seems like much more work. I agree it would be interesting, but I think it's just an idea.
Rich: what impact doeds this have on user-agent/client connecting to a server?
MNot: that is the key question; this is often not a user in front of a browser.
Darrel: In our code we log/report uses that trigger deprecation fields.
Hans: I recall a fall-back from London, any thoughts? What about maintenance windows, can that be handled?
Erik: It's interesting for the lifecycle approach. As the draft is written, it's just purely deprecation soon to be removed.
Rich: I see nobody volunteering to write lifecycle document.
MNot: But should we move it forward just for inertia?
Q Misell: Agree with Mark.
Darrel: There is existing use; can we document current practice or be more forward looking?
MNot: We're going between two paths, documenting practice or moving the indjustry forward?
Santario: Darrel it's out in the wild, do you have numbers?
Darrel: Can't say more than "non-trivial amount", sorry If they're already using it succesfully do we need to write a spec?
MNot: It's different for APIs which are can be implemented in one place, not necessarily in generic tools. I'd be more comfortable if we looked around first.

**WG to think about it's role and talk about it on the list.  Deprecation header compared to a general "lifecycle" concept is an example.**

- REST API Media Types

## Proposed WG Documents

- Link relationship types for authentication; Evert Pot
Common to use IANA link registry as a vocabulary. Authentication-related API's are commonly needed. I wrote a document in 2019, several people asked me about standardizing it, so I brought it here.
Defined four link types (authenticate, logout, register-user ("sign up"), authenticated-as ("who am i"))

Maybe drop register-user from draft, does not seem to be used. Maybe change `logout` to something more descriptive
MNot: I raised the name-change issue. Link relations are semantic or functional. I support adoption, especially as I am the designated expert for link relations.

Hans: Do I see this once when I connect to the site, or each time?
Evert: The answer depends on what you're doing, probably. For example, public browsing compared to adding a new document. I would like browser to support logout, common chrome for logout-from-site
Ian: Logout could also be useful for password managers. I didn't see the idea of multiple headers, such as signon or single-sign-one
Evert: Link headers can have "titles" which could be used to distinguish.
Ian: Should doc be descriptive about multiple uses? *Editorial note: yes*
Darrel: did you have requests for a link relation to get an API key?
Evert: I think it exists in the OAuth2 world, and that might be the place for that.
Kenichi: *sorry, missed the question, work interruption*
Evert: answer missed.
MNot: To get most use out of link-relation need to document what the action should do. Could be all in the link-relation spec, or in the applications that use that. Seems like this is in the middle, and we can resolve during WG discussions.

**Strong consensus to adopt; to be confirmed on the list.**
If adopted we need to tell SEC area that we're working on this, for their review/input.

- Byte Range Patch; Austin William Wright
See slides.
Yoshi: character sets can be multi-byte. Bytes won't be the same if client and server uses different charsets.
Austin: Express the data as binary.
Ian: Logs are write-once, read-many.
Austin: Yes, I was treating it as not that :)
Ian: What if "expected length" isn't accurate -- is server expected to save that space? Should be documented in security considerations.
Austin: I agree.
Q: What if you run out of space in a multi-part request, for example?
Austin: that's an issue, HTTP is ambiguous about multi-part if they're atomic
Hans: I like resumable uploads. Is this more applicable to http WG? Seems like you're solving many problems in once.
Austin: I think of it as simple solution that solves many problems. Maybe we don't specify all three that are in the doc right now.
MNot: There is an RFC for indefinite-length Content-Range. I'm a bit conflicted about this. On the one hand, PATCH formats is in scope, on the other using byte-range ties it to HTTP byte ranges. I suggest you bring it to HTTP and introduce it.


## Discussions/Any Other Business

No time.
