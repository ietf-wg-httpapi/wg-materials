HTTPAPI at IETF 110
===================

MINUTES
======

Administrivia 
-------------
* Note well
* Note-taker (Rich), Jabber Scribe (Darrel)
* Agenda bashing

Draft Updates
-------------

* Rate Limit Headers - Roberto Polli
  [draft](https://github.com/ietf-wg-httpapi/ratelimit-headers)
  Darrel update: there are some PR's around goals, and performance (sending only what's needed).
        
* Deprecation Header - Erik Wilde
  [draft](https://datatracker.ietf.org/doc/draft-ietf-httpapi-deprecation-header/)
  Moved to an official WG draft. Like the Sunset header.
  Deprecation is on the resource level (not fields within it). Darrel thinks some people are using finer grain (draft doesn't say how to do so) so he'll bring those he know who are using it to review the doc.
  No open issues in the GH repo, most recent batch of changes were editorial. Please put issues on the repo and if not editorial, post a pointer to the mailing list.
  Chris(?): Not clear what clients are to do with the information they get. Erik: most likely action is logging something. Chris noting that can be useful.
  Sanjay agrees adding client view is a good idea. Darrel mentions useful to developer tooling, too.
  Seems close to WGLC (working group last call, before giving to AD's and IESG for review).
  Chris: it would be bad for a client to just blindly follow the "new" version as if it were the Deprecated version.
  Alexander: precise semantics would help clients know what to do.
  Chris: alternate/replacement/latest links need some clarification.
    
* Linkset - Erik Wilde
  [draft](https://datatracker.ietf.org/doc/draft-ietf-httpapi-linkset/)
  Exposing HTTP Link header field as resources.
  Interesting implementation: GS1 digital link, turning bar codes into URL's which can then be linked. (Massive use expected).
  five open issues; most of them are small.
  Phil Archer: https://id.gs1.org/01/9506000134352?linkType=all is an example. We're using the full power to represent the language, e.g.
  Phil: We're using the linkset, although it might be different (e.g., linkset in the querystring and Accept header). How many of those things would be appropriate to raise as issues in the standard?
  Mnot: I hope Phil could define his own media type (Phil: yes) and then embed the linkset in that.
  Erik: don't see anything wrong with what you're doing, as long as you change the media-type when it's not just a linkset.

* Problem Details (bis) - Sanjay Dalal
  [draft](https://github.com/ietf-wg-httpapi/rfc7807bis)
    Mnot: Useful to coordinate problem types within a community. Either IANA registry or wiki could be viable, but if we're encouragine re-use maybe registry.
    Darrel: want re-use, seen people getting needlessly specific.
    Mnot: that aligns with my experience.
    Chris: in favor of repository of common error types.
    Darrel: how to distinguish between HTTP status and problem details?
    Rich gave more background in IANA registries.
    Discussion of auto-fetching a problem registry.
    Mnot commented on some of the open issues: authors will work on registry thoughts. The "multiple problems" issue must be addressed and authors will work on it. The 'type' issues are the deepest ones; he thinks sentiment is against introducing a new media type.
    Sanjay: what does WG think of the "Warning" object?
    Discussion.
    Will take some points to the list.

Drafts to consider adopting

* Content-Warning Header - Erik Wilde
  [draft](https://datatracker.ietf.org/doc/draft-cedik-http-warning/)
  Andre could not make it; discussion on the mailing list.

* JSON Type Registry Discussion - Darrel Miller
    People want more complicated semantics that aren't in JSON primitives. JSON schema helps a bit. OpenAPI adds more. Mention of OData, GraphQL, GRPC, etc.
    Is there value in having a globally-unique serialization registry? Syntax-only? Standardize scheme format? Does this help things/improve interop?
    Discussion in jabber while Darrel was talking.
    Is this like XML Schema part 2 (for json schema)? Darrel: no, it's different.
    Will take discussion to the list.  Or maybe DISPATCH?
    Chris: is this useful? Need multi-party agreement? Yes. I don't know if we have agreement, or if the problem is well-enough specified.
    Darrel: this is not a new standard, but a place for "everyone" to define their own data types.