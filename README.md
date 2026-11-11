# Books and Publishing

The common books vocabulary -- the books (titles and editions) publishers, retailers and libraries list, and the authors who wrote them -- distilled from the APIs that already exist. Scholarly works belong to research repositories. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Books, Book Publishing, Ebooks, eBooks, Library, Libraries, Audiobooks, Publishing in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| book | 12 | 10 | id 60%, name 60% | titles 5, books 5, isbn 1, volumes 1 |

Cohort: 132 providers with harvested OpenAPI, 12 crosswalks. Of the providers exposing a book: 17% create, 83% list, 67% fetch, 17% update, 8% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A book agrees only on an id and a title. ISBN, authors, publisher and publication date are each carried by a minority: Google Books nests them under `volumeInfo`, library systems model titles as holdings, and retailers as products.

## Measured against the standard

The census reads what providers publish. Where the domain has a standard, the standard's own
definition is read as one more voice: how much of the measured core it defines, and what it
defines that no provider in the cohort publishes. Crosswalks are in [standards/](standards).

| Standard | Concept | Core defined by the standard | Fields only the standard has |
| --- | --- | ---: | ---: |
| [schemaorg-30.1](https://github.com/schemaorg/schemaorg/tree/v30.1) | `book` | 50% | 120 |

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Titles, volumes, editions, ebooks, audiobooks and works beneath a library path are books.
- Authors were measured and dropped.
- Duplicates merged: the eventwren family.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
