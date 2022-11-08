# HTTPAPI at IETF 115
Chairs: Darrel, Richard
Secretary: Mark
Minutes: Rich, Erik Kinnear, Momoka


## Ben Schwartz, Interactive Authentication of non-Interactive HTTP Requests
#https://datatracker.ietf.org/doc/draft-schwartz-httpapi-popup-authentication/
[slides](https://datatracker.ietf.org/meeting/115/materials/slides-115-httpapi-interactive-authentication-of-non-interactive-http-requests)
(Also presented at OAuth)
"Popup authentication"
see slide.

Martin Thomson: lots of popups are problematic. Does application have to control the browser, pull out cookies, etc? Right now it's cut/paste screen display with "the token". That's an important use-case but maybe not the only thing we need to discuss.

Mike Bishop: Sympathetic to abuse, but it's just a different popup not a new one. WWhat does this address that "redirect to local server" doesn't? (missed answer, sorry)


Aaron Parecki: 1st slide is all we need. A lot of things is done in OAuth. Do need to address new clients not known to oauth server which isn't within oauth use cases. oauth wg is looking at that.


Pieter Kasselman: be careful around security side; this seems to allow new lateral or other attacks. Try to avoid having the end-user having to make a decision, at least give them information to help them avoid making a bad/insecure decision. Attackers are focusing on the end-user not the protocol now and getting sophisticated.

Eric Kinnear: We use a custom URI scheme to have auth content come back to the application.

Ben Schwartz: The difference is that we shouldn't need to hardcode this for any list of services

Eric Kinnear: Lets reduce the bouncing around. Less user confusion.

Martin Thomson: What does the website know about the client? I'm thinking of "crates.io" knows me, does the auth, passes that back to the client. Ben: yes.

Ben Schwartz: the authentication will be from the same origin.

Martin Thomson: 

chair: this is useful to HTTPapi world but it's work for OAuth for this to work.

Ben Schwartz: We will make a more OAuth version of this protocol.

Aaron: I agree to the concerns of unknown clients talking to unknown servers. Will write what is a assumption and how to deploy it.

OAUTH folks agree to work on this in OAuth.

## YAML mediatype; yaml-mediatypes Roberto Polli

Roberto: in WGLC, media type people gave positive feedback and suggestions (e.g., change the extension from yml to .yaml)  Main open issue is clipboard identifiers.

Alexey Melnikov: registration seems fine, MSFT is first-come first-serve so expect nothing to do; Alexey ee approve it.

## WG Documents - Status Update, Darrell

- Deprecation Header: format of Date header, maintain compatibility with Sunset header, should we merge? Let's decide now to avoid revisiting it in IETF 116. Mnot only commenter. HTTP will be using @integer-since-1970-epoch for dates. They are okay with Deprecation header. Roberto: prefers human-readable not an integer.  Mark: we will need to reply to IESG if we don't use an existing IETF practice. Darrel: world is moving to a display aide for headers

- Idempotency Key. Last issue to be closed now. Any comments from the room? Any interest in using it? A couple of non-committal yes's. Marius: resumable uploads in HTTP WG is thinking of using it.

- Link Template. Now uses structured fields. Will handle issue about "anchor" header using templates.  Then ready for WGLC.

- schema+yaml: waiting for schema folks to address fragments.

- Problem Details for HTTP APIs

- Rate Limit Headers. Discussion about one header field with structured values, versus three "simple" headers. Roberto: believe industry uses/wants three fields, merging will diverge from industry practice. Chris: I am sympathetic that intermediaries don't currently have all the parser, but Im skeptical they won't. Mark: should not focus primarily on current syntax; RFCs are long-term, should think of future. If we did this for Cache-control and split into separate fields it would be bad. Sbhould split headers by semantics, not just into separate header fields. Roberto: I am concerned about diverging from practice. Rich: x-ratelimit might be current practice, things are changing. Chris: are we documenting existing practice or defining a new standard? 

ACTION: Strong consensus for structured fields. Will confirm on the list, and ask the authors to do a PR that uses structured fields.


https://ietf-wg-httpapi.github.io/


## Proposed WG Documents

popup-authentication (see above)?

