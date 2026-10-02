# Hatter client delivery runtime

Consumes the exact delivered Scene/identity before opening the Crowsi STATE
subscription. Reuses PP client state, navigation, revision fencing and rebasing;
does not implement a second state authority. Site data and owner input declarations
are data only. Trusted renderer emits native DOM and exact action handles.

Navigation URLs locate product views; they cannot supply canonical Role/source
context. Site/owner handlers must resolve all fixed context from an exact accepted
Scene. A stale action or late fetch cannot submit/rebase itself to a newer head.
No automatic owner provisioning, inference, installation or login occurs.

A site may acknowledge a selected, durably registered producer before its first
snapshot exists: `bootstrap.input = { key, revision: null, requirementRef }`.
`requirementRef`, when supplied, identifies only that exact projection-read
requirement. The first validated STATE snapshot for the same key satisfies that
read; other unavailable owners and setup requirements remain unchanged. This
does not decide authentication, Models readiness or semantic adoption. Missing
snapshots use the existing Crowsi subscription, not a polling or retry channel.

An invalid/lost mutation response is `DeliveryOutcomeUncertain`, retaining the
browser request nonce for investigation. No automatic mutation resend occurs.
Only the canonical owner receipt can establish whether the operation committed.
# Site presentation and declared setup controls

The site may provide `bootstrap.page` with a display-only `title`, `description`,
`emptyMessage` and `dataLabel`. These do not alter readiness or create a Scene.
Original typed failures and state data remain available in expandable details.
`bootstrap.actions[].input` uses the existing Zixcel input declaration and trusted
renderer; submission sends the declared action ID and exact values to the site's
existing command endpoint. The site and canonical owner validate inputs and the
reviewed revision. Navigation/disposal releases input state; commands are not
automatically retried and failed requests cannot imply successful owner effects.
