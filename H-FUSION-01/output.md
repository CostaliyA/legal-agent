**breach-response-plan.docx**

# BREACH RESPONSE PLAN
## Unauthorized Sharing of Telehealth Users’ Health Data with Advertising Platforms

**Privileged & Confidential — Attorney Work Product — Draft for Counsel Review**

---

## 1. Purpose, Scope, and Assumptions

This plan addresses the Company’s response to the reported sharing of telehealth users’ health data with advertising platforms. It covers four workstreams required by the matter task: **notification, consent, deletion, and regulator-facing steps**, together with immediate containment, documentation, and remediation.

This plan assumes, subject to verification, that:

- The Company operates a telehealth service and collected user information—potentially including email addresses, IP addresses, account/enrollment information, questionnaire responses, and other information identifying a user as seeking or receiving mental-health treatment.
- The Company transmitted some of that information to one or more advertising platforms or ad-tech vendors, potentially including through pixels, SDKs, custom audiences, conversions APIs, or direct uploads.
- Some transmissions may have occurred without valid user authorization or may have exceeded the Company’s privacy representations.
- Some data may have been hashed or encrypted. Hashing should not be treated as a safe harbor without legal review.

This is a response plan, not a legal opinion. Counsel must confirm the Company’s regulatory status, the applicable discovery date, the affected population, the data categories, and whether any consent order or contractual notification obligation applies.

---

## 2. Immediate Actions

### 2.1 Convene incident response team and preserve evidence

1. Convene legal, privacy, security, compliance, product, engineering, marketing, communications, and executive leadership.
2. Engage outside counsel as appropriate to direct the investigation and preserve privilege.
3. Issue a litigation hold covering logs, ad-platform configurations, audience uploads, pixel/SDK configurations, vendor contracts, privacy policies, consent flows, user complaints, and internal communications.
4. Preserve systems and data relevant to identifying what was shared, with whom, when, and under what disclosures. Do not delete data or configurations except under a documented preservation protocol.

### 2.2 Suspend ongoing ad-platform transmissions

1. Immediately suspend transmissions of health data and potentially identifying user data to ad platforms pending legal review.
2. Disable or reconfigure pixels, SDKs, custom-audience uploads, conversion tracking, retargeting, and similar integrations that may transmit covered information.
3. Preserve copies of configurations and data flows before changing them.
4. Instruct vendors not to use previously received data for advertising, retargeting, model training, or product development pending further instruction.

### 2.3 Start the legal-classification analysis

Counsel should promptly determine:

- Whether the Company is a **vendor of personal health records**, **PHR-related entity**, or **third-party service provider** under the FTC Health Breach Notification Rule, 16 C.F.R. Part 318.
- Whether the activity is instead governed by HIPAA because the Company is a HIPAA-covered entity or acting as a business associate. The HBNR excludes HIPAA-covered entities and activities performed as a HIPAA business associate.
- Whether any state breach-notification, health-privacy, consumer-protection, or ad-tech law applies. The attached sources do not supply state-law analysis; separate counsel review is required.
- Whether any FTC consent order or other settlement order binds the Company.

The HBNR analysis must be based on the Company’s actual data flows. The rule’s scope and defined categories are fact-specific, and the rule does not import the FTC Act’s jurisdictional tests. See `ecfr-hbnr-source-notes.md`, “Scope and covered entities — 16 CFR §§ 318.1–318.2.”

### 2.4 Communications discipline

1. Centralize all external communications under legal and communications review.
2. Do not make public statements, user statements, or regulator statements that misstate the data shared, the recipients, the purposes, the Company’s privacy practices, or the Company’s HIPAA status.
3. Do not claim HIPAA compliance unless verified. The BetterHelp final order prohibits misrepresentations about HIPAA-covered status and HIPAA compliance. See `betterhelp-final-order-official-mirror.txt`, p. 7, Provision III.F. The BetterHelp complaint and public-comment analysis also describe alleged HIPAA-certification misrepresentations, but those are allegations and proposed-order context, not findings binding on the Company. See `betterhelp-complaint-official-mirror.txt`, pp. 1–2; `betterhelp-public-comment-analysis.txt`, pp. 1–2.

---

## 3. Legal Framework and Key Distinctions

### 3.1 FTC Health Breach Notification Rule

