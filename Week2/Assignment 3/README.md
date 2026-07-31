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

## Version 2 — Layer added: more specific real context (FastAPI)
 
**Prompt:** `Explain Python lists for backend development. I'm learning FastAPI.`
 
**Output (excerpt):**
> In FastAPI, lists are used heavily for request/response data, since FastAPI is built on Pydantic... `@app.post("/items/") def create_items(items: List[Item]): return {"count": len(items)}`
 
**What improved in the output:** The response now included FastAPI-specific examples (Pydantic models, request bodies, response_model, Query params) instead of generic backend talk — I could see exactly where lists show up in a FastAPI app.
 
**What still failed:** It assumed I already understood FastAPI basics like Pydantic models and route decorators, so parts of the explanation went over my head.
 
**What I'd try next:** Specify the audience — tell it I only know basic Python, not FastAPI internals.
 
---

## Version 3 — Layer added: defined audience
 
**Prompt:** `Explain Python lists for backend development. I'm learning FastAPI. Explain for someone who knows basic Python.`
 
**Output (excerpt):**
> Since you already know basic Python lists ([], indexing, loops, etc.), here's how that knowledge applies directly when building APIs with FastAPI... Simple mental model: Basic Python list = data stored in memory. FastAPI list = same data, but now traveling in/out of your API as JSON, with automatic validation.
 
**What improved in the output:** The response stopped assuming FastAPI knowledge and instead bridged from what I already knew (basic list operations) into each FastAPI use case step by step, with a "why this matters" recap at the end.
 
**What still failed:** The explanation was now correctly pitched, but it was long and code-heavy across three separate scenarios — there was no simple, minimal example to start from.
 
**What I'd try next:** Ask for simple examples to strip away the extra explanation and focus on minimal, runnable code.
 
---
## Version 4 — Layer added: specified output format (simple examples)
 
**Prompt:** `Explain using simple examples.`
 
**Output (excerpt):**
> 1. Basic list (Python, no FastAPI) — `fruits = ["apple", "banana", "cherry"]`
> 2. Receiving a list in a FastAPI request — minimal code + exact input/output shown
> 3. Returning a list from FastAPI
> 4. Query parameter as a list
 
**What improved in the output:** The output reorganized into short, numbered examples, each with the minimal code plus the exact input/output — much easier to scan and test than the previous prose-heavy version.
 
**What still failed:** It dropped the explicit "you already know basic Python" framing from Version 3 and didn't compare lists to any other data structure, so it wasn't clear when a list is the wrong choice.
 
**What I'd try next:** Ask for a table comparing lists to dictionaries, to clarify when to use each.
 
---


