
# HTTPAPI at IETF 121

Wednesday, Session II, 13:00-14:30 UTC
Liffey MR 3

## Chair

Note well reminders
Note taker(s) Rich in the notepad; volunteers can contribute
Document update
- api-catalog submitted
- deprecation-header in RFC queue

## Documents

See the meeting materials for all slides.

Privacy (exposing API keys via HTTP) -- Mike Bishop. Marius: there are authenticated requests that don't contain private material, such as AWS (key-id,signature) method. Mike: Can requests be replayed? Marius: often there's an expiration date. Darrel: Don't see it in the GitHub repo. *Rich to fix that* Lucas: are other HTTP mechanisms such as chunked, that could do the protection? Mike: Maybe there are oter mitigations like this. Mike/Lucas think of some words about that. JHoyland: some mitigations could be bypassed by listening on port 80 for example. Maybe credential is hash(tls-exporter,credential) to avoid re-use. Mike: yes, not listening on 80 is still susceptible, adn that seems like a way to void sending credentials. JRicher: Jon's idea sounds like token binding, and there's lots of baggage/issues with using them. Mike: Want to focus on deployment using existing things. Jon: I agree. Maybe use http or https as first item of the hash.

HTTPbis signature work -- Justin Richer. Intro to 9421. It is end-to-end, compared to TLS hop-by-hop, and handles dealing with HTTP semantics that can change over hops. Lucas: thanks for accepting for volunteering, the https://httpsig.org/ site is very useful. Marius: can I use signatures to identify the client, or just verify the integrity of the message? Justin: Yes, you can verify/validate the key, so at laest authenticate the software making the call (and doesn't seem like a good idea to verify users).

Digests-fields problem types - Marius Kleidl. RFC 9530, HTTP Digest Rields. Does not have a method for signaling integrity/digest errors back to client. RFC 9457 has problem details for HTTP APIs; this is defining digest-specific problem types as instances of 9457 messages. Lucas, as a co-author: maybe add a couple of high-level problems, not boil the ocean and define super fine-grain issues. Justin: support this, but be aware of oracle attacks (giving away information to an adversarty); here's some examples of signature failures. Not opposed but there's lots of work. Thibault: Do you have specific types of errors? Lucas: not many for reasonable reasons. Rich: maybe do problems types for signatures later, not in this document. Justin: Needs work filtering through problem/responses. I agree we should not make it part of this document, will contribute. Darrel: see chat discussion about maybe needing naming guidance for structuring error identifiers. *To confirm on the list*

REST media types -- Roberto. Summary of current state and open issues/solutions. See slides. Darrel: we can register media-type for a complete OAS doc. This is possible now because of 3.1.1, and we don't need a "component" identifier. Avoids the structured suffix issue. Darrel to review and see if it's now ready for WGLC.

Patch-byterange -- Austin via email: been busy and travelling, will give updates before next IETF.

Ratelimit-headers -- Darrel as co-author of the. draft, not as chair. Added that multiple named policies can be in effect. Added quota-units, with a few base one and a registry. Others, too, see the slides. Hans-Jorg: I think partition key is very useful; perhaps "user" and other built-in categories is useful, also maybe organization and client-id. Darrel: Maybe, I prefered to use concepts from http, jwt. Hans-Jorg: that's a good point, to discuss. Justin: detailed issue about syntax; need a registry and syntax rules. Darrel/Justin: Agree about "take inspiration" is the right intent. Marius: agree PK's are useful, want to document names/meanings in API doc. Maybe provide advice about what to do when rate limits are reached. Darrel: we should think of problem types for all such errors.

Idempotency-key-header -- Lot of discussion. Chairs made consensus calls that idempotency service are out of scope. But please look at the open issues in the repository.

## Expired documents

- authentication link -- got SECDIR review, need WG please review the issues in the repo

- link-hint - Mark, needs to be modified to use structured fields, takes some slow careful work.

## Any other business

Out of time.

