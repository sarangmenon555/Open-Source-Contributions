# Monthly Reviews

A monthly summary of progress, learning and goals. Newest month first.

---

## November 2026

### Progress

- Opened [PR #38](https://github.com/fossasia/eventyay-paypal/pull/38) on FOSSASIA's `eventyay-paypal`, adding unit tests for PayPal refund handling and payment data shredding (tests only, 2 files). Status: Open – Under Review.
- Set up this public tracker to record contributions accurately.

### New repositories explored

- fossasia/eventyay-paypal

### Contributions submitted and merged

| Submitted | Merged | Closed without merging | Open |
| --- | --- | --- | --- |
| 1 (PR #38) | 0 | 0 | 1 |

Earlier work (the CryptoHub commit and VigyBag PRs #2701 and #2702) is recorded in the [Contribution Log](CONTRIBUTION-LOG.md).

### Technical skills developed

- Writing unit tests with `pytest`, fixtures, `monkeypatch` and mocks.
- Reading a payment provider's refund flow and its privacy-shredding logic.
- Acting on automated code review feedback.

### Challenges and lessons learned

- Automated review flagged that over-stubbed tests can pass even if production behaviour regresses.
- Boundary cases need care, such as the 180-day refund window with fractional days.
- Privacy shredding must be checked across every nested item, not only the first.

### Goals for December 2026

- Address the six review findings on PR #38 and record the maintainer response.
- Explore at least one more project and read its contribution guidelines before opening a PR.
