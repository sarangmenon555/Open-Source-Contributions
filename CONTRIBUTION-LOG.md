# Contribution Log

A chronological record of meaningful open-source work. Statuses are kept accurate: a pull request that was closed without merging is never recorded as a merged contribution, and one implementation is never counted twice.

**Status key:** Merged · Open – Under Review · Closed – Not Merged

## Summary

| # | Project | Work | Status |
| --- | --- | --- | --- |
| 1 | CryptoHub (KaranUnique) | Direct commit `45066d7` – Lenis cleanup and route handling | Direct commit |
| 2 | VigyBag (codervivek5) | [PR #2701](https://github.com/codervivek5/VigyBag/pull/2701) – About Us page (26 Dec 2025) | Closed – Not Merged |
| 3 | VigyBag (codervivek5) | [PR #2702](https://github.com/codervivek5/VigyBag/pull/2702) – React animation and accessibility (26 Dec 2025) | Closed – Not Merged |
| 4 | FOSSASIA eventyay-paypal | [PR #38](https://github.com/fossasia/eventyay-paypal/pull/38) – Python unit tests (16 Nov 2026) | Open – Under Review |

---

## 1. CryptoHub – Direct commit

- **Repository:** [KaranUnique/CryptoHub](https://github.com/KaranUnique/CryptoHub)
- **Commit history:** [commits by sarangmenon555](https://github.com/KaranUnique/CryptoHub/commits?author=sarangmenon555)
- **Type:** Direct commit
- **Commit:** `45066d7` – "Refactor: improve Lenis cleanup and optimize route handling" (parent `88a0e7a`, referenced as #339 on the commit page)
- **File changed:** `src/App.jsx` (+41 −39)

**What I did**

- **Lenis smooth-scroll cleanup:** the `requestAnimationFrame` loop previously had no way to stop. I stored the frame ID, called `cancelAnimationFrame` in the effect cleanup, then `lenis.destroy()` and reset `lenisRef.current` to `null`, so the scroll loop no longer keeps running after the component unmounts.
- **Route handling:** replaced the chained `location.pathname === ...` comparisons with a `dashboardRoutes` array and an `includes` check, and moved the auth route list into a matching `authRoutes` array. Both are wrapped in `useMemo` so they are not recreated on every render.
- **Behaviour change:** `/profile` was added to the dashboard route list so it is treated like the other dashboard pages.
- **Cleanup:** removed redundant comments, tidied the formatting of the nested dashboard routes, and moved the `/cookies` route ahead of the catch-all `*` route so the 404 route is last.

**Learning**

- Always cancel animation-frame loops and destroy third-party instances in `useEffect` cleanup.
- `useMemo` can keep constant lists stable across renders.
- Keep catch-all routes last for readability.

---

## 2. VigyBag – PR #2701: About Us page enhancements

- **Repository:** [codervivek5/VigyBag](https://github.com/codervivek5/VigyBag)
- **Pull request:** [#2701 – Enhance About Us page with animations and layout](https://github.com/codervivek5/VigyBag/pull/2701)
- **Branch:** `sarangmenon555:patch-1` → `codervivek5:main` (1 commit, `fdf6183`)
- **Opened:** 26 December 2025
- **Closed:** 26 December 2025, closed by me (the author)
- **Status:** **Closed – Not Merged**
- **Workstream:** VigyBag About Us / frontend (shared with PR #2702)
- **File changed:** `src/User/pages/AboutUs/Aboutus.jsx`

**What I did**

- Added scroll-triggered visibility animations to the About Us page using the browser `IntersectionObserver` API, managed with React `useState` and `useEffect`.
- Animated the headings, text blocks, images and embedded video so content appears as it enters the viewport.
- Refreshed the page styling with gradient backgrounds, improved typography and section dividers.
- Improved hover and focus states for better interactivity.
- Reorganised the page into responsive sections (mission, story, choose, values).
- Handled the observer lifecycle (set up on mount, observe elements, disconnect on unmount).

**Review feedback (public automated review by CodeRabbit)**

- The `IntersectionObserver` setup, `0.1` threshold and cleanup were assessed as correct.
- The lazy-loaded video iframe, `aria-label` and `referrerPolicy` were noted as good accessibility and performance practice.
- Suggested extracting the repeated animation pattern into a reusable `AnimatedSection` wrapper component.
- Flagged the PR description as incomplete: it needed a fuller "Changes proposed" section and screenshots.
- No maintainer review or merge decision was recorded.

**Outcome:** Not merged. The PR was closed on the day it was opened.

**Learning**

- Write complete PR descriptions with screenshots so reviewers can evaluate visual changes quickly.
- Repeated animation code should be a reusable component rather than duplicated per element.
- Check the project's contribution guidelines and issue assignment before opening a PR.

---

## 3. VigyBag – PR #2702: React component animation and accessibility improvements

- **Repository:** [codervivek5/VigyBag](https://github.com/codervivek5/VigyBag)
- **Pull request:** [#2702 – Update Aboutus.jsx](https://github.com/codervivek5/VigyBag/pull/2702)
- **Branch:** `sarangmenon555:main` → `codervivek5:main` (1 commit, 1 file changed, +277 −147)
- **Opened:** 26 December 2025
- **Commit reference:** [`be89de7`](https://github.com/codervivek5/VigyBag/pull/2702/changes/be89de794998e8ac8782d9928684edc76eff419c)
- **Status:** **Closed – Not Merged**
- **Workstream:** Same VigyBag About Us / frontend workstream as PR #2701. It is **not counted as a separate contribution** in the statistics.

**What I did**

- Reworked `Aboutus.jsx` with visibility-based animations for the Mission, Story, Why Choose VigyBag and Our Values sections.
- Added smooth fade and slide transitions to content elements.
- Made minor accessibility improvements to embedded media.

**Relationship to PR #2701:** This is a second attempt at the same About Us animation work, submitted from a different branch (`main` rather than `patch-1`). It is recorded as part of one workstream and is not counted as a separate contribution.

**Outcome:** Not merged.

---

## 4. FOSSASIA eventyay-paypal – PR #38: Unit tests for refunds and payment data shredding

- **Repository:** [fossasia/eventyay-paypal](https://github.com/fossasia/eventyay-paypal)
- **Pull request:** [#38 – Add unit tests for PayPal refund handling and payment data shredding](https://github.com/fossasia/eventyay-paypal/pull/38)
- **Branch:** `sarangmenon555:test/refund-and-shred-payment-info` → `fossasia:dev` (1 commit, `99f24b1`)
- **Opened:** 16 November 2026
- **Status:** **Open – Under Review**
- **Type:** Tests only. No production code was changed.
- **Files added:** `tests/test_refund.py`, `tests/test_shred_payment_info.py`

**What I did**

*Refund handling (`tests/test_refund.py`)*

- `Paypal.execute_refund` raises `PaymentException` when the payment has no completed capture, without calling PayPal.
- Logs `eventyay.event.order.refund.failed` and raises when the refund request or the refund detail lookup returns an error.
- Raises when the refund response contains no refund ID.
- `COMPLETED` marks the refund done, `PENDING` keeps it in transit, and any other status logs the PayPal reason (or the status itself) and raises.
- Verifies the correct capture ID, merchant ID, currency and amount are sent, including partial refunds.
- `payment_refund_supported` and `payment_partial_refund_supported` allow refunds up to and including 180 days after payment, not after, and not when there is no payment date.

*Payment data shredding (`tests/test_shred_payment_info.py`)*

- `Paypal.shred_payment_info` keeps only `id`, `payer`, `update_time`, `purchase_units` (reduced to payments) and the `_shredded` marker.
- Payer email, name and shipping data are removed.
- Missing `purchase_units` is stored as an empty list, and empty payment info is left untouched.
- PayPal log entries are reduced to `id`, `sale_id` and `parent_payment` in `resource` and marked shredded, including when the payment info itself is empty.

**Review feedback so far (public automated reviews)**

- CodeRabbit: no actionable comments; assessed the change as low risk.
- Sourcery: raised 6 findings, all still to be addressed:
  1. Shredding may reduce only the first `purchase_units` entry, so the fixture should include several units.
  2. The 180-day check may truncate fractional days, so a fractional-day boundary test is needed.
  3. Refund tests use empty payment data and a stubbed capture lookup, so at least one test should exercise the real capture lookup.
  4. The fixture limits capture statuses to `COMPLETED`, so a partially refunded capture should be covered.
  5. Log-entry fixtures use empty `data`, so the stubbed query exclusion should be matched to production behaviour.
  6. The `PENDING` test should assert the transit state is saved with `update_fields=["state"]`.
- Copilot could not review (reviewer quota).
- No human maintainer review has been recorded yet.

**Next steps:** Work through the six findings, update the tests, and record the maintainer response here. Findings 1 and 2 may point to behaviour in the production code, which needs investigating before any claim is made.

**Learning**

- Writing tests with `pytest`, fixtures, `monkeypatch` and mocks for a payment provider.
- Over-stubbing can make tests pass even when production behaviour regresses.
- Boundary testing matters, including whole versus fractional days.
- Privacy shredding needs coverage for every nested item, not just the first.
