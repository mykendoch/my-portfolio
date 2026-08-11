# GitHub Link Strategy — What Reviewers Look For

When an employer or client asks for your **GitHub link**, they are usually trying to answer a few practical questions:

- Can you write readable, maintainable code?
- Do you commit regularly and describe changes clearly?
- How do you structure a project (folders, services, tests, CI)?
- Can you explain trade-offs in architecture and tooling?

That is different from asking for a **live demo** or a **case study**, which show product judgment, UX, and delivery under real constraints (payments, auth, ops).

---

## If repos are private, who sees my work?

**Only people you invite on GitHub see the code.** Private repositories are visible to you, collaborators you add, and (if applicable) your organization — nobody else can browse or clone them.

**Everyone else sees this portfolio README** — the public proof of your work:

- Case studies with scope, architecture, and feature breakdowns
- Tech stack and integration details
- Live demo URLs where products are publicly accessible
- Screenshots and walkthroughs (available on request)

**The portfolio URL is what you send in job applications and client pitches.** It is designed to stand on its own: a reviewer can evaluate your systems thinking, domain expertise, and delivery history without ever opening a repo.

**Optional extras for serious reviewers** (under mutual agreement or NDA):

- Time-boxed private repo access
- Sanitized demo repository with redacted credentials and sample modules
- Architecture PDF or recorded walkthrough

Plain English: **private code protects client IP; the portfolio and live demos are how the world sees your impact.**

---

## Why many portfolio entries are live demo + case study only

Most of my production work is **client or company-owned**:

- Healthcare systems (HMIS, Medcom), fintech (M-Pesa, airtime), and farm SaaS (AgriFarm / Cowalima) contain proprietary business logic, schemas, and integrations.
- Repositories are **private** or under NDA. Sharing raw code would expose client IP, credentials patterns, or competitive detail.

For those projects, this portfolio is the intentional substitute: architecture diagrams, feature breakdowns, tech stack, and deployment context — without leaking implementation specifics.

---

## What you *can* review without private repo access

| Asset | What it shows |
|-------|----------------|
| **This portfolio** (`my-portfolio`) | Scope, architecture, modules, and how systems fit together |
| **Live URLs** | Working product — checkout flows, admin tools, performance |
| **Sanitized screenshots / walkthrough** | UX and domain workflows (available on request) |
| **Architecture overview** | Services, data flow, integrations (in each project section below) |
| **Private code on request** | Time-boxed access for serious hiring/partner discussions, after mutual agreement |

---

## Link pattern by project type

Each project in [README.md](./README.md) includes a **Links & Code Access** block where applicable. The pattern:

| Type | GitHub | Live / case study |
|------|--------|-------------------|
| **Client / commercial** (e.g. AgriFarm, Credo247, HMIS, Admark) | *Private — available on request* | Live URL when public + this case study |
| **Proposal / assessment only** (e.g. Olsupat Lodge need-assessment) | N/A — not shipped product code | Live assessment or marketing site + proposal summary |

**Examples**

- **AgriFarm (Cowalima AI)** — Production SaaS at [cowalima.co.ke](https://cowalima.co.ke). Code is private (client/commercial). Review via live site + portfolio case study; repo access by request.
- **Credo247** — Production at [credo247.com](https://credo247.com). Code is private (client-owned). Review via live site + portfolio case study; repo access by request.
- **Admark Enterprises** — Live at [admark.co.ke](https://admark.co.ke). Code is private (client-owned). Available on request.
- **Olsupat Lodge** — Public need-assessment at [cowalima.co.ke/olsupat](https://cowalima.co.ke/olsupat). Full website build is a separate client engagement; no public application repo.

---

## What to send when someone asks for "your GitHub"

1. **Profile:** [github.com/mykendoch](https://github.com/mykendoch)
2. **Portfolio:** [github.com/mykendoch/my-portfolio](https://github.com/mykendoch/my-portfolio) (this repository)
3. **Live demos** where available (see each project's Links section)
4. **Optional:** offer private repo walkthrough, sanitized demo repo, or screen-share for roles that require deep code review

Plain English summary: **GitHub proves how you build; the portfolio and live demos prove what you have shipped.** For NDA work, the second matters more — and this document explains how to evaluate both fairly.
