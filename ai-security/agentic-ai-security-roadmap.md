# Agentic AI Security Roadmap (خارطة طريق أمن الذكاء الاصطناعي الوكيل)

*Study notes — AI Security. A self-study roadmap for Agentic AI Security, written in my own words and translated bilingually (English/Arabic), cross-referenced against [`ai-adaptive-active-defense-deception-system.md`](ai-adaptive-active-defense-deception-system.md) and the deeper write-up in my [`-AI-Security`](https://github.com/CyberHolicq8i/-AI-Security) repo.*

## What This Is (ما هو هذا الملف)

I came across a roadmap graphic for getting into Agentic AI Security and it matched almost exactly what I'm already trying to build toward through my [GRC & AI Governance portfolio](https://github.com/CyberHolicq8i/grc-ai-governance-portfolio) and my [AI Security](https://github.com/CyberHolicq8i/-AI-Security) work. So instead of just saving the image, I rewrote it as my own study roadmap — in my own words, mapped to what I've already learned, and translated into Arabic since that's the language I think through some of this in first.

This isn't a finished skillset. It's the map I'm studying against.

---

## Phase 1 — Cybersecurity Foundations (أساسيات الأمن السيبراني)

Before "AI security" means anything, the basics have to be solid:

- Networking: TCP/IP, HTTP, DNS
- Linux & Windows administration
- Authentication vs. authorization
- IAM / RBAC
- APIs & REST
- Web application security
- Cloud fundamentals
- Python

Everything downstream in this roadmap assumes this layer already exists. You can't secure an AI agent's tool calls if you don't understand what a tool call actually does at the network and OS level.

---

## Phase 2 — AI & LLM Fundamentals (أساسيات الذكاء الاصطناعي والنماذج اللغوية الكبيرة)

Understanding how the technology actually works, not just how to prompt it:

- LLMs, tokens, and context windows
- Embeddings and vector databases
- Retrieval-Augmented Generation (RAG)
- Function/tool calling
- System prompts
- Fine-tuning
- The difference between an "LLM application" and an "agent"
- Model inference

Tools worth getting hands-on with: Python, the OpenAI/Anthropic APIs, Hugging Face, Ollama.

---

## Phase 3 — Agent Architecture (بنية الوكلاء)

An agent isn't just a chatbot with extra steps. The pipeline looks like:

**User → LLM → Planner → Tools → Memory → Environment**

Study areas:

- Single-agent vs. multi-agent systems
- Agent memory
- Tool calling and MCP (Model Context Protocol)
- Agent orchestration
- Permissions and human-in-the-loop checkpoints
- Agent-to-agent communication

Frameworks to know: LangGraph, CrewAI, AutoGen, the OpenAI Agents SDK, MCP.

---

## Phase 4 — LLM Security (أمن النماذج اللغوية الكبيرة)

Before agent security, LLM security has to be understood on its own terms — this is the ground my [prompt-injection and RAG security note](https://github.com/CyberHolicq8i/-AI-Security/blob/main/01-Prompt-Injection-and-RAG-Security.md) already covers:

- Prompt injection and indirect prompt injection
- Jailbreaking
- Data leakage and sensitive information disclosure
- Insecure output handling
- Model poisoning and RAG poisoning
- Excessive agency
- Supply-chain attacks on AI components

Baseline reference: **OWASP GenAI Security**.

---

## Phase 5 — Agentic AI Threats (تهديدات الذكاء الاصطناعي الوكيل)

This is where LLM security and agent security stop being the same conversation. The **2026 OWASP Agentic Top 10** is the reference list I'm studying against:

| # | Risk | الخطر |
| --- | --- | --- |
| ASI01 | Agent Goal Hijack | اختطاف هدف الوكيل |
| ASI02 | Tool Misuse & Exploitation | إساءة استخدام الأدوات واستغلالها |
| ASI03 | Identity & Privilege Abuse | إساءة استخدام الهوية والصلاحيات |
| ASI04 | Agentic Supply Chain | سلسلة التوريد الخاصة بالوكلاء |
| ASI05 | Unexpected Code Execution | تنفيذ برمجي غير متوقع |
| ASI06 | Memory & Context Poisoning | تسميم الذاكرة والسياق |
| ASI07 | Insecure Inter-Agent Communication | اتصال غير آمن بين الوكلاء |
| ASI08 | Cascading Failures | أعطال متسلسلة |
| ASI09 | Human-Agent Trust Exploitation | استغلال الثقة بين الإنسان والوكيل |
| ASI10 | Rogue Agents | وكلاء منفلتون |

---

## Phase 6 — Agent Red Teaming (الاختبار الهجومي للوكلاء)

Learning to attack agents on purpose, so I understand what defending one actually requires. Attack surface areas: prompt injection, tool poisoning, tool parameter manipulation, privilege escalation, agent hijacking, memory poisoning, RAG poisoning, malicious MCP servers/tools, data exfiltration, code execution, cross-agent attacks, agent impersonation, and goal manipulation.

The lesson I took from this phase: don't just run a jailbreak checklist — build a full attack **chain**. Something like:

**Malicious document → RAG → Agent → Poisoned instruction → Privileged tool → Data exfiltration**

A chained scenario like that teaches far more than testing each weakness in isolation. It's the same chain-over-checklist thinking behind the deception-system concept in [`ai-adaptive-active-defense-deception-system.md`](ai-adaptive-active-defense-deception-system.md) — you learn more from tracing a full attacker path than from testing weaknesses one at a time.

---

## Phase 7 — Agent Defense (الدفاع عن الوكلاء)

Four pillars I'm organizing my defensive study around:

**Identity (الهوية):** least privilege, short-lived credentials, OAuth, RBAC/ABAC, service identities.

**Tool security (أمن الأدوات):** tool allowlists, parameter validation, sandboxing, capability restrictions, human approval for high-risk actions.

**Data (البيانات):** input/output validation, secrets management, DLP, encryption, RAG access controls.

**Agent runtime (بيئة تشغيل الوكيل):** behavioral monitoring, activity logging, kill switches, rate limits, action budgets, isolation.

---

## Phase 8 — Agent Security Engineering (هندسة أمن الوكلاء)

Moving this from theory toward something production-shaped:

- Secure agent architecture and threat modeling
- AI supply-chain security and model governance
- Secrets management, container security, Kubernetes security
- API security and cloud IAM
- CI/CD security
- Security testing and observability

Worth noting: NIST's current AI security work explicitly covers single- and multi-agent systems now — this has moved past being a purely theoretical research problem.

---

## Phase 9 — Agentic AI Detection & SOC (الكشف عن تهديدات الوكلاء ومركز العمليات الأمنية)

This phase matters most to me because of where I sit today — inspection and regulatory enforcement is already a detection mindset. Monitoring the pipeline **Agent → Tool → API → Data → Action**, watching for:

- Unusual tool call sequences
- Privilege escalation
- Abnormal API activity
- Prompt injection attempts
- Data exfiltration
- Agent-to-agent communication anomalies
- Suspicious code execution
- Memory modifications

Platforms to build detections in: Splunk, Microsoft Sentinel, Elastic, Wazuh.

---

## Phase 10 — Governance & Risk (الحوكمة والمخاطر)

This is the phase that overlaps most directly with my [GRC & AI Governance portfolio](https://github.com/CyberHolicq8i/grc-ai-governance-portfolio):

- NIST AI RMF and the NIST GenAI Profile
- OWASP Agentic Security
- AI governance and AI risk assessments
- AI inventory
- Model/vendor risk and third-party AI risk
- AI incident response
- Security policies
- Audit & compliance

The NIST GenAI Profile in particular pushes a **lifecycle-oriented** approach to managing generative-AI risk, not a one-time checklist — which matches how I already think about GRC.

---

## Projects I'm Using to Prove This Out (مشاريع لإثبات الفهم عمليًا)

Reading about this is not the same as building it. These are the projects on my list, roughly in the order I plan to tackle them:

1. **Secure single-agent assistant** — an agent with guardrails, tools, and memory that can search docs and answer questions safely.
2. **Multi-agent collaboration system** — a researcher/analyst/writer team of agents working a shared task.
3. **Agent memory & long-term recall** — short- and long-term memory using a vector DB plus summarization.
4. **Custom tool & MCP server** — build tools and an MCP server other agents can discover and use securely.
5. **Agent red-teaming lab** — a lab for testing prompt injection, tool misuse, memory poisoning, and privilege escalation.
6. **Agent defense framework** — input validation, output filtering, permissioning, and human approval for risky actions.
7. **Agent monitoring & observability** — dashboards and alerts for agent actions, tool calls, and API usage.
8. **RAG security project** — a RAG system with access controls, poisoning detection, and audit logs.
9. **Agent detection in a SIEM** — ingest agent logs into Splunk/Sentinel/Elastic/Wazuh and build actual detections.
10. **AI governance & risk dashboard** — track AI inventory, model risk, policy status, incidents, and compliance in one place.

---

## Key Takeaway (الخلاصة الأساسية)

The pattern that keeps showing up across every phase of this roadmap is the same one from my prompt-injection notes: AI security is never just "secure the model." It's classical cybersecurity fundamentals, applied to a pipeline that now includes retrieval, memory, tool calls, and autonomous action — plus a governance layer on top to answer for it when something goes wrong.

That's why I'm studying **Cybersecurity + AI/LLM Security + AI Governance** together instead of as three separate tracks.
