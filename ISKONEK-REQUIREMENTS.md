# iSKonek — Product and Security Requirements

For SK Barangay Catubugan, Boac, Marinduque.

## Confirmed decisions
1. **Eligibility:** Youth residents of Barangay Catubugan may apply. SK administrators manually approve accounts.
2. **Administration:** The SK Chairperson and selected SK officers manage the portal with role-based, different permissions.
3. **Identity verification:** Applicants provide their full name, username, password, and the minimum additional information needed to verify eligibility. An application is reviewed before access is activated.

## User roles
- **Applicant:** Can submit an access application and see its status without access to protected portal pages.
- **Youth member:** Can view approved public SK announcements/documents, request printing appointments, and access youth programs.
- **SK officer:** Only explicitly assigned permissions, such as reviewing printing requests or publishing announcements.
- **SK administrator:** Approves/rejects applications, manages accounts and roles, oversees service requests, and reviews security/audit events.
- **Primary administrator:** Chairperson account with control over officer access. Use a second trusted recovery method.

## Core features
- Account application and manual approval queue.
- Secure login, logout, password reset, account suspension, and role checks.
- Announcements with author and publication/edit timestamps.
- Public document directory linking only to files approved for public release.
- Printing appointment request, approval, rejection, completion, and status history.
- Youth project/program information and a secure suggestion/interest form.
- Admin dashboard with aggregate usage, account status, appointment queue, and minimal audit events.
- Mobile-friendly, accessible interface.

## Security requirements before launch
- Use a real authentication provider and database; never trust browser-only role flags.
- Passwords must be handled by the authentication provider and never stored as plaintext.
- Protect all admin operations with server-side authorization.
- Rate-limit login attempts; use secure cookies/sessions and HTTPS.
- Validate inputs server-side; protect against common web vulnerabilities.
- Do not expose private application details or admin APIs to ordinary users.
- Log security-relevant actions without logging passwords or unnecessary sensitive information.
- Establish backup, recovery, account-retention, and incident-response procedures.
- Use least-privilege access for officers and remove access promptly when roles change.
- Publish a clear privacy notice and define purpose, lawful basis, access, retention, and deletion procedures under applicable Philippine privacy rules.
- Collect only the personal data needed for eligibility verification. Do not collect government ID uploads by default unless the SK has determined they are necessary and has appropriate safeguards.
- Since youth may be minors, provide age-appropriate notices and implement appropriate safeguards and guardian processes where legally required.

## Suggested implementation
- Frontend: responsive web app.
- Authentication and database: a managed provider such as Supabase, configured with row-level security and server-side role checks.
- Hosting: static frontend hosting plus protected server/database services.
- Store documents in a controlled document directory; public files should be deliberately published, and confidential records must not be placed in public storage.

## Current repository status
`index.html` is a visual/browser-only prototype. Demo credentials, sign-ins, announcements, and appointments are local to the page and are not secure or persistent. Do not use it for real resident information or operational bookings until the backend, authentication, authorization, and privacy controls have been implemented and tested.

## Suggested rollout
1. Finalize eligibility rules and exact data fields with the SK.
2. Set up authentication, database schema, and access policies.
3. Build application approval and officer role management.
4. Connect announcements, public documents, and printing appointments.
5. Test authorization, privacy, mobile accessibility, backups, and recovery.
6. Pilot with a small group before public launch.