If the Company is a covered entity under the HBNR and the incident is a reportable breach, the rule requires notification to affected U.S. individuals and the FTC, with media notice when 500 or more residents of one State or jurisdiction are affected. A third-party service provider reports to the covered vendor or PHR-related entity. See `ecfr-hbnr-source-notes.md`, “Who must be notified — § 318.3.”

Timing:

- Individual notice, media notice, and service-provider notice are due **without unreasonable delay and no later than 60 calendar days after discovery**.
- FTC notice for incidents involving **500 or more people** is contemporaneous with individual notice.
- For incidents involving **fewer than 500 people**, logged notices may be submitted annually within 60 calendar days after calendar year end.

See `ecfr-hbnr-source-notes.md`, “Timing — § 318.4.”

Methods and content:

- Individual notice is written, by mail or qualifying email.
- Urgent phone or other notice supplements, but does not replace, written notice.
- The rule also addresses substitute notice, media notice, and required notice contents.

See `ecfr-hbnr-source-notes.md`, “Methods and content — §§ 318.5–318.6.”

Enforcement:

- Violations are treated as violations of an FTC Act rule and may attract civil penalties.
- The rule applies to breaches discovered on or after 24 September 2009.
- The sunset is conditional; the regulation does not state an automatic 17 February 2026 expiration date.

See `ecfr-hbnr-source-notes.md`, “Enforcement and dates — §§ 318.7–318.9.”

### 3.2 BetterHelp final order: binding only on BetterHelp, but an enforcement benchmark

The BetterHelp final order is the operative settlement instrument in that matter. It is not binding on the Company unless the Company is a party, successor, or otherwise subject to its terms. The BetterHelp complaint contains allegations, not adjudicated findings. The proposed consent and public-comment analysis are pre-final materials and should not be treated as the operative order. See `ftc-enforcement-source-notes.md`, “BetterHelp”; `betterhelp-proposed-consent.txt`, p. 1, ¶ 2; `betterhelp-public-comment-analysis.txt`, p. 1.

The final order is nonetheless a useful compliance benchmark because it addresses similar facts: alleged sharing of health information and identifiers with ad platforms, alleged privacy misrepresentations, and alleged failures to obtain affirmative express consent. See `betterhelp-complaint-official-mirror.txt`, pp. 2–6, 10.

Key final-order provisions:

- **Provision I** prohibits disclosing **Treatment Information** to a Third Party for advertising, marketing, promotion, offering, offering for sale, or selling any product or service, and prohibits disclosing **Covered Information** for the purpose of targeting the consumer to whom the information pertains. See `betterhelp-final-order-official-mirror.txt`, pp. 6–7.
- **Provision II** requires **Affirmative Express Consent** before disclosing any consumer’s Covered Information to any Third Party, subject to the order’s definitions and exceptions. See `betterhelp-final-order-official-mirror.txt`, p. 7.
- **Provision III** prohibits misrepresentations about collection, use, disclosure, deletion, privacy, security, consumer control, privacy-program participation, and HIPAA status. See `betterhelp-final-order-official-mirror.txt`, p. 7.
- **Provision IV** imposes data-deletion steps, including identifying third parties that received Covered Information without Affirmative Express Consent, instructing them to delete it, and demanding written confirmation. See `betterhelp-final-order-official-mirror.txt`, pp. 7–9.
- **Provision V** required notice to specified Covered Users. See `betterhelp-final-order-official-mirror.txt`, p. 9.
- **Provision VI** requires a comprehensive privacy program with board reporting, a designated responsible employee, risk assessments, safeguards, vendor-contract reviews, access limits, training, and retention limits. See `betterhelp-final-order-official-mirror.txt`, pp. 9–10.

### 3.3 GoodRx enforcement context

The FTC describes GoodRx as its first HBNR enforcement action, based on alleged disclosures of consumers’ health information and failure to provide required breach notices. The complaint should be treated as allegations and the final stipulated order as the binding settlement instrument in that matter. See `ftc-enforcement-source-notes.md`, “GoodRx.”

---

## 4. Notification Workstream

### 4.1 Determine whether HBNR notification is triggered

Counsel should document:

- The Company’s status under 16 C.F.R. §§ 318.1–318.2.
- The date of “discovery” for HBNR purposes.
- Whether the incident is a reportable breach.
- The number of affected U.S. individuals.
- The number of affected residents in each State or jurisdiction.
- Whether the Company is a third-party service provider that must report to a covered vendor or PHR-related entity.
- Whether any contractual notice to ad platforms, enterprise customers, or partners is required.

