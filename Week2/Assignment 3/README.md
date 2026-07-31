# 🪜 Week 2 · Assignment 3 — The Prompt Ladder
 
> AI Fluency Course 
 
---
 
## 🎯 Brief
 
Start with a genuinely weak prompt, improve it across five versions — one layer per version, no bundling — and compare each output against the last. Write four notes per version: what changed in the prompt, what actually improved in the output, what still failed, and what to try next. End with a final prompt a stranger could use without you in the room.
 
**Topic chosen:** explaining Python lists, tied to my FastAPI learning track.
 
---

## Baseline
 
**Prompt:** `Explain Python lists.`
 
**Output (excerpt):**
> A list is an ordered, mutable collection that can store items of different data types. Created using square brackets... Common operations: append(x), insert(i, x), remove(x), pop(i), sort(), len(list)...
 
Generic, textbook-level — the kind of answer you'd get from any programming FAQ, with no connection to what I'm actually building.
 
---
 
## Version 1 — Layer added: real context (backend development)
 
**Prompt:** `Explain Python lists for backend development.`
 
**Output (excerpt):**
> In backend systems, lists are commonly used to hold and process collections of data — API responses, database query results, request payloads... Example (Flask-style API): `active_users = [u for u in users if u.get("active", True)]`
 
**What improved in the output:** The explanation shifted from a general description to how lists are actually used in backend systems (API responses, batch processing, DB query results) — the content became situational instead of generic.
 
**What still failed:** It still explained backend concepts in the abstract. It never connected to a specific framework, so I couldn't picture where this fits into code I'd actually write.
 
**What I'd try next:** Add FastAPI as context, since that's the framework I'm learning.
 
---
