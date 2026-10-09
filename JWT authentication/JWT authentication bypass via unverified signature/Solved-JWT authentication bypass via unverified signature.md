
# JWT Authentication Bypass via Unverified Signature

<p align="center">
  <img src="https://img.shields.io/badge/Platform-PortSwigger_Web_Security_Academy-FF6633?style=for-the-badge" alt="PortSwigger Web Security Academy">
  <img src="https://img.shields.io/badge/Topic-JWT_Security-0078D4?style=for-the-badge" alt="JWT Security">
  <img src="https://img.shields.io/badge/Focus-Authentication-6F42C1?style=for-the-badge" alt="Authentication">
</p>

> **Lab:** JWT authentication bypass via unverified signature  
> **Platform:** PortSwigger Web Security Academy  
> **Category:** JSON Web Token (JWT) / Authentication  
> **Objective:** Test whether a modified JWT is trusted without proper signature verification and use the weakness to access the lab's admin functionality.

---

## 1. Overview

This lab demonstrates an authentication flaw that occurs when an application accepts a JSON Web Token (JWT) without correctly validating its signature. A JWT commonly carries claims about a user or session. If the application trusts those claims without verifying that the token is authentic, an attacker may be able to modify a claim and impersonate another user.

The purpose of this write-up is to document the lab workflow, the role of Burp Suite in inspecting the session token, and the security impact of missing JWT signature verification.

## 2. Learning Objectives

- Recognize a JWT-style session token in an HTTP request.
- Inspect a token's header and payload using Burp Suite and a JWT viewer/editor.
- Understand why changing a token's claims must not grant additional privileges unless the signature is valid.
- Document the impact and appropriate remediation for authentication bypass vulnerabilities.

## 3. Tools Used

| Tool | Purpose |
| --- | --- |
| PortSwigger Web Security Academy | Provides the authorized practice lab. |
| Burp Suite Proxy | Intercepts and inspects browser-to-application traffic. |
| Burp Suite Repeater | Allows controlled resending and modification of HTTP requests. |
| JWT Editor / JWT viewer | Helps inspect JWT headers, payloads, and signatures. |
| Web browser | Opens the lab and signs in to the application. |

## 4. Technical Background

A typical signed JWT has three Base64URL-encoded sections separated by periods:

```text
header.payload.signature
```

- **Header:** Declares token metadata, often including the signing algorithm.
- **Payload:** Contains claims, such as a subject or user identifier.
- **Signature:** Allows the server to verify that the token has not been modified and was signed by a trusted party.

Decoding a JWT does not verify its signature. The server must validate the signature and relevant claims before using the token for authentication or authorization.

## 5. Lab Walkthrough

### Step 1 — Start the lab

Open the PortSwigger lab page and select **Access the lab**. Use only the lab environment provided for this exercise.

![Lab launch screenshot](images/01-lab-start.png)

> **Screenshot note:** Add your exported lab-launch screenshot as `images/01-lab-start.png`.

### Step 2 — Sign in to the application

Open **My account** and sign in using the credentials supplied by the lab. Confirm that the application creates an authenticated session.

![Login screenshot](images/02-login.png)

### Step 3 — Intercept an authenticated request

With Burp Suite configured as the browser's proxy, refresh the authenticated page or open an account page. In Burp Suite, inspect the request in **Proxy** and send a relevant request to **Repeater** for controlled testing.

![Burp request screenshot](images/03-burp-repeater.png)

### Step 4 — Identify the session token

Inspect the request headers or cookies and locate the session value. In the original notes, this value appeared to use the JWT format, with three sections separated by periods.

Do not publish a live session token. Tokens copied from a lab session should be treated as sensitive and replaced with placeholders in public documentation.

### Step 5 — Inspect the JWT

Use Burp Suite's JWT Editor or another local JWT viewer to decode the token's header and payload. Identify the claim used by the application to associate the token with a user. Decoding is an inspection step only; it does not prove the token's signature is valid.

![JWT inspection screenshot](images/04-jwt-inspection.png)

### Step 6 — Test signature validation in the lab

In the authorized lab request, modify the user-identifying claim to the administrator identity used by the lab. Resend the request in Repeater and observe whether the application accepts the modified token even though its signature no longer matches the modified contents.

For example, if the token uses a `sub` claim for the identity, the relevant payload may contain a claim like this:

```json
{
  "sub": "administrator"
}
```

This is an illustrative claim only, not a complete JWT. Use the actual claim name and token structure observed in your lab. The vulnerability being tested is the server's failure to properly verify the signature—not the ability to create a legitimate signature.

![Modified JWT screenshot](images/05-modified-jwt.png)

### Step 7 — Verify access to the admin functionality

Use the modified session token in the lab request and check the response. If the application accepts the forged identity, follow the lab's instructions to open the admin functionality and verify the result. Record the exact endpoint, response, and completion state from your own run.

![Admin access screenshot](images/06-admin-access.png)

> **Evidence accuracy:** The supplied notes describe the goal of reaching the admin panel, but they do not include the final request, response, exact claim edit, or a clearly recorded lab-completion message. Add those details from your own Burp history and screenshots before presenting this as a fully verified solution.

## 6. Finding Summary

| Field | Details |
| --- | --- |
| Finding | JWT authentication bypass due to missing signature verification |
| Affected component | The application's JWT-based session validation |
| Root cause | The server may trust token claims without verifying the signature correctly |
| Security impact | A user may be able to modify identity or privilege-related claims and impersonate another account |
| Evidence to retain | Sanitized request/response, redacted token, and screenshot showing the lab result |

## 7. Remediation Recommendations

1. **Verify every JWT signature on the server.** Never trust claims from a token until signature validation succeeds.
2. **Allow only expected signing algorithms.** Do not select or accept an algorithm solely because an untrusted token declares it.
3. **Validate claims.** Check issuer, audience, expiration, not-before time, and other required claims.
4. **Enforce authorization independently.** Administrative permissions must be checked on the server for every protected action.
5. **Use secure JWT libraries and configurations.** Avoid custom verification logic and add tests for invalid, altered, expired, and incorrectly signed tokens.
6. **Monitor suspicious token behavior.** Log authentication failures and unexpected privilege changes without storing complete session tokens in logs.

## 8. Key Takeaways

- A JWT payload can often be decoded by anyone who has the token; decoding is not the same as verification.
- Any change to a signed token should cause signature verification to fail.
- Authentication and authorization decisions must not rely on unverified claims.
- Burp Suite Proxy and Repeater are useful for inspecting and safely testing requests in an authorized lab.

## 9. References

- [PortSwigger Web Security Academy — JWT attacks](https://portswigger.net/web-security/jwt)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)

## 10. Ethical Use

This write-up is for educational purposes and authorized security testing. Perform these techniques only in PortSwigger labs, systems you own, or environments where you have explicit permission to test. Do not use modified tokens against real users or systems without authorization.

---

<p align="center">
  <i>Documenting practical web security lessons, one lab at a time.</i>
</p>
