# HTTPAPI WG Meeting - IETF 112

Friday November 12th 12:00 UTC

* Chairs: Darrel Miller, Rich Salz
* Minutes: Bron Gondwana

## Administrivia

- Note well
- Note-taker
- Jabber Scribe
- Agenda bashing

Slides: [insert URL here]


## Draft Updates

Review of existing documents (90 minutes total; 10-15 each doc)
-	Link Template https://datatracker.ietf.org/doc/html/draft-nottingham-link-template-03
-	Deprecation Header https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-deprecation-header-02
-	Idempotency Key https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-idempotency-key-header
-	Linkset https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-linkset-04 (done, ready to advance?)
-	Ratelimit headers https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-ratelimit-headers-01 
-	rfc7807bis https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-rfc7807bis-01 

## Discussions/Any Other Business

# MINUTES

Rich gave the notewell and the really well.

### Query Method (from HTTP working group)

Mark Nottingham presenting

(it's called safe-method-with-body) https://datatracker.ietf.org/doc/html/draft-ietf-httpbis-safe-method-w-body-02


New HTTP method (QUERY) - safe, idempotent, cacheable.

Like GET but with a body.

Comments?  Looks useful from chat.

Phil Archer: nothing that defines format of query? 

Mark: same as PATCH - defined the command, but not the format.  Don't think we need a common query format (out of scope for the HTTP working group, has a lot of semantics)

Mark: would be great for someone to come up with a graph for a standard format.

Phil: seeing this SQL example makes me think "that's what you want to do"

Mark: mirrors the query format in URIs.  People think it's name=value, but that's just HTML.

Question about the name - is "QUERY" right?

Mark: we couldn't come up with a better name.  Could also call it GET_WITH_BODY, but that's not the direction we took.

Or "FAT_GET", or "FETCH" (via chat)?

Erik Wilde from chat: would be good to give advice for people moving from POST.

### link template

Mark Nottingham again

Question: is there interest in adopting this?

There are some open issues.

Phil Archer: yes, this fits well with work in digital link.

Link relation "handled-by" - for general redirects.

Darrel: use case when returing a list of that contains a whole lot of things, want to create a list that links for each of them.

Q: is the var-base a way to create a globally unique value?

Mark: yes, to give it a namespace so you can find what a widget_id means.

Mark: pretty straight forward, not a big spec.

Martin Thomson: var-base isn't straightforward (via chat)

chairs: what next?

Mark: could do a call for adoption.

ACITON: call for adoption for link-template on the list.

### linkset

Erik Wilde presenting

There are implementations out there already!  GS1 and FAIR (see slides).  Keen to get it stable so they have a place to reference.

Phil Archer: Johnson and Johnson and Proctor and Gamble among others.

Currently 0 open issues, think

Rich Salz: IETF is often deadline driven. People often come out of the woodwork when there's a deadline.  Rich explained in detail how the shepherding / publishing process works.  The process takes a while, but still a couple of months maybe.

ACTION: chairs will issue a 2 week working group last call.  Rich will write the shepherd's writeup.

### rfc7807bis

Darrel Miller presenting

Two major issues.  HTTP problem warnings and "attach warning to regular request".  Second one has been punted to another spec.

Mark N: just closed this issue, the conversation seemed to conclude that it's OK.

Erik Wilde: wanted to support what Mark said.  We have an example, but it looks like a mechanism.  We have to go one way or the other.  People might think this is a thing and use it how they think it works.  That would be the worst case!

Sanjay Dalal: it is just an example.  Based on comments, can put some more words cautioning that it's an example only.

Mark: Different classes of multiple problems - multiple instaces of the the same problem type, or multiple different problem types.  Maybe all have the same recommended status code - in which case you should use that.

The only time to use 207 Multi-Status is when there are incompatible recommended HTTP status codes.

Sanjay: tried to combine, but agree with Mark that we can have separate examples.

Mark: think this can all be handled as part of the editing.

### ratelimit-headers

Updated recently.

Most popular items - naming of headers.  Compat with existing deployments?  But current practice starts with X-, so we'll already break compat.

Mark: scoping applicability of a header being left out / amiguous can make it really hard to figure out later.  Intuative thing would be to not define a static scope, say it's undefined, but define a vocabulary of primatives that people can use to scope it (eg to a site, resource, etc)

### deprecation header

Erik Wilde presenting

No new version of the draft - encourage people to read it.

Very simple mechanism - can say "is deprecated" - or will be deprecated in the future.

Discussion of whether the example is valid - tending towards yes.

Design is already in the wild

Mark: in semantics revision, documented multiple forms as bad practice (true vs date).  Causes parsing issues.

Sadly OpenAPI uses boolean, so - don't use that as a model to follow.

Erik: use sunset - haven't heard any complaints about it, but agree it's not best practice.

Sanjay: think it's easy enough, won't be confusing.

Darrel: just when mapping to programming languages it makes things hard for devs.

(via chat - "we'll fix OpenAPI", "do it! not much use out there")

### Idempotency key

Erik: need some kind of correlation key, don't have that now, if we wanted to map to OASIS repeatable requests.

DarrelL what's better?  Simple way in IETF spec and point to OASIS for repeatable requests, or make IEFT spec allow both types.

### api-health-check

Sanjay: This is a common problem, having it defined in a standard way would be useful, but there are a lot of popular implementations, and if this is different that might hinder adoption.

Erik: with many things, there are 20 ways out there already, and we come up with the 21st way and hope it's more convincing than the others.  Think for health-check, it's a pattern in a lot of APIs so it could have some impact to do it here - a building block that you don't have to come up with by yourself.

Darrel: it's a media-type like problem, which addresses a horizontal need.

### Other business

Mark - add ideas of whatever you want to work on - I can help, but have limited time so upvote/downvote what you're interested in!

### purpose of group

About this group: we need to finish some things before we take on too much more work.

Darrel: Was supposed to be revised a while back - but this is somewhat diferent to other groups because we don't have stuff to do.

Mark: kind of put a poison pill in this charter, because wanted to have a link to people doing real APIs in the real world - if it was just IETFers chatting about APIs then didn't want to keep it going forever.

Mark: suspect if we get runs on the board - specs shipped that add values to the API community, then we might get more people come here.  Would be great to ship specs and see what happens next.  Have been happy with the nature of the meetings, maybe we even need interims occasionally.

Francesca: there is requirement in the charter to assess whether group is functioning well, so action for Francesca to take to IESG and have a discussion.  Personally think it's functioning well, but it's subjective!  No documents yet doesn't necessarily mean it's not working well.  Agree interims might be nice.

ACITON: Francesca will have an informal chat with the IESG.