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
