---
name: green-review
description: >
  Reviews code, architecture, or configuration for green software practices aligned
  with the Green Software Foundation's principles. Auto-invokes when writing new
  API endpoints, database queries, cloud/infrastructure config, background jobs,
  data pipelines, or caching logic. Also invokable directly with /green-review.
  Do NOT auto-invoke for UI-only changes, documentation edits, or test-only changes.
---

# Green Software Review

You are performing a sustainability review using the Green Software Foundation's
principles. Your job is to identify carbon inefficiencies and suggest improvements.

## Review Checklist

Work through these categories and flag any issues found:

### ⚡ Energy Efficiency
- [ ] Are there tight loops or heavy computations that could be batched or deferred?
- [ ] Is work being done eagerly that could be done lazily?
- [ ] Are expensive operations (crypto, image processing, ML inference) avoided on the
      critical path where possible?
- [ ] Is idle polling used instead of event-driven / push patterns?

### 🌐 Network Efficiency
- [ ] Are payloads minimised? (pagination, field selection, compression)
- [ ] Is data transferred that isn't needed by the consumer?
- [ ] Are multiple round trips avoidable (e.g., via batching, GraphQL, or BFF patterns)?
- [ ] Is a CDN or edge cache being used for static/cacheable content?

### 🗄️ Compute & Storage
- [ ] Are database queries optimised? (proper indexes, avoiding N+1, limiting result sets)
- [ ] Is caching used appropriately to avoid redundant computation?
- [ ] Is the storage format efficient? (compressed, columnar where appropriate)
- [ ] Is data retained longer than needed?

### ☁️ Cloud & Infrastructure
- [ ] Are resources over-provisioned relative to actual load?
- [ ] Does the workload scale to zero when idle?
- [ ] Is the deployment region chosen for carbon intensity of the grid?
- [ ] Are spot/preemptible instances used for interruptible workloads?
- [ ] Is there opportunity for time-shifting (running batch jobs during low-carbon grid windows)?

### 🔋 Hardware & Embodied Carbon
- [ ] Is hardware being fully utilised, or are there always-on instances sitting mostly idle?
- [ ] Could a managed/serverless service replace a self-managed VM, reducing embodied overhead?

## Output Format

For each issue found, produce:

```
[PRINCIPLE] Short title
Severity: 🔴 High / 🟡 Medium / 🟢 Low
Problem: One sentence describing the inefficiency.
Suggestion: Concrete fix or alternative approach.
```

Then close with a **Summary** section:
- Total issues by severity
- The single highest-priority change that would most reduce carbon impact
- Whether an SCI baseline measurement would be worthwhile here

If the code is already well-optimised, say so clearly — false positives erode trust.

## Reference

Green Software Patterns: https://patterns.greensoftware.foundation  
SCI Specification: https://sci.greensoftware.foundation  
GSF Principles: https://learn.greensoftware.foundation/practitioner/carbon-efficiency
