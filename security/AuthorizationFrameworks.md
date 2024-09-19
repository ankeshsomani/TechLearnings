# AuthorizationFrameworks

## What is Authorization
Authorization is the process of determining what acess or resources a user is allowed after successful authentication.
This is often managed using Access Control lists (ACLs) or Role based access control(RBAC)
Authentication - Determines who are you.
Authorization - Determines what you are allowed to.

## Authorization Frameworks
Systems or standards that defines how users are granted access to resources based on their roles, permissions or policies.

### OAuth2.0
   Used widely for authorizing third-part applications to access user data without user sharing their login credentials(username, password).
   OAuth allows apps to obtain access token that represent user's permission to acess specific user resources.
   Ex/- "Sign in with Google", "Sign in with facebook"
   
### OpenID Connect (OIDC)
   Build on top of OAuth2.0.It provides authentication and authorization by adding an identity layer to OAuth2.0.
   After authenticating the users, it sends an ID token along with acess token, which verifies the identity and grants specific permission to the user.  
   used for single sign on (SSO) applications.
   
### Role-Based Access control (RBAC)
  Assigns permissions based on user roles.
  Example: In a content management system, an Admin can create, edit, and delete content, while an Editor can only modify existing content.

### Attribute-based Access Control (ABAC)
  Assigns permissions based on the attribute of user, resource and environment.
  Example: A user from the HR department can access payroll data only during work hours and from within the company's network.

### Access Control lists (ACLs)
  Assigns permission to specific user or groups for each resource.
  Example: A file might have an ACL that allows User A to read and write but allows User B to only read.

### SAML (Security Assertion Markup Language)
  Used for SSO. Allows user to login in once and access multiple services wihout reauthenticating.
  Example: Logging into multiple cloud-based services after signing in once with an identity provider (e.g., Microsoft Active Directory).
