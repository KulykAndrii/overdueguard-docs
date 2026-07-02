# OverdueGuard — Documentation

OverdueGuard is a monday.com board view that escalates overdue tasks through your
chain of responsibility. Instead of pinging the same person forever, it notifies
different people as an item gets more overdue — day 1 the assignee, day 3 their
manager, day 7 a director — and keeps notification noise down with built-in
deduplication.

---

## Quick start (2 minutes)

1. **Install** OverdueGuard from the monday.com marketplace.
2. Open the board you want to monitor and add the view: **+ (Add view) → Apps → OverdueGuard**.
3. Click **Add rule**.
4. Fill in the form:
   - **Date column** — the column that holds the due date.
   - **Status column** — the column that tracks completion.
   - **Done values** — which status labels mean "this item is finished" (items with
     these statuses are never treated as overdue).
   - **Overdue after (days)** — how many days past the due date before the first
     notification fires. `0` means "the day after the due date".
   - **Notify** — who gets notified: the item's owner (subscribers) or a specific user.
5. Click **Save**. That's it — OverdueGuard scans your board once a day and notifies
   the right people about anything overdue.

## How scanning works

- Scans run **once per day** in the **timezone configured on the rule**, so "overdue"
  is evaluated against your local calendar date, not a fixed server time.
- An item counts as overdue when its date has passed **and** its status is not one of
  your "done" values.
- **Deduplication:** the same person is not notified about the same item more than
  once every 24 hours, even if multiple rules cover the same board.

## Escalation tiers (Pro)

A rule can have multiple tiers, each with its own threshold and audience:

| Tier | Overdue after | Notify |
|------|---------------|--------|
| 1    | 1 day         | Assignee |
| 2    | 3 days        | Manager |
| 3    | 7 days        | Director |

As an item gets more overdue, responsibility climbs the chain automatically — no
helper columns, no per-tier automation sprawl.

## Plans

| | Free | Pro |
|---|------|-----|
| Rules per account | 1 | Unlimited |
| Escalation tiers per rule | 1 | Multiple |
| Daily scan + deduplication | ✓ | ✓ |
| Price | $0 | $9 / month |

## FAQ

**Which columns does OverdueGuard support?**
Any monday.com *Date* column and any *Status* column.

**Does it modify my board data?**
No. OverdueGuard only reads your items to detect overdue ones and sends monday
notifications. It never changes columns, statuses, or items.

**Where is my data stored?**
Rule configurations are stored in monday's own app storage, scoped to your account.
OverdueGuard does not store your board content on external servers.

**Why didn't someone get a notification?**
Three common reasons: (1) the item's status matches one of your "done" values;
(2) the item hasn't crossed the tier's "overdue after" threshold yet; (3) the same
person was already notified about that item within the last 24 hours (deduplication).

**Can I edit or delete a rule?**
Yes — every rule in the table has **Edit** and **Delete** actions.

## Support

Questions, bugs, feature requests: **kyluk5@gmail.com**
We aim to respond within 2 business days.

---

*OverdueGuard is developed by AndrDev. Not affiliated with monday.com.*
