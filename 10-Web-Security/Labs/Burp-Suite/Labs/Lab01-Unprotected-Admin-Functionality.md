🧪 Lab 01 - Unprotected Admin Functionality
Platform: PortSwigger Web Security Academy
Category: Access Control
Difficulty: Apprentice
Status: ✅ Solved

Objective
Identify an administrator interface that is accessible without authentication and perform an administrative action.

Background
The application contains an administrator panel that is not protected by proper access control mechanisms. Instead of verifying user permissions on the server, the administrator interface is simply hidden from normal users.

Methodology
Opened the lab in Burp Suite's built-in Chromium browser.
Browsed the application to understand its structure.
Observed requests using Burp HTTP History.
Tested common administrator paths.
Investigated the robots.txt file.
Found the following entry:

User-agent: \*
Disallow: /administrator-panel

Navigated to:

/administrator-panel

Successfully accessed the administrator panel without authentication.
Deleted the user carlos.
Verified that the lab was solved.
Vulnerability
Broken Access Control
The administrator interface was publicly accessible without verifying whether the user had administrator privileges.

Evidence
Discovered administrator endpoint:


/administrator-panel

Administrative action performed:

Deleted user: carlos
Impact
An attacker could:

Access administrative functionality
Delete users
Modify sensitive data
Compromise the entire application
Severity: High

Root Cause
The application relied on hiding the administrator interface instead of enforcing authorization on the server.

No authentication or authorization checks were performed before granting access.

Remediation
Developers should:

Enforce server-side authorization checks
Deny access by default
Verify user roles before every privileged action
Never rely on hidden URLs for security
Burp Suite Skills Practiced
HTTP History
Request Analysis
Reconnaissance
robots.txt Analysis
Pentester's Notes
The robots.txt file unintentionally disclosed the administrator interface.

Although robots.txt is intended for search engine crawlers, attackers frequently inspect it for hidden resources.

Lessons Learned
Hidden resources should never be considered secure.
Always inspect robots.txt.
Broken Access Control often begins with information disclosure.
Server-side authorization is mandatory.
Status
✅ Lab Solved
