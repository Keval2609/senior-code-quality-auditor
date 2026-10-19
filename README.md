# senior-code-quality-auditor

[![skills.sh compatible](https://img.shields.io/badge/skills.sh-standard-blue.svg)](https://skills.sh)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An autonomous AI Agent Skill that audits, refactors, and guides code changes using the **7 Coding Laws of Senior Engineers**. 

Its guiding thesis: **"Make the next change easier."**

---

## What This Skill Does

When activated, your agent shifts into a Senior Quality Auditor mindset:

1. **Flattens Nested Code (Law 1):** Eliminates pyramid `if-else` blocks in favor of top-level guard clauses.
2. **Domain-Driven Naming (Law 2):** Flags ambiguous placeholders (`data`, `result`, `item`, `handle`) and introduces precise domain terms.
3. **Vendor Boundaries (Law 3):** Prevents third-party schemas (Stripe, Twilio, AWS) from bleeding into business logic.
4. **Illegal State Elimination (Law 4):** Replaces "everything-optional" models with strict discriminated unions and value types.
5. **Separates Decisions from Actions (Law 5):** Extracts business rules into pure, mock-free functions.
6. **Production-Ready Observability (Law 6):** Enforces structured error codes and context while actively blocking secrets/tokens from logs.
7. **Scoped Pull Requests (Law 7):** Prevents monster PRs by breaking multi-concern diffs into reviewable chunks.

---

## How to Install

Install this skill into your local workspace using any standard skill manager:

### Using `skills.sh` CLI (Recommended)
```bash
npx skills add <YOUR_GITHUB_USERNAME>/senior-code-quality-auditor
```

### Using Claude Code CLI
```bash
claude skill add <YOUR_GITHUB_USERNAME>/senior-code-quality-auditor
```

### Manual Installation
Clone this repository directly into your project's agent skills directory:
```bash
# For Universal / Antigravity / Cursor Agents:
git clone https://github.com/<YOUR_GITHUB_USERNAME>/senior-code-quality-auditor.git .agents/skills/senior-code-quality-auditor

# For Claude Code:
git clone https://github.com/<YOUR_GITHUB_USERNAME>/senior-code-quality-auditor.git .claude/skills/senior-code-quality-auditor
```

---

## Quick Test Prompts

Verify that the skill is actively governing your agent with these sample prompts:

### 1. Test Law 1 & Law 2 (Nesting and Naming)
> *"Review this function and refactor it:*
> ```typescript
> function handleData(d: any) {
>   if (d) {
>     if (d.user) {
>       if (d.user.active) {
>         return doStuff(d);
>       }
>     }
>   }
>   return null;
> }
> ```*"

### 2. Test Law 3 & Law 6 (Vendor Leaks & Redaction)
> *"Audit this payment handler and highlight any security or architectural issues:*
> ```typescript
> async function handleWebhook(payload: any) {
>   console.log("Processing payload", payload.stripe_cust_id, payload.api_key);
>   if (payload.txn_status === "succeeded") {
>     await db.orders.update(payload.stripe_cust_id, { status: "PAID" });
>   }
> }
> ```*"

### 3. Test Law 5 & Law 7 (Mock-Heavy Logic & PR Splitting)
> *"I have a 1,200-line checkout handler that makes DB calls, verifies user discounts, sends emails, and updates inventory. Help me write tests and prepare the pull requests."*

---

## License

MIT © [Your Name / Organization]
