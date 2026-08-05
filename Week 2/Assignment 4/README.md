# 🔁 Week 2 · Assignment 4 — Prompting Fundamentals on Real Tasks v2
 
> Prompt iteration log — target task: writing a README for a FastAPI CRUD project
 
---
 
## 🎯 Brief
 
Take one real task (not a toy example). Write the naive one-line prompt, save the output. Iterate five more versions, each applying one named technique. Run the final version on both Claude and ChatGPT and compare honestly. Distill everything into one reusable template.
 
---

## Prompt 0 — Naive Baseline
 
**Prompt:** `Write a README for my FastAPI project.`
 
**Output (excerpt):**
```markdown
# FastAPI CRUD API
A simple REST API built with FastAPI and Uvicorn for performing CRUD
(Create, Read, Update, Delete) operations on resources such as items or users.
## Features
- Create new records
- Retrieve a single record or a list of records
...
## License
MIT
```
 
The embarrassing baseline: generic, template-shaped, no sense of who the README is for or why the project exists.
 
---

## Prompt 1 — Role Assignment
 
**Prompt:** `You are an experienced backend developer. Write a README for my FastAPI project.`
 
**What improved:** The README became more opinionated and practical — it added a "Notes for contributors" section flagging real risks (no DB persistence, no auth) that a working developer would actually warn about, not just template filler.
 
**What still failed:** Still assumed generic endpoints and a generic project structure instead of my actual project, and gave no sense of why the project exists or who it's for.
 
---

## Prompt 2 — Context & Motivation
 
**Prompt:** `You are an experienced backend developer. I'm creating my first FastAPI CRUD API for my GitHub portfolio and to learn backend development. Write a professional README that is beginner-friendly and suitable for recruiters viewing my repository.`
 
**What improved:** The README stopped reading like generic software documentation and started reading like a portfolio piece — it added an "About This Project" section and a "What I Learned" section that speak directly to a recruiter's question of "what does this show me about the author," which no earlier version did.
 
**What still failed:** Section layout was still inconsistent with earlier versions (no fixed structure), and it still doesn't show real endpoints — this addressed tone and audience, not structure or specificity.
 
---
## Prompt 3 — Few-shot Example
 
**Prompt:** Added a minimal 4-section example (`Project Name / Features / Installation / Usage`) on top of Prompt 2, asking for the same style.
 
**What improved:** The output tightened up and matched the example's structure exactly — no wandering into extra sections, very scannable.
 
**⚠️ What still failed — the honest miss:** This is the version where a change made things *worse*. The example's minimal structure overrode the context layer: the "About This Project" and "What I Learned" sections from Prompt 2 disappeared entirely, even though the recruiter/portfolio framing was still in the prompt. Few-shot structure won out over stated context — showing an example is a stronger signal than describing intent.
 
---

## Prompt 4 — Output Structure
 
**Prompt:** Named the exact headers to return (`# Title`, `## Features`, `## Installation`, `## Endpoints`, `## Technologies`), replacing the loose few-shot example with an explicit structure.
 
**What improved:** The Endpoints section came back as a real table (lost since Prompt 1), and the structure became fully predictable — every run would return the same five sections in the same order.
 
**What still failed:** By naming only five sections, the portfolio-specific content from Prompt 2 (About This Project, What I Learned) got locked out again — explicit structure is even more restrictive than the few-shot example was, since now those sections aren't just unlikely, they're actively excluded unless listed.
 
---

## Prompt 5 — Step Decomposition (Final)
 
**Prompt:** Instead of asking for the README directly, broke the task into ordered stages — identify project → features → installation → usage → endpoints/technologies → assemble — then supplied the fixed structure from Prompt 4, on top of role and context.
 
**What improved:** This is the first version that kept *everything*: the portfolio framing from Prompt 2 survived alongside the full structure and a worked `curl` example — forcing the model through each stage before assembling stopped it from dropping sections the way Prompts 3 and 4 did.
 
**What still failed:** It's the longest, most verbose version — for a very small project this borders on over-documented, and a recruiter skimming for 10 seconds still has to scroll past setup detail to see the actual point of the project.
 
---

## 🤖 Cross-Model Comparison — Claude vs. ChatGPT
 
> ⏳ **Status: incomplete.** Prompt 5 has only been run on Claude so far. The assignment requires running the identical final prompt on ChatGPT and comparing honestly — this section will be filled in with real, specific differences once that's done, not left as a generic "both were fine."
 
| Dimension | Claude (Prompt 5 output) | ChatGPT |
|---|---|---|
| Tone | Practical, slightly conversational; frames the project's purpose in the first sentence | *pending* |
| Structure adherence | Followed the requested 7-section structure exactly, in order | *pending* |
| Accuracy | Endpoint table and example match the CRUD scope described; no invented tech | *pending* |
| Failure points | Runs long for a small project; installation still uses placeholder repo URL | *pending* |
 
---

 ## ✅ Final Reusable Prompt Template
 
Works for anyone documenting a small backend API project — swap the bracketed details.
 
```
Role:
You are an experienced backend developer.
 
Context:
I am creating a [FRAMEWORK] [PROJECT TYPE] project for [PURPOSE — e.g.
a GitHub portfolio, a work handoff, an open-source release].
 
Task:
Write a professional, beginner-friendly README suitable for [AUDIENCE —
e.g. recruiters, new contributors].
 
Requirements:
- Explain what the project does and why it exists in 1-2 sentences.
- Include clear installation steps.
- Include a usage example with expected output.
- List the API endpoints (if applicable) in a table.
- List the technologies/stack used.
- Keep language simple and avoid unexplained jargon.
 
Output Structure:
# Title
## Features
## Installation
## Usage
## Endpoints
## Technologies
## License
 
Work through the project's purpose, features, installation, and usage
step by step before assembling the final README.
```
 
---

## 📊 Ladder Summary
 
| Version | Technique | What it fixed | What it broke or missed |
|---|---|---|---|
| 0 | Naive baseline | — | Generic, no audience, no purpose |
| 1 | Role assignment | Added practical, opinionated detail (real risks) | Still generic project structure |
| 2 | Context & motivation | Added portfolio framing, "What I Learned" | No fixed structure, no real endpoints |
| 3 | Few-shot example | Tightened structure, very scannable | **Overrode context — lost the portfolio sections entirely** |
| 4 | Output structure | Endpoints returned as a real table, fully predictable | Locked out any section not explicitly named |
| 5 | Step decomposition | Kept structure *and* context *and* worked example together | Longest, most verbose version |

