# HTTPAPI WG Meeting - IETF 118

Monday, 6 November 2023, 12:00-14:00 UTC

* Chairs: Darrel Miller (remote), Rich Salz (on-site)
* Secretary: Mark Nottingham
* Meetecho: https://gce.conf.meetecho.com/conference/?group=httpapi
* Zulip: https://zulip.ietf.org/#narrow/stream/223-httpapi
* Minutes: https://codimd.ietf.org/notes-ietf-118-httpapi

## Administrivia

- Note well
- Note-taker - Mark Nottingham, Rich Salz
- Zulip/Meetecho Scribe (optional)
- Francesca is back; area re-organization.  We are moving to the new WIT (web and internet) area.  No change in AD
- 
- Agenda bashing

## WG Documents - Status Update

### [YAML Media Type](https://datatracker.ietf.org/doc/draft-ietf-httpapi-yaml-mediatypes/)

In RFC Editor Queue. Was incorrectly marked as waiting for IESG; Francesca unblocked it, and it is now in EDIT state.

### [Link-Template HTTP Header Field](https://datatracker.ietf.org/doc/draft-ietf-httpapi-link-template/)

Two issues open regarding internationalization; that's what's holding it back. Please give input.

### [Problem Details](https://datatracker.ietf.org/doc/draft-ietf-httpapi-rfc7807bis/) 

Now RFC 9457.

## WG Document Presentations

### [API Catalog]([https://datatracker.ietf.org/doc/draft-ietf-httpapi-api-catalog/) 

Kevin Smith: -00 published; a well-known URI for a catalog for APIs. Aims to facilitate machine discovery and automated consumption. 

Kevin: Original draft proposed a format based on linkset. Some publish categories in different formats; likset, apis.json, HAL, RESTDesc, etc.

Kevin: -01 will remove the link relation; RFC6573 instead. 

MNot: Not thrilled with a .well-known but if it gets ignored that is okay.
I think we should at least have a default format.

Kevin: Fair points. In the -00 draft it gives an example; it's not going to recommend one. We can take up on the list whether we recommend one.

Sanjay Dalal: For big companies, there may be various groups with APIs. There might be multiple cataloges -- e.g., internal, public, customers, partners. Is it possible to have dispatchers from the main catalogue?

Kevin: I don't see why not. The format should be flexible. The question about internal or private APIs, it may be that the well-known URI for private APIs would be on an intranet host. Need to think about it more.

Darrel: Mark, I want to clarify -- were you saying there shouldn't be a well-known URI?

Mark: I wouldn't do it, but I won't block.

Darrel: There is not a github repo for this.

Rich: My preference would be to migrate repos over to our org. We get lots of contributions through github.

Kevin: Will do.

Rich: action to work with Kevin to get things into 

### [Byte Range Patch](https://datatracker.ietf.org/doc/draft-ietf-httpapi-patch-byterange/)

Austin William Wright: This is a media type for writing to a particular byte offset to a document, just like a filesystem operation.

Austin: One major question is how to represent indefinitely long writes. Doesn't fit into Content-Range.

Mike Bishop: Resumable uploads is in httpbis; if there's overlap, we should align.

Austin: Yes; this has spun out from that. This doesn't intend to replace resumable, but resumable could use it.

Marius Kliedl: I think changing the syntax is problematic. You're doing it in a special situation. This will cause confusion. Defining something new is a better alternative.

Austin: Agreed. Either will work; there may be others.

Mnot:  Content-range is kind of an awful header, it's from the "prehistoric" times. Had to be backward compatible. This doesn't have to be backward compatible, I don't see any advantage in re-using it. Define a new header, anyone can define one, just use structured-fields.

Austin: I think subscription updates, 206 responses, are possible future use-cases for this.


### [Link Hints](https://www.ietf.org/archive/id/draft-ietf-httpapi-link-hint-00.html)

Mark Nottingham. Recently adopted.

A specification to define pre-composed "target attributes" Intent is to come up with a set of link types that are useful. They are hints as to what's at the resource, not a contract.  It is in the WG github org. I haven't done work on it, will do so by next IETF.

Darrel: Why did you use the word "formats"?

MNot: We can change the word I picked six years ago, not a big deal.

### Side note

Darrel: It is very valuable to our current authors to provide feedback *now* before they leave the WG and face the IESG, directorates, larger IETF community.  It can be disheartening to authors who think leaving WG last call.

Francsco: Remember that chairs can request early review from directorates.

MNot: We have an HTTP area directorate which can review things.

Darrel: I updated the projects board so visit https://github.com/ietf-wg-httpapi and click on "projects" to see list.

### [Media types](https://datatracker.ietf.org/doc/draft-ietf-httpapi-rest-api-mediatypes)

Roberto Polli.  Still many open issues.  See
https://github.com/ietf-wg-httpapi/mediatypes/issues?q=is%3Aopen+is%3Aissue

