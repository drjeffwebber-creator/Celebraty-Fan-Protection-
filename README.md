Celebrity & Fan Protection

An open-source safety framework designed to help celebrities, public figures, organizations, and their fans identify, document, and report impersonation and scam activity.

«Status: Early-stage project / prototype»

Why this project exists

Online impersonators can copy a celebrity's name, photographs, biography, and public information to create convincing fake accounts.

These accounts may then attempt to:

- deceive fans
- request money
- promote fraudulent investments
- request cryptocurrency or gift cards
- collect passwords or personal information
- build false romantic or personal relationships
- distribute malicious links
- damage the reputation of the person being impersonated

This project aims to provide a transparent, privacy-conscious framework for reducing those risks.

Project goals

For celebrities and public figures

- Establish a trusted record of officially controlled accounts.
- Detect suspicious accounts using publicly available signals.
- Make impersonation reports easier to document.
- Preserve evidence in a structured format.
- Help authorized representatives respond to incidents.

For fans

- Make it easier to distinguish official accounts from suspicious accounts.
- Provide warnings around common impersonation and scam patterns.
- Give fans a safe way to report suspected impersonation.
- Encourage verification through official channels before sending money or sensitive information.

For platforms and developers

Provide reusable schemas, detection components, APIs, and documentation that can be integrated into existing trust-and-safety systems.

---

Core principles

1. Evidence before accusation

A suspicious account should be treated as a signal requiring investigation, not automatically declared fraudulent.

2. Privacy first

The project should collect the minimum information necessary to investigate an incident.

Private addresses, passwords, financial credentials, private messages, or unnecessary personal information should never be stored.

3. Human review

Automated systems should assist investigators rather than make irreversible accusations solely from an algorithmic score.

4. Platform-aware verification

This project does not replace the verification systems operated by social-media platforms.

An account should only be considered officially controlled when appropriate evidence or platform confirmation is available.

5. Fan safety

The system should prioritize preventing financial loss, credential theft, harassment, and other forms of abuse.

---

Proposed architecture

                 ┌─────────────────────┐
                 │ Celebrity / Manager │
                 └──────────┬──────────┘
                            │
                     Official accounts
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Official Account DB │
                 └──────────┬──────────┘
                            │
                            ▼
┌───────────────┐    ┌──────────────────┐
│ Fan Reports   │───►│ Detection Engine  │
└───────────────┘    └────────┬─────────┘
                              │
                         Risk signals
                              │
                              ▼
                    ┌──────────────────┐
                    │ Review / Triage  │
                    └────────┬─────────┘
                             │
                ┌────────────┴────────────┐
                ▼                         ▼
        Confirmed concern            False positive
                │                         │
                ▼                         ▼
        Platform report              Close report

Main components

Official Account Registry

Stores references to accounts that have been verified through an appropriate process.

Example:

{
  "person_id": "person_001",
  "platform": "example-platform",
  "username": "official_example",
  "verification_status": "confirmed",
  "verification_source": "authorized_representative"
}

Impersonation Detection

The detection layer can examine signals such as:

- username similarity
- display-name similarity
- copied profile descriptions
- reused publicly available images
- suspicious account creation patterns
- links to suspicious domains
- repeated requests for money
- cryptocurrency payment requests
- gift-card requests
- requests for authentication credentials

Detection results should produce a risk signal, not a definitive accusation.

Example:

{
  "account": "@example_person",
  "risk_level": "high",
  "signals": [
    "username_similarity",
    "copied_profile_image",
    "financial_request"
  ],
  "requires_human_review": true
}

Fan Reporting

Fans should be able to submit:

- suspicious username
- platform
- account URL
- reason for suspicion
- optional screenshot
- date/time of observation

Sensitive information should be removed whenever possible.

Evidence Handling

Reports should preserve enough information to investigate an incident without unnecessarily collecting personal data.

Recommended evidence:

- public account URL
- public username
- timestamp
- screenshot
- description of suspicious behavior
- relevant public messages or posts

Do not request passwords, authentication codes, bank credentials, or private financial information.

---

Risk levels

The initial prototype can use four levels:

Level| Meaning
Low| Weak or inconclusive signals
Medium| Multiple suspicious signals
High| Strong impersonation indicators
Critical| Strong indicators combined with active financial or credential fraud

Risk scores should assist human review rather than automatically determine guilt.

---

Fan safety rules

Fans should be encouraged to:

1. Verify accounts through the celebrity's known official channels.
2. Never send passwords or authentication codes.
3. Be cautious about unexpected requests for money.
4. Be especially careful with cryptocurrency and gift-card requests.
5. Avoid suspicious links.
6. Report suspected impersonators to the relevant platform.
7. Preserve evidence if they believe they have been scammed.
8. Contact the appropriate financial institution or authorities when financial loss has occurred.

---

Security model

The project should protect:

- submitted evidence
- reporter identity
- authorized representative accounts
- authentication credentials
- internal investigation information

Recommended controls include:

- encryption in transit
- encryption at rest
- role-based access control
- audit logging
- secure authentication
- rate limiting
- abuse prevention
- retention limits
- secure deletion

---

Abuse prevention

Because this system could itself be abused, it must not become a tool for harassment or mass-reporting.

Safeguards should include:

- rate limits
- duplicate-report detection
- evidence requirements for high-impact actions
- human review
- appeal mechanisms
- reporter-abuse monitoring
- separation between suspicion and confirmed findings

---

Privacy

The project follows a data-minimization approach.

Do not store information simply because it is available.

Before collecting information, ask:

«Is this information necessary to protect the celebrity or fan?»

If the answer is no, do not collect it.

See "PRIVACY.md" for the detailed privacy model.

---

Threat model

The project considers threats including:

- celebrity impersonation
- romance scams
- investment scams
- cryptocurrency scams
- phishing
- malicious links
- account takeover
- fake management accounts
- fake charity campaigns
- coordinated impersonation networks

See "docs/threat-model.md".

---

Roadmap

Phase 1 — Documentation

- [x] Define project goals
- [x] Define threat model
- [ ] Define verification policy
- [ ] Define reporting workflow
- [ ] Define privacy requirements

Phase 2 — Prototype

- [ ] Account registry
- [ ] Report submission
- [ ] Evidence schema
- [ ] Basic username similarity detection
- [ ] Basic profile similarity detection
- [ ] Risk scoring
- [ ] Reviewer dashboard

Phase 3 — Security

- [ ] Authentication
- [ ] Role-based access control
- [ ] Audit logging
- [ ] Evidence encryption
- [ ] Abuse prevention
- [ ] Data-retention controls

Phase 4 — Platform integration

- [ ] Platform reporting integrations
- [ ] Webhook support
- [ ] API
- [ ] Browser/mobile reporting interface
- [ ] Authorized representative verification

---

Contributing

Contributions are welcome.

Before contributing:

1. Read "CONTRIBUTING.md".
2. Read "SECURITY.md".
3. Do not submit real victims' private information.
4. Use synthetic examples in tests.
5. Never include passwords, authentication codes, financial credentials, or private communications.

---

Responsible disclosure

If you discover a security vulnerability, do not publicly disclose sensitive details before the project maintainers have had an opportunity to investigate.

See "SECURITY.md".

---

License

This project will use an open-source license specified by the project maintainers.

---

Disclaimer

This project is a safety and research framework.

It does not independently establish someone's legal identity, determine criminal liability, or guarantee that an account is fraudulent.

Verification and enforcement should involve appropriate evidence, authorized representatives, platform processes, and human review.

---

Vision

Make it harder for impersonators to exploit trust and easier for fans to recognize legitimate communication.# Celebraty-Fan-Protection-
