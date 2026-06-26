# Proof of Concept (PoC): Paywall Bypass via Business Logic Flaw

## 📝 Vulnerability Description
A Business Logic Vulnerability was identified that allows users to bypass the paywall and access premium/subscription-only content for free. By manipulating URL parameters (specifically promotional offer tags) and combining it with a new free account registration using a temporary email, the system's authorization check is bypassed, granting full access to premium articles.

## 🔍 Vulnerability Classification
- **Vulnerability Type:** Business Logic Flaw / Paywall Bypass / Improper Authorization
- **Severity:** Medium

## 👣 Steps to Reproduce
1. Navigate to the target website using a manipulated promotional URL parameter (e.g., `http://[target-website].com/free??lmo_offer=%0Foffers2%0FAS-AS.DIGITAL.3YAR.X.DISC.30.M&country=**`).
2. Observe that the site initially returns a 404 "Page not found" error or broken page.
3. Minimize the current tab and use a temporary email service (e.g., Oxaam) to generate a throwaway email address (e.g., `quantam34@...`).
4. Go to the "Create free account" or Registration section on the target website.
5. Fill out the registration form using the generated temporary email, provide dummy data for job title/industry, and complete the account creation process.
6. Return to the original manipulated link or use the website's search bar to find a specific premium article (e.g., "Why big AI labs are hiring so many philosophers").
7. Click on the premium article link.
8. **Result:** The full premium content is fully accessible from start to finish without requiring any paid subscription.

## 💥 Impact
Malicious actors or regular users can easily bypass the subscription model of the website. This logic flaw leads to unauthorized access to paid digital assets, resulting in a direct loss of revenue and devaluing the premium subscription service for legitimate paying users.

## 🛡️ Mitigation / Remediation
- **Server-Side Validation:** Implement strict server-side validation for all promotional codes and URL parameters. Do not rely on client-side state or malformed URL handling to grant access tokens.
- **Strict Authorization Checks:** Ensure that premium content authorization strictly checks the user's actual subscription status and roles in the backend database before rendering the full article.
- **Email Verification:** Implement strict email verification and consider restricting or flagging the use of known temporary/throwaway email domains for account registration.

## ⚠️ Disclaimer
This Proof of Concept (PoC) is documented for educational purposes and responsible disclosure only.