If there is uncertainty, do not let the 60-day outer limit run without a documented legal assessment and, where appropriate, a conservative notification decision.

### 4.2 Individual notice

For affected U.S. individuals, if HBNR applies:

1. Prepare written notice by mail or qualifying email.
2. Use urgent phone or other notice only as a supplement to written notice.
3. Use substitute notice where contact information is insufficient, as permitted by the rule.
4. Ensure the notice is accurate, plain-language, and consistent with the known facts.
5. Legal-review the notice against the required content elements in 16 C.F.R. §§ 318.5–318.6.

Recommended content, subject to legal review:

- A clear description of what happened and when.
- The categories of information involved.
- The categories of recipients involved.
- The likely consequences.
- The steps the Company has taken and will take.
- What affected individuals can do.
- Contact information for questions.
- A statement that is not misleading about HIPAA status, privacy, or the absence of risk.

Do not wait for the complete root-cause analysis before preparing notice; use known facts and supplement if necessary, consistent with the “without unreasonable delay” standard.

### 4.3 Media notice

If 500 or more residents of one State or jurisdiction are affected, prepare media notice as required by the HBNR. See `ecfr-hbnr-source-notes.md`, “Who must be notified — § 318.3.” Coordinate media notice with individual notice and FTC notice.

### 4.4 FTC notice

1. If 500 or more individuals are affected, submit FTC notice contemporaneously with individual notice.
2. If fewer than 500 individuals are affected, determine whether the incident qualifies for annual logged notice within 60 calendar days after calendar year end.
3. If the Company is a third-party service provider, report to the covered vendor or PHR-related entity as required by the rule.
4. Maintain a written record of the submission date, contents, and confirmation.

### 4.5 Order-specific notice benchmarks

If the Company is subject to a consent order or similar settlement, follow its specific notice terms. The BetterHelp final order, for example, required notice to specified Covered Users by email using the last known verified email address, by a deadline of 14 days after the effective date, using an exact copy of the prescribed notice with no other information or attachments; if no email was available, notice was to be sent through the primary means of communication. See `betterhelp-final-order-official-mirror.txt`, p. 9, Provision V.

That 14-day requirement is order-specific to BetterHelp. For the Company, the HBNR outer limit is 60 calendar days after discovery, but the Company should consider earlier notice where facts are sufficiently developed. See `ecfr-hbnr-source-notes.md`, “Timing — § 318.4.”

### 4.6 Communications with users and the public

- Do not describe the incident as “limited” or “non-sensitive” unless verified.
- Do not state that hashed data was anonymous. The BetterHelp complaint alleged that hashing was not intended to conceal identities from ad platforms and that platforms could effectively undo hashing. See `betterhelp-complaint-official-mirror.txt`, p. 10, ¶ 49. The final order’s deletion provisions expressly include hashed or encrypted Covered Information. See `betterhelp-final-order-official-mirror.txt`, p. 8, Provision IV.A.1.
- Do not include unrelated promotional material in a court-ordered or regulator-required notice.
- Route all press inquiries to the designated spokesperson.

---

## 5. Consent Workstream

### 5.1 Immediate consent moratorium

Suspend any ad-platform disclosure that depends on consent until the Company can establish that the consent is valid, specific, informed, and obtained before the disclosure. Consent should not be inferred from continued use, cookie-banner closure, hovering, muting, pausing, or similar interactions.

### 5.2 Adopt an Affirmative Express Consent standard

Use the BetterHelp final order’s definition as a benchmark. “Affirmative Express Consent” means a freely given, specific, informed, and unambiguous indication of the consumer’s wishes, such as a clear affirmative action, following a Clear and Conspicuous disclosure of:

1. The categories of information to be collected, used, or disclosed.
2. The specific purpose(s) for the collection, use, or disclosure.
3. The names or categories of Third Parties receiving the information; if categories are used, a hyperlink to a separate page listing the names of the Third Parties.
4. A simple, easily located means to withdraw consent.
5. Any limitations on the consumer’s ability to withdraw consent.

