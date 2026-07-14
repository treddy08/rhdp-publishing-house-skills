# Spec Quality Guidelines

Guidelines for evaluating and generating project specs. Used by the intake agent.

## Required Sections in design.md

A complete spec MUST have all of these:

1. **Project Name** — clear, descriptive
2. **Problem Statement** — what gap this fills, why it's needed (2-3 sentences)
3. **Target Audience** — role, experience level, what they already know
4. **Prerequisites** — what the learner needs before starting; can the lab validate them?
5. **Learning Objectives** — action-verb list (Configure, Deploy, Create, Troubleshoot)
6. **Content Type** — lab or demo
7. **Products & Technologies** — official Red Hat product names
8. **Module Map** — table with module number, title, estimated duration
9. **Environment** — what the learner sees when the lab starts, plus automation needs
10. **Infrastructure Requirements** — platform, sizing, AI/MaaS, external services, non-GA products
11. **Assessment Strategy** — how success is measured per module

## Infrastructure Requirements

Capture what you know now — guesstimates are fine during intake. Spec refinement fills gaps.

### Base Infrastructure
- Which base CI type: `ocp4-cluster`, `ocp-workloads`, `cloud-vms-base`, or existing CI name
- Cloud provider: CNV (default), AWS, GCP, Azure. CNV unless exception granted.
- Automation approach: Ansible, GitOps (Helm + ArgoCD), or combo

### Cluster Sizing
- Node types and counts with resources. Say "6 workers (8 vCPU, 32GB RAM, 100GB disk)" not just "OpenShift cluster"
- GPU nodes: count + type if applicable
- RHEL nodes: count + sizing if VM-based lab

### Multi-User
- Topology: shared-cluster, per-student, or cnv-pool
- Max concurrent users: required if per-student or cnv-pool

### AI / MaaS
- `ai_requirement`: maas | gpu | none
- `ai_model_tier`: open-source (default, auto-approved) | frontier (requires justification)
- `ai_model_name`: specific model if known
- `ai_justification`: required if frontier or gpu — explain why open-source is insufficient
- **Default path:** MaaS + open-source → auto-approved. Frontier or GPU → routes to human infra review.

### External Services
- List named external services (e.g., github.com, registry.access.redhat.com)
- Vague entries ("internet", "any public IP") → rejected
- Empty list → auto-approved

### AAP
- Version required if "Ansible Automation Platform" in products

### Non-GA Products
- List non-GA products/versions
- Include access plan: how will access be provided during provisioning?
- Empty list → auto-approved; non-empty → routes to infra review

Not all fields must be known at intake. "TBD but estimating ~X" is fine.

## Approval Checklist Fields (spec.yaml)

The following are authored during intake and stored in `approval_checklist` in spec.yaml:

| Field | Where | What |
|---|---|---|
| `prerequisites_verifiable` | `approval_checklist.content_lead` | Can lab auto-validate prereqs? (true/false) |
| `assessment_strategy` | `approval_checklist.content_lead` | How success is measured per module |
| `differentiation` | `approval_checklist.content_lead` | Author's narrative: how this differs from existing content |

Auto-computed by Central (not authored):
- `rcars_overlap_pct` — computed from products + audience query against RCARS catalog
- `rcars_top_matches` — top 3 RCARS matches
- `peak_environments` — max_concurrent_users × topology factor
- `cost_per_run_est` — indicative cost from sizing

## Optional Sections

- Design Principles — pedagogical approach, constraints
- Success Criteria — how to measure effectiveness
- Differentiation — how this differs from existing content (also captured in approval_checklist)

## Quality Checks

### Learning Objectives
- Start with action verbs: Configure, Deploy, Create, Implement, Troubleshoot, Monitor, Scale
- NOT: Understand, Learn, Know, Be familiar with (too vague)
- Each objective should be testable

### Problem Statement
- Specific, not generic — reference a real persona with a real need

### Module Map
- Each module should be 10-30 minutes
- Total duration should match content type (lab: 1-4 hours, demo: 15-45 minutes)
- Modules should build on each other logically

### Products & Technologies
- Use official Red Hat product names (Red Hat OpenShift, not just OpenShift)
- Include version if relevant
- List upstream projects separately

### Environment
- **Learner view first** — describe what exists when the lab starts
- **Automation scope second** — what automation must provision
- Be specific about cluster requirements

### Assessment Strategy
- Must be explicit per module
- "Trust-based" is acceptable but must be stated clearly
- Prefer verification scripts or visible UI results where possible
