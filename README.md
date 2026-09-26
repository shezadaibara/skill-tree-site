# Skill Tree — published site

**[shezadaibara.github.io/skill-tree-site](https://shezadaibara.github.io/skill-tree-site/)**

What should you learn next? This site reads the open job postings of 49
employers — mostly German, mostly technology and industry — works out what each
role demands, and draws the result as a graph and a matrix you can read: which
skills are in demand now, which ones travel together, and how that changes week
to week. Filter to one employer and the same data shows what it hires for.

## Feedback is welcome — open an issue

This is a work in progress, and the fastest way to improve it is to hear where
it's wrong. **[Open an issue](https://github.com/shezadaibara/skill-tree-site/issues/new/choose)**
and pick the kind that fits:

- **Wrong or missing skill** — a skill that shouldn't be on the graph, one that
  should be, or two names that are really the same thing.
- **Add an employer** — a company whose careers page is worth reading.
- **Idea or suggestion** — anything else: a view you'd want, a question you
  wish the site answered, a trend worth tracking.

Issues are kept across rebuilds, so nothing you file gets lost.

## This repository is a build artifact

It holds a compiled front end and generated JSON, and nothing else. There is no
source here. It is **force-pushed as a single commit** on each publish, so the
history is always one deep and old data is replaced rather than accumulated.
Pull requests against it would be overwritten by the next build, so please use
an issue instead.

## Where the data comes from

Every posting is fetched from the employer's own applicant tracking system,
through the public endpoint their careers page already calls — Greenhouse,
Lever, Ashby, SmartRecruiters, Workday, Personio, Teamtailor, Phenom, Oracle
HCM, SAP SuccessFactors, or a sitemap plus `JobPosting` JSON-LD. No aggregator
is scraped, and `robots.txt` is respected in every case.

The corpus refreshes weekly. The header shows two dates and they mean different
things:

- **postings fetched** — when a board last returned these roles, so how fresh
  the job data is;
- **extracted** — when that text was last processed into skills.

## Reading it

Node size is how many postings demand a skill; colour is its category; line
weight is how strongly two skills travel together. Selecting a node shows who
asked for it and the sentence they used.

The matrix is the same data seen the other way: which companies want each skill,
and how much. Role chips narrow both views to one kind of work.

## Crawling

`robots.txt` asks crawlers to index the site but not `/data/`: the posting
excerpts belong in the page that explains them, not in a search index of their
own.

It only binds once the site is served from a host root. Crawlers read
`/robots.txt` and nothing else, and a GitHub project page lives at a subpath —
so while the site is at `shezadaibara.github.io/skill-tree-site/`, the rule has
to be set in the `shezadaibara.github.io` repository instead:

```
User-agent: *
Disallow: /skill-tree-site/data/
```

## Licence

The compiled front end and the generated aggregates are MIT-licensed — see
`LICENSE`.

**Job posting excerpts are not.** Each skill carries at most one short verbatim
sentence from the posting it came from, shown so that a reader can see who asked
for something rather than take the graph on trust. Those sentences remain the
work of the employers who wrote them and are reproduced here as brief quotation
for attribution. They are not licensed onward by this repository.
