# HTTPAPI WG - IETF 113 Minutes

Thursday March 24th 09:00 UTC  (10:00 Europe/Vienna)

* Chairs: Darrel Miller, Rich Salz
* Minutes: Martin Thomson, Mark Nottingham

## RateLimit Field for HTTP

[slides](https://datatracker.ietf.org/doc/draft-ietf-httpapi-ratelimit-headers/) – Roberto Polli

Roberto: almost done with this specification; changed to structured fields; three fields; only using delta seconds for the reset time; the limit and reset fields are required (use both if you want to support this spec); 

### [issue 79](https://github.com/ietf-wg-httpapi/ratelimit-headers/issues/79): separate field for policies?

Suggestion is to make -limit a single integer, with -policy containing a list of all of the policies.

mnot: lots of fields, very verbose; might makes sense with different rates.  policy and limit are not dynamic.  can we combine all of this information into one field like a dictionary?

RateLimit: quota=10, remaining=6, reset=3, policy;l=10,w=3

roberto: implementers weren't willing to use a single header

mnot: this seems odd to me; would like to dig in and find out why

martin: a single field is workable; using SF with a single integer might lead to people taking shortcuts with SF syntax; and separate parameters can be very compact, working well with compression, even.

rich: ohai talked about this proposal or something like it for providing feedback between multiple entities

roberto: we might file an issue for OHAI

roberto: the feedback from implementers is that they don't even want to have the information in the same field

mnot: it's great that you are engaging with folks who are using similar things; implementers and potential implementers; when we do that, we need to ensure that we bring back their feedback in the form of arguments rather than preferences; it would be good to understand the reasons that motivate their preferences.  it's hard to parse "they want to" as feedback.

roberto: challenge is to find something that will be accepted by implementers

mnot: part of the challenge, yes; we might have different calibrations

bron gondwana: something that people want to use has value in itself; we're competing against people throwing anything they like in the header

dret (erik wilde): sometimes we have a different view of the people we're designing for; mnot seems to regard this as professionals, for those we might assume that they might use structured fields; in the API space we have a lot of developers who are not core HTTP developers, it's just a means to an ends; if you tell them that they need an additional parser, ... it's a different client base

martin: use sf parsers; hand-parsing is a footgun

mnot: parsing HTTP headers by hand is exactly what we want to avoid here; using integers hides the complexity, which might later break; using libraries is easy.  if we get feedback that implementers and users prefer things, that's useful input, but we only have one person's experience

darrel: most API developers are not implementing throttling infrastructure; the people writing throttling libraries will be making these decisions; hopefully consumes of those APIs will use a library.

hans-jörg: useful work.  I like Erik's distinction of user groups.  casual users will just be throttled by the APIs; people who want to consume this information really need to understand; agree with darrel about libraries.  let's make this conceptually clear

bron: regexes matching remaining would seem to be the general pattern I'd expect

mnot: the lag in meetecho is amazing; I don't want to paint this as a choice between extremes; one is a field per atom, no parameters; the other end is a SF with all the data packed in it; if it is not self-greasing, then it will break if someone adds a parameter; maybe we should write this up and see how things work out

darrel (chair): take this to the list/issues and move on

### [issue 41](https://github.com/ietf-wg-httpapi/ratelimit-headers/issues/41): upper bound on reset time?

not discussed

### [issue 65](https://github.com/ietf-wg-httpapi/ratelimit-headers/issues/65): field names

Roberto says no, but not discussed


## REST API mediatypes

[slides](https://datatracker.ietf.org/doc/draft-ietf-httpapi-rest-api-mediatypes/) – Roberto Polli

Roberto: trying to register some media type that are widely used. E.g., openAPI relies on YAML and JSON Schema, but they have not been registered. 

* yaml and +yaml
* openapi+json and openapi+yaml
* schema+json and schema+yaml
* ld+yaml

Martin (in chat): Who wants a JSON schema in YAML? should this be json-schema+json?

Roberto: Just took them from JSON schema community

mnot: go through the most official liaison channel you can in order to seek feedback from different bodies...  you need to ensure that they are OK with this or we can end up in a very awkward position

Francesca (from chat): please also involve mediaman.

darrel: the openAPI community is very supportive of this effort; they might be receptive to feedback

mnot: linked data and yaml

mt: consider splitting the document into multiple pieces

darrel: mediaman talked about multiple suffixes (+ld+json); we might benefit from stopping and separating things out

roberto: might be willing to work on something

dret (in chat): volunteers to help with an application/yaml and +yaml doc


## Document Status

Darrel shares his screen and his status.

We're a little unusual in terms of having lots of documents.  Shows [github project board](https://github.com/orgs/ietf-wg-httpapi/projects/1/views/1).

Projects are organization-global.  You can have multiple projects.  Repositories can be managed separately, but assigned to a project and tracked centrally.

mnot asks about what the policies are with statuses; is this set by chairs, or open for editors to set?

darrel: somewhat best effort, for editors to share status with  chairs; happy as a chair to tweak these and help out

question about labels, these are per-repository

rich: has a script that can create a standard set of labels

mnot (in chat): it's possible to setup a default set of labels for new repositories in an org (scribe note: though this might not work for transferred repositories)

### [Linkset](https://datatracker.ietf.org/doc/draft-ietf-httpapi-linkset/) 

Thank you to the authors for their patience. Just needs internationalisation review. Up for telechat on 27 April.


### [Problem Details for HTTP APIs](https://datatracker.ietf.org/doc/draft-ietf-httpapi-rfc7807bis/)

mnot: can we run through this?

AD HOC AGENDA BASH ACCEPTED

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/35

lukewarm response to this, should we drop this?

last call for including this in the spec

darrel: an interesting idea for something like warnings; how fatal is the word "problem"?

roberto: this can have some value

hans-jorg: argue for keeping it in

mnot: that's helpful; I will make a PR, which might reveal that it is a horrible idea

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/34

intend to merge a PR for this soon

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/6

sanjay was sad to lose examples, but we seem to have consensus, intend to merge a PR here too

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/32

blocked by another issue that is not on this listing...

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/36

7807 doesn't allow for new standard properties to be added to the structure; anything not in 7807 is in the problem type

this means we can't defined a new standard property as that could conflict with problem-specific fields

mnot: reviews the options: bad, worse, fiddly; against minting a new media type, defining a prefix might work, want to hear what others have to say

dret: suggest a prefix, but use URIs for the field names; a new media type isn't attractive; defining conventions means that new problem types need to opt-in specially, but that prevents new APIs from being able to uniformly use new attributes without all the problem types individually selecting those attributes; a prefix has a low chance of collision.

mnot: agree on most things; on the fiddly option, opt-in has some nasty interactions with tools; agree that the prefix scheme is OK; some developers will hate that; $/::/bikeshed-

darrel: conventions are tricky, which is something JSON schema allows with vocabularies and dialects.  you can add a vocabulary and declare a dialect.  there are some mechanics we can reuse, but it is somewhat dependent on those new-ish JSON schema features

mnot: that it looks like JSON might be a hazard, wary of doing stuff that might surprise people with a data model that is foreign to them

resolution: try a prefix, but defer the bikeshedding

https://github.com/ietf-wg-httpapi/rfc7807bis/issues/10

waiting for a proposal, if nothing happens we'll drop it from the spec

### [Idempotency Key](https://datatracker.ietf.org/doc/draft-ietf-httpapi-idempotency-key-header/)

Currently expired. Current status?
Darrel: will talk to Sanjay about bring this back to life

dret: it was not intentional to allow it to expire, but there are a few open issues that need to be addressed; we don't have a good plan on what issues need to be fixed before we create a new version, but we intend to keep it alive


## [Deprecation Header](https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-deprecation-header)

Not discussed.

## Using The Date Header Field in HTTP Requests [date-requests](https://datatracker.ietf.org/doc/html/draft-thomson-httpapi-date-requests) – Martin Thomson

Martin: This has come up in OHAI. Marking the time of a request is sometimes desireable -- especially for anti-replay. We could build something bespoke, but HTTP already has the Date header field. Allows you to limit the amount of state you need to keep to avoid replay attacks.

Martin: Biggest discussion is about the "bad clock problem." Very common issue, and often more drift than you'd think. To correct errors, suggestion is to copy the date from the response; new RFC7807 problem type to signal this.

Martin: is this useful? Is the group interested?

Mark: Focus should be on whether API folks find this useful; if we're not sure we can find a home elsewhere (HTTP or OHAI)

Martin: It came up because of a potential relationship with Idempotency-Key

Roberto: this is about timestamps, the title should reflect that

Darrel: don't see a lot of need for this (niche usage), relation to problem types

Mark: possible link to Signatures?

Martin: discussed; purpose is usage limitation, so the connection is weak

Mark: concerned about interactions with idempotency-key

Martin: claims that the two are complementary

Will update draft and bring it back to the list to continue discussion about the most appropriate venue for the work



## [Link Template](https://datatracker.ietf.org/doc/html/draft-nottingham-link-template-03) 

Call for adoption on list (honest)


## [Health Check](https://datatracker.ietf.org/doc/html/draft-inadarei-api-health-check-06)

Currently an individual draft. 

Erik: I got in touch with the author; not much progress. 


## AOB

Francesca: It would be good for the Chairs to create milestones.

Martin: Please don't put dates on them; they only mislead.

Rich: Yes; will discuss offline. Perhaps priorities would help.

Darrel: There's the possibility of setting up a Twitter bot to provide more visibility. 