The disclosure must be separate from any privacy policy, terms of service, terms of use, or similar document. Consent cannot be inferred from hovering over, muting, pausing, or closing content, and cannot be obtained through an interface that subverts or impairs user autonomy, decision-making, or choice. See `betterhelp-final-order-official-mirror.txt`, pp. 2–3, Definition A.

### 5.3 Apply the Clear and Conspicuous standard

The disclosure must be difficult to miss and easily understandable by ordinary consumers. It must stand out by size, contrast, location, duration, and other characteristics; be unavoidable in interactive electronic media; use understandable diction and syntax; appear in each language in which the triggering representation appears; and not be contradicted or mitigated by other content. When the audience includes children or another specific group, “ordinary consumers” includes reasonable members of that group. See `betterhelp-final-order-official-mirror.txt`, p. 3, Definition B.

### 5.4 Implement consent operationally

1. Rebuild consent flows so that health-data sharing for advertising is opt-in, not opt-out.
2. Separate health data from ad-tech data flows. Do not pass Treatment Information or data that identifies a user as seeking or receiving mental-health treatment to ad platforms for advertising or targeting.
3. Maintain a vendor list and purpose-specific disclosures.
4. Log consent version, timestamp, user identifier, disclosures shown, and withdrawal.
5. Provide a simple withdrawal mechanism and honor withdrawals promptly.
6. Re-consent existing users where required; do not treat prior privacy-policy acceptance as sufficient.
7. Train marketing and engineering personnel on the consent standard.

### 5.5 Important limitation

Consent is not a cure for past unauthorized disclosures. Notification and deletion must proceed separately. In addition, the BetterHelp final order’s Provision I is an absolute prohibition on certain advertising uses of Treatment Information and on using Covered Information for targeting; those prohibitions are not merely consent requirements. See `betterhelp-final-order-official-mirror.txt`, pp. 6–7. The Company should adopt the same substantive separation: no ad-platform use of treatment information, and no targeting based on health information, even if a consent interface is later deployed.

---

## 6. Deletion Workstream

### 6.1 Identify what was shared and with whom

Prepare a detailed inventory covering:

- Each ad platform, analytics vendor, pixel provider, SDK provider, data broker, and custom-audience recipient.
- The categories of data sent, including email addresses, IP addresses, persistent identifiers, account/enrollment information, questionnaire responses, treatment information, and any derived or inferred data.
- Whether the data was hashed, encrypted, or otherwise transformed.
- The purpose of each transmission.
- The legal basis or consent relied upon.
- The dates and volumes of transmissions.

The BetterHelp final order’s definitions are useful benchmarks: “Covered Information” includes email addresses, persistent identifiers, Treatment Information, and identifiable information combined with those categories; “Treatment Information” includes information concerning a consumer’s use of, creation of an account associated with, or response to a questionnaire related to a service. See `betterhelp-final-order-official-mirror.txt`, pp. 4–6, Definitions E and K.

### 6.2 Treat hashed or encrypted data as potentially covered

Do not exclude hashed or encrypted data from the deletion analysis. The BetterHelp final order’s deletion provision expressly includes hashed or encrypted Covered Information. See `betterhelp-final-order-official-mirror.txt`, p. 8, Provision IV.A.1.

### 6.3 Send deletion instructions and demand confirmation

For each recipient that received covered information without valid consent, or that received data the Company is no longer authorized to share:

1. Send written notice that the data was allegedly disclosed without valid authorization or in a manner inconsistent with the Company’s obligations.
2. Instruct the recipient to delete all such data, including derivatives, copies, and hashed or encrypted forms.
3. Demand written confirmation of deletion.
4. Require the recipient to instruct downstream subcontractors or affiliates to delete the data.
5. Prohibit further use of the data for advertising, retargeting, model training, analytics, or product development.

The BetterHelp final order required, within 90 days after the effective date, that BetterHelp provide a copy of the Complaint and Order to identified third parties, notify them of the FTC’s allegations, instruct them to delete Covered Information, demand written confirmation, and provide the instructions to the FTC. See `betterhelp-final-order-official-mirror.txt`, p. 8, Provision IV.B. That provision is order-specific to BetterHelp, but it is a useful checklist for the Company’s deletion demands and regulator-facing documentation.

### 6.4 Stop future disclosures pending confirmation

