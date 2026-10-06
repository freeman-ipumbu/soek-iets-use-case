# Windhoek pilot playbook

The Soek.Iets pilot should prove one focused proposition: **can neighbourhood-first discovery and evidence-led trust make small local trades easier to find and safer to assess?**

This is an operating playbook, not a claim that a public service, regulated payment product or national marketplace is already live.

## Pilot scope

**Geography:** Windhoek only.

**Initial users:** a small, deliberately recruited group of buyers and micro-sellers who can be supported directly.

**Useful categories:** pre-loved goods, local craft, fashion, home, children’s items, electronics, business tools and sport. Categories may be restricted further when moderation or safety capacity is not ready.

**Currency:** Namibian dollars, consistently formatted as `N$`.

**Discovery unit:** approximate neighbourhood or public trading area. Never a seller’s private address.

**Pilot success:** evidence of useful discovery, clear understanding of current listing-review states, independently observed fulfilment and operable safety—not vanity registration numbers or a claim that the product records completed trades.

## Staged rollout

```mermaid
flowchart LR
    A[Private product alpha] -->|quality gates pass| B[Invited seller preparation]
    B -->|inventory and moderation ready| C[Closed buyer pilot]
    C -->|safety and fulfilment evidence| D[Partner certification]
    D -->|legal, security and operations sign-off| E[Controlled public Windhoek launch]
    E -->|measured local density and support capacity| F[Wider Namibia evaluation]
```

### Stage 1 — Private product alpha

- Complete core journeys on common phone widths.
- Confirm all price displays use `N$`.
- Exercise success, empty, loading, error and permission-denied states.
- Confirm every button and link has a real destination or a clear unavailable status.
- Verify that discovery exposes no dedicated exact-location field, warns users not to type addresses or coordinates, and applies the approved moderation and filtering tests.
- Confirm planned payment and identity features are visibly inactive.

### Stage 2 — Invited seller preparation

- Recruit a manageable group across several Windhoek neighbourhoods.
- Help each seller create accurate listings with current photographs and condition notes.
- Explain that supported uploads receive bounded container checks and metadata scrubbing, not a guarantee that an image or item is genuine.
- Review categories and prohibit items the team cannot safely moderate.
- Record seller-readiness decisions without describing them as KYC.
- Test support and listing-review turnaround before inviting buyers.

### Stage 3 — Closed buyer pilot

- Invite buyers in areas with enough relevant inventory.
- Observe whether users understand `My neighbourhood`, `Nearby areas` and `All Windhoek`.
- Ask users to explain why an illustrative preview recommendation appeared, and verify that they do not attribute its modelled signals to approved live listings.
- Test Soek Requests where inventory is thin.
- Exercise the complete demand loop: request review, public neighbourhood demand, an eligible seller response linked to the seller's live listing, and buyer shortlist or decline.
- Exercise participant-only enquiry threads and set the expectation that the pilot uses manual refresh rather than push, email or SMS notifications.
- Use public-point handover guidance and record fulfilment outcomes as pilot research outside the marketplace product; do not present those observations as a platform completion or review state.
- Keep payment outside any “protected” claim until a production partner rail is active.

### Stage 4 — Partner certification

- Agree the exact role of Soek.Iets, TPTS and any other authorised providers.
- Complete commercial, regulatory, privacy and security review.
- Define identity, payment, webhook, timeout, reversal and reconciliation contracts.
- Test failure paths, duplicate events, interrupted handovers and provider downtime.
- Train support and operations staff before enabling any user-facing status.

### Stage 5 — Controlled public Windhoek launch

- Release by supported geography and category rather than opening every market at once.
- Maintain daily trust-and-safety coverage during the initial launch window.
- Monitor supply quality, buyer demand, reports and response time. Monitor platform completion, cancellations or trade-linked reviews only after those features are explicitly activated; until then, keep any research observations separate from product status.
- Pause growth when operational capacity or safety quality falls below the agreed threshold.

## Pre-pilot checklist

### Product

- [ ] Buyer, seller and operations journeys pass device and accessibility QA.
- [ ] Listing, request, seller-response and live-listing enquiry actions persist reliably with owner- or participant-scoped reads and writes.
- [ ] Enquiry follow-up messages reject non-participants and contact details, and the interface accurately states that notification delivery and read receipts are not active.
- [ ] Listing edit, pause, sold, remove and resubmit states have been exercised without implying payment, delivery or completion.
- [ ] Up to four supported listing photos can be reviewed, privately delivered and removed; malformed, animated and oversized uploads fail safely.
- [ ] Illustrative preview reasons match the preview score, and approved live listings are described accurately as proximity-then-recency ordered.
- [ ] PWA update and offline behaviour cannot display a stale route as the current page.
- [ ] No placeholder statistics, fake reviews or fabricated live activity appear.
- [ ] Every integration is labelled with its actual activation state.

