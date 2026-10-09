# Week 8 Reading: Law, Ethics, and the Closing Web
### DSA 405 · Week 8 · Friday, Oct 9

**This document is educational material, not legal advice.** The
law in this area is not settled and differs by country and state, and a project with real
legal consequences requires advice from a lawyer.

We go through the four buckets and the five cases together in class on Friday, so you
do not need to read this before class. Keep it open during the team activity: the six
scenarios you work on are at the end. Read it in full before you write A8, because the
bucket analysis in A8 uses all of it. You do not need to memorize any of it.

A `robots.txt` is a text file in which a site's owner states which pages automated
programs may fetch; you can see any site's by opening `site.com/robots.txt` in a
browser.

---

## "Is scraping legal" is four questions

The single question is really **four separate questions under four different bodies of
law**, and most of the confusion around scraping comes from mixing them together. In this
course we call these four categories **buckets**. Sorting a situation into its buckets is
usually enough to see it clearly, and the in-class scenarios and assignment A8 both ask
you to do exactly that.

| Bucket | The question | The law | The key point |
|---|---|---|---|
| **1. Hacking** | Was an authorization gate defeated? | CFAA (US) | Public pages with no login have no authorization gate. Pages behind a login do. |
| **2. Contract** | Were terms accepted that forbid this? | Breach of contract | Terms you clicked "I agree" to are far more binding than terms that are only posted on the site. |
| **3. Circumvention** | Was a technical protection measure defeated? | DMCA §1201 | The newest and fastest-changing area of this law. |
| **4. Privacy** | Is it personal data about identifiable people? | GDPR, CCPA/CPRA | "Public" is not a defense here. |

The laws in the table, spelled out once: the **CFAA** is the Computer Fraud and Abuse
Act, the main US anti-hacking law. The **DMCA** is the Digital Millennium Copyright
Act; its section 1201 forbids defeating a technical protection. The **GDPR** is the
European Union's privacy law, and **CCPA/CPRA** is California's.

An **authorization gate** is a barrier, such as a login screen, that controls who may
enter part of a site. Most student projects fall into the category where all four
questions resolve favorably: the data is public, contains no personal information, sits
behind no login, requires no circumvention of any protection, and the terms permit
collection. The course guardrails exist to keep your project in that category, and that is
why they are written the way they are.

---

## Five cases worth knowing

### 1. *Van Buren v. United States* — Supreme Court, 2021
A police officer used his lawful access to a database to look up a license plate for an
improper reason. He was prosecuted under the CFAA for "exceeding authorized access."

**Held:** the CFAA asks a **gates-up-or-down** question. That phrase is the Court's own
shorthand, and it means: either a gate (a barrier such as a login or a permission level)
blocked the person, or it did not. The CFAA covers accessing areas of a system the person
is not entitled to reach. It does not cover misusing information the person was entitled
to see.

**Significance:** the decision substantially narrowed the CFAA. Breaking a website's rules is
not automatically a federal crime.

### 2. *hiQ Labs v. LinkedIn* — Ninth Circuit, 2019 and 2022
hiQ scraped public LinkedIn profiles. LinkedIn sent a cease-and-desist letter (a formal
demand to stop) and blocked it.

**On the CFAA, hiQ won.** Where a page is open to anyone without credentials there is no
authorization gate to breach. The court also noted that LinkedIn's own `robots.txt` permitted
what hiQ was doing.

**hiQ lost anyway.** It had created accounts and accepted LinkedIn's User Agreement, and in
November 2022 the case ended in a consent judgment (a court order both sides agreed to):
a $500,000 payment, a permanent injunction (a court order forbidding hiQ from ever
scraping LinkedIn again), and destruction of the scraped data.

**The lesson:** the CFAA blocks hacking claims over public pages, but it does not
override a contract that was accepted. That is how hiQ won the CFAA question and still
lost the case. That combination is a normal outcome in this area, and worth remembering
when a headline says a scraper "won."

### 3. *Meta v. Bright Data* — N.D. California, January 2024
Meta sued a scraping company over collection of public Facebook and Instagram pages.

**Held:** Judge Chen granted summary judgment for Bright Data (summary judgment is a
ruling made without a full trial, when the decisive facts are not in dispute). Meta's
terms bar *logged-in* scraping. They do not bar logged-off scraping of publicly
accessible content, because a company that never logs in never "uses" the service in
the contractual sense. Meta dropped the rest of its claims and gave up its right to
appeal.

**Significance:** this is now the leading US contract-law decision on logged-out public
scraping, and it makes **scraping while logged out the most legally defensible approach**
available.

### 4. *Reddit v. Perplexity, SerpApi, Oxylabs, AWMProxy* — S.D. New York, filed Oct 2025
Reddit alleges that the defendants scraped Reddit content out of Google search results
at very large scale, hiding their identities and rotating IP addresses to defeat
anti-bot systems (software that detects and blocks automated visitors). They then sold
the data to an AI answer engine.

