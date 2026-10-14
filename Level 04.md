# Level 04 — Network Security

## Overview

- **Platform:** Hack This Site
- **Category:** Web Security Fundamentals
- **Objective:** Investigate a password-recovery mechanism that sends a hardcoded password by email.

## Initial Observations

The challenge describes a password-protection script that stores the password directly in its code. To help Sam recover the password, a separate script sends it to him by email.

The page contains a form with the following attributes:

- **Method:** `POST`
- **Action:** `/missions/basic/4/level4.php`
- **Hidden field name:** `to`
- **Hidden field value:** `sam@hackthissite.org`

The form also contains a submit button labeled `Send password to Sam`.

## Investigation Methodology

1. Inspected the HTML form using the browser's Developer Tools.
2. Identified the form's submission method and destination.
3. Examined the hidden input responsible for specifying the email recipient.
4. Changed the recipient to the email address associated with my Hack This Site account.
5. Submitted the form and verified that the challenge was completed.

## Findings

The email recipient was specified through a client-side hidden input.

Modifying the recipient allowed the password-recovery mechanism to send the message to the alternative address used during the challenge.

The challenge was successfully completed.

## Technical Analysis

The form exposed the email recipient through a hidden HTML field. Although the field was not visible in the normal page interface, its value could be inspected and modified through browser Developer Tools.

This behavior demonstrates the risk of trusting client-controlled parameters for security-sensitive operations.

If a server accepts an arbitrary recipient without appropriate validation or authorization, an attacker may redirect sensitive messages to an unintended destination.

## Security Implications

- Hidden fields are not security controls.
- Client-supplied parameters must be validated on the server.
- Password-recovery mechanisms should not disclose credentials through email.
- Recovery workflows should use appropriate verification and short-lived, single-use reset tokens.

## Lessons Learned

- Inspecting form attributes can reveal important application behavior.
- Client-side values can be modified before submission.
- Successful exploitation must be confirmed through observable application behavior.
- Security controls must be enforced on the server, not merely in the interface.

## References

- [Hack This Site](https://www.hackthissite.org/)
