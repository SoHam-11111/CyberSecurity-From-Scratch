🧪 Lab 02 - Unprotected Admin Functionality with Unpredictable URL
Platform: PortSwigger Web Security Academy
Category: Access Control
Difficulty: Apprentice
Status: ✅ Solved

Objective
Identify an administrator interface hidden behind an unpredictable URL and demonstrate unauthorized administrative access.

Background
The application attempts to protect its administrator interface by assigning it an unpredictable URL instead of enforcing proper authorization.

This is an example of Security Through Obscurity, which is not a secure access control mechanism.

Methodology
Opened the application using Burp Suite.
Browsed the website normally.
Investigated HTTP History.
Examined application resources.
Reviewed the page source (Ctrl + U).
Located a hidden administrator URL embedded in the HTML source.
Opened the administrator interface.
Deleted the user carlos.
Confirmed successful completion of the lab.
Vulnerability
Broken Access Control
The administrator interface could be accessed directly without any authorization checks.

The only protection was an unpredictable URL.

Evidence
Administrator URL was discovered inside the HTML source code.

Administrative action performed:

Deleted user: carlos
Impact
An attacker who discovers the hidden administrator URL can:

Access privileged functionality
Delete users
Modify application data
Fully compromise the application
Severity: High

Root Cause
The application relied on URL secrecy rather than enforcing authorization.

Knowing the URL granted administrative access.

Remediation
Developers should:

Implement server-side authorization checks
Verify user roles for every administrative request
Avoid relying on hidden or unpredictable URLs
Apply the principle of least privilege
Burp Suite Skills Practiced
HTTP History
Reconnaissance
HTML Source Analysis
Access Control Testing
Pentester's Notes
The administrator interface was not disclosed through robots.txt.

Instead, it was embedded within the HTML source code, demonstrating the importance of reviewing page source during reconnaissance.

Lessons Learned
Security through obscurity is not security.
Hidden URLs can often be discovered through client-side resources.
Reviewing page source is a fundamental reconnaissance technique.
Authorization must always be enforced on the server.
Comparison with Lab 01
Lab	Discovery Technique
Lab 01	robots.txt
Lab 02	HTML Source Code
Although the discovery methods differed, both vulnerabilities resulted from missing server-side authorization.

Status
✅ Lab Solved
