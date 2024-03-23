HTTPAPI  IETF119
Date: 2024-03-21
Chairs: Rich Saltz, Darrel Miller
Secretary: Mark Nottingham

Updated status diagrams here: https://ietf-wg-httpapi.github.io/
Updated project status board here: https://github.com/orgs/ietf-wg-httpapi/projects/1/views/1

## Document Progress
YAML media type is now RFC9512

## Authentication Links
DarrelMiller to request review from SECDIR

## Link Hints
Needs more investigation. HTTP structured fields might be too HTTP specific.
Serializing into HTML is a goal

## MediaTypes
Security Considerations document is now available in the OpenAPI GitHub repo so it can be referenced in this draft. Suggestion to add application/openapi to the current mediatypes. Rich pointed out that Roberto is contributing even though he has had a new job for some time.

## Idempotency
Mnot brought up some issues that were blocking.  We will need to redo WGLC
This is some good discussion in the GitHub repo, https://github.com/ietf-wg-httpapi/idempotency/issues. Please review.

Rich: off-list email from authors saying they are working on an updated draft.

## ByteRange
New version has been published. Summary of changes from Austin:
- New syntax for content offset
- Now possible to overwrite a region.
- Now uses Structured Fields.

Austin also pointed out:
- Limit scope to publishing media type for now, defer other use cases to later.
- Use of headers to communicate metadata for the partial updates would be more suitable to httpbis WG

Please review.

## Deprecation
Rich: My notes in the agenda and during the meeting are wrong.  From the authors, off-list: "What is expected? We published a draft 03 addressing the time format related blocker." **Chairs will review and probably do a WGLC**

Thank you all, it was short and sweet.
