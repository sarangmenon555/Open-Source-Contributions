# GSoC Preparation

A developing record of my preparation for Google Summer of Code (GSoC): organisations explored, codebases studied, skills built and goals. Entries are added only for work that has actually been done.

## Organisations and Projects Being Explored

| Organisation / Project | Interest | Status |
| --- | --- | --- |
| FOSSASIA – eventyay-paypal | Python payment-provider plugin; already contributing tests ([PR #38](https://github.com/fossasia/eventyay-paypal/pull/38)) | Exploring |

## Understanding of Project Codebases

### FOSSASIA – eventyay-paypal

- Studied the PayPal provider's refund execution (`execute_refund`), refund eligibility checks (`payment_refund_supported`, `payment_partial_refund_supported`) and privacy shredding (`shred_payment_info`) well enough to write tests for them.
- Understood the refund outcome states (`COMPLETED`, `PENDING`, other) and how errors are logged and raised.

## Technical Skills and Technologies

| Area | Current focus |
| --- | --- |
| Python | Unit testing with `pytest`, fixtures, `monkeypatch`, `unittest.mock` |
| JavaScript / React | Components, hooks (`useState`, `useEffect`), `IntersectionObserver`, accessibility attributes |
| Engineering practice | Pull request descriptions, code review, boundary and privacy testing |

## Contributions to Potential GSoC Organisations

| Organisation | Contribution | Status |
| --- | --- | --- |
| FOSSASIA | [PR #38](https://github.com/fossasia/eventyay-paypal/pull/38) – unit tests for refunds and data shredding | Open – Under Review |

No merged contributions yet.

## Project Ideas and Mentor Interactions

- No project ideas have been formally chosen yet.
- Only public, appropriate interactions are recorded here. Private maintainer conversations are not published.

## Preparation Progress and Goals

- [x] Open a first test-focused PR with a FOSSASIA project.
- [ ] Address the review findings on PR #38 and get a maintainer response.
- [ ] Choose two or three candidate projects and study their codebases.
- [ ] Get at least one contribution merged to a candidate organisation.
