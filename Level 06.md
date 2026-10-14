# Level 06 — Cryptography

## Overview

- **Platform:** Hack This Site
- **Category:** Cryptography Fundamentals
- **Objective:** Analyze a character-transformation algorithm and recover the original password from an encrypted string.

## Initial Observations

The challenge provides an encrypted password and access to a tool that encrypts user-supplied strings.

The initial encrypted string was:

`fcg67:6=`

Rather than guessing the password, I used controlled inputs to investigate how the transformation behaved.

## Investigation Methodology

### 1. Tested a known input

Input:

`password`

Output:

`pbuv{txk`

This showed that the transformation affected individual characters.

### 2. Tested repeated characters

Input:

`aaaaaaaa`

Output:

`abcdefgh`

The output changed with each character's position. This suggested that the transformation was position-dependent rather than a fixed substitution.

### 3. Tested numeric characters

Input:

`0123456789`

Output:

`02468:<>@B`

Comparing the input and output revealed a consistent pattern: the character codes increased by a value corresponding to each character's zero-based position.

### 4. Reversed the transformation

Based on the observed pattern, I hypothesized that the original characters could be recovered by subtracting the position-dependent offset from each encrypted character's code.

I worked through the characters individually, using notes to track the calculations and correct an initial mistake.

The recovered password candidate was:

`fbe33506`

### 5. Validated the result

I submitted the recovered candidate to the challenge and received the successful completion message.

## Findings

The challenge used a predictable, position-dependent character transformation that could be analyzed using chosen inputs.

By comparing known inputs with their outputs, I inferred the transformation rule and reversed it to recover the password.

## Technical Analysis

The observed behavior is consistent with a transformation of the form:

`encrypted[i] = characterCode(plaintext[i]) + i`

where `i` is the zero-based character position.

The corresponding reversal is:

`plaintext[i] = characterCode(encrypted[i]) - i`

This describes the behavior observed in the challenge's test cases. It should not be interpreted as a secure cryptographic algorithm.

## Security Implications

- Predictable character transformations provide little protection for sensitive data.
- A publicly available encryption function can be analyzed using controlled inputs.
- A reversible transformation is not necessarily secure encryption.
- Real password storage should use a dedicated password-hashing algorithm with appropriate salts and work factors, rather than a reversible character transformation.

## Lessons Learned

- Use controlled experiments to investigate unknown algorithms.
- Repeated characters can help reveal position-dependent behavior.
- Compare input and output systematically to identify patterns.
- ASCII character codes can be inspected using reference tables or tools; memorizing them is unnecessary.
- Verify a recovered value against the original transformation and the challenge's expected behavior.
- Keep track of character positions carefully to avoid calculation errors.

## References

- [Hack This Site](https://www.hackthissite.org/)