### Safety and operations

- [ ] Prohibited-items policy and seller rules are approved.
- [ ] Reports create a traceable case with owner, priority and status.
- [ ] Escalation paths exist for suspected fraud, threats, illegal goods and vulnerable users.
- [ ] Public handover guidance is visible in the trade journey.
- [ ] Administrative roles follow least privilege.
- [ ] Material moderation actions are logged and reviewable.
- [ ] Soek Requests remain non-public until reviewed; system-supplied seller records contain no dedicated buyer-contact or exact-location field; free-text warnings, filters, moderation and reporting are tested.
- [ ] Seller responses reference only the responder's own live listing and can be shortlisted, declined or withdrawn only by the correct participant.

### Legal and privacy

- [ ] Operating entity, customer-facing contacts and complaint channel are confirmed.
- [ ] Terms, privacy notice, community rules and seller terms receive Namibia-specific counsel review.
- [ ] Data inventory, lawful basis, retention and deletion procedures are documented.
- [ ] Provider roles and data-processing responsibilities are contractually clear.
- [ ] Accepted Terms, Privacy Notice and Community Rules versions are recorded, and the process for material updates and re-acceptance is approved.
- [ ] Marketing claims match the product’s live status.

### Partner and financial rails

- [ ] TPTS and/or another appropriately authorised provider has approved the production scope.
- [ ] No flow relies on a screenshot or forwarded message as payment proof.
- [ ] Fees, limits, settlement timing, refunds and disputes are disclosed before commitment.
- [ ] Reconciliation and exception handling pass production-like tests.
- [ ] A rollback or feature-disable path is rehearsed.

### Security and resilience

- [ ] Threat model and abuse cases are reviewed.
- [ ] Authentication, session handling and administrative access are tested.
- [ ] Public hosting no longer depends on forgeable client-supplied identity headers; cryptographically verified portable sessions and cross-site request protections are tested.
- [ ] Dependency, secret and deployment configuration checks pass.
- [ ] The listing-photo boundary has a documented production decision for server-side decode/re-encode, malware monitoring, retention and orphan cleanup; pilot container sanitisation is not treated as complete image safety.
- [ ] Backups, restore, monitoring and incident communications are rehearsed.
- [ ] Security findings have owners and launch-blocking severity criteria.

## Seller activation workflow

```mermaid
stateDiagram-v2
    [*] --> ProfileStarted
    ProfileStarted --> Submitted: onboarding complete
    Submitted --> ReadinessReview: marketplace review
    ReadinessReview --> ChangesNeeded: incomplete or unclear
    ChangesNeeded --> Submitted: seller updates profile
    ReadinessReview --> PartnerPending: readiness approved
    PartnerPending --> Verified: provider check succeeds
    PartnerPending --> Restricted: provider check fails or expires
    Verified --> Active: listing and payout gates pass
    Active --> Paused: policy, risk or support action
    Paused --> Active: reviewed and restored
```

Marketplace readiness and provider verification remain separate throughout this workflow.

The `PartnerPending`, `Verified`, payout-gate and partner-driven activation states above describe the target partner workflow. They are not active identity, payment or payout protections in the current private pilot.

## Listing lifecycle

```mermaid
stateDiagram-v2
    [*] --> Review: create or resubmit
    Review --> Live: operator approves
    Review --> Rejected: operator rejects
    Rejected --> Review: owner edits or resubmits
    Live --> Review: owner edits
    Live --> Paused: owner pauses
    Paused --> Review: owner resubmits
    Live --> Sold: owner marks sold
    Review --> Removed: owner removes
    Live --> Removed: owner removes
    Paused --> Removed: owner removes
```

These are content and availability states. `Sold` is an owner statement, not proof that money moved, a handover occurred or either party can leave a trade-linked review.

## Soek Request and conversation workflow

```mermaid
flowchart LR
    Q[Buyer submits request] --> M[Marketplace review]
    M -->|approved and open| D[Neighbourhood demand feed]
    D --> R[Eligible seller links own live listing]
    R --> C[Buyer shortlists or declines]
    L[Buyer enquires on live listing] --> T[Participant-only thread]
    T --> F[Manual in-product refresh]
    F -. no delivery or payment claim .-> H[Public-point handover guidance]
```

A request response is not a reservation, and a message is not a completed trade. Push, email and SMS notifications are not part of the current pilot; do not set response-time expectations the product cannot deliver.

## Listing-review standard

A listing can move toward publication when an operator can answer yes to each applicable question:

