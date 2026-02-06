Product Requirements Document: OrgSmith (Final Edition)

Project Name: OrgSmith

Theme: Hierarchical AI Organizational Simulator & Execution Engine

Scale: Startup-Scale (5–25 Agents)

Target Audience: AI Founders, Technical Executives, Hackathon Judges

1. Executive Summary

OrgSmith is a high-fidelity organizational simulator that transforms AI agents into a structured engineering company. Unlike "agent swarms," OrgSmith uses human-centric hierarchy, token-based work shifts, and a rigorous Escalation Protocol. This protocol ensures that specialized problems are solved at the lowest possible level, protecting the human "Founder" from operational noise while maintaining full executive visibility.

2. Hierarchical Escalation & Communication Protocol (Nuance Layer)

To mimic a real-world company, OrgSmith enforces a filtered communication pipeline.

2.1 The Escalation Ladder

Level 1: Specialist Autonomy: Specialists (Devs, Analysts) attempt to solve tasks using their assigned tools and local memory.

Level 2: Peer Consultation: If a Specialist is stuck, they ping a Peer in their own 5-member team for a "Code Review" or "Collaborative Thought."

Level 3: Team Lead (TL) Intervention: If Peers cannot solve it, the task is flagged to the TL. The TL provides a "Strategic Correction" or "Architectural Decision."

Level 4: Departmental Director: If a block affects cross-department dependencies (e.g., Tech is blocked by DevOps), Directors sync.

Level 5: Founder (Executive Gate): The Director only interrupts the Founder if:

The Token Budget is depleted.

There is a "Strategic Pivot" required (Goal Conflict).

Multiple Directors reach a deadlock.

2.2 Gatekeeping & Filtering Mechanics

Confidence Scoring: Every agent includes a confidence_score (0.0 - 1.0) in their internal monologue. If the score is < 0.7, the agent must escalate.

The "Director Firewall": Directors summarize all specialist activity into "Daily Briefings." The Founder sees the summary by default; the raw logs are only accessible via a "Deep Dive" inquiry.

Notification Priority: * Low: Specialist task completion.

Medium: Lead-level peer review.

High: Director-level escalation (Requires Founder Attention).

3. Simulation Physics: Token-as-Hours

3.1 The "Work Day" Constraint

Shift Limit: 50,000 tokens per agent per "Shift."

Rest Period: Once the limit is hit, the agent enters IDLE_REPORTING state. They cannot execute tools until the Director (or Founder in Avatar Mode) approves the next shift's objectives.

Overhead Tax: Every escalation "costs" tokens (simulating communication overhead). This incentivizes agents to solve problems autonomously at Level 1.

4. Functional Departments (The Startup Core)

Department

Lead Agent

Specialist Roles

Artifacts Produced

Product

Product Director

Researcher, Analyst, Writer

Product Brief, User Stories, PRDs

Tech

Chief Tech Lead

Backend, Frontend, Security

System Design, API Specs, Code

DevOps

Cloud Architect

CI/CD, SRE, Auditor

Terraform, Deploy Logs, Secrets

Data

Data Director

ETL, ML, Analyst

Schemas, Validation, Insights

5. Human-in-the-Loop: Avatar Mode

The Founder can "Hot-Swap" into any role.

State Preservation: When a human takes over an agent, the AI's internal memory is loaded into the Human's UI as "Context Briefing."

Manual Override: The Founder can answer a "Blocked" query as the Tech Lead, and the downstream Dev agents will treat that input as an "Executive Order."

6. Real-Time Telemetry & Artifact Generation

The Office Feed: A real-time stream of filtered activity.

Artifact First Policy: No agent can write a line of code until a .md specification is produced and "Signed Off" by their superior.

Traceability: Every file change is linked back to a specific Task ID, a specific Artifact (Spec), and a specific Agent.

7. Success Metrics for Hackathon

The "Noise Test": Can the Founder stay productive without being pinged by specialists for trivial errors?

The "Escalation Test": Does a critical failure correctly bubble up to the Director?

The "Artifact Test": Does the org produce a readable "Technical Design Document" before the code exists?

The "Execution Test": Does the final repo match the original Product Brief?

8. Technical Stack

Orchestrator: Python/FastAPI (State Management).

LLM: Claude 3.5 Sonnet (Strategic Thinking & Tool Use).

Memory: SQLite (Persistent Ledger) + Vector Store (Long-term context).

Frontend: React/Tailwind (Mission Control Dashboard).

https://docs.google.com/document/d/1pBmGn8tg8333nOUXAwnSOSPJhL1_blqOWuDVvpSlhvo/edit?tab=t.0