Most are about JSON Schema. From Roberto offline email: 

> RE: the openapi spec, we should decide whether we want to proceed with a bare openapi mediatype reservation (e.g. without defining the fragment identifier, and without defining the relationship with json-schema) or finding a robust way to integrate a fluid json-schema spec.

Darrel: I think some issues can be resolved fairly soon. I am less confident about resolving json-schema issues. Should we split this so we can deliver the openapi registration?

Austin: There are only two registrations here. We've (the authors of json schema doc) been trying to figure out how to publish. This document lacks many of the interop requirements; we would not be able to be backwards compatible. Yes, let's break it up.

Darrel: Thanks. The other open question is about MEDIAMAN, regarding community formats to be registered in the standards tree. Does your work there make it not worthwhile to do these RFCs?

MNot: Intent is to make it eaiser for "legitimate" communities to register entries. Seems likely to be done, but also likely that the publication will be done as part of a larger comprehensive RFC that is being worked on. But that doesn't stop publishing RFCs.

Darrel: So if openapi definition is low-hanging fruit, proceed with RFC and if json-schema takes longer, see what the options are.

MNot: Yes.

Action: Rich/Darrel to talk with Roberto about splitting.

### [Auth Link Relation](https://datatracker.ietf.org/doc/draft-ietf-httpapi-authentication-link/)

Darrel: It doesn't have a github repo; that may be why we're not getting engagement. It's also expired. We should ask Evert to submit an update.

### [The Idempotency-Key HTTP Header Field](https://datatracker.ietf.org/doc/draft-ietf-httpapi-idempotency-key-header/)

Sanjay: I'll get to minor editorial issues. 

Darrel: David Benjamin proposed that the client could send the header even if it doesn't know if the server supports it. That isn't in the draft yet. If you could do the editorial work and push a new version, we might be ready for WGLC.

David Benjamin: I remember skimming the PR a while ago, but I don't remember. Happy to take another look.

### [Rate Limit Headers](https://datatracker.ietf.org/doc/draft-ietf-httpapi-ratelimit-headers/)

Darrel: We talked about correlation between the headers in the last IETF. We also talked about changing both fields to SF items, so you could have multiple policies. That PR has been updated and ready for review.

Darrel: Open issues about a scope parameter, with the ability be explicit about quota units. Using SF Item allows this. If folks have opinions about that, there are open issues on the repo. I haven't yet added text.

Darrel: The recent draft added a registry. Now that we're using SF Items, it would be a parameter registry. Is that an appropriate use of a registry?

MNot: What is in the registry now?

Darrel: l for limit, r for remaining limnit, t for timeout seconds remaining.  Right now you don't know, e.g., if limit is in # of requests or bytes. Now I'm not sure if hacing an arbitrary extensible set is a good idea or not.

Mnot: Generally use a registry for somewhat uncoordinated interop. But here, this is about core semantics of the RL header, and if you're changing things bring it back to the WG to issue a new RFC. Perhaps the units (and scope) need extensibility and a registry. For basic semantics, you probably want to create a bit more friction for uncoordinated extension.

Marius: I agree that a registry for types of units would be great.

Austin: I wonder about interaction with caching, if I client thinks old information from a cached object has outdated information.

Mnot: There is language in HTTP to address that kind of thing.

## Adoption?

### [Relative JSON pointer](https://datatracker.ietf.org/doc/html/draft-handrews-relative-json-pointer-02) 

Darrel: Henry wasn't able to join us today. Carsten has brought up some points. He didn't object, but did add it'd be nice to see in the JSON Path specification.

MNot: Has anyone talked to the jsonpath chairs?

Rich: No; action taken to do so.

## Deprecation or Lifecycle?

Darrel: Summarises the history. Hoped that someone would step up and write something about lifecycle. We decided to set a deadline. 

Sanjay: In my experience, I've not yet come across use cases (for general lifecycle). From that perspective, with two headers that are well-scoped, there's an advantage. Leaning towards keeping Deprecation header.

Darrel (not chair hat): One scenario was signalling resources in a preview state.

MNot: I feel a little bad because I pushed lifecycle concept a little bit. I do know that if you take a "date" field to the IETF, there will be people who feel more strongly.

Sanjay: I am fine if we make the value of the Deprecation field a structured field.

MNot: Okay, maybe that solves that problem. If we had time and energy to look at API lifecycle, we could do something intersting. But if there isn't desire then maybe we do that in a few years.

Sanjay: Question to the WG, do we have any way to find out where this header is used?  Any thoughts?

Darrel: We're trying to be forward-looking, and should not be (too) worried about breaking existing use of non-standard header fields.

Sanjay will work on new version that uses structure fields and then move to WGLC soon.

## Discussions/Any Other Business

- As time permits.
