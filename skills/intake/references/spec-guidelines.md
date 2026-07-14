# Spec Quality Guidelines

Guidelines for evaluating and generating project specs. Used by the intake agent.

## Required Sections in design.md

A complete spec MUST have all of these:

1. **Project Name** — clear, descriptive
2. **Problem Statement** — what gap this fills, why it's needed (2-3 sentences)
3. **Target Audience** — role, experience level, what they already know
4. **Learning Objectives** — action-verb list (Configure, Deploy, Create, Troubleshoot)
5. **Content Type** — lab or demo
6. **Products & Technologies** — official Red Hat product names
7. **Module Map** — table with module number, title, estimated duration
8. **Prerequisites** — what the learner needs before starting
9. **Environment** — what the learner sees when the lab starts, plus automation needs
10. **Infrastructure Requirements** — platform, sizing, and resource details

## Infrastructure Requirements

Capture what you know now — guesstimates are fine during intake. Spec refinement fills gaps.

- **Base infrastructure** — which base CI type: ocp4-cluster, ocp-workloads, cloud-vms-base, or existing CI name
- **Sizing** — node types and counts with resources. Say "OCP 4.18 with 3 masters (4 CPU, 16GB RAM) and 6 workers (8 CPU, 32GB RAM, 100GB disk)" not just "OpenShift cluster"
- **Cloud provider** — CNV (default), AWS, GCP, Azure. CNV unless exception granted.
- **Automation approach** — Ansible, GitOps (Helm + ArgoCD), or combo
- **Existing workloads** — list any AgnosticD workloads, GitOps repos, or Ansible collections to reuse
- **New workloads** — what needs to be developed and by whom

Not all fields must be known at intake. "TBD but estimating ~X" is fine.

## Optional Sections

- Design Principles — pedagogical approach, constraints
- Success Criteria — how to measure effectiveness
- Differentiation — how this differs from existing content

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
