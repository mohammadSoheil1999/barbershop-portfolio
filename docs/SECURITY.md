# Security and Privacy

- Passwords use adaptive hashing rather than plaintext storage.
- Signed authentication tokens carry role and tenant context.
- Protected routes enforce authorization and tenant scope on the server.
- Business-owned queries include tenant constraints.
- Appointment-slot uniqueness is tenant-scoped at the database boundary.
- Input validation and origin/CORS policy belong at the API boundary.
- Notification credentials, database credentials, production URLs, and provider secrets remain server-side and are not included here.

The public portfolio excludes customer identity and production data. The screenshots use the fictional portfolio brand “Luxorius” and contain no customer records.

This summary describes the design at a safe level and is not a claim of formal security certification.