1. Is the title specific and not misleading?
2. Is the condition stated plainly—new, pre-loved, handmade or refurbished?
3. Is the `N$` price plausible and free of hidden mandatory charges?
4. Do the seller-supplied facts and current item photos support the description without being treated as proof of ownership or authenticity?
5. Is the approximate neighbourhood sufficient without exposing a home address?
6. Is the category allowed and within current moderation capacity?
7. Are warranty, invoice, ownership or safety claims supported where required?
8. Does the listing avoid off-platform payment pressure or fake urgency?

## Daily operating rhythm

**Opening review**

- Check system health, partner status and unresolved high-priority cases.
- Review overnight reports and listings that may create immediate harm.
- Confirm that public status notices match reality.

**Queue work**

- Process seller readiness, listing review and Soek Request review in received order unless risk changes priority.
- Record the reason for rejection, pause or restriction.
- Separate support questions from trust-and-safety investigations.

**Marketplace quality**

- Review demand with thin supply and inventory with no useful exposure.
- Look for repeated images, duplicate descriptions, improbable pricing and account clusters.
- Check whether new sellers receive fair exploration without weakening safety.
- Review request responses for relevance and pressure tactics, and participant reports for attempts to share contact details or move payment outside any active protected rail.

**Closing review**

- Reconcile unresolved cases, handovers and partner exceptions.
- Assign every open high-priority item to a named owner.
- Record incidents, decisions and changes needed before the next operating window.

## Incident priorities

| Priority | Example | Initial action |
| --- | --- | --- |
| Critical | Credible threat to physical safety, active account takeover or material payment-system incident | Restrict affected capability, preserve evidence, escalate immediately and follow the incident plan. |
| High | Suspected fraud ring, prohibited high-risk item, repeated impersonation or compromised seller | Pause relevant accounts/listings, investigate linked activity and notify the responsible operator. |
| Medium | Misleading condition, fulfilment dispute, harassment or repeated policy breach | Open a case, gather both sides and apply proportionate restrictions. |
| Low | Copy quality, category correction or ordinary support request | Route to the normal queue and resolve with a clear explanation. |

Exact response targets should be set only after staffing and support hours are committed. This document does not invent them.

## Pilot measures

Define each measure before collecting it and report denominators alongside rates. The current product does not record trade completion, cancellations, trade-linked reviews or behaviour-based reputation. Until those features are activated, the trade-reliability measures below are research observations kept separate from marketplace status.

### Marketplace usefulness

- Search-to-relevant-result rate by neighbourhood and category.
- Time from first search to a meaningful item view or Soek Request.
- Demand coverage: requests that receive a relevant seller response.
- Local density: useful active listings per supported area/category.

### Trade reliability

- Fulfilment rate among trades that reached an agreed handover.
- Cancellation rate, split by buyer, seller and system/partner cause.
- Dispute and report rate per completed trade.
- Repeat participation after a successfully completed trade.

### Trust comprehension

- Percentage of tested users who correctly interpret readiness, verification and review statuses.
- Percentage who identify that payment screenshots are not proof and that illustrative preview signals are not earned live-seller reputation.
- Report discovery and completion rate in usability testing.
- Appeals and overturned moderation decisions.

### Operations

- Queue age by type and priority.
- Time to first meaningful action on safety reports.
- Share of actions with complete reason and audit attribution.
- Partner exceptions that reconcile automatically versus manually.

No target should be chosen merely because it looks impressive. Targets must reflect actual staffing, category risk and user harm tolerance.

## Public-launch gates

| Gate | Evidence required | Owner type |
| --- | --- | --- |
| Product quality | Full journey QA, recovery states, accessibility and mobile acceptance | Product and engineering |
| Trust operations | Trained reviewers, case procedures, escalation and appeal path | Marketplace operations |
| Legal and privacy | Approved terms/notices, operating entity, data and provider roles | Legal/privacy |
| Security | Resolved launch blockers, access review, monitoring, restore and incident drill | Security/engineering |
| TPTS/provider | Signed scope, certification, support model, settlement and reconciliation | Partner/finance |
| Marketplace health | Adequate useful supply and supportable invited demand | Pilot lead |
| Communications | Claims, launch material and status page match live capability | Product/communications |

If one gate fails, the corresponding feature stays inactive or the launch pauses. “Almost ready” is not an integration state.

## Expansion rule

Soek.Iets should not expand beyond Windhoek because the map looks small. Expansion becomes reasonable when the pilot demonstrates:

- enough local supply and demand to make neighbourhood discovery useful;
- stable fulfilment and a manageable incident rate;
- support and moderation capacity that scales with participation;
- partner rails that reconcile reliably;
- users who understand the platform’s trust and location language;
- a repeatable method for mapping areas without exposing exact locations.

The next city or town is a new operating context, not a copy-and-paste switch.
