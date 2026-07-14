# Intake Questions — Canonical List

Ask these questions **exactly as written**, **in this order**, **one at a time**.
Skip any question whose `spec.yaml field` already has a value.
After each answer, immediately write to spec.yaml.

---

## Q1: Main Goal

> **What will someone be able to DO after completing this?** Be specific — a concrete, measurable outcome.

- **spec.yaml field:** `spec.title` (derive a short title from the goal)
- **Also captures:** the problem statement for design.md

## Q2: Target Audience

> **Who is this for?** What's their role, experience level, and what background knowledge should they have?

- **spec.yaml field:** `spec.audience` (one of: `beginner`, `intermediate`, `advanced`)

## Q3: Products and Technologies

> **Which Red Hat products and technologies are involved?** Include full product names and versions if known.

- **Used in:** design.md Products & Technologies section

## Q4: Content Type (if not set)

> **Is this a hands-on lab, a guided demo, or a workshop?**

- **Skip if:** `project.content_type` is already set
- **spec.yaml field:** `project.content_type` (one of: `lab`, `demo`, `workshop`)

## Q5: Showroom Type (if not set)

> **Will this be a standard Showroom lab (Classic) or an embedded Zero-Touch experience?**

- **Skip if:** `project.showroom_type` is already set
- **spec.yaml field:** `project.showroom_type` (one of: `classic`, `zero_touch`)

## Q6: Environment

> **What does the learner start with, and what needs to be pre-configured by automation?** For example: a shared OpenShift cluster with operators pre-installed, or a per-student cluster with nothing installed.

- **spec.yaml field:** `spec.environment.topology` (one of: `shared-cluster`, `per-student`, `cnv-pool`)
- **Also captures:** environment details for design.md

## Q7: Total Duration

> **How long should this take end to end?** Consider the complexity of what you described.

- **spec.yaml field:** `spec.duration_hours`

## Q8: Module Structure

> **Let me propose a module breakdown based on what you've described.** [Present proposed modules with titles and estimated durations, 15-45 min each.] **Does this structure work, or would you adjust it?**

- **spec.yaml field:** `spec.modules` (list of `{title, duration_min}`)

## Q9: Module Relationship

> **How do these modules relate to each other?**
> 1. **Sequential** — they build on each other and must be done in order
> 2. **Independent with shared context** — can be done in any order but share a scenario
> 3. **Fully independent** — standalone topics

- **Used in:** design.md Module Map section

## Q10: Difficulty Level

> **What difficulty level best describes this content?** Beginner, intermediate, or advanced?

- **spec.yaml field:** `spec.audience` (update if different from Q3)

## Q11: OpenShift Version

> **Which OpenShift version should this target?** For example: 4.17, 4.18, 4.19.

- **spec.yaml field:** `spec.environment.ocp_version`

## Q12: Infrastructure Requirements

> **Let me confirm the infrastructure needs.** Based on what you described:
> - **Base infrastructure:** [propose: ocp4-cluster, ocp-workloads, or cloud-vms-base]
> - **Sizing:** [propose based on complexity]
> - **Cloud provider:** CNV (default) or exception?
> - **Automation approach:** Ansible, GitOps (Helm + ArgoCD), or combo?
>
> **Does this sound right, or should I adjust anything?**

- **Used in:** design.md Infrastructure Requirements section

## Q13: Reference Material

> **Do you have any reference material I should work from?** Internal docs, existing labs, recorded demos, architecture diagrams, or blog posts?

- **Used in:** informs design.md content

---

## Rules

- Ask ONE question at a time. Wait for the answer before asking the next.
- Use the **exact wording** above. Do not rephrase, merge, or reorder questions.
- If the user's answer to one question also answers a later question, mark that later question as answered and skip it.
- After each answer, immediately update `publishing-house/spec.yaml` with the captured value.
- If an answer is vague, ask a single follow-up to clarify before moving on.
