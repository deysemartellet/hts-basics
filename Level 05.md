# Level 05 — Network Security

## Overview

- **Platform:** Hack This Site
- **Category:** Web Security Fundamentals
- **Objective:** Verify whether changes to a password-recovery mechanism prevent unauthorized redirection of password emails.

## Initial Observations

The challenge states that Sam has become aware of users modifying the email form to receive his password. He claims to have made the email program more secure.

The page still provides a button labeled `Send password to Sam`.

## Investigation Methodology

1. Inspected the HTML associated with the email submission button.
2. Examined the form's hidden recipient field.
3. Observed that the recipient still contained Sam's email address.
4. Changed the recipient to the email address associated with my Hack This Site account.
5. Submitted the form and verified that the password email was received.
6. Confirmed successful completion of the challenge.

## Findings

The recipient field remained modifiable through the browser's Developer Tools.

Changing the recipient allowed the email to be redirected to the alternative address used during the challenge.

The challenge was completed successfully, demonstrating that the behavior described in the previous level remained possible.

## Technical Analysis

This level demonstrates the importance of retesting security controls after a claimed improvement.

The observed behavior indicates that the modification described in the challenge did not prevent the tested recipient-redirection technique.

The exact server-side implementation was not inspected. Therefore, the finding is limited to the observed behavior rather than a claim about the internal code.

## Security Implications

- Client-controlled form fields must not be trusted for authorization decisions.
- Security fixes should address the underlying cause of a vulnerability.
- Retesting should reproduce the original steps used to demonstrate the issue.
- Password-recovery mechanisms should use secure, verified recovery workflows instead of emailing plaintext passwords.

## Lessons Learned

- A claimed security improvement must be validated through testing.
- Repeating a previously successful test can reveal an ineffective fix.
- Comparing related challenges helps identify recurring security weaknesses.
- Findings should be supported by observed behavior and clearly stated limitations.

## References

- [Hack This Site](https://www.hackthissite.org/)
