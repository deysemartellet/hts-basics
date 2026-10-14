# Level 02 — Network Security

## Overview
- **Platform:** Hack This Site
- **Category:** Web security fundamentals
- **Objective:** Investigate a password-protection mechanism that relies on an external plaintext file.

## Investigation

### Initial observations
The challenge states that the password-protection script attempts to load the real password from an unencrypted text file. However, the file was not uploaded to the server.

### Methodology
1. Inspected the page using the browser's Developer Tools.
2. Examined the available JavaScript resources.
3. Monitored network requests using the Network panel.
4. Submitted the form with an empty password field and observed the result.

### Findings
Submitting the form with an empty password allowed the challenge to be completed.

### Technical analysis
The observed behavior is consistent with a password comparison that accepts an empty value when the expected password cannot be loaded.

The missing password file appears to cause the authentication mechanism to behave insecurely.

The exact server-side implementation was not inspected, so the precise internal cause remains an inference rather than a directly verified finding.

### Security implications
Authentication mechanisms should fail securely when a required credential file is missing or cannot be read.

An application must not allow authentication to succeed simply because a password could not be retrieved.

### Lessons learned
- Missing resources can expose weaknesses in authentication logic.
- Successful HTTP responses do not necessarily indicate correct application behavior.
- Testing an application's normal functionality can reveal unexpected security issues.
- Distinguish observed behavior from inferred implementation details.

## References
- [Hack This Site](https://www.hackthissite.org/)