The BetterHelp final order prohibited further disclosure to identified third parties until BetterHelp confirmed receipt of the deletion instructions, and prohibited using those third parties to advertise until receipt was confirmed. See `betterhelp-final-order-official-mirror.txt`, pp. 8–9, Provision IV.C. The Company should adopt a similar hold: no further data sharing or advertising use of the relevant vendors until deletion instructions are acknowledged and legal approves.

### 6.5 Internal deletion and retention

1. Delete covered information that is no longer reasonably necessary, subject to legal holds and applicable retention laws.
2. Adopt a written retention schedule that states the purposes for collection, the business need for retention, and a set timeframe for deletion.
3. Document the deletion methodology.
4. Audit vendor contracts for data-use, deletion, downstream-transfer, and audit rights.
5. Ensure deletion covers backups, logs, derived audiences, and model-training datasets where legally required and technically feasible.

The BetterHelp final order includes safeguards for inventorying covered information and deleting data no longer reasonably necessary, along with a retention schedule requirement. See `betterhelp-final-order-official-mirror.txt`, pp. 9–10, Provision VI.E.1 and VI.E.6.

---

## 7. Regulator-Facing Steps

### 7.1 FTC

1. Prepare the HBNR notification package if applicable.
2. Submit FTC notice for 500+ incidents contemporaneously with individual notice; for fewer than 500, determine annual logged-notice treatment.
3. Maintain a regulator chronology: discovery, containment, data categories, recipients, affected population, notice dates, deletion demands, and confirmations.
4. Designate a single legal point of contact for FTC communications.
5. Do not make oral or written statements to the FTC that are inconsistent with the Company’s privacy policies, user notices, or internal records.

If the Company is subject to an order with specific FTC reporting requirements, follow those requirements exactly. The BetterHelp final order, for example, required submissions to a specified FTC email address with a specified subject line and required production of third-party instruction letters and confirmations. See `betterhelp-final-order-official-mirror.txt`, p. 8, Provision IV.A–B. Those details are order-specific and should not be used unless applicable.

### 7.2 Media notice

If the 500-resident threshold in a State or jurisdiction is met, coordinate media notice with the FTC filing and individual notice. See `ecfr-hbnr-source-notes.md`, “Who must be notified — § 318.3.”

### 7.3 HIPAA and other regulators

If the Company is a HIPAA-covered entity or business associate, the HBNR excludes that activity, and HIPAA breach-notification and OCR analysis must proceed separately. See `ecfr-hbnr-source-notes.md`, “Scope and covered entities — 16 CFR §§ 318.1–318.2.” Do not assert that HBNR compliance satisfies HIPAA or vice versa.

State attorneys general, state health-privacy regulators, and foreign regulators are outside the attached source set. Counsel should assess those obligations separately and calendar any deadlines.

### 7.4 Cooperation and privilege

- Cooperate with regulators through counsel.
- Preserve documents; do not create unsupported after-the-fact explanations.
- Use privileged channels for legal analysis, but remember that factual business records are not privileged merely because counsel is involved.
- Correct any prior inaccurate statement promptly and in writing.

---

## 8. Privacy Program and Remediation

Whether or not an order applies, adopt remediation consistent with the BetterHelp final order’s privacy-program framework:

1. Document the privacy program in writing.
2. Provide the program and updates to the board or governing body at least annually and promptly after a covered incident.
3. Designate a qualified responsible employee with direct reporting to an executive.
4. Conduct and document risk assessments at least annually and after incidents.
5. Implement safeguards proportionate to the volume and sensitivity of the data, including:
   - Data inventory and deletion of data no longer necessary.
   - Technical and procedural controls to prevent collection, use, or disclosure inconsistent with privacy representations.
   - Audits of third-party contracts, privacy policies, and terms of service.
   - Role-based access limits.
   - Mandatory annual privacy training, including advertising-related data use.
   - A public retention schedule with purposes, business need, and deletion timeframes.

See `betterhelp-final-order-official-mirror.txt`, pp. 9–10, Provision VI.

Additional remediation:

- Remove health data from ad platforms and audiences.
- Reconfigure analytics and advertising systems to exclude sensitive health signals.
- Update privacy policies and notices to accurately describe data flows.
- Review HIPAA-related statements and seals; remove or correct any unsupported claims.
- Implement vendor due diligence and contractual prohibitions on secondary use.
- Establish a recurring ad-tech data-flow audit.

---

## 9. Timeline

