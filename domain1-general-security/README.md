
# Domain 1. General Security Concepts
## Lab. IAM Roles and Least Privilege in Auth0

### Objective
Implement role based access and least privilege in Auth0. Prove that users only see resources permitted to their role.

### Why it matters
Least privilege reduces blast radius and aligns with Security+ principles for confidentiality and authorization control. This is foundational for CIAM readiness.

### Prerequisites
Auth0 tenant. Test app. Your repo cloned or GitHub web editor.

### Steps
1. Create roles in Auth0  
   Admin. Manager. User.
2. Define permissions  
   `read:reports` and `write:reports` for a Reports API. Use Auth0 permissions under APIs.
3. Create three test users  
   `admin@test.local` with Admin. `mgr@test.local` with Manager. `user@test.local` with User.
4. Assign permissions to roles  
   Admin gets read and write. Manager gets read. User gets no reports scope.
5. Configure your application to request scopes  
   Add `audience` and `scope` to the OIDC auth request. Example scopes: `read:reports write:reports`.
6. Build a minimal verification endpoint  
   In your app or a quick container, decode the access token and print the `scope` claim. Also gate a mock endpoint so that write requires `write:reports`.
7. Test logins  
   Log in as each account. Call the protected endpoint. Observe allowed and denied cases.
8. Capture evidence  
   Screenshots. Roles list. Permissions mapping. Token payload showing `scope`. Allowed and denied responses.

### Expected results
Admin can read and write. Manager can read only. User is denied. Token scopes match the assigned role.

### Security+ links
Access control models. Authorization versus authentication. Least privilege. Separation of duties.

### CIAM links
Role design. Consent and scope hygiene. Principle of minimal data exposure.

### Artifacts to commit
- `domain1-general-security/screenshots` with 3 to 5 PNGs  
- `domain1-general-security/token-sample.json` with a redacted token payload  
- `domain1-general-security/notes.md` with one paragraph on what broke and how you fixed it
