HTTPAPI WG Meeting - IETF 109
Friday November 20th, 2020 7:30am UTC
Chairs: Darrel Miller, Rich Salz

Meetecho: https://az.conf.meetecho.com/conference/?group=httpapi
Jabber: httpapi@jabber.ietf.org
Minutes: https://codimd.ietf.org/notes-ietf-109-httpapi

# Agenda

## Administrivia

- Note well
- Note-taker - Bron Gondwana
- Jabber Scribe - Mark Nottingham
- GitHub Use

### Agenda bash:

Mark Nottingham: might be good to have a discussion to set expectations about how drafts get adopted in the working group and the process for that.

Rich: yeah, good point - I will do that.

### describing how the charter for this group works

Mark: this group is a bit different from many groups in which there aren't specific milestones or deliverables called out about particular work to do.

Rich: every working group has a charter which describes what the group works on, and also what the group will **not** work on (out of scope).  This is done by the group rechartering, which gets approved by the area director and the collection of area directors called the IESG.  This gets sent to a mailing list ietf@ietf.org.  Typically the charter says what will happen and when (hopefully) by.  Milestones are aspirational and can also change over time.

Mark: when we proposed the charter for this group, while we did the drafts that happen here in the http working group, there are different communities there and we thought it might be good to have a separate working group just for http APIs.  Hope that this group will form a community of people working on specifications that make HTTP APIs more functional and interoperable.  We have an open remit.

This is quite a generous amount of leeway for the IETF, so it's good to have a discussion here about how we'll go about doing those adoptions.

We count quite strongly the intent of implementers.  If many voices say "yes, we'll do this" then that means it's more likely to be used.  Avoid "hope-based standardisation".

HTTP WG recently started to use Github to track candidates for draft adoption.

Finally - there's a built-in doomsday clause - we close if we're not geting work done.

Barry Leiba: documents may change a lot once adopted to the working group!  There's no guarantee it will stay the same.

Mark: when we adopt a document we have to check with Barry as AD.  With HTTP working group hat on, would help if there's coordination between the two.  Can do that at a chair level.

#### Questions:

Yaron Sheffer: can you please repeat the timeline for the working group (milestones)

Rich: was just making up an example, that's not a timeline for this group.  Milestones are set in months and they are always aspirational.  1 month to adopt, 6 months to revise, that's optimistic.  AD will be nagging chairs to update milestones.

### using github

Rich: does anyone have concerns or objections about using github?

{ the lurkers support it in jabber }

Rich: our plan is to use github.  PLease read process doc.

We have a github org: `ietf-wg-http`.

One repo for each document, one for meeting materials.

See `quicwg` and `httpwg` usage for how tooling is used there.

#### Questions:

Yaron Sheffer: existance of working group with a doomsday condition in the charter is a strong incentive to create standards, so if we create a bunch of useless HTTP APIs, it could create damage.  Do we have processes to make sure there's wide consensus before we adopt or standardise things?

Barry (AD): we would ask for interest in implementation amongst those here, we have a wide group here.

Mark: the risk of doing actual damage is fairly small, unless you're considering damage to the IETF's reputation (which happens on a daily basis).  This drives the challenge that we face.

Rich: we've used half our time, we can discuss more on the mailing list.

## Drafts to consider adopting

- Rate Limit Headers - Roberto Polli
https://ioggstream.github.io/draft-polli-ratelimit-headers/draft-polli-ratelimit-headers.html

* from the Italian government
* widespread support
* replace a wide set of headers with three simple headers that show rate.
* Quotas "units", so it just gives you an idea about how far through the total you are.
* 5 open issues need input (see slides)
* via jabber:
    * "units" makes it hard to predict whether a particular request will be accepted.
* This is NOT inventing a new model, just standardise existing pattern.
* Why not timestamps?  Need NTP.

ADOPTION REQUEST:
* Mark (via chat): +1 for adoption, but may change.
* Yep, know it can change.  WG is master, but will need to talk to implementations.

Clarifying questions? None

Opposed to adoption?  None

Show of hands!
* Opposed or not ready to decide?
    * 0 raised
    * 16 non-raised
    * 50 participants

Rich: Will confirm adoption request on the list.

- Deprecation Header - Erik Wilde
https://tools.ietf.org/html/draft-dalal-deprecation-header-03

Erik: works in API design company, looking for patterns for APIs.

{We lost Erik for a bit - best joke from Jabber "maybe he ran out of quota"}

* Q: Sunset is information, but Deprecation is standards track - is that a problem?
* A: Martin / Mark -> no.

Lots of support for adoption on the list.

Any concerns about it being adopted?  None

Rich: will call for adoption on the list.


- Linkset media types and link relation - Erik Wilde
https://www.ietf.org/archive/id/draft-wilde-linkset-07.txt

Comments:
* Phil Archer: GS1 is the standards body behind the barcode.  Strongly endorse this, have a standard in public review "informative until this becomes and RFC".  Every healthcare company in the world is asking for this.
* Alexey Melnikov: worth checking that this doesn't duplicate existing work.  Looked at rfc 6690.
* A: CORE model isn't what they need.
* Alexey: can you elaborate?  Underlying model doesn't matter.
* A: will have to get back to you on what the exact differences were.

There's also another document that's trying to do similar things.

Rich: will provisionally take to the list, will need to resolve the duplication and the competing document.
 
- Content-Warning Header - Erik Wilde
https://tools.ietf.org/html/draft-cedik-http-warning-02#section-1

Some condition wasn't exactly as it should be, but not an error.

Some implementations already exist.

Clarifying questions?  None

Mark: can't see how this could be harmful.  Generally support adoption.

Chris Lemmons: is this exclusively for JSON documents?  It's not clear to me if this has scopes for XML, CBOR, HTML, etc.  There might not be a place in the body to put the warning.

{we're already over time}

Rich: Will need to take discussion to the mailing list, won't call for adoption yet.

Final call for action: tell your colleagues that this group exists.