The core claim is **DMCA §1201 anti-circumvention**, not ordinary copyright infringement:
the allegation that defendants defeated a technological measure controlling access.

**Status as of late July 2026:** Judge Engelmayer declined to dismiss the core §1201(a)
claims. He found that Google's CAPTCHA-based anti-scraping system (a CAPTCHA is a puzzle
meant to be easy for a person and hard for a program) qualifies as an access control,
and that Reddit sits within the statute's "zone of interests" (the legal test for
whether Reddit is the kind of party this law is meant to protect). A §1201(b) trafficking
claim and the unfair-competition and unjust-enrichment counts were dismissed. The case is
now moving into discovery, the stage in which each side must hand over its evidence to
the other.

**Significance:** the case changes the question being asked. The public-data cases asked
whether the data was public; this one asks whether a protection was defeated and what was
done with the data afterward. Under that framing, the fact that the data was public no
longer protects the scraper.

**Practical consequence:** rotating proxies to defeat a rate limit, or solving a CAPTCHA
with a program, is a different legal category from reading a public page at a slow,
limited rate. The course guardrails forbid both for this reason.

### 5. *Clearview AI* — European and UK regulators
Clearview scraped billions of publicly posted face images to build a search tool.
Regulators fined it repeatedly, including €30.5M in the Netherlands, €20M in Italy, and
£7.5M in the UK.

**The lesson:** for **personal data**, "it was public" is not a defense. Under GDPR,
processing personal data requires a lawful basis regardless of how the data was obtained.
Non-personal data such as prices, listings, and rankings sits outside GDPR entirely, which
is one reason the course guardrails forbid personal data outright.

---

## Where `robots.txt` fits

`robots.txt` was standardized as **RFC 9309** in 2022. It is a standard rather than a
law, so ignoring it is not itself illegal, but it matters anyway, for three reasons. The
*hiQ* court cited LinkedIn's permissive `robots.txt` in hiQ's favor, so it can help a
scraper. Ignoring a `Disallow` line gives the other side evidence that the scraper acted
in bad faith, meaning it knew what the site permitted and collected anyway. And it is the clearest statement a site operator can make about what they
consider acceptable, so respecting it is professional courtesy, and it also reduces legal
risk.

Reading one:

```
User-agent: *              # applies to everyone
Disallow: /admin/          # do not fetch anything under /admin/
Disallow: /search          # do not fetch search result pages
Allow: /catalogue/         # this is explicitly fine
Crawl-delay: 10            # wait 10 seconds between requests
Sitemap: /sitemap.xml      # a list of the site's pages, provided for crawlers
```

`Crawl-delay` is not part of RFC 9309, but many sites publish it, and honoring it takes
little effort and shows good faith.

Treat `robots.txt` as a minimum: it states the least a site expects, not a promise that
everything it does not mention is acceptable.

---

## Six standing rules

1. **Scrape logged out, not logged in.** Every case above supports the same conclusion:
   collecting from public pages while logged out is legally safer than collecting while
   logged in.
2. **Never bypass a protection.** No CAPTCHA solving, no proxy rotation to defeat rate
   limits, no disguising the scraper as an ordinary browser. These actions fall under
   DMCA §1201, the newest and most actively enforced area described above.
3. **Personal data is covered by different, stricter laws.** Names, faces, emails,
   locations. Avoid it.
4. **Apply a rate limit.** One request per second is a respectful rate. Sending too many
   requests, by itself, can support a legal claim of trespass: the claim that you used
   someone's computer systems in a way that burdened or harmed them.
5. **Identify the client honestly** in the user-agent string, with contact information.
6. **If an API exists, use the API.** It is more stable, and it raises fewer legal
   questions. Week 11 covers APIs for this reason.

---

## In class: six scenarios

Work through these in teams of three. For each one, decide **which of the four buckets
apply**, whether you would proceed, and what changes would make the collection defensible.

**A.** A county health department publishes restaurant inspection scores as web pages. No
login. `robots.txt` has no `Disallow` covering them. A scraper collects all 4,000 at one
request per second.

**B.** A rental listings site requires a click on "I agree" before browsing, and the terms
prohibit automated access. The listings themselves are then public. A scraper collects them.

**C.** A scraper collects public professional profiles, including names, employers, and job
titles, to study hiring patterns in a field.

**D.** A retailer rate-limits after 50 requests. The scraper routes through a rotating
residential proxy service and continues collecting public product prices.

**E.** A university publishes its course catalog publicly, but `robots.txt` contains
`Disallow: /catalog/`. The catalog is scraped anyway for a scheduling tool.

**F.** A state open-data CSV released under CC BY 4.0 is downloaded, analyzed, and published
without naming the source.

Come with an opinion on each; we will spend time in class discussing. One of the six carries more legal risk than the others. 
