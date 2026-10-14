# Level 01 — The Idiot Test

## Overview
- **Platform:** Hack This Site
- **Category:** Web security fundamentals
- **Objective:** Identify how the password for the level is exposed.

## Investigation

### Initial observations
The challenge suggests reviewing the page's HTML.

### Methodology
1. Opened the browser's Developer Tools.
2. Inspected the password form and its surrounding HTML.
3. Examined the HTML comments for potentially sensitive information.

### Findings
The page's HTML contained a comment revealing the password.

### Security implications
HTML comments are not displayed as normal page content, but they are delivered to the client and can be inspected. Sensitive information must not be embedded in client-side source code or comments.

### Lessons learned
- Understand the difference between rendered content and the underlying HTML.
- Use browser Developer Tools to inspect page structure.
- Treat all information delivered to the client as accessible to that client.

## References
- [Hack This Site](https://www.hackthissite.org/)