| Timing | Action | Owner |
|---|---|---|
| Immediately | Suspend ad-platform transmissions; preserve evidence; issue hold; convene response team | Legal / Security / Engineering |
| Within days | Identify recipients, data categories, discovery date, affected population; assess HBNR/HIPAA/state law | Legal / Privacy |
| Within days | Prepare draft individual notice, FTC notice, media notice if applicable; centralize communications | Legal / Communications |
| No later than 60 calendar days after discovery | Send individual notice and media notice if required; submit FTC notice if 500+ | Legal / Compliance |
| Contemporaneous with individual notice for 500+ | Submit FTC notice | Legal |
| Within 60 days after year end for <500 | Submit annual logged FTC notice if applicable | Legal |
| Promptly | Send deletion demands; demand written confirmation; stop future sharing pending confirmation | Privacy / Procurement |
| Ongoing | Document deletion, consent changes, vendor audits, board reporting | Compliance |
| Before any renewed ad-tech use | Confirm valid Affirmative Express Consent and legal approval; prohibit Treatment Information for advertising/targeting | Legal / Marketing |

The 60-day HBNR deadline is an outer limit; do not treat it as a target. See `ecfr-hbnr-source-notes.md`, “Timing — § 318.4.” If a consent order applies, follow its shorter or more specific deadlines.

---

## 10. Documentation and Preservation

Maintain a single incident file containing:

- Discovery chronology.
- Data-flow diagrams.
- Vendor and recipient list.
- Data categories and sample records.
- Consent screenshots and version history.
- Privacy policies and representations.
- Contracts and data-processing terms.
- Deletion demands and confirmations.
- Draft and final notices.
- Regulator submissions and confirmations.
- Board and executive briefings.
- Remediation tickets and completion evidence.

Do not destroy drafts or communications. Use a documented retention protocol.

---

## 11. Open Questions and Uncertainties

Counsel should resolve the following before finalizing notifications:

1. Is the Company a covered entity under the HBNR, or is it a HIPAA-covered entity/business associate for the relevant activity?
2. What is the legally operative “discovery” date?
3. Exactly what data was transmitted, to which platforms, for what purposes, and over what period?
4. Was any data hashed or encrypted, and could it be reidentified by the recipient?
5. How many U.S. individuals are affected, and how many reside in each State or jurisdiction?
6. Did the Company make privacy representations that are inconsistent with the sharing, including “strictly private,” “never shared,” “anonymous,” or HIPAA-related claims?
7. Did any consent exist, and was it valid, specific, informed, and prior to disclosure?
8. Are minors or other vulnerable populations affected?
9. Do any ad-platform contracts require notice, deletion, or indemnity?
10. Does any FTC order, state consent order, or other settlement apply to the Company?
11. Are state breach-notification or health-privacy laws triggered?
12. Are there foreign users or foreign-law obligations?

---

## 12. Source Key

- `ecfr-hbnr-source-notes.md` — FTC Health Breach Notification Rule scope, notification recipients, timing, methods, enforcement, and conditional sunset.
- `ftc-enforcement-source-notes.md` — GoodRx and BetterHelp enforcement context; final order controls over complaint and pre-final materials.
- `betterhelp-complaint-official-mirror.txt` — FTC allegations against BetterHelp; not adjudicated findings. Cited for alleged data flows, privacy representations, and hashing allegations.
- `betterhelp-final-order-official-mirror.txt` — Operative BetterHelp final order; binding on BetterHelp, used here as an enforcement and compliance benchmark. Cited for definitions, advertising prohibitions, affirmative express consent, deletion, notice, and privacy-program provisions.
- `betterhelp-proposed-consent.txt` — Pre-final proposed consent; cited only to show that BetterHelp neither admitted nor denied the complaint allegations except as stated in the order.
- `betterhelp-public-comment-analysis.txt` — Pre-final public-comment analysis; cited only as context for the proposed complaint counts and proposed order, not as operative law.

**Bottom line:** The Company should immediately stop the ad-platform data flows, preserve evidence, determine HBNR/HIPAA/state-law status, prepare individual and FTC notice on the HBNR timeline, send deletion demands with written confirmation requirements, rebuild consent around a Clear and Conspicuous Affirmative Express Consent standard, and avoid any statement that misrepresents the data sharing or the Company’s HIPAA status.
