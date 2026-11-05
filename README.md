# IAM: The Access Review

## 🎫 The Ticket

It's 5 October 2026, my first day on the security team at Northwind Health, a fictional healthcare organisation with about 400 clinics.

My first ticket arrives. The IT Manager writes:

> We've never properly reconciled the patient admin portal against HR. Here are both exports. **Tell me what's wrong, what to fix first, and how we stop it happening again.**

<br>

Before deciding what needs fixing, I need to understand what the records are telling me.

<br>



## What I'm Working With

I have two lists: the HR records showing who works for the organisation, and an export showing who can access the patient portal. Every account should have a legitimate owner and a reason for its level of access. That includes contractors, whose access may have an expiry date.

I'm not hunting for "bad accounts." I'm hunting for **access that no longer makes sense**. An account can look perfectly normal in the export and still have permissions it shouldn't.

<br>

## How I Worked Through It

**1. Does the account match HR?**  
I started with employment status, contract end dates and recent login activity. If someone has left but their account remains active, that needs investigating. The HR record could be outdated, so I can't automatically assume the access is unauthorised.

**2. Is the access still appropriate?**  
Finding a matching HR record doesn't mean the permissions are right. I checked access levels, administrative privileges and shared credentials against job responsibilities, paying particular attention to admin access because the risk if it is misused hits harder.

**3. What needs further investigation?**  
Some accounts couldn't be assessed from the exports alone. For those, I needed to establish who owned the account, why the access existed and who could confirm whether it was still required. If nobody could explain who was responsible for an account, that was worth recording too.

**4. What needs attention first?**  
I ranked the findings by risk, considering the privileges involved, the available information and the potential consequences. Not every discrepancy requires the same response.

<br>

## What I Found

The review covered seven accounts.

| Severity | Accounts | Finding |
|---|---:|---|
| 🔴 Critical | 2 | Login activity after employment or contract end dates |
| 🟠 High | 2 | Orphaned admin account and shared credentials |
| 🟡 Medium | 2 | Extended leave and Finance access requiring review |
| 🟢 Low | 1 | Engineering admin access requiring justification |
| **Total** | **7** | |

<br>

## Why `treyes` Goes First

Two accounts were rated Critical, so I needed to decide which required attention first. The contractor's recorded end date was **31 July 2026**, but the portal export showed an admin login on **28 September 2026**.

Almost two months later, the account still had administrative access. I prioritised `treyes` because those privileges increased the potential impact of misuse.

**My recommendation:** Confirm whether the contract was extended and continued access was approved. If there's no valid authorisation, disable the account and investigate the login activity.

But there's a distinction I don't want to overlook. **The records raise a serious concern, but they don't prove a breach occurred.**

It's possible the contract was extended without HR being updated. That would point to a governance gap that still needs correcting, but it's different from someone accessing the system without authorisation. I need to establish what happened before deciding what action is justified.

<br>

## Looking Back at the Review

With the investigation complete, I looked back at how I'd approached the ticket. What helped me make a sound decision, and where would I need more information next time?

Starting with the HR reconciliation was the right call. It surfaced discrepancies before I decided what needed attention, and prioritising by risk kept the focus on administrative privileges.

But the exports had their limits. Take `treyes`: the contract end date and later admin login raised a concern, but they couldn't tell me whether an extension had been approved. That needed confirmation from outside the data I'd been given. Next time I'd want a clearer way to establish account ownership, check approval history and understand why access was originally granted.

Acting too quickly has a cost. Disabling access someone still legitimately needs disrupts the business without resolving the actual problem, so every decision has to balance **maintaining security and allowing the business to operate without unnecessary disruption.** The same applies to prevention: finding inappropriate access is one part of the job, and understanding how it remained in place shows which controls need improving.

The question I'd carry into the next review:

**Does this access still have a legitimate purpose, and can the organisation account for it?**

<br>


## Explore the Investigation

| Document | What's Inside |
|---|---|
| [01. Source Data](./01-Documents/01.%20Source%20Data.md) | Original HR records and patient portal export |
| [02. Findings & Recommendations](./01-Documents/02.%20Findings%20%26%20Recommendations.md) | Access discrepancies, risk ratings and proposed actions |
| [03. Preventive Controls](./01-Documents/03.%20Preventive%20Controls.md) | Recommendations to prevent recurring access issues |
| [04. IT Manager Summary](./01-Documents/04.%20Summary%20for%20the%20IT%20Manager.md) | Key findings and recommended priorities |


<br>

---

[All Case Studies](https://github.com/itsanitarose/IAM-Case-Studies) · [Week 2: Permission Sprawl & RBAC →](https://github.com/itsanitarose/IAM-Permission-Sprawl-RBAC)

*<sub>Northwind Health is fictional. This is independent work. No production systems were changed.</sub>*
