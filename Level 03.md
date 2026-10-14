# Level 03 — Network Security

## Overview

- **Platform:** Hack This Site
- **Category:** Web Security Fundamentals
- **Objective:** Investigate weaknesses in a password-protection mechanism after the password file has been uploaded.

## Initial Observations

The challenge states that Network Security Sam has uploaded the password file this time, but deeper problems remain.

The password form uses the following attributes:

- **Method:** `POST`
- **Action:** `/missions/basic/3/index.php`
- **Hidden field value:** `password.php`

These observations suggested that the password file might be accessible through a direct request.

## Investigation Methodology

1. Inspected the HTML form using the browser's Developer Tools.
2. Identified the form's submission method and destination.
3. Observed the hidden input containing the value `password.php`.
4. Navigated directly to the corresponding resource.
5. Observed the server's response.
6. Used the discovered value to complete the challenge.

## Findings

The resource at `/missions/basic/3/password.php` was directly accessible through the browser and returned a value.

Using that value in the challenge's password form resulted in successful completion of Level 3.

The challenge displayed the following confirmation:

> Congratulations, you completed basic 3 again! No points awarded.

## Technical Analysis

The challenge demonstrates how sensitive information can be exposed when a resource containing a password is accessible without appropriate access controls.

A hidden HTML input is not secret: its value can be inspected by the user and may be submitted to the server.

However, the hidden field alone does not establish a vulnerability. The significant finding was that the password resource could be accessed directly and returned a value that allowed the challenge to be completed.

The observed behavior is consistent with an information disclosure issue involving a password-related resource.

## Security Implications

- Sensitive credentials should not be exposed through publicly accessible resources.
- Hidden HTML inputs must not be treated as security controls.
- Server-side access controls should protect sensitive files and resources.
- Authentication should be designed so that knowledge of a resource path does not grant unauthorized access to credentials.

## Lessons Learned

- Inspecting form attributes can reveal useful investigation leads.
- Direct resource access can expose
