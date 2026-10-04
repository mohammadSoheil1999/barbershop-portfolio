# Engineering Notes

## Shared runtime versus separate deployments

A shared tenant-aware runtime reduces duplicated releases and makes product improvements reusable. It also raises the cost of authorization mistakes, so tenant scope must be centralized, tested, and derived from verified authentication state.

## Scheduling consistency

Availability shown in a browser can become stale. The durable protection belongs at the database/service boundary: re-check eligibility when creating the appointment and use tenant-scoped uniqueness or a transaction to prevent two users from claiming the same slot.

## Customization model

Storing branding as tenant settings avoids branching the application for each business. Validation should constrain names and color values, while defaults keep incomplete configurations usable.

## Reliability priorities

High-value tests cover tenant isolation, role boundaries, concurrent booking, cancellation rules, notification-provider failure, inactive accounts, and mobile/RTL workflows. Production operation also requires structured logs, health checks, backups, and restore exercises.

