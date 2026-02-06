# OrgSmith

**Hierarchical AI Organizational Simulator & Execution Engine**

OrgSmith is a high-fidelity organizational simulator that turns AI agents into a structured engineering company. Instead of chaotic “agent swarms,” OrgSmith uses human-centric hierarchy, token-based work shifts, and a rigorous escalation protocol so that work is solved at the lowest responsible level while keeping the human Founder in full control.

---

## 1. Concept Overview

OrgSmith models a startup-scale org (5–25 agents) with realistic operational constraints:

- Hierarchical roles: Specialists → Team Leads → Directors → Founder  
- Token-as-hours workday simulation  
- Human-in-the-loop “Avatar Mode” for direct intervention  
- Artifact-first execution: specs before code, traceable artifacts, and real-time telemetry  

**Target users:** AI founders, technical leaders, and hackathon builders who want to orchestrate multiple LLM agents as if they were a real engineering org.

---

## 2. Hierarchical Escalation & Communication Protocol

To mimic a real company, OrgSmith enforces a structured escalation ladder and filtered communications.

### 2.1 Escalation Ladder

1. **Level 1 – Specialist Autonomy**  
   Specialists (e.g., Devs, Analysts) try to complete tasks using their tools and local memory.

2. **Level 2 – Peer Consultation**  
   If blocked, a Specialist consults a Peer within their 5-member team for “Code Review” or “Collaborative Thought.”

3. **Level 3 – Team Lead (TL) Intervention**  
   If peers can’t resolve the issue, the Team Lead provides “Strategic Correction” or “Architectural Decision.”

4. **Level 4 – Departmental Director**  
   When a block crosses department boundaries (e.g., Tech blocked by DevOps), Directors coordinate to unblock.

5. **Level 5 – Founder (Executive Gate)**  
   The Founder is only interrupted if:
   - The token budget for a task/org slice is depleted  
   - A **strategic pivot** is required (goal conflict)  
   - Multiple Directors are in deadlock

### 2.2 Gatekeeping & Filtering Mechanics

- **Confidence Scoring**  
  Every agent logs a `confidence_score` in `[0.0, 1.0]`.  
  If `confidence_score < 0.7`, the agent must escalate instead of silently guessing.

- **Director Firewall**  
  Directors compress all specialist activity into **Daily Briefings**.  
  - Founder sees briefings by default  
  - Raw logs are only exposed via explicit “Deep Dive” requests

- **Notification Priority**

  - Low: Specialist task completion  
  - Medium: Lead-level peer review / corrections  
  - High: Director-level escalation requiring Founder attention  

---

## 3. Simulation Physics: Tokens-as-Hours

OrgSmith treats LLM tokens as a proxy for “work hours.”

### 3.1 Workday Constraints

- **Shift Limit**  
  Each agent has a maximum of **50,000 tokens per Shift**.

- **Rest Period**  
  Once the limit is hit, the agent enters an `IDLE_REPORTING` state:
  - Cannot execute tools
  - Can only report status until the Director (or Founder in Avatar Mode) approves the next shift’s objectives

- **Overhead Tax**  
  Every escalation consumes additional tokens, simulating communication overhead.  
  This incentivizes agents to resolve issues at the lowest possible level.

---

## 4. Functional Departments (Startup Core)

OrgSmith organizes agents into realistic departments with clear outputs.

| Department | Lead Agent         | Specialist Roles                  | Primary Artifacts                         |
|-----------|--------------------|-----------------------------------|-------------------------------------------|
| Product   | Product Director    | Researcher, Analyst, Writer       | Product Briefs, User Stories, PRDs        |
| Tech      | Chief Tech Lead     | Backend, Frontend, Security       | System Design, API Specs, Code            |
| DevOps    | Cloud Architect     | CI/CD, SRE, Auditor               | Terraform, Deploy Logs, Secrets           |
| Data      | Data Director       | ETL, ML, Data Analyst             | Schemas, Validation Reports, Insights     |

---

## 5. Human-in-the-Loop: Avatar Mode

OrgSmith is built for **Founder-in-the-loop** collaboration, not full automation.

- **Hot-Swap Into Any Role**  
  The Founder can assume any agent’s role (e.g., Tech Lead, Product Director) at will.

- **State Preservation**  
  When a human takes over an agent:
  - The agent’s internal memory is surfaced as a **Context Briefing** in the UI  
  - The human continues with full situational awareness

- **Manual Override**  
  If the Founder answers a “Blocked” query (e.g., as Tech Lead), downstream Dev agents treat that input as an **Executive Order** and continue execution accordingly.

---

## 6. Telemetry & Artifact Generation

OrgSmith is designed to be observable and artifact-first.

- **Office Feed**  
  A real-time stream of filtered organizational activity: task events, escalations, approvals, and artifact creation.

- **Artifact-First Policy**  
  No agent may write code before there is a `.md` specification:
  - A superior must “sign off” on the spec before implementation
  - Encourages design-before-implementation discipline

- **Traceability**  
  Every file change is linked to:
  - A specific **Task ID**  
  - A specific **Artifact** (e.g., spec document)  
  - A specific **Agent** (human or AI)  

---

## 7. Success Metrics (Hackathon / Evaluation)

OrgSmith can be evaluated using these “org realism” tests:

- **Noise Test**  
  Can the Founder stay productive without being spammed by specialists for trivial issues?

- **Escalation Test**  
  Do critical failures reliably escalate to the Director and then to the Founder only when needed?

- **Artifact Test**  
  Does the organization produce a readable **Technical Design Document** *before* any code is written?

- **Execution Test**  
  Does the final repository (code + artifacts) match the original Product Brief?

---

## 8. Technical Stack

Current planned stack:

- **Orchestrator:** Python / FastAPI (state and workflow management)  
- **LLM:** Claude 3.5 Sonnet (strategic reasoning & tool use)  
- **Memory:** SQLite (persistent ledger) + Vector Store (long-term context)  
- **Frontend:** React + Tailwind (Mission Control dashboard)

---

## 9. Status & Roadmap

This repository currently contains:

- Initial documentation (`README.md`)  
- Infographic HTML prototypes (`index.html`, `newindex.html`)  

Planned next steps:

- Implement core orchestration loop with escalation logic  
- Define agent schemas, confidence scoring, and token accounting  
- Build minimal Mission Control dashboard  
- Integrate artifact-first workflow and traceability hooks  

---

## 10. License

TBD.  
Once a license is finalized, it will be added to this repository as `LICENSE`.
