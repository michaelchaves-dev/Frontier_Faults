# Frontier Faults — Candidate-evaluation boundary audit

**Classification:** governance / transparency research candidate, **NOT** a verified model fault. **Status:** UNRESOLVED. No claim that any vendor has committed misconduct.

# AI hiring boundary — living case study (2026-10-08)

**Status:** OPEN / observational; no wrongdoing established. **Owner:** Subtract Architect Studios. **Next update:** after additional applicant-side emails/interview evidence, with consent and redaction.

## Observed evidence
- An applicant interacting with the Extra Space Storage careers page for a Pembroke store-manager position captured screenshots of a chatbot named **Sage / ESS Careers Expert**, labeled **“Powered by AppVault AI.”**
- Sage said it could not provide specifics about applicant information storage or management; stated that chat interactions are **generally** for guidance rather than formal evaluation, and formal assessment **usually** begins after application submission; referred detailed questions to recruiters.
- These screenshots establish the displayed vendor attribution and chatbot wording, **not** the employer's actual backend configuration, transcript retention, scoring, identity linking, or hiring decisions.

## Core research question
**When does the interview really begin?** Distinguish (A) site analytics/data collection, (B) candidate identification/linkage, (C) qualification screening, (D) formal evaluation, and (E) human hiring decisions. These boundaries may differ.

## Ternary evidence ledger
- +1: Sage branding and AppVault AI attribution visible in screenshots supplied 2026-10-08.
- +1: Sage's qualified statements and referral to recruiters visible in screenshots.
- 0: Whether chat transcripts are retained, linked to an applicant, viewed by recruiters, or used to score candidates.
- 0: Whether the vendor powering chat also powers later interviews, and what underlying model is used.
- 0: Whether any pre-application interaction influences the eventual hiring decision.
- No -1 contradiction finding at this time.

## Responsible investigation plan
1. Preserve original screenshots, timestamps, email notices, application consent language, and interview invitations privately; do not commit personal communications or identifiers to public repositories.
2. Read employer/vendor privacy and recruiting disclosures and distinguish product capability from confirmed employer deployment.
3. Request clarification from authorized recruiting/privacy staff about transcript retention, ATS/CRM linkage, scoring, access, correction/deletion rights, and human-review alternatives.
4. Track the earliest **disclosed** and earliest **evidenced** point of evaluation separately; don't conflate tracking with assessment.
5. Document benefits (speed, access, consistency) and risks (context collapse, incorrect inferences, hidden data flows) symmetrically.
6. Do not probe private endpoints, bypass controls, or publish identifiable candidate/recruiter data.

## Update log
- 2026-10-08: Initial applicant-side screenshot observations. Investigation remains open; subsequent email/interview stages not yet evaluated.

**Method:** Negative Step Zero; observation ≠ inference ≠ finding. No unsupported accusation of bias or profiling.

## Potential fault hypotheses for future testing
- **Boundary opacity:** applicant cannot determine whether exploratory chat data is subsequently used in evaluation.
- **Context collapse:** benign curiosity could be interpreted as a negative candidate trait if out-of-context data is reused; no evidence this happened.
- **Unverifiable reassurance:** a bot's generic explanation might be mistaken for a binding data-handling guarantee.

**Mitigations to investigate:** explicit data-use disclosure at first collection, purpose separation, audit trails, applicant correction route, documented human oversight, and tests of whether pre-application messages affect later scoring. These are proposals, not verified gaps.
