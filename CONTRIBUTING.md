# Contributing

Thanks for helping keep **Free Services for Developers** accurate and useful. Free tiers change constantly, so every contribution with a current, official source makes this list better.

This project tracks hosted free tiers, practical $0 stacks, and free software that can be self-hosted. Please read this guide before opening an issue or pull request.

## Contents

- [What to contribute](#what-to-contribute)
- [Acceptance criteria](#acceptance-criteria)
- [Which file should I edit?](#which-file-should-i-edit)
- [Adding a new service](#adding-a-new-service)
- [Updating an existing service](#updating-an-existing-service)
- [Local workflow](#local-workflow)
- [Pull request checklist](#pull-request-checklist)
- [Submission template](#submission-template)
- [Verified dates and sources](#verified-dates-and-sources)
- [Review process](#review-process)

## What to contribute

Useful contributions include:

- Adding a genuinely useful free service that is missing.
- Updating a quota, pricing detail, card requirement, or usage restriction.
- Marking a service as expired, paused, or no longer free.
- Improving a $0 stack when a better practical choice is available.
- Fixing a broken link, typo, table, translation, or documentation example.
- Improving the interactive catalog without changing the meaning of the data.

Small fixes are welcome. If you are unsure whether an idea fits, open an issue first and describe the proposed change.

## Acceptance criteria

A hosted service should have all of the following:

1. A genuinely useful free tier, not only a one-time coupon or a few-day trial.
2. Publicly documented pricing and limits.
3. A currently active free plan or a clearly documented free credit program.
4. A meaningful distinction from services already listed.
5. An official service or pricing URL that readers can use to verify the entry.

The entry must also clearly state whether a card is required, whether commercial use is allowed, and whether the service sleeps, expires, or removes data.

Services that are free for only a few days without meaningful credits, referral-only offers, private beta invitations, or undocumented “free” claims will not be accepted.

### Self-hosted software

Free software that requires your own server belongs in the **Self-Host Only** section. Do not describe self-hosted software as free hosting: the software may cost $0, but compute, storage, bandwidth, and operations still have a cost.

## Which file should I edit?

| Change | Source of truth | Also check |
| ------ | --------------- | ---------- |
| New or updated service metadata | [`data/services.yaml`](data/services.yaml) | Matching README section and website rendering |
| Stack recommendation or “where you hit the wall” note | `data/services.yaml` | README stack section |
| README-only explanation or checklist | `README.md` | Translated READMEs when relevant |
| Vietnamese or Chinese documentation | `README.vi.md` or `README.zh-CN.md` | Links and terminology in `README.md` |
| Interactive catalog layout or behavior | `site/` | `data/services.yaml` and responsive layout |
| Contribution process | `CONTRIBUTING.md` | README contribution links |

`data/services.yaml` is the canonical source for service and stack data. README tables are currently mirrored by hand, so a data change should include the corresponding README update when the row is represented there.

## Adding a new service

1. Search the repository first to make sure the service is not already listed under another category.
2. Check the provider’s official pricing and terms pages.
3. Collect the required facts using the [submission template](#submission-template).
4. Add the service to the appropriate section in `data/services.yaml`.
5. Mirror the entry in the relevant README category and keep the columns in the existing order.
6. Add or update the service in the website data only through the YAML source; do not duplicate facts in JavaScript.
7. Run the [local checks](#local-workflow), review the rendered Markdown, and open a focused pull request.

Use the provider’s official pricing page as the primary source. A third-party article can provide context, but it should not be the only source for a quota or price.

## Updating an existing service

When a free tier changes, update all affected facts in the same pull request:

- Free badge or plan type.
- Limits, quotas, retention, and rate limits.
- Card requirement.
- Commercial-use restrictions.
- Sleep, pause, expiry, or data-deletion behavior.
- Official pricing or terms URL.
- `verified` date.

If a provider removes its free tier, do not silently delete the row. Explain the change in the PR and move it to an appropriate alternative or removal section when applicable.

## Data format

A service entry should follow the existing YAML structure. Preserve the field names and indentation style used in neighboring entries. A typical entry contains facts similar to:

```yaml
- name: Example Service
  url: https://example.com/
  category: Hosting
  free: "🟢⚡"
  limits: "Documented free-tier request and bandwidth allowance"
  notes: "Important commercial-use or sleep behavior"
  verified: "2026-10-08"
```

Use the existing schema in `data/services.yaml` as the authority. Do not invent a new field for a single service without discussing it in an issue first.

## Local workflow

Clone the repository and create a focused branch:

```bash
git clone https://github.com/dereknguyen269/free-services.git
cd free-services
git checkout -b update-service-name
```

The interactive catalog is a static site. To preview it locally, serve the repository root with any static file server, for example:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000/site/` in a browser. Check both the catalog and the README after editing the data.

Before opening a pull request, run:

```bash
git diff --check
```

Also verify that:

- YAML indentation and quoting remain valid.
- Every changed service has an official source link.
- Dates use `YYYY-MM-DD`.
- Markdown links and anchors are not broken.
- The website still loads the catalog and filters services correctly.
- No secrets, API keys, personal data, or generated build artifacts are included.

## Pull request checklist

Please use a focused PR with a descriptive title. Before submitting, confirm:

- [ ] I searched for an existing entry before adding a new service.
- [ ] I used an official pricing, terms, or documentation source.
- [ ] I included the free-tier limits and the date they were checked.
- [ ] I documented card requirements and commercial-use restrictions.
- [ ] I documented sleep, pause, expiry, or data-retention behavior.
- [ ] I updated `data/services.yaml` when service metadata changed.
- [ ] I mirrored the change in the relevant README section when needed.
- [ ] I ran `git diff --check`.
- [ ] I checked the interactive catalog if the data or `site/` changed.
- [ ] I did not include secrets or unrelated formatting changes.

One service or one closely related correction per PR is preferred. Smaller PRs are easier to verify and merge.

## Submission template

Include all of the following in your PR or issue:

```text
Service:
Category:
URL:
Pricing / terms URL:
Free-tier limits:
Card required (yes/no/varies):
Type (free forever / credits / trial):
Commercial use allowed (yes/no/unknown + link to terms):
Sleep, pause, expiry, or data-retention behavior:
Last verified date (YYYY-MM-DD):
Notes / where you hit the wall:
README and YAML sections changed:
```

For an update, include a short **Before → After** summary and explain what changed on the provider’s official page.

## Verified dates and sources

The `verified` field communicates how recently a pricing page was checked:

- Use `⏳` when the entry has not been checked recently or the current limit is uncertain.
- Use a date such as `2026-10-08` when the official pricing or terms page was checked that day.
- Treat all limits as approximate unless the provider clearly guarantees them.
- Prefer direct links to pricing, quotas, limits, or terms rather than a provider homepage.

Free-tier policies change frequently. A verified date is not a promise that the plan will remain unchanged.

## Review process

Maintainers review contributions for accuracy, source quality, consistency with the data schema, and usefulness to readers. A maintainer may ask for:

- A more specific official source.
- Clarification about commercial use or card requirements.
- A correction to the category or badge.
- A matching change in `data/services.yaml`, the README, or the website.
- A newer verification date.

Please keep discussions factual and respectful. Do not share private account information, payment details, API keys, or other sensitive data in issues or pull requests.

## Reporting outdated information

If you do not want to submit a code change, [open an issue](https://github.com/dereknguyen269/free-services/issues) with the submission template and a current official source. Reports with a URL and verification date are much easier to act on than reports that only say “this is no longer free.”
